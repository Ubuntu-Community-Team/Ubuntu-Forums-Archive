---
title: "Need Help Installing Wacom Bamboo Fun Tablet"
date: 2010-06-26
forum: New to Ubuntu
---

### Post by Jay_PC on 2010-06-26
Alright, so this being my first post Ill tell you all I'm completely Retarded when it comes to Linux... I'm used to the whole 'Does everything for you' Windows setup, but I'm not afraid to learn, I have lite Programing experience but don't have any with Linux command line... so go easy on me

I'm running Ubuntu Studio Lucid 10.04 and I have a Wacom Bamboo fun tablet. Seeing as the Controller driver CD doesn't work in Linux(I was hopeful, but go figure) I cant install it. (no plug and play support here huh.) 

So Ive been trying to do my homework before I Started this post but its just not coming to me. I saw the Linux Wacom Project. and their saying something about adding a line to some XFree86 Which I have no clue about. Im assuming theirs no package file that just unpacks everything to the correct places.

Any help would really be of Use.

---

### Post by Favux on 2010-06-26
Hi Jay_PC,

Welcome to Ubuntu forums!

Please see [HOW TO Set Up the Bamboo Pen & Touch in Lucid]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").  That should get you going.

Hope this helps.

---

### Post by Jay_PC on 2010-06-26
EDIT: ok so I looked in the linucwacom0.8.8-3/src/2.6.30 and there is no wacom.ko file... this is probably important to note. is there suposed to be or do I need to use another file like 'wacom.h' ?

ok I am still in step 1, I just ran the line 
```

./configure  --enable-wacom --prefix=usr

```and im getting this:

```

Note:  this package only supports Xorg server older than 1.6.5.
           You are running a newer version. 
Please build xf86-input-wacom  instead.

You can build the kernel driver from this package  though.

```and then I enter Make then:

```
sudo  cp ./src/2.6.30/wacom.ko/lib/modules/'unname  -r'/kernel/drivers/input/tablet/wacom.ko
```and I get this:

```
cp:  cannot stat `./src/2.6.30/wacom.ko': No such file or directory
```I  figure something didn't go as planned, again any help would be useful

---

### Post by stoneage on 2010-06-26
> **Jay_PC said:**
> 
```
cp:  cannot stat `./src/2.6.30/wacom.ko': No such file or directory
```I  figure something didn't go as planned, again any help would be useful

It is probably just the wrong kernel version?

Look in the ./src/ directory and see if there is a wacom.ko in another kernel version directory.

---

### Post by Jay_PC on 2010-06-26
> **stoneage said:**
> It is probably just the wrong kernel version?

Look in the ./src/ directory and see if there is a wacom.ko in another kernel version directory.

I just thought that one, I looked and theres no wacom.ko in any of them just these:


wacom.h
wacom_wac.h
wacom_wac.c
wacom_sys.c
Makefile
Makefile.ln

---

### Post by Favux on 2010-06-26
No, it's not in those other directories.  It should be in the one you're suppose to copy.  You must not have followed the directions correctly.  The output from configure might show you what you did wrong.

---

### Post by Jay_PC on 2010-06-26
```
----------------------------------------
  BUILD ENVIRONMENT:
       architecture - x86_64-linux-gnu
       linux kernel - yes 
  module versioning - no 
      kernel source - no 
     XFree86 source - no 
           Xorg SDK - yes /usr/include/xorg
          XSERVER64 - yes
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

```Does this help at all? if not I dont know where im looking for that Configure output and what im looking for in it. 

Favux, I went to the page you said to go to and started from scratch, running the terminal doing 'cd ./Desktop' and then downloading the File I ran that block of code line by line in the terminal... I dont know where I went wrong. also what do you mean by 

> It should be in the one you're suppose to copy.

---

### Post by Favux on 2010-06-26
Hi Jay_PC,

```
wacom.o - no
```
Indicates the wacom.ko won't build.  It looks like you missed:
```
sudo apt-get install linux-headers-generic

```
Because:
```
kernel source - no
```
doesn't show a kernel source.

---

### Post by Favux on 2010-06-26
Oops, you're using Ubuntu Studio.  You may have the rt kernel.  To see enter:
```
uname -r
```
If you do enter:
```
sudo apt-get install linux-headers-rt
```
instead.

---

### Post by Jay_PC on 2010-06-27
I Checked and 'uname -r' returns '2.6.32-21-preempt' 

also I appreciate you not complaining about how lost I am.

---

