---
title: "OpenFOAM- best tutorial?"
date: 2011-04-03
forum: New to Ubuntu
---

### Post by iskate2 on 2011-04-03
Hello everyone this is my first post in this forum.

I am an engineering student at UF and would like to learn OpenFOAM CFD. I have a dedicated ubuntu laptop that, with the help of a couple of more advanced users, I have installed OpenFOAM on. Now using it is a whole different story.

Can anyone recommend an online tutorial or user guide to aid in getting started? Much appreciation to anyone who can help!

---

### Post by dwhite on 2011-04-04
hi,

have been using OpenFOAM for a about  5 months now and i found it very helpful to work through the user guide from the OpenFOAM website at

[http://www.openfoam.com/docs/](http://www.openfoam.com/docs/)

i found the learning curve pretty steep, but short :D, you should be cranking out some solutions and writing your own meshes in pretty short order (my problems are pretty simple so i write the meshes right in openfoam but for more complicated situations you can import meshes from other mesh generating programs but i have no idea how that goes (although it's covered in the guide)

---

### Post by Sadiq Huq on 2011-10-27
Check out these video tutorials, The examples are explained in detail for the benefit of the beginners. Along the way, You will also learn how to use the official documentation. [comflics.blogspot.com]("http://www.comflics.blogspot.com")
Subscribe to the [youtube channel]("http://www.youtube.com/user/comflics/videos") for updates

---

### Post by mmkr825 on 2012-08-30
Hi everyone,
[LEFT]                          I am fresher to OpenFOAM,  and i developed my  own solver for predicting velocity profile and  particle concentration profile for suspension flow (for steady state).  And in my momentum equation, the viscosity is not constant, it is  function of particle volume fraction. 
[/LEFT]
          And i written the momentum equation as follows:
    [B]
    tmp<fvVectorMatrix> UEqn
    (
        fvm::div(phi, U)
      - fvm::laplacian(nu*pow(1-T/0.68,-1.82), U)
    );
     UEqn().relax();

    sources.constrain(UEqn());

    solve(UEqn() == -fvc::grad(p));[/B]

where T is the particle volume fraction (dimensionless scalar field).

For predicting particle volume fraction, the governing equation written as:

[B]solve
    (
        fvm::div(phi, T)
      - fvm::laplacian(0.62*pow(a,2)*mag(symm(fvc::grad(U)  ))*pow(T,2)*pow(0.68-T,-1), T)
    );[/B]

And i used SIMPLE scheme for pressure velocity coupling. I checked dimensions.   
When i use the **wmake** command it is compiling with no errors (i  think  there is no error in the solver). But when i  run my case using   solver the error message coming like as follows, 
[B][U]
error message:-[/U][/B]

[I]Create time

Create mesh for time = 0

Reading transportProperties

Reading field p

Reading field U

Reading field T

Reading/calculating face flux field phi

No field sources present


SIMPLE: convergence criteria
    field p     tolerance 0.01
    field U     tolerance 0.001
    field T     tolerance 1e-05


Starting time loop

Time = 1

DILUPBiCG:  Solving for Ux, Initial residual = 1, Final residual = 4.00548e-06, No Iterations 4
DILUPBiCG:  Solving for Uy, Initial residual = 0, Final residual = 0, No Iterations 0
#0  Foam::errorprintStack(Foam::Ostream&) in "/opt/openfoam211/platforms/linuxGccDPOpt/lib/libOpenFOAM.so"
#1  Foam::sigFpe::sigHandler(int) in "/opt/openfoam211/platforms/linuxGccDPOpt/lib/libOpenFOAM.so"
#2  Uninterpreted: 
#3  FoamDILUPreconditioner::calcReciprocalD(Foam::Fi    eld<double>&, Foam::lduMatrix const&) in   "/opt/openfoam211/platforms/linuxGccDPOpt/lib/libOpenFOAM.so"
#4  FoamDILUPreconditionerDILUPreconditioner(Foam:   :lduMatrix::solver  const&, Foam::dictionary const&) in   "/opt/openfoam211/platforms/linuxGccDPOpt/lib/libOpenFOAM.so"
#5  Foam::lduMatrixpreconditioner::addasymMatrixCons   tructorToTable<FoamDILUPreconditioner>::New(Foam    ::lduMatrix::solver const&, Foam::dictionary const&) in   "/opt/openfoam211/platforms/linuxGccDPOpt/lib/libOpenFOAM.so"
#6  Foam::lduMatrixpreconditioner::New(Foam::lduMatr   ix::solver  const&, Foam::dictionary const&) in   "/opt/openfoam211/platforms/linuxGccDPOpt/lib/libOpenFOAM.so"
#7  FoamPBiCG::solve(Foam::Field<double>&,   Foam::Field<double> const&, unsigned char) const in   "/opt/openfoam211/platforms/linuxGccDPOpt/lib/libOpenFOAM.so"
#8  Foam::fvMatrix<double>::solve(Foam::dictionary const&) in   "/opt/openfoam211/platforms/linuxGccDPOpt/lib/libfiniteVolume.so"
#9  Foam::fvMatrix<double>::solve() in   "/home/malli_reddy/OpenFOAM/malli_reddy-2.1.1/platforms/linuxGccDPOpt/bin/myDiffusiveFoam"
#10  
 in "/home/malli_reddy/OpenFOAM/malli_reddy-2.1.1/platforms/linuxGccDPOpt/bin/myDiffusiveFoam"
#11  __libc_start_main in "/lib/i386-linux-gnu/libc.so.6"
#12  
 in "/home/malli_reddy/OpenFOAM/malli_reddy-2.1.1/platforms/linuxGccDPOpt/bin/myDiffusiveFoam"
Floating point exception
_malli_reddy@ubuntu:~/OpenFOAM/malli_reddy-2.1.1/PROJECT/myDiffusive$ _

          [/I][B]can anyone suggest me what is the error and how to rectify it.
                                               thank you.[/B]

---

