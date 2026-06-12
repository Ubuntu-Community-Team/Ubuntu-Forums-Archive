---
title: "Can't install pianobar through terminal: source?"
date: 2010-12-29
forum: New to Ubuntu
---

### Post by damien750 on 2010-12-29
Hey there, I'm sure there's a basic way to fix this, but it's beyond me. I've run searches but apparently this is so basic, everyone (but me) already knows.

I'm trying to install pianobar (pandora player) via terminal. 

When I try to apt-get the program, this is what happens.

```
damien@tenuki:~$ sudo apt-get install pianobar
[sudo] password for damien: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package pianobar
damien@tenuki:~$ 

```

Is there some way I tell the terminal where to look online to find the pianobar program? I know some apt-get commands work right out of a fresh install, so what do I need to change?

---

### Post by Windows Nerd on 2010-12-29
It does not seem to be in the repositories, I have forgotten how to search for packages via commandline (due to me using arch all the time now), but a quick Google seach should tell you how.

Anyways, since it is not in the repos, you will have to build it from source. There is a thread on these very forums detailing this in a nice how-to:

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1533357](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1533357)

I found this with a quick Google search. I kindly ask that you try the same with any future simple questions before posting your question on the forums :).

Scott

---

### Post by gmargo on 2010-12-30
It's in the Maverick and later repositories, but apparently not Lucid and before.

[http://packages.ubuntu.com/maverick/pianobar](http://packages.ubuntu.com/maverick/pianobar)

---

### Post by Aero_Zeppelin on 2010-12-30
Pianobar is there by default in the maverick repositoris.Which version of ubuntu are you currently on?

---

### Post by Windows Nerd on 2010-12-30
> **Arindam Momin said:**
> Pianobar is there by default in the maverick repositoris.Which version of ubuntu are you currently on?
He's probably on Lucid or before if apt-get says the package doesn't exist.

---

### Post by dalmeida on 2011-04-28
To install pianobar from source you just need to download the latest version via git:
```
 git clone https://github.com/PromyLOPh/pianobar.git 
```
Then make sure you have all dependencies installed: 
make, libao, libfaad2, libmad, pthreads. 
```

sudo apt-get install build-essential
sudo apt-get install libao-dev libmad0-dev libfaad-dev

```

Once all dependencies are installed, run:
```

make clean
make
make install

```

voila, pianobar is installed and you can run it from command line by typing:
```
pianobar
```

**** The latest version of pianobar  (2011.04.27-dev) found in git fixes the error below :P

Error: Protocol incompatible. Please upgrade libpiano.

---

### Post by rokytnji on 2011-08-07
```
~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.3 LTS
Release:	10.04
Codename:	lucid

```

Got there eventually, Thanks :)