### Post by Favux on 2010-06-27
Well, that's a new one.  rt(real time) kernel is/was for better audio playback.  Quick scan of Synaptics didn't show preempt.  But I guess you can try:
```
sudo apt-get install linux-headers-preempt
```
What error do you see with generic?

---

### Post by Jay_PC on 2010-06-27
I opted out of the RT because the downside was there was the risk of locking up. and im mostly using this for graphics and small studio recording. Im not gonna be doing any live mixing so im not too worried lol 

the generic worked, didn't give me any errors so next is:

```


cd linuxwacom-0.8.8-3

./configure --enable-wacom --prefix=/usr

```

---

### Post by Favux on 2010-06-27
Correct, if you unpacked the tar:
```
tar xjvf linuxwacom-0.8.8-3.tar.bz2

```
Which is the command line equivalent of right clicking on it and telling it to extract.

Before the package management programs like apt-get and the gui front-end for it Synaptic Package Manager all linux programs came as source code.  You'd download it (the tar (a compression format like zip)) and then unpack it.  The actual three commands are;
```
./configure
```
which sets up the source code for the system it's on.  Then:
```
make
```
which compiles the source code.  Then:
```
sudo make install
```
which installs the make or compile.  sudo gives you root or super user status so you can change system files not just user files.

All the rest is window dressing because linuxwacom is a reasonably big and complicated program.  Since you're not trying to install linuxwacom you skip the last command and instead copy (cp) the compiled wacom.ko into place.

---

### Post by Jay_PC on 2010-06-27
> **Favux said:**
> 
All the rest is window dressing because linuxwacom is a reasonably big and complicated program.  Since you're not trying to install linuxwacom you skip the last command and instead copy (cp) the compiled wacom.ko into place.

Thats what I missed last time I never did ./configure

now how do I copy it into place, Move the folder on the Desktop?

---

### Post by Favux on 2010-06-27
That's the:
```
sudo cp ./src/2.6.30/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko

```
command.  It copies the wacom.ko from /src/2.6.30/ in the unpacked linuxwacom tar ball to /lib/modules/`uname -r`/kernel/drivers/input/tablet/.  Which is the modules directory specific to the current kernel you are running.  So if the kernel is updated the tablet will seem to break.  Just go back into the unpacked tar and repeat the copy command.

Now after a reboot the tablet will work.  But the buttons won't, etc.  Which is why next is updating the xf86-input-wacom to ~0.10.7.

---

### Post by Jay_PC on 2010-06-27
its back! so when I ran that command it  gave me:

```
cp: cannot stat `./src/2.6.30/wacom.ko': No such file or directory
```

this is the same issue I was having before... Im just confused as to what wacom.ko **IS** like where did it come from, is it suposed to be the contents of the src/2.6.30 folder?

---

### Post by Favux on 2010-06-27
The wacom.ko should be made by the compile (make).  It should be located in:
```
linuxwacom-0.8.8-3/src/2.6.30/wacom.ko

```
If it isn't in 2.6.30 see if it's anywhere else. in /src/.

---

### Post by Jay_PC on 2010-06-27
I looked its not in src at all..... im doing a System scan to see if it put it in some bzare place for whatever reason

it found 4 wacom.ko, one in each of these locations

/lib64/modules/2.6.32-21-preempt/kernel/drivers/input/tablet
/lib64/modules/2.6.32-22-preempt/kernel/drivers/input/tablet
/lib64/modules/2.6.32-21-preempt/kernel/drivers/hid
/lib64/modules/2.6.32-22-preempt/kernel/drivers/hid

Does that mean it worked and I just never knew?

---

### Post by Jay_PC on 2010-06-27
ok Im fairly sure everything is installed but my tablet still doesn't work. I think its a product Id thing... its a Bamboo fun not a pen, pen and touch, or touch...

---

### Post by Favux on 2010-06-27
Probably not.  That's likely the default wacom.ko that doesn't work.  But it does look like the copy command for the preempt kernel needs to be different:
```
sudo cp ./src/2.6.30/wacom.ko /lib64/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
```
But it still won't work if the wacom.ko wasn't compiled.  Did you try the rt header for it?

As I get it you told Ubuntu Studio not to install the rt kernel and it installed preempt instead.  You probably have to ask the Ubuntu studio folk what header to use.  If in your  Build environment you're not seeing;
```
 kernel source - yes /lib64/modules/2.6.32-21-preempt/build 

```
or something similar you are not going to build the wacom.ko.

---

### Post by Jay_PC on 2010-06-27
I ran all three and they all seemed to give me the same thing

```

