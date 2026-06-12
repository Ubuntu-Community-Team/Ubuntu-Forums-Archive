---
title: "how to install IE4Linux on Ubuntu 8.10"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by manuleka on 2009-01-18
i'm wanting to install IE4Linux on Ubuntu 8.10 but can't find any guide to this... i know there has been giude for previous versions but i just wanna be sure before i apply or go through the same process... 

cheers for any help

---

### Post by jgoguen on 2009-01-18
Go to **System -> Administration -> Software Sources** and make sure that **Community-maintained Open Source software (universe)** is checked.  Then, under the **Third-Party Software** tab, make sure there's a line that contains:
```
http://wine.budgetdedicated.com/apt intrepid main
```If not, click the **Add** button and add paste this line into the box:
```
deb http://wine.budgetdedicated.com/apt intrepid main
```Push the **Close** button.  Then, go to **System -> Administration -> Synaptic Package Manager** and install the **cabextract** and **wine** packages.

Now, open a terminal (Applications -> Accessories -> Terminal) and enter each command, pushing Enter after each one:
```
wget http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz
``````
tar zxvf ies4linux-latest.tar.gz
``````
cd ies4linux-*
``````
./ies4linux
```From there, choose the options you want and install.  If the installer crashes on you, just re-enter the last command, choose the same options, and carry on.

---

