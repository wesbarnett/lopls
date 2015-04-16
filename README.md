# L-OPLS Force Field for GROMACS

James W. Barnett
jbarnet4@tulane.edu

This is a [GROMACS](http://www.gromacs.org) implementation of the L-OPLS
modifications to the OPLS-AA force field. I have added the few
parameters that were changed in some `if` statements such that if you include
`define = -DLOPLS` in your mdp files, then the LOPLS parameters will be used for
those that have changed. 

Note that the original `atomtype` numbers (prefixed
with `opls_`) can still be used, except for the methyl/methylene hydrogen
(`opls_140`). L-OPLS splits this up into two different atom types. In this case
`opls_140A` is the methyl hydrogen and `opls_140B` is the methylene hydrogen.
`opls_140` is then just used in the case of methane hydrogens.

To install, place the `oplsaa.ff` folder where GROMACS can find it, like in
a directory pointed to by the environmental variable `GMXLIB`:

    git clone git@github.com:wesbarnett/lopls.git
    cd lopls
    cp -r oplsaa.ff $GMXLIB/

Then include `oplsaa.ff/forcefield.itp` in your topology file as normal, except
add `define = -DLOPLS` to your mdp files when you want to use the modifications.

Additionally I've added [TIP4P2005](http://dx.doi.org/10.1063/1.2121687) and
[TIP4PEW](http://dx.doi.org/10.1063/1.1683075) water models to the force field
directory.

If you use the L-OPLS parameters be sure to read and cite the following in
addition to any OPLS papers:

* [S. W. I. Siu, K. Pluhackova, and R. A. Bockmann. J. Chem. Theory Comp., 8, 4 (2012)](http://dx.doi.org/10.1021/ct200908r)

## Disclaimer

I've done my best in transcribing and converting the parameters for usage with
GROMACS. That said, it is up to the user to ensure that the parameters are
correct and that simulations are set up according to the methods presented in
the papers above.