linux-headers-preempt is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```says this now for all 3. now is it important I run this from the linuxwacom-0.8.8-3 folder or from the src folder.

also when I make I get this 

```
:
~/Desktop/linuxwacom-0.8.8-3$ make
Making all in src
make[1]: Entering directory `/home/john/Desktop/linuxwacom-0.8.8-3/src'
make[2]: Entering directory `/home/john/Desktop/linuxwacom-0.8.8-3/src'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/john/Desktop/linuxwacom-0.8.8-3/src'
make[1]: Leaving directory `/home/john/Desktop/linuxwacom-0.8.8-3/src'
make[1]: Entering directory `/home/john/Desktop/linuxwacom-0.8.8-3'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/home/john/Desktop/linuxwacom-0.8.8-3'

```

---

### Post by Favux on 2010-06-27
Run the cp command from the source folder.  It looks like the header is installed.  Hmmm.

The other stuff doesn't mean anything.

---

### Post by Dougie187 on 2010-06-27
try this and post the results from the configure step like you did before.

```

make clean
./configure
make
```

Then Follow the remaining directions. 

Just to clarify, I'm trying to get make to rebuild your project, since previously it built, but without the .ko file. Sometimes I've had issues where make won't make the stuff I want because it's already built. So
```
make clean
```
cleans the build environment
```
./configure
```
configures the make file
```
make
```
builds the program (or driver)

I don't know if this helps, but be sure to post the results from ./configure like you did before so we can see if your headers are found.

---

### Post by Jay_PC on 2010-06-27
```
----------------------------------------
  BUILD ENVIRONMENT:
       architecture - x86_64-linux-gnu
       linux kernel - yes 2.6.30
  module versioning - no 
      kernel source - yes /lib/modules/2.6.32-22-preempt/build
     XFree86 source - no 
           Xorg SDK - yes /usr/include/xorg
          XSERVER64 - yes
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

Note: this package only supports Xorg server older than 1.6.5.
          You are running a newer version. 
Please build xf86-input-wacom instead.

You can build the kernel driver from this package though.


```Just noticed 
 kernel source - yes /lib/modules/2.6.32-22-preempt/build
has changed

---

### Post by Favux on 2010-06-27
Right.  It looks like Dougie187's 'make clean' suggestion helped (thanks!).  So:
```
kernel source - yes /lib/modules/2.6.32-22-preempt/build

```
is what we were looking for.  I wonder what header you installed to get that?

Anyway that only gets us partway because:
```
wacom.o - no
```
needs to be:
```
wacom.o - yes
```
because that's the wacom.ko and we want it to compile.  Did you include:
```
--enable-wacom
```
in
```
./configure --enable-wacom --prefix=/usr
```
Because the flag '--enable-wacom' tells it to compile the wacom.ko.  If so I suppose it's possible you need:
```
./configure --enable-wacom --prefix=/usr --libdir=/usr/lib64
```

Boy non-rt Ubuntu Studios is tough!

---

### Post by Jay_PC on 2010-06-27
Great this:[FONT=monospace]
[/FONT]```
[FONT=monospace]
./configure --enable-wacom --prefix=/usr --libdir=/usr/lib64[/FONT]
```

Worked.
```

----------------------------------------
  BUILD ENVIRONMENT:
       architecture - x86_64-linux-gnu
       linux kernel - yes 2.6.30
  module versioning - no 
      kernel source - yes /lib/modules/2.6.32-22-preempt/build
     XFree86 source - no 
           Xorg SDK - yes /usr/include/xorg
          XSERVER64 - yes
           dlloader - yes
               XLib - yes /usr/lib
         xf86config - no
                TCL - yes /usr/include/tcl8.4
                 TK - yes /usr/include/tcl8.4
            ncurses - yes

  BUILD OPTIONS:
            wacom.o - yes
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
```

also Favux, If anything this will serve as a troubleshooting guide for anyone who tries to install this on non rt Ubuntu Studio

---

### Post by Favux on 2010-06-27
Outstanding!!!

Hopefully it's all downhill from here.

---

### Post by Jay_PC on 2010-06-27
so its

```
 
make clean[FONT=monospace]

./configure --enable-wacom --prefix=/usr --libdir=/usr/lib64[/FONT]

make

```it actually worked this time I checked the ./desktop/linuxwacom0.8.8-3/src/2.6.30 Directory and surprise! theres wacom.ko then I ran:

```
cp ./src/2.6.30/wacom.ko /lib64/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
```

Should I restart now? or should I run:

```

sudo depmod -a[FONT=monospace]
[/FONT]lsmod | grep wacom