### Post by manuleka on 2009-01-19
installation keeps getting error... so i give up :( 

90%  HHUPD.CAB!! An error ocurred when downloading. Please run IEs4Linux again. Corrupted file: ie6/EN-US/HHUPD.CAB

---

### Post by jgoguen on 2009-01-19
Try removing ~/.ies4linux/ (**rm -r ~/.ies4linux/**) and run it again.  The installer picks up where it left off, which may mean that the corrupted file doesn't get replaced.

---

### Post by halovivek on 2009-01-19
> **manuleka said:**
> installation keeps getting error... so i give up :( 

90%  HHUPD.CAB!! An error ocurred when downloading. Please run IEs4Linux again. Corrupted file: ie6/EN-US/HHUPD.CAB

Guide for installing ie4linux on Ubuntu
1.You need to install Wine and Cabextract.If your source doesn&#8217;t contain Wine and Cabextract,you can add this source:
Run sudo gedit /etc/apt/sources.list
and then add below two lines to your sources.list:

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty universe
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main

Run :

sudo apt-get update
sudo apt-get install wine
sudo apt-get install cabextract

2.installing the ie4linux:

(1)Download the source files by run: wget [http://www.tatanka.com.br/ies4linux/downloads/ies4linux-2.0.tar.gz](http://www.tatanka.com.br/ies4linux/downloads/ies4linux-2.0.tar.gz) -O - | tar xvzf -

If above address is unsuccessful,you also can try this :

wget [http://modzer0.cs.uaf.edu/~hardwarehank/files/ies4linux-2.0.tar.gz](http://modzer0.cs.uaf.edu/~hardwarehank/files/ies4linux-2.0.tar.gz) -O - | tar xvzf -

(2)and then run:

cd ies4linux-2.0
./ies4linux

(3)the installation is begining once you run ./ies4linux.You need to answer severl question during installation:

the fist question is that:

Welcome, ray! I&#8217;m IEs4Linux.
I can install IE 6, 5.5 and 5.0 for you easily and quickly.
You are just four &#8216;enter&#8217;s away from your IEs.
I&#8217;ll ask you some questions now. Just answer y or n (default answer is the bold one)

so don&#8217;t estate,just select IE6 and then press &#8220;ENTER&#8221; :)

the sencond question is :

Do you want to install IE 5.5 SP2 too? [ y / n ]
And do you want to install IE 5.01 SP2? [ y / n ]

as seldom people use IE 5.5,i believe,I choosed NO

the third question is :

IEs can be installed using one of the following locales:
EN-US PT-BR DE FR ES IT NL SV JA KO NO
DA CN TW FI PL HU AR HE CS PT RU EL TR
Default is . Hit enter to keep it or choose a different one:

Choose the locale you want.

(4)once you have selected the lacate,installing procees is done,and then you can run the ie4linux by this command on terminal:

/home/ray/bin/ie6

Enjoy!



you can try from these links
[link1]("http://yourubuntulinux.blogspot.com/2007/12/how-to-install-ie4linux-on-ubuntu-710.html")
[link2]("http://www.wonderhowto.com/how-to/video/how-to-install-ie4linux-on-ubuntu-linux-184056/")
i have installed and it is working fine.

---

### Post by jgoguen on 2009-01-19
Some of this is out of date or not correct for the OP's request:

> **halovivek said:**
> Guide for installing ie4linux on Ubuntu
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty universe
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main
OP is running 8.10, so this should read **intrepid**, not **feisty**.

> **halovivek said:**
> (1)Download the source files by run: wget [http://www.tatanka.com.br/ies4linux/downloads/ies4linux-2.0.tar.gz](http://www.tatanka.com.br/ies4linux/downloads/ies4linux-2.0.tar.gz) -O - | tar xvzf -

If above address is unsuccessful,you also can try this :

wget [http://modzer0.cs.uaf.edu/~hardwarehank/files/ies4linux-2.0.tar.gz]("http://modzer0.cs.uaf.edu/%7Ehardwarehank/files/ies4linux-2.0.tar.gz") -O - | tar xvzf -

(2)and then run:

cd ies4linux-2.0
./ies4linux
There is a later version available.  Users should always (always always always always, without a really good reason to do otherwise) download from  [FONT=monospace][/FONT]http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz instead, as this will always point to the latest available version.

> **halovivek said:**
> (3)the installation is begining once you run ./ies4linux.You need to answer severl question during installation:
This is no longer the case when using **./ies4linux** to do the install.  If you choose the option for no GUI, then these may be asked (but I don't believe so, I can't remember) but the command you and I both specified will display a graphical interface rather than asking questions.

> **halovivek said:**
> /home/ray/bin/ie6
Please be sure to remind users to replace *ray* with their own username.  It seems obvious, and sometimes I forget to put that reminder myself, but it is something to make sure to say so people stop and think to change instead of just copying and pasting like they would have been doing for all previous commands.

> **halovivek said:**
> you can try from these links
The first link has similarly out of date information with regards to the repository information.  The rest of it seems fine, but anyone going to these links should be warned to replace **gutsy** with the correct version - for the OP, that would be **intrepid**.  I don't know about the second one, it seems to be a video and I couldn't view it.

---

### Post by manuleka on 2009-01-19
> **jgoguen said:**
> Try removing ~/.ies4linux/ (**rm -r ~/.ies4linux/**) and run it again.  The installer picks up where it left off, which may mean that the corrupted file doesn't get replaced.

now it wouldn't download error corruption at 0% :(

---

### Post by jgoguen on 2009-01-19
OK, well what do you need installed?  Maybe I can construct a gui-less command for you, that may help.  Do you need only IE6, or do you need 7 as well?  I've never gotten 7 to work properly...  Answer a few questions and I'll see what I can do:

Do you need only IE6, or do you also need other versions (5, 5.5, or 7)?
Do you need Flash installed?
Do you want icons on your desktop, menu, or both?

---

### Post by manuleka on 2009-01-19
> **jgoguen said:**
> OK, well what do you need installed?  Maybe I can construct a gui-less command for you, that may help.  Do you need only IE6, or do you need 7 as well?  I've never gotten 7 to work properly...  Answer a few questions and I'll see what I can do:

Do you need only IE6, or do you also need other versions (5, 5.5, or 7)?
Do you need Flash installed?
Do you want icons on your desktop, menu, or both?

thanks

i need IE6 Only
i do need Flash installed
i do need icon on desktop and menu

thanks again for your help :)

---

### Post by jgoguen on 2009-01-19
Alright, run this command in the same place you ran **./ies4linux** before.

```
./ies4linux --no-gui --install-corefonts
```

This will print everything out to the terminal window instead of displaying a GUI.  I find that this way doesn't have as many problems.

---

### Post by manuleka on 2009-01-19
> **jgoguen said:**
> Alright, run this command in the same place you ran **./ies4linux** before.

```
./ies4linux --no-gui --install-corefonts
```

This will print everything out to the terminal window instead of displaying a GUI.  I find that this way doesn't have as many problems.

Goes further than before but now i get stuck here:

> 
IEs4Linux will:
  - Install Internet Explorers: 6.0
  - Using IE locale: EN-US
  - Install Adobe Flash 9.0
  - Install MS Core Fonts
  - Install everything at: /home/manu/.ies4linux
[ OK ]

Downloading everything we need
  Downloading from microsoft.com:
   DCOM98.EXE
   mfc42.cab
   249973USA8.exe
   ADVAUTH.CAB
   CRLUPD.CAB
   100% HHUPD.CAB
   100% IEDOM.CAB
   100% IE_EXTRA.CAB
   40%  IE_S1.CABAn error ocurred when downloading. Please run IEs4Linux again. Corrupted file: ie6/EN-US/IE_S1.CAB

---

### Post by jgoguen on 2009-01-19
Please remove ~/.ies4linux/ (**rm -r ~/.ies4linux/**) and re-run with the **--debug** option:
```
./ies4linux --no-gui --install-corefonts --debug
```
Paste the output if it fails again.  That will let us know why that file failed (size and/or MD5 mismatch).

---

### Post by manuleka on 2009-01-19
hi here's the result

> 
manu@wind:~/ies4linux-2.99.0.1$ ./ies4linux --no-gui --install-corefonts --debugIEs4Linux 2 is developed to be used with recent Wine versions (0.9.x). It seems that you are using an old version. It's recommended that you update your wine to the latest version (Go to: winehq.com).

DEBUG: Hi, I'm Linux
IEs4Linux will:
  - Install Internet Explorers: 6.0
  - Using IE locale: EN-US
  - Install Adobe Flash 9.0
  - Install MS Core Fonts
  - Install everything at: /home/manu/.ies4linux
[ OK ]

Downloading everything we need
  Downloading from microsoft.com:
   DCOM98.EXE
DEBUG: DCOM98.EXE: correctsize 1229056 correctmd5 9a7bc7ff37168217123a5e28aadef897
DEBUG: DCOM98.EXE: size 1229056 md5 9a7bc7ff37168217123a5e28aadef897
   mfc42.cab
DEBUG: mfc42.cab: correctsize 632755 correctmd5 fbe551338463f13c6a5e215db55ac21b
DEBUG: mfc42.cab: size 632755 md5 fbe551338463f13c6a5e215db55ac21b
   249973USA8.exe
DEBUG: 249973USA8.exe: correctsize 838328 correctmd5 069c9efff9e21793ef60c445c36c5509
DEBUG: 249973USA8.exe: size 838328 md5 069c9efff9e21793ef60c445c36c5509
   ADVAUTH.CAB
DEBUG: ie6/EN-US/ADVAUTH.CAB: correctsize 47213 correctmd5 9e5b306f34c1494867c96d5d9f5cbdbf
DEBUG: ie6/EN-US/ADVAUTH.CAB: size 47213 md5 9e5b306f34c1494867c96d5d9f5cbdbf
   CRLUPD.CAB
DEBUG: ie6/EN-US/CRLUPD.CAB: correctsize 12984 correctmd5 fda9426f6277fdb1f60bb9d4b423c8b0
DEBUG: ie6/EN-US/CRLUPD.CAB: size 12984 md5 fda9426f6277fdb1f60bb9d4b423c8b0
   HHUPD.CAB
DEBUG: ie6/EN-US/HHUPD.CAB: correctsize 704025 correctmd5 7bb5797d4b003dfac817baf767aa9433
DEBUG: ie6/EN-US/HHUPD.CAB: size 704025 md5 7bb5797d4b003dfac817baf767aa9433
   IEDOM.CAB
DEBUG: ie6/EN-US/IEDOM.CAB: correctsize 110162 correctmd5 9c3824c4f8b7fe9f99f54710ba961134
DEBUG: ie6/EN-US/IEDOM.CAB: size 110162 md5 9c3824c4f8b7fe9f99f54710ba961134
   IE_EXTRA.CAB
DEBUG: ie6/EN-US/IE_EXTRA.CAB: correctsize 141680 correctmd5 5519735dd00440485fa8bace656e139b
DEBUG: ie6/EN-US/IE_EXTRA.CAB: size 141680 md5 5519735dd00440485fa8bace656e139b
   0%   IE_S1.CABtouch: cannot touch `/home/manu/.ies4linux/downloads/ie6/EN-US/IE_S1.CAB': Permission denied
DEBUG: Download PID=9507
An error ocurred when downloading. Please run IEs4Linux again. Corrupted file: ie6/EN-US/IE_S1.CAB


does the first few lines say that it can't recognize wine 1? i'm currently using wine 1.0.1 

is ies4linux only compatible with wine 0.9.x?

---

### Post by jgoguen on 2009-01-20
No, that's an error in how they're checking the WINE version.  I use WINE 1.1.13 with it.  The error at the end suggests that it can't create the file that it's complaining about.  Try running these commands.  If any of them gives you an error, stop and tell us which one and post all your output.  Do these from the same place you ran my last command.
```
rm -rf ~/.ies4linux/
mkdir -p /home/manu/.ies4linux/downloads/ie6/EN-US/
touch /home/manu/.ies4linux/downloads/ie6/EN-US/IE_S1.CAB[FONT=monospace]
[/FONT]./ies4linux --no-gui --install-corefonts --debug
```

---

### Post by manuleka on 2009-01-20
manu@wind:~/ies4linux-2.99.0.1$  ./ies4linux --no-gui --install-corefonts -debug
IEs4Linux 2 is developed to be used with recent Wine versions (0.9.x). It seems that you are using an old version. It's recommended that you update your wine to the latest version (Go to: winehq.com).

Error: unknown option "-debug"
run "./ies4linux --help" for more info
manu@wind:~/ies4linux-2.99.0.1$

---

### Post by jgoguen on 2009-01-20
You mis-typed that last command: it should be **--debug** (two dashes) and you accidentally missed one.  Try running that one again with the extra dash and see how it goes.

---

### Post by manuleka on 2009-01-21
```

manu@wind:~/ies4linux-2.99.0.1$ ./ies4linux --no-gui --install-corefonts --debugIEs4Linux 2 is developed to be used with recent Wine versions (0.9.x). It seems that you are using an old version. It's recommended that you update your wine to the latest version (Go to: winehq.com).

DEBUG: Hi, I'm Linux
IEs4Linux will:
  - Install Internet Explorers: 6.0
  - Using IE locale: EN-US
  - Install Adobe Flash 9.0
  - Install MS Core Fonts
  - Install everything at: /home/manu/.ies4linux
[ OK ]

Downloading everything we need
  Downloading from microsoft.com:
   0%   DCOM98.EXEDEBUG: Download PID=10737
   17%  DCOM98.EXEAn error ocurred when downloading. Please run IEs4Linux again. Corrupted file: DCOM98.EXE

manu@wind:~/ies4linux-2.99.0.1$

```
when i run the command again it seem to continue downloading from 17% then stopped at some point on 86% so i rerun the command again and it continued from there ??

```

manu@wind:~/ies4linux-2.99.0.1$ ./ies4linux --no-gui --install-corefonts --debugIEs4Linux 2 is developed to be used with recent Wine versions (0.9.x). It seems that you are using an old version. It's recommended that you update your wine to the latest version (Go to: winehq.com).

DEBUG: Hi, I'm Linux
IEs4Linux will:
  - Install Internet Explorers: 6.0
  - Using IE locale: EN-US
  - Install Adobe Flash 9.0
  - Install MS Core Fonts
  - Install everything at: /home/manu/.ies4linux
[ OK ]

Downloading everything we need
  Downloading from microsoft.com:
   0%   DCOM98.EXEDEBUG: Download PID=12459
   83%  DCOM98.EXEAn error ocurred when downloading. Please run IEs4Linux again. Corrupted file: DCOM98.EXE

manu@wind:~/ies4linux-2.99.0.1$ ./ies4linux --no-gui --install-corefonts --debugIEs4Linux 2 is developed to be used with recent Wine versions (0.9.x). It seems that you are using an old version. It's recommended that you update your wine to the latest version (Go to: winehq.com).

DEBUG: Hi, I'm Linux
IEs4Linux will:
  - Install Internet Explorers: 6.0
  - Using IE locale: EN-US
  - Install Adobe Flash 9.0
  - Install MS Core Fonts
  - Install everything at: /home/manu/.ies4linux
[ OK ]

Downloading everything we need
  Downloading from microsoft.com:
   0%   DCOM98.EXEDEBUG: Download PID=14488
   100% DCOM98.EXE
DEBUG: DCOM98.EXE: correctsize 1229056 correctmd5 9a7bc7ff37168217123a5e28aadef897
DEBUG: DCOM98.EXE: size 1229056 md5 9a7bc7ff37168217123a5e28aadef897
   0%   mfc42.cabDEBUG: Download PID=14864
   100% mfc42.cab
DEBUG: mfc42.cab: correctsize 632755 correctmd5 fbe551338463f13c6a5e215db55ac21b
DEBUG: mfc42.cab: size 632755 md5 fbe551338463f13c6a5e215db55ac21b
   0%   249973USA8.exeDEBUG: Download PID=16352
   100% 249973USA8.exe
DEBUG: 249973USA8.exe: correctsize 838328 correctmd5 069c9efff9e21793ef60c445c36c5509
DEBUG: 249973USA8.exe: size 838328 md5 069c9efff9e21793ef60c445c36c5509
   0%   ADVAUTH.CABDEBUG: Download PID=17887
   100% ADVAUTH.CAB
DEBUG: ie6/EN-US/ADVAUTH.CAB: correctsize 47213 correctmd5 9e5b306f34c1494867c96d5d9f5cbdbf
DEBUG: ie6/EN-US/ADVAUTH.CAB: size 47213 md5 9e5b306f34c1494867c96d5d9f5cbdbf
   0%   CRLUPD.CABDEBUG: Download PID=18015
   100% CRLUPD.CAB
DEBUG: ie6/EN-US/CRLUPD.CAB: correctsize 12984 correctmd5 fda9426f6277fdb1f60bb9d4b423c8b0
DEBUG: ie6/EN-US/CRLUPD.CAB: size 12984 md5 fda9426f6277fdb1f60bb9d4b423c8b0
   0%   HHUPD.CABDEBUG: Download PID=18071
   100% HHUPD.CAB
DEBUG: ie6/EN-US/HHUPD.CAB: correctsize 704025 correctmd5 7bb5797d4b003dfac817baf767aa9433
DEBUG: ie6/EN-US/HHUPD.CAB: size 704025 md5 7bb5797d4b003dfac817baf767aa9433
   0%   IEDOM.CABDEBUG: Download PID=19356
   100% IEDOM.CAB
DEBUG: ie6/EN-US/IEDOM.CAB: correctsize 110162 correctmd5 9c3824c4f8b7fe9f99f54710ba961134
DEBUG: ie6/EN-US/IEDOM.CAB: size 110162 md5 9c3824c4f8b7fe9f99f54710ba961134
   0%   IE_EXTRA.CABDEBUG: Download PID=19590
   100% IE_EXTRA.CAB
DEBUG: ie6/EN-US/IE_EXTRA.CAB: correctsize 141680 correctmd5 5519735dd00440485fa8bace656e139b
DEBUG: ie6/EN-US/IE_EXTRA.CAB: size 141680 md5 5519735dd00440485fa8bace656e139b
   0%   IE_S1.CABDEBUG: Download PID=19892
   100% IE_S1.CAB
DEBUG: ie6/EN-US/IE_S1.CAB: correctsize 1525813 correctmd5 f83fa15c6af002077acb90bc09ed73e7
DEBUG: ie6/EN-US/IE_S1.CAB: size 1525813 md5 f83fa15c6af002077acb90bc09ed73e7
   0%   IE_S2.CABDEBUG: Download PID=22631
   29%  IE_S2.CABAn error ocurred when downloading. Please run IEs4Linux again. Corrupted file: ie6/EN-US/IE_S2.CAB

manu@wind:~/ies4linux-2.99.0.1$ ./ies4linux --no-gui --install-corefonts --debugIEs4Linux 2 is developed to be used with recent Wine versions (0.9.x). It seems that you are using an old version. It's recommended that you update your wine to the latest version (Go to: winehq.com).

DEBUG: Hi, I'm Linux
IEs4Linux will:
  - Install Internet Explorers: 6.0
  - Using IE locale: EN-US
  - Install Adobe Flash 9.0
  - Install MS Core Fonts
  - Install everything at: /home/manu/.ies4linux
[ OK ]

Downloading everything we need
  Downloading from microsoft.com:
   DCOM98.EXE
DEBUG: DCOM98.EXE: correctsize 1229056 correctmd5 9a7bc7ff37168217123a5e28aadef897
DEBUG: DCOM98.EXE: size 1229056 md5 9a7bc7ff37168217123a5e28aadef897
   mfc42.cab
DEBUG: mfc42.cab: correctsize 632755 correctmd5 fbe551338463f13c6a5e215db55ac21b
DEBUG: mfc42.cab: size 632755 md5 fbe551338463f13c6a5e215db55ac21b
   249973USA8.exe
DEBUG: 249973USA8.exe: correctsize 838328 correctmd5 069c9efff9e21793ef60c445c36c5509
DEBUG: 249973USA8.exe: size 838328 md5 069c9efff9e21793ef60c445c36c5509
   ADVAUTH.CAB
DEBUG: ie6/EN-US/ADVAUTH.CAB: correctsize 47213 correctmd5 9e5b306f34c1494867c96d5d9f5cbdbf
DEBUG: ie6/EN-US/ADVAUTH.CAB: size 47213 md5 9e5b306f34c1494867c96d5d9f5cbdbf
   CRLUPD.CAB
DEBUG: ie6/EN-US/CRLUPD.CAB: correctsize 12984 correctmd5 fda9426f6277fdb1f60bb9d4b423c8b0
DEBUG: ie6/EN-US/CRLUPD.CAB: size 12984 md5 fda9426f6277fdb1f60bb9d4b423c8b0
   HHUPD.CAB
DEBUG: ie6/EN-US/HHUPD.CAB: correctsize 704025 correctmd5 7bb5797d4b003dfac817baf767aa9433
DEBUG: ie6/EN-US/HHUPD.CAB: size 704025 md5 7bb5797d4b003dfac817baf767aa9433
   IEDOM.CAB
DEBUG: ie6/EN-US/IEDOM.CAB: correctsize 110162 correctmd5 9c3824c4f8b7fe9f99f54710ba961134
DEBUG: ie6/EN-US/IEDOM.CAB: size 110162 md5 9c3824c4f8b7fe9f99f54710ba961134
   IE_EXTRA.CAB
DEBUG: ie6/EN-US/IE_EXTRA.CAB: correctsize 141680 correctmd5 5519735dd00440485fa8bace656e139b
DEBUG: ie6/EN-US/IE_EXTRA.CAB: size 141680 md5 5519735dd00440485fa8bace656e139b
   IE_S1.CAB
DEBUG: ie6/EN-US/IE_S1.CAB: correctsize 1525813 correctmd5 f83fa15c6af002077acb90bc09ed73e7
DEBUG: ie6/EN-US/IE_S1.CAB: size 1525813 md5 f83fa15c6af002077acb90bc09ed73e7
   0%   IE_S2.CABDEBUG: Download PID=23952
   29%  IE_S2.CABAn error ocurred when downloading. Please run IEs4Linux again. Corrupted file: ie6/EN-US/IE_S2.CAB

manu@wind:~/ies4linux-2.99.0.1$ ./ies4linux --no-gui --install-corefonts --debugIEs4Linux 2 is developed to be used with recent Wine versions (0.9.x). It seems that you are using an old version. It's recommended that you update your wine to the latest version (Go to: winehq.com).

DEBUG: Hi, I'm Linux
IEs4Linux will:
  - Install Internet Explorers: 6.0
  - Using IE locale: EN-US
  - Install Adobe Flash 9.0
  - Install MS Core Fonts
  - Install everything at: /home/manu/.ies4linux
[ OK ]

Downloading everything we need
  Downloading from microsoft.com:
   DCOM98.EXE
DEBUG: DCOM98.EXE: correctsize 1229056 correctmd5 9a7bc7ff37168217123a5e28aadef897
DEBUG: DCOM98.EXE: size 1229056 md5 9a7bc7ff37168217123a5e28aadef897
   mfc42.cab
DEBUG: mfc42.cab: correctsize 632755 correctmd5 fbe551338463f13c6a5e215db55ac21b
DEBUG: mfc42.cab: size 632755 md5 fbe551338463f13c6a5e215db55ac21b
   249973USA8.exe
DEBUG: 249973USA8.exe: correctsize 838328 correctmd5 069c9efff9e21793ef60c445c36c5509
DEBUG: 249973USA8.exe: size 838328 md5 069c9efff9e21793ef60c445c36c5509
   ADVAUTH.CAB
DEBUG: ie6/EN-US/ADVAUTH.CAB: correctsize 47213 correctmd5 9e5b306f34c1494867c96d5d9f5cbdbf
DEBUG: ie6/EN-US/ADVAUTH.CAB: size 47213 md5 9e5b306f34c1494867c96d5d9f5cbdbf
   CRLUPD.CAB
DEBUG: ie6/EN-US/CRLUPD.CAB: correctsize 12984 correctmd5 fda9426f6277fdb1f60bb9d4b423c8b0
DEBUG: ie6/EN-US/CRLUPD.CAB: size 12984 md5 fda9426f6277fdb1f60bb9d4b423c8b0
   HHUPD.CAB
DEBUG: ie6/EN-US/HHUPD.CAB: correctsize 704025 correctmd5 7bb5797d4b003dfac817baf767aa9433
DEBUG: ie6/EN-US/HHUPD.CAB: size 704025 md5 7bb5797d4b003dfac817baf767aa9433
   IEDOM.CAB
DEBUG: ie6/EN-US/IEDOM.CAB: correctsize 110162 correctmd5 9c3824c4f8b7fe9f99f54710ba961134
DEBUG: ie6/EN-US/IEDOM.CAB: size 110162 md5 9c3824c4f8b7fe9f99f54710ba961134
   IE_EXTRA.CAB
DEBUG: ie6/EN-US/IE_EXTRA.CAB: correctsize 141680 correctmd5 5519735dd00440485fa8bace656e139b
DEBUG: ie6/EN-US/IE_EXTRA.CAB: size 141680 md5 5519735dd00440485fa8bace656e139b
   IE_S1.CAB
DEBUG: ie6/EN-US/IE_S1.CAB: correctsize 1525813 correctmd5 f83fa15c6af002077acb90bc09ed73e7
DEBUG: ie6/EN-US/IE_S1.CAB: size 1525813 md5 f83fa15c6af002077acb90bc09ed73e7
   0%   IE_S2.CABDEBUG: Download PID=24329
   29%  IE_S2.CABAn error ocurred when downloading. Please run IEs4Linux again. Corrupted file: ie6/EN-US/IE_S2.CAB

manu@wind:~/ies4linux-2.99.0.1$ 

```

---

### Post by wangsuda on 2009-01-22
> **jgoguen said:**
> Go to **System -> Administration -> Software Sources** and make sure that **Community-maintained Open Source software (universe)** is checked.  Then, under the **Third-Party Software** tab, make sure there's a line that contains:
```
http://wine.budgetdedicated.org/apt intrepid main
```
If not, click the **Add** button and add paste this line into the box:
```
deb http://wine.budgetdedicated.com/apt intrepid main
```Push the **Close** button.  Then, go to **System -> Administration -> Synaptic Package Manager** and install the **cabextract** and **wine** packages.

Now, open a terminal (Applications -> Accessories -> Terminal) and enter each command, pushing Enter after each one:
```
wget http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz
``````
tar zxvf ies4linux-latest.tar.gz
``````
cd ies4linux-*
``````
./ies4linux
```From there, choose the options you want and install.  If the installer crashes on you, just re-enter the last command, choose the same options, and carry on.

Thank you! This worked perfectly!

---

### Post by jgoguen on 2009-01-22
> **manuleka said:**
> when i run the command again it seem to continue downloading from 17% then stopped at some point on 86% so i rerun the command again and it continued from there ??
Yes, sorry, I could've sworn I mentioned that earlier...I feel dumb now :(  If a download fails, and you re-run the script, it will pick up where it left off.  It won't pick up at the same file location, if a download fails the file is removed before the script exits.

---

### Post by jgoguen on 2009-01-22
> **wangsuda said:**
> Thank you! This worked perfectly!
Glad to hear it :)

---

### Post by manuleka on 2009-01-22
thanks jgoguen

i kept re-running the ./ies4linux --no-gui --install-corefonts --debug

and it continued downloading untill after the IE_S*.CAB files then it continued till finish... 

now i've got the IE4Linux running great on my WIND :) 

i do get some error with the WINE link on my Software Sources though (everytime i run a system update check) - it's on this thread:
[http://ubuntuforums.org/showthread.php?t=1047079](http://ubuntuforums.org/showthread.php?t=1047079)

---

### Post by jgoguen on 2009-01-23
I replied there.  I think the errors may be because I screwed up the address in an earlier post here :(  It's fixed now, and the other thread has directions for how to fix it.  Import the GPG key, make the change I say, and you should be fine.  You may still see the error about the Translation file not being found, but that's OK.

---

### Post by manuleka on 2009-01-25
again thanks jgoguen :) everything is fixed for now :) your help has been muchly appreciated

---

### Post by jgoguen on 2009-01-25
Not a problem.  Glad to hear it's all working well for you :D

---

