---
title: "build error"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by anandnz on 2010-05-02
Hi experts,

I am trying configure celestial and starmap, but couldn't as i have bothered with following error

bodr:

elmer:
 Depends: libvtk5.2-qt4 but it is not going to be installed

gcu-bin:

gpiv:

gpiv-mpi:

gpivtools:
 Recommends: plotmtv  but it is not installable
  Conflicts: gpivtools-mpi  but 0.6.0-1build1 is to be installed

libnecpp0:

necpp:

proj:

proj-bin:

so i am trying to install Plotmtv1.4.4t, but i get following errors/


" quote "
~/Downloads/Plotmtv1.4.4t$ xmkmf -a Imakefile
mv -f Makefile Makefile.bak
imake -IImakefile/config/cf -DTOPDIR=Imakefile -DCURDIR=.
cc1: error: Imakefile/config/cf: Not a directory
imake: Exit code 1.
  Stop.

Please help
Thanks in advance
-- Anand

---

### Post by Diabolis on 2010-05-02
> 
Depends: libvtk5.2-qt4 but it is not going to be installed

Recommends: plotmtv but it is not installable
Conflicts: gpivtools-mpi but 0.6.0-1build1 is to be installed

Resolve that.
```

sudo apt-get install libvtk5.2-qt4 gpivtools-mpi

```

---

### Post by anandnz on 2010-05-02
Hi Diabolis.

Thank you, but i tried that already. I cannot remember until i go back home and try that but i got conflict errors. 

So i thought of resolving Plotmtv1.4.4, not sure if my approach is right.
Since i cannot update, Plotmtv1.4.4 software as it's not installed as the message said, i tried to build using xmkmf -a Imakefile, unfortunately these are the errors 

mv -f Makefile Makefile.bak
imake -IImakefile/config/cf -DTOPDIR=Imakefile -DCURDIR=.
cc1: error: Imakefile/config/cf: Not a directory
imake: Exit code 1.
  Stop.

Cheers
- Anand

---

### Post by anandnz on 2010-05-03
Hi Diabolis,

Thank you very much.  I think after i run the command again it certainly worked as it build something.
how syaptic Package Manager gave the following errors for science (universe) package update.
achilles:
bodr:
celestia-common:
elmer:
 Depends: libvtk5.2-qt4 but it is not going to be installed
gcu-bin:
gpiv:
gpiv-mpi:
gpivtools:
 Recommends: plotmtv  but it is not installable
  Conflicts: gpivtools-mpi  but 0.6.0-1build1 is to be installed
gpivtools-mpi:
 Recommends: plotmtv  but it is not installable
libnecpp0:
necpp:
proj:
proj-bin:

Help is appreciated.

Cheers
-- Anand

---

### Post by anandnz on 2010-05-04
Hi Experts,

I am trying to rephrase the above issue with me ..

I downloaded  Plotmtv1.4.4 and xmkmf utility and at the place of makefile, i run the command to generate makefile but i get the following error 
~/Downloads/Plotmtv1.4.4t$ xmkmf -a Imakefile
mv -f Makefile Makefile.bak
imake -IImakefile/config/cf -DTOPDIR=Imakefile -DCURDIR=.
cc1: error: Imakefile/config/cf: Not a directory
imake: Exit code 1.
  Stop.

2. So tried to make full make by leaving the printer options and compiler options undisturbed, assuming i have xdrivers in default place i have run the command mv -f Makefile Makefile.bak
imake -IImakefile/config/cf -DTOPDIR=Imakefile -DCURDIR=.
cc1: error: Imakefile/config/cf: Not a directory
imake: Exit code 1.
  Stop.

Now scratching my head for help.. Any help is appreciated. 
Thanks in Advance
-- Anand

---

### Post by anandnz on 2010-05-04
Hi 

I got this resolved by adding the repository of dapper in the repositories.
i have the said software installed 

But i am curious why i wasn't able to build not just plotmv but i could not ./configure and make the octave as well however i got old versions than the web downloaded by synaptic manager. Any ideas ??


cheers
- Anand

---