```
owner@owner-desktop:~/pianobar$ make clean
rm -f src/main.o src/player.o src/settings.o src/terminal.o src/ui_act.o src/ui.o src/ui_readline.o src/ui_dispatch.o src/libpiano/crypt.o src/libpiano/piano.o src/libpiano/xml.o src/libwaitress/waitress.o src/libwaitress/waitress.o/test.o \
			src/libezxml/ezxml.o src/libpiano/crypt.lo src/libpiano/piano.lo src/libpiano/xml.lo src/libwaitress/waitress.lo \
			src/libezxml/ezxml.lo pianobar libpiano.so* libpiano.a waitress-test
owner@owner-desktop:~/pianobar$ make
c99 -O2 -DNDEBUG -I src/libpiano -I src/libwaitress \
			-I src/libezxml -DENABLE_FAAD \
			-DENABLE_MAD -c -o src/main.o src/main.c
src/main.c: In function &#8216;BarMainGetLoginCredentials&#8217;:
src/main.c:106: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result
c99 -O2 -DNDEBUG -I src/libpiano -I src/libwaitress \
			-I src/libezxml -DENABLE_FAAD \
			-DENABLE_MAD -c -o src/player.o src/player.c
c99 -O2 -DNDEBUG -I src/libpiano -I src/libwaitress \
			-I src/libezxml -DENABLE_FAAD \
			-DENABLE_MAD -c -o src/settings.o src/settings.c
c99 -O2 -DNDEBUG -I src/libpiano -I src/libwaitress \
			-I src/libezxml -DENABLE_FAAD \
			-DENABLE_MAD -c -o src/terminal.o src/terminal.c
c99 -O2 -DNDEBUG -I src/libpiano -I src/libwaitress \
			-I src/libezxml -DENABLE_FAAD \
			-DENABLE_MAD -c -o src/ui_act.o src/ui_act.c
c99 -O2 -DNDEBUG -I src/libpiano -I src/libwaitress \
			-I src/libezxml -DENABLE_FAAD \
			-DENABLE_MAD -c -o src/ui.o src/ui.c
src/ui.c: In function &#8216;BarUiStartEventCmd&#8217;:
src/ui.c:832: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result
src/ui.c:843: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result
src/ui.c:850: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result
src/ui.c:855: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result
c99 -O2 -DNDEBUG -I src/libpiano -I src/libwaitress \
			-I src/libezxml -DENABLE_FAAD \
			-DENABLE_MAD -c -o src/ui_readline.o src/ui_readline.c
c99 -O2 -DNDEBUG -I src/libpiano -I src/libwaitress \
			-I src/libezxml -DENABLE_FAAD \
			-DENABLE_MAD -c -o src/ui_dispatch.o src/ui_dispatch.c
c99 -O2 -DNDEBUG -I src/libpiano -I src/libwaitress \
			-I src/libezxml -DENABLE_FAAD \
			-DENABLE_MAD -c -o src/libpiano/crypt.o src/libpiano/crypt.c
c99 -O2 -DNDEBUG -I src/libpiano -I src/libwaitress \
			-I src/libezxml -DENABLE_FAAD \
			-DENABLE_MAD -c -o src/libpiano/piano.o src/libpiano/piano.c
c99 -O2 -DNDEBUG -I src/libpiano -I src/libwaitress \
			-I src/libezxml -DENABLE_FAAD \
			-DENABLE_MAD -c -o src/libpiano/xml.o src/libpiano/xml.c
c99 -O2 -DNDEBUG -I src/libpiano -I src/libwaitress \
			-I src/libezxml -DENABLE_FAAD \
			-DENABLE_MAD -c -o src/libwaitress/waitress.o src/libwaitress/waitress.c
c99 -O2 -DNDEBUG -I src/libpiano -I src/libwaitress \
			-I src/libezxml -DENABLE_FAAD \
			-DENABLE_MAD -c -o src/libezxml/ezxml.o src/libezxml/ezxml.c
c99 -O2 -DNDEBUG  src/main.o src/player.o src/settings.o src/terminal.o src/ui_act.o src/ui.o src/ui_readline.o src/ui_dispatch.o src/libpiano/crypt.o src/libpiano/piano.o src/libpiano/xml.o \
			src/libwaitress/waitress.o src/libezxml/ezxml.o -lao -lpthread -lm \
			-lfaad -lmad -o pianobar
owner@owner-desktop:~/pianobar$ make install
install -d //usr/local/bin/
install -m755 pianobar //usr/local/bin/
install: cannot create regular file `//usr/local/bin/pianobar': Permission denied
make: *** [install] Error 1
owner@owner-desktop:~/pianobar$ sudo -su
sudo: option requires an argument -- 'u'
usage: sudo -h | -K | -k | -L | -V
usage: sudo -v [-AknS] [-p prompt]
usage: sudo -l[l] [-AknS] [-g groupname|#gid] [-p prompt] [-U username] [-u
            username|#uid] [-g groupname|#gid] [command]
usage: sudo [-AbEHknPS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
            username|#uid] [-g groupname|#gid] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
            username|#uid] file ...
owner@owner-desktop:~/pianobar$ sudo make install
[sudo] password for owner: 
Sorry, try again.
[sudo] password for owner: 
install -d //usr/local/bin/
install -m755 pianobar //usr/local/bin/
install -d //usr/local/share/man/man1/
install -m644 contrib/pianobar.1 //usr/local/share/man/man1/
owner@owner-desktop:~/pianobar$ pianobar
Welcome to pianobar (2011.07.09-dev)! Press ? for a list of commands.
[?] Email: biker
[?] Password: 
(i) Login... Ok.
(i) Get stations... Ok.
	 0)     AC/DC Radio
	 1)     Audioslave Radio
	 2)     Avenged Sevenfold Radio
	 3)     Buckcherry Radio
	 4)     Charlie Sexton Radio
	 5)     Chris Rea Radio
	 6)     Depeche Mode Radio
	 7) q   Evanescence Radio
	 8)     Faith No More Radio
	 9)     Gary Numan/Tubeway Army Radio
	10)     Gorillaz Radio
	11)  Q  biker's QuickMix
	12)     Hoobastank Radio
	13)     Jace Everett Radio
	14)     Les Claypool Radio
	15)     Little Feat Radio
	16)     Marilyn Manson Radio
	17)     Nickelback Radio
	18) q   Nine Inch Nails Radio
	19)     Puddle Of Mudd Radio
	20)     Savoy Brown Radio
	21)     Seether Radio
	22)     Stevie Ray Vaughan Radio
	23)     The Black Keys Radio
	24)     The Cult Radio
	25)     The Fabulous Thunderbirds Radio
	26)     Thin Lizzy Radio
	27)     Thousand Foot Krutch Radio
	28)     ZZ Top Radio
[?] Select station: 13
|>  Station "Jace Everett Radio" (537634583027811730)
(i) Receiving new playlist... Ok.
|>  "Bad Things" by "Jace Everett" on "Jace Everett"
|>  "Millionaire" by "Slaid Cleaves" on "Unsung"
#   -01:10/02:48

```

Just thought I should mention that one needs to cd into the directory of pianobar in /home before running make clean, make, and sudo is needed before make install command also. Also one needs to install git also before starting what dalmeidas post recommends if you don't have git installed (like me). I struggle a bit with Ubuntu because I am used to running AntiX which does not set up sudo by default.

---

### Post by james_xxx on 2011-11-14
Since the most recent changes made by Pandora, the changes that then had to be made to pianobar now require that also libgnutls-dev be installed for pianobar to compile correctly.

Here again are dalmeida's instructions, modified to also include the installation of this new package:
```
git clone https://github.com/PromyLOPh/pianobar.git
sudo apt-get install build-essential
sudo apt-get install libao-dev libmad0-dev libfaad-dev libgnutls-dev libjson0-dev
```

Then to compile & install:
```

cd pianobar
make clean
make
sudo make install
```

---

### Post by james_xxx on 2012-05-12
It would appear that libjson0-dev is now also required in order for pianobar to properly compile.

I'll just edit my above post, to add this package to the instructions.

---