```

---

### Post by Favux on 2010-06-27
Congratulations!  Run depmod first before rebooting.

---

### Post by Jay_PC on 2010-06-27
I rebooted now what, do I run ```
lsmod | grep wacom
```

---

### Post by Favux on 2010-06-27
The tablet should now be working, or at least the stylus.  The lsmod command is to check the status of the wacom.ko if it isn't working.  On some systems it doesn't auto-load so you have to add it to the modules file in /etc/.

---

### Post by Jay_PC on 2010-06-27
YAY! Finaly everything is working. now I folowed your instructions on toggling the touch... down to the notification, and i'm not getting any errors. but its not turning off, its displays that its turning on and off, but even when its off it still works.

---

### Post by Favux on 2010-06-27
OK, the tablet buttons won't work unless you do II., installing the newer xf86-input-wacom.  Did you do that?

---

### Post by Jay_PC on 2010-06-27
Yeah I now im figuring how to configure the buttons to custom commands

---

### Post by Favux on 2010-06-28
Wow!  Serious progress.

---

### Post by Jay_PC on 2010-06-28
Well im quickly learning what the commands do, I almost spaced looking at the comments in the toggle-touch.sh and missed 

```
xinput --lis
``` to find the device number.

now im trying to understand what to modify to change what the buttons do.

---

### Post by Favux on 2010-06-28
Just make sure your device numbers don't change when replugging in the tablet or rebooting.

In a terminal enter 'man xsetwacom'.

---

### Post by Jay_PC on 2010-06-28
Now I know how to check the Device Number I can always check if its not working

---

### Post by Jay_PC on 2010-06-28
Hmmm Ive got no Shell Experience but Im trying to use your toggle script  to mass toggle devices 1-20 or something of that sort.  since I cant  figure out how to get the device id of "Wacom BambooFun 2FG 6x8 Finger  touch" I figured since xsetwacom returns:

```

xsetwacom get  (wrong device name here) Touch
Cannot find device '1'.
```

I  can just make a loop and it would skip any devices it 'cant find'

Is  there any way to get how many devices there are from xinput?

---

### Post by Favux on 2010-06-28
Hi Jay_PC,

You might want to start with:
```
xsetwacom list
```
Also there were several scripts that "parsed" the device name around page 90 here:  [http://ubuntuforums.org/showthread.php?t=1321238](http://ubuntuforums.org/showthread.php?t=1321238)

---

### Post by Jay_PC on 2010-06-29
Ok So I have everything working now. but for kicks I tried a Dual Screen setup any way to change the active area's reach? like I only want it on the larger monitor, and have the mouse for the other screen

---

### Post by Favux on 2010-06-29
> Ok So I have everything working now
Great, good work!

Dual monitors is always hit and miss, depending on the video chipset and state of wacom support.  You could check out these two threads:
[http://ubuntuforums.org/showthread.php?t=1461978](http://ubuntuforums.org/showthread.php?t=1461978)
[http://ubuntuforums.org/showthread.php?t=1488693](http://ubuntuforums.org/showthread.php?t=1488693)

---

### Post by Jay_PC on 2010-07-02
So... i HAD everything working, but now when I plug the tablet in it dosent respond... I checked
```

xinput --list
```

and the tablet doesn't show up. 

Recently I had a Problem with the nVidia Graphics Driver, giving me a "Ubuntuy is running in low graphics mode" so I opted to return to the Default Graphics driver, and after doing this, it hasn't worked.

so I think when I did that it set all my configurations back to Default. now how might I go about fixing this before I just remove and re install. or would that be my best bet

---

### Post by Favux on 2010-07-02
If you accepted the kernel update that came through yesterday then the new kernel doesn't have the compiled wacom.ko in it's modules directory, it has the default wacom.ko which doesn't work.  Try recopying the compiled wacom.ko into place.  If that doesn't work you'll have to recompile (I.).

---

### Post by Jay_PC on 2010-07-02
So I need to Copy wacom.ko to the new kernel folder. so 2.6.32-preempt... ok I coppied it to the folder its still not working so now I need to re compile wacom.ko

Somthing like this?

```
cd ./Desktop

cd linuxwacom-0.8.8-4

make clean

./configure --enable-wacom --prefix=/usr --libdir=/usr/lib64

make

sudo cp ./src/2.6.30/wacom.ko /lib64/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko

sudo depmod -a

lsmod | grep wacom
```

---

### Post by Jay_PC on 2010-07-02
all set now, I feel retarded for not realizing the update would change the driver directory

---

