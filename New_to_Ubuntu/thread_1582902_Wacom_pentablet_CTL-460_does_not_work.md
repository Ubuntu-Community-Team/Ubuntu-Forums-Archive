---
title: "Wacom pen/tablet CTL-460 does not work"
date: 2010-09-27
forum: New to Ubuntu
---

### Post by JMeK on 2010-09-27
Hi, 

I am a dinosaur to begin with (from the 1950&#347;) and also completely new at Ubuntu.So please take it easy with me!
 I started with Ubuntu Studio 10.04 day before yesterday. First problem I encounterd was: my Wacom tablet (Bamboo Pen model CTL-460) doesn work anymore. 
I followed exactly the instructions already given [here]("http://frankgroeneveld.nl/2010/04/11/get-wacom-bamboo-fun-pen-working-in-ubuntu-lucid/"), but unfortunately this does not work (in Ubuntu studio - or is it just me:(?

Is there any other solution?

Greetings,

Koos "JMeK"

---

### Post by Favux on 2010-09-27
Hi Koos "JMeK",

Welcome to Ubuntu forums!

The reason the instructions you followed didn't work is linuxwacom 0.8.6 is no longer posted.  It would be 0.8.6-2, and in fact it's up to 0.8.8-8.  Either should be OK.  There were some fixes to pressure in xf86-input-wacom that might affect your stylus also, so you might want to update that too.

So:
1) Bamboo Pen doesn't work because the default wacom.ko (usb kernel driver) in Lucid (10.4) is from an older linuxwacom that does not support it.  So no usb communication to the tablet.  That means you need to compile a newer wacom.ko.

2) Some fixes in more recent xf86-input-wacom's may affect your stylus performance.  The default in Lucid is 0.10.5 and current is 0.10.8 plus.  This supplies the X driver wacom_drv.so.

See the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").  If you want to use one of sample .xsetwacom.sh's remember to delete the eraser, touch, and pad sections since you don't need them.  Just keep the stylus section.

Hope this helps.

Good luck!

---

### Post by JMeK on 2010-09-27
Thank you. I will follow the link you provided and try.

---

### Post by JMeK on 2010-09-28
Hi Favux,

I Followed the link to [Bamboo P&T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1") and followed the steps in sections

 **I.  Install LinuxWacom's 0.8.8-8 wacom.ko** (the USB kernel driver)
and
**II.  Install Xorg's xf86-input-wacom for Lucid** (the X driver)

And this is where I get stuck. The pen is not working (yet -), but I do have five new items on my desktop. So maybe there is still hope -lol. 
So I can see these five new items on my desktop:
1. file* linuxwacom-0.8.8-8.tar.bz2*
2. folder* linuxwacom-08.8-8*
3. folder* xf86-input-wacom*
4. file* util-macros-1.8.0.tar.bz2*
5. folder* util-macros-1.8.0*

I really don't know what to do next. 
FYI: I did notice in the terminal at one point it said: ./src/2.6.30/wacom.ko file or folder does not exist (or words like that -my version of ubuntu-studio is in Dutch language)

I hope you have some more advice for me. Note: you cannot underestimate my level of knowledge in these matters. I even had a hard time to find out where to find that thing called "terminal". And now that I found it, I'm proud to be able to copypaste things in there and think of myself as the ultimate geek. So...that&#347; my level. Please take it slow with me.

---

### Post by TonKi on 2010-09-28
I followed [this]("http://frankgroeneveld.nl/2010/04/12/get-wacom-bamboo-pen-working-in-ubuntu-karmic/") guide, replace karmic with lucid/maverick - worked for me

---

### Post by JMeK on 2010-09-28
Thanks TonKi

As I indicated in my first post, I did try the suggestions made by Frank Groeneveld [here]("http://frankgroeneveld.nl/2010/04/11/get-wacom-bamboo-fun-pen-working-in-ubuntu-lucid/"), but unfortunately this didn't work. Or is that not what you meant?

---

### Post by Favux on 2010-09-28
Hi Koos,

> I did notice in the terminal at one point it said: ./src/2.6.30/wacom.ko file or folder does not exist
That's a big clue.  Nice job noticing it!  That's probably telling us the new wacom.ko in step I. isn't being compiled.  To check enter in a terminal:
```
lsmod | grep wacom
```
And it's probably due to some difference with Ubuntu Studio 10.04 over Ubuntu.  Let's see if we can find out what.  Enter in a terminal:
```
uname -a
```
We'll look at the output of both.

---

### Post by JMeK on 2010-09-28
Hi Favux!

Happy to see you again.

lsmod | grep wacom

doesn't give any output. It just returns me to my blinking cursor. 

After that:

uname -a

returns this message:

Linux boy 2.6.32-24-generic #43-Ubuntu SMP Thu Sep 16 14:17:33 UTC 2010 i686 GNU/Linux

If you want I can add screenshots to these posts.

---

### Post by Favux on 2010-09-28
OK, the i686 means you could have a 64-bit install or it could be 32-bit.  Do you know which?  Is Ubuntu Studio 64-bit in other words?  If you don't know we could try:
```
uname -m
```

---

### Post by JMeK on 2010-09-28
The code: uname -m 

gives: i686


Is that bad or real bad? -p
The good news is: the messages from terminal are getting shorter!

---

### Post by Favux on 2010-09-28
Alright, I'm going to guess that your Ubuntu Studios is 64-bit.  In that case I probably know what the problem is.  Rather than doing a bunch more diagnostics let's try my guess.

In part I. change this line:
```
./configure --enable-wacom --prefix=/usr
```
to
```
./configure --enable-wacom --prefix=/usr --libdir=/usr/lib64
```
If you use the same 0.8.8-8 linuxwacom package on your Desktop rather than a new one, run this command:
```
make clean
```
before the "./configure etc." line.

And you probably need to do the same in part II. with xf86-input-wacom.  Change:
```
./autogen.sh --prefix=/usr


```
to
```
make clean

./autogen.sh --prefix=/usr --libdir=/usr/lib64
```

---

### Post by Favux on 2010-09-28
Just thought of something.  Before you try the above post check in Synaptic Package Manager if xserver-xorg-input-all is installed.  If it isn't install it.  Don't worry if it also wants to install xserver-xorg-input-wacom, let it. And then reboot.

---

### Post by JMeK on 2010-09-28
Hi Favux

I checked, and *xserver-xorg-input-all *is installed. 

I'm afraid I don't know anything about 32 or 64 bit. Hell, I started emailing only two years ago. I really am from the Stone Age you see.

As for your suggestion to replace the code with

./configure --enable-wacom --prefix=/usr --libdir=/usr/lib64
I did this, but it seems to have no effect. Sorry to take so much of your time & energy

Koos

---

### Post by Favux on 2010-09-28
No problem.  This time did you see the "./src/2.6.30/wacom.ko file or folder does not exist" error when you copied (cp) the wacom.ko into place?

What does:
```
lsmod | grep wacom
```
show now?
Also:
```
modinfo -n wacom
```

---

### Post by JMeK on 2010-09-28
I copypaste from terminal:

koos@boy:~$ sudo cp ./src/2.6.30/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
[sudo] password for koos: 
cp: kan status van `./src/2.6.30/wacom.ko&#8217; niet opvragen: Bestand of map bestaat niet
koos@boy:~$ lsmod | grep wacom
koos@boy:~$ modinfo -n wacom
/lib/modules/2.6.32-24-generic/kernel/drivers/input/tablet/wacom.ko
koos@boy:~$ 

Translation Dutch-English: cannot get status of ./src/2.6.30/wacom.ko : File or folder does not exist.

Also
```
lsmod | grep wacom
```

As you can see just returns to my cursor.
I think maybe my machine  needs coffee.

---

### Post by Favux on 2010-09-28
> cp: kan status van `./src/2.6.30/wacom.ko’ niet opvragen: Bestand of map bestaat niet
Is telling us that the wacom.ko is not compiling.  I guess it is possible it is and is being placed in another kernel folder in /src instead of 2.6.30.  But I doubt it.  So we need to look at the section towards the end of the ./configure output; the Build section.  That will tell us if configure is set up to make the wacom.ko.  There might be errors near the Build or in make we have to look at.
> koos@boy:~$ modinfo -n wacom
/lib/modules/2.6.32-24-generic/kernel/drivers/input/tablet/wacom.ko
is telling us the path to a wacom.ko.  Maybe the default wacom.ko which won't work, but it is there.  It should be showing up in lsmod.

So add 'wacom' (without the quotes) to the bottom of the list in the modules file in /etc :
```
gksudo gedit /etc/modules
```
gksudo is the graphical version of sudo and gives you super user/root priviledges so you can change system files.  gedit is gnome editor or Text Editor and it is graphical which is why you use gksudo.  After adding 'wacom' Save, Close, and reboot.

Now check if wacom shows up in:
```
lsmod | grep wacom
```

---

### Post by JMeK on 2010-09-28
It does:

koos@boy:~$ lsmod | grep wacom
wacom                  21745  0 
koos@boy:~$

---

### Post by Favux on 2010-09-28
OK, good!  That solves one problem.  The wacom.ko wasn't being auto-loaded by your system.  That happens on some systems.  We fixed it by using the modules file.

The wacom.ko is too small to be the new one.  As a matter of fact I thought the default 0.8.4-4 one was about 27000 big.  The one you are trying to compile should be about 33000 big.  That's about the only way I know to tell them apart.

So now we have to look at the output of ./configure, especially the Build part near the end.  And as I mentioned you need to look out for errors, usually just before it.

As for 64-bit or 32-bit.  Somewhere near the download for Ubuntu Studios you used it should tell you which it is.  The i686 means you could run either version.

---

### Post by JMeK on 2010-09-28
Should I run the whole sequence of code again, or just this one line?

```

./configure --enable-wacom --prefix=/usr --libdir=/usr/lib64

```

---

### Post by Favux on 2010-09-28
```
cd ./Desktop

cd linuxwacom-0.8.8-8

make clean

./configure --enable-wacom --prefix=/usr

```
And then the output.  Let's look at that first before looking at the output of:
```
./configure --enable-wacom --prefix=/usr --libdir=/usr/lib64
```

---

### Post by JMeK on 2010-09-28
The output does a lot of checking. I copypaste the second half part of it, wich starts with: WARNING

 WARNING:
*** Unable to guess kernel source directory
***   Looked at /lib/modules/2.6.32-24-generic/source, /lib/modules/2.6.32-24-generic/build,
***     /usr/src/linux, /usr/src/linux-2.6.32-24-generic, and
***     /usr/src/linux-2.6
*** Kernel modules will not be built
***
checking for Xlib... yes
checking for XSERVER... yes
checking for xserver libc-wrapper header-files... no
checking if scaling tablet to screen size is needed... no
checking if Xorg server is version 1.4 or later... yes
checking if Xorg is 7.3 or earlier... no
checking if Xorg server is version 1.5.2 or later... yes
checking if Xorg server is version 1.6 or later... yes
checking if Xorg server is version 1.7 or later... yes
checking if Xorg SDK defined IsXExtensionPointer... yes
checking if Xorg SDK defines dixScreenOrigins... yes
checking XInput extension version... >= 2.0
checking for lib xf86config... checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for tclsh... /usr/bin/tclsh
checking for tcl version... 8.4
checking for tcl header files... found, /usr/include/tcl8.4
checking for tk header files... found, /usr/include/tcl8.4
checking ncurses.h usability... yes
checking ncurses.h presence... yes
checking for ncurses.h... yes
checking if libwacomcfg should/can be built... yes
checking if libwacomxi should/can be built... yes
checking if wacdump should/can be built... yes
checking if xidump should/can be built... yes
checking if xsetwacom should be built... yes
checking if wacomxrrd should be built... checking X11/extensions/Xrandr.h usability... yes
checking X11/extensions/Xrandr.h presence... yes
checking for X11/extensions/Xrandr.h... yes
yes
checking for Wacom X driver module path... /usr/lib/xorg/modules/input
checking for dynamic driver loading support... yes
checking if wacom_drv.{o,so} should be compiled... yes
checking if gcc accepts -fno-merge-constants... yes
checking if gcc accepts -fno-stack-protector... yes

configure: creating ./config.status
config.status: creating Makefile
config.status: creating mkxincludes
config.status: creating src/Makefile
config.status: creating src/util/Makefile
config.status: creating src/xdrv/Makefile
config.status: creating src/2.6.16/Makefile
config.status: creating src/2.6.18/Makefile
config.status: creating src/2.6.24/Makefile
config.status: creating src/2.6.30/Makefile
config.status: creating src/wacomxi/Makefile
config.status: creating src/wacomxi/wacomcpl
config.status: creating src/include/xdrv-config.h
config.status: src/include/xdrv-config.h is unchanged
config.status: creating src/include/kernel-config.h
config.status: src/include/kernel-config.h is unchanged
config.status: creating src/include/util-config.h
config.status: src/include/util-config.h is unchanged
config.status: executing depfiles commands

----------------------------------------
  BUILD ENVIRONMENT:
       architecture - i486-linux-gnu
       linux kernel - yes 
      kernel source - no 
     XFree86 source - no 
           Xorg SDK - yes /usr/include/xorg
          XSERVER64 - no
           dlloader - yes
               XLib - yes /usr/lib
         xf86config - no
                TCL - yes /usr/include/tcl8.4
                 TK - yes /usr/include/tcl8.4
            ncurses - yes

  BUILD OPTIONS:
            wacom.o - no
            wacdump - no 
             xidump - no 
        libwacomcfg - no
         libwacomxi - no
          xsetwacom - no
          wacomxrrd - no
              hid.o - no 
       wacom_drv.so - no /usr/lib/xorg/modules/input 
        wacom_drv.o - no
  wacom*_drv quirks - IsXExtensionPointer key-events dixScreenOrigins
----------------------------------------
You can build the kernel driver from this package by
./configure --enable-wacom


NOTE: this package only supports Xorg server older than 1.7.
          You are running a newer version. 
Please build the X driver from xf86-input-wacom.

koos@boy:~/Desktop/linuxwacom-0.8.8-8$ 

/end copypaste

---

### Post by Favux on 2010-09-28
Alright, here's the answer:
```
WARNING:
*** Unable to guess kernel source directory
*** Looked at /lib/modules/2.6.32-24-generic/source, /lib/modules/2.6.32-24-generic/build,
*** /usr/src/linux, /usr/src/linux-2.6.32-24-generic, and
*** /usr/src/linux-2.6
*** Kernel modules will not be built
***
```
It can't find the kernel source directory to compile against.  So that's why:
```
wacom.o - no
```
under Build Options.  It should say:
```
wacom.o - yes
```
What is the output of?:
```
uname -r
```

---

### Post by JMeK on 2010-09-28
2.6.32-24-generic

In the mean time, is there anything I can do for *you*, maybe do a google search on any topic, or make you a drawing, anything?

---

### Post by Favux on 2010-09-28
That looks good.  So now let's try:
```
cd ./Desktop

sudo apt-get install linux-headers-generic

cd linuxwacom-0.8.8-8

make clean

./configure --enable-wacom --prefix=/usr
```
and then the same with:
```
./configure --enable-wacom --prefix=/usr --libdir=/usr/lib64
```

---

### Post by JMeK on 2010-09-28
In both cases, it says under BUILD OPTIONS:
```
wacom.o - no
```

---

### Post by Favux on 2010-09-28
Boy, I am beginning to really dislike Ubuntu Studios.  It always seems to be a problem and the problem is always different.

On the library/dependency line did you get everything?  It goes way to the right out of the box.  Did you get all of it?
```
sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev tk8.4-dev tcl8.4-dev libncurses5-dev libxrandr-dev

```
I guess we can try:
```
./configure --enable-wacom
```
Maybe you have some kind of server setup.

---

### Post by JMeK on 2010-09-28
please ignore

---

### Post by JMeK on 2010-09-28
Yes, I copypasted waaayy out of the box (copypasting being my first and foremost talent)
And 
```

./configure --enable-wacom
```
gives
bash: ./configure: File or folder doesnt exist

Can you explain 'server setup'? You mean the way I'm hooked up to the internet? Maybe it's important.

Anyway, given your own experience with Ubuntu Studio, maybe I should consider starting with a more basic Ubuntu, and build the multimedia applications from there (with help from the community)? I have to be flexible with this, and there is no need to torture ourselves unnecessary.

---

### Post by Favux on 2010-09-28
Well installing Ubuntu 10.4 and proving to yourself you can get the tablet working couldn't hurt.

You could also try DoctorMo's PPA:  [https://launchpad.net/~doctormo/+archive/wacom-plus](https://launchpad.net/~doctormo/+archive/wacom-plus)  It's not as up to date but it should work if it will install.

---

### Post by Burning_tree on 2010-09-28
Glad to see this thread.  I need to install my Wacom tablet as well.  

I tried the [guide]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1") here, but whenever I enter 

cd xf86-input-wacom

I get "No such file or directory".

---

### Post by Favux on 2010-09-28
The xf86-input-wacom package should be sitting on the Desktop.  Make sure you're in the Desktop directory first:

/home/yourusername/Desktop

then:  cd xf86-input-wacom

---

### Post by JMeK on 2010-09-29
> **Burning_tree said:**
> Glad to see this thread.  I need to install my Wacom tablet as well.  

I tried the [guide]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1") here, but whenever I enter 

cd xf86-input-wacom

I get "No such file or directory".

Sad for you, but good for me. I was really beginning to doubt my mental capabilities. What seems to be working for everyone, just doesn't work here, 

Keep me informed if you make any progress

Good luck!

---

### Post by JMeK on 2010-09-29
> **Favux said:**
> The xf86-input-wacom package should be sitting on the Desktop.  Make sure you're in the Desktop directory first:

/home/yourusername/Desktop

then:  cd xf86-input-wacom

Hi Favux!

A new day, with new opportunities. I will not surrender yet.

As a matter of fact, the folder xf86-input-wacom **is **on my desktop. So when I type in the terminal

```
/home/koos/Desktop
```
it returns the message

```
bash: /home/koos/Desktop: is a folder
```

And when I type

```
cd xf86-input-wacom
```

The output goes:

```
bash: cd: xf86-input-wacom: File or folder does not exist
```

And still no pen.

---

### Post by Saprissa on 2010-09-29
Some directory navigation essentials...

If the folder is on your desktop, try: 

```
cd /home/koos/Desktop/xf86-input-wacom
```

The cd (change directory) command is relative to the directory you are in.

If you're in /home/koos and you input "cd xf86-input-wacom" it will not find the folder because you have to change to the Desktop folder first.

The code above is absolute...that is to say, beginning from the root (which is /) you move to home (/home) then to Desktop(/home/Desktop) the to xf86-input-wacom (/home/Desktop/xf860-input-wacom)

Sorry to interrupt...

---

