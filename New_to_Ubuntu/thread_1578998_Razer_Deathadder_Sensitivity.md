---
title: "Razer Deathadder Sensitivity"
date: 2010-09-21
forum: New to Ubuntu
---

### Post by Sharky8U2 on 2010-09-21
Hi, I'm pretty new to Ubuntu.

I have a Razer Deathadder 3500 mouse. Currently my mouse is too sensitive for me to comfortably navigate the interface.

All sliders are at their lowest. I have found software which can supposedly help [Here (link)]("http://bu3sch.de/joomla/index.php/razer-nextgen-config-tool"). I cannot install it, the issue may be related to [this (link)]("http://forums.opensuse.org/english/get-help-here/hardware/406154-razer-deathadder-install-2.html#post2152059").

Could you please suggest an alternative, or guide me step by step to install the tarball. I have never done that before and cannot seem to get it right, many of the guides are too vague for me to understand anyway.

Thanks in advance.

---

### Post by realzippy on 2010-09-21
Start with:

```
sudo apt-get install libusb-dev python-qt4 cmake git-core
```

```
git clone git://git.bu3sch.de/razer.git
cd razer
cmake .            #do not forget the "space" and "dot"
make
sudo make install
sudo ldconfig

```

Does this work without compiling errors?
Then we can go on with installing the razr start script and edit your xorg.conf...

---

### Post by Sharky8U2 on 2010-09-21
Thanks, it's working much better, but when I try "ldconfig", this shows:

```
sharky8u2@sharky8u2-desktop:~/razer$ ldconfig
/sbin/ldconfig.real: Can't create temporary cache file /etc/ld.so.cache~: Permission denied

```

---

### Post by realzippy on 2010-09-21
then run:

```
sudo ldconfig
```


(sudo gives the permission)

---

### Post by Sharky8U2 on 2010-09-21
Ok, that worked. Don't know what happens after this. I'll see if the readme (came with tarball) can help.
Thanks again.

Readme has this:

```
INSTALLING
==========

First you need to install the tool libraries and binaries. Do this by typing
in the following commands:

  sudo -i	# become root
  make install
  ldconfig

To automatically start the required system daemon "razerd" at system bootup time,
you need to install the init-script. This software package includes a generic
example script, that should work out-of-the-box on many Linux distributions.
To install it, invoke the following commands:

  sudo -i	# become root
  cp ./razerd.initscript /etc/init.d/razerd
  ln -s /etc/init.d/razerd /etc/rc2.d/S99razerd
  ln -s /etc/init.d/razerd /etc/rc5.d/S99razerd
  ln -s /etc/init.d/razerd /etc/rc0.d/K01razerd
  ln -s /etc/init.d/razerd /etc/rc6.d/K01razerd

```

So we did the first bit, but no directory is found when I try the "cp" line. Do I need to change the path somehow?

---

### Post by realzippy on 2010-09-21
**Now** you have to check **if** you have a *xorg.conf* file....

Run:

```
gedit /etc/X11/xorg.conf
```

If a file opens,post it's content please...

---

### Post by Sharky8U2 on 2010-09-21
```

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

```

---

### Post by realzippy on 2010-09-21
Sorry.have to help my neighbor.I am back at 18.00 CET

---

### Post by realzippy on 2010-09-21
Back earlier...

Referring to this: (README):

[I]X11-WINDOW (X.ORG) CONFIGURATION
================================

The X-server [COLOR="Red"]must _not_ be configured to a specific mouse device[/COLOR] like [COLOR="Red"]/dev/input/mouse0[/COLOR],
because on configuration events razerd has to temporarly unregister the mouse from the
system. This will confuse the X-server, if it's configured to a specific device.
Configure it to the generic /dev/input/mice device instead. This will enable the X-server
to pick up the mouse again after a configuration event from razerd.

Example xorg.conf snippet:
...
  Section "InputDevice"
    Identifier	"Mouse"
    Driver	"mouse"
    Option	"Device" "/dev/input/mice"
  EndSection
...

Alternatively do not specify a "Device" at all. The X-server will autodetect
the device then:
...
  Section "InputDevice"
    Identifier	"Mouse"
    Driver	"mouse"
  EndSection
...

In any case, do _NOT_ use:
    Option	"Device" "/dev/input/mouseX"[/I]


Your xorg.conf is pretty small,which is ok if everything runs,you have installed the nvidia-driver with System/Admin/Hardwaredrivers.
So there is no "input device" section,which rules the mouse,this is done by HAL instead of.
So I suggest to ignore this in the moment and test if the razerstuff works..
README:

USING THE TOOLS
===============

[I]To use the tools, the "razerd" daemon needs to be started as root, first.
Without the background daemon, nothing will work. The daemon is responsible
for doing the lowlevel hardware accesses and for tracking the current state
of the device.
While the daemon is running, the user interfaces "razercfg" (commandline) and
"qrazercfg" (graphical user interface) can be used.
[/I]

Means:
**Reboot** the machine (if you have not already after compiling..).then:

```
sudo razerd
```

to start daemon in the backround;think there will be no output (if daemon starts successfully)

Then:

```
qrazercfg
```

...the GUI should appear.
I ignored:

[I]To automatically start the required system daemon "razerd" at system bootup time,
you need to install the init-script. This software package includes a generic
example script, that should work out-of-the-box on many Linux distributions.
To install it, invoke the following commands:

  sudo -i	# become root
  cp ./razerd.initscript /etc/init.d/razerd
  ln -s /etc/init.d/razerd /etc/rc2.d/S99razerd
  ln -s /etc/init.d/razerd /etc/rc5.d/S99razerd
  ln -s /etc/init.d/razerd /etc/rc0.d/K01razerd
  ln -s /etc/init.d/razerd /etc/rc6.d/K01razerd


UDEV notification:

The  make install  step did already install the UDEV script automatically.
It installed the script to
  /etc/udev/rules.d/01-razer-udev.rules
This should work on most distributions.

[/I]

because of:
*The  make install  step did already install the UDEV script automatically.*


If things do not work,we will do this.

---

### Post by Sharky8U2 on 2010-09-21
I really appreciate you helping me with this.

I type in "sudo razerd" and get this:

```
sharky8u2@sharky8u2-desktop:~$ sudo razerd
[sudo] password for sharky8u2: 
Razer device service daemon
**qraSegmentation fault**

```

"qrazercfg" obviously doesn't work, but here is the error I get if I try (in case it helps):

```
sharky8u2@sharky8u2-desktop:~$ qrazercfg
Failed to connect to razerd socket: [Errno 111] Connection refused
Is razerd running?

```

---

### Post by realzippy on 2010-09-21
**qrazercfg** will only run if the daemon **razerd** is running,which gives the segfault error.
So open terminal,type (line by line):

```
cd razer
sudo su
cp razerd.initscript /etc/init.d/razerd
ln -s /etc/init.d/razerd /etc/rc2.d/S99razerd
ln -s /etc/init.d/razerd /etc/rc5.d/S99razerd
ln -s /etc/init.d/razerd /etc/rc0.d/K01razerd
ln -s /etc/init.d/razerd /etc/rc6.d/K01razerd
exit
```

**Reboot**

Now "razerd" daemon should be started when booting;so just try:

```
qrazercfg
```

..if it again starts whining:
*Is razerd running?*
try to start the daemon before and try again:

```
sudo razerd
qrazercfg
```

---

### Post by Sharky8U2 on 2010-09-21
I type in "cp razerd.initscript /etc/init.d/razerd" but still get this:

```
root@sharky8u2-desktop:~# cp razerd.initscript /etc/init.d/razerd
cp: cannot stat `razerd.initscript': **No such file or directory**
```

I am in root. Am I doing something wrong here?

---

### Post by realzippy on 2010-09-21
Yes,wrong.You are in root`s directory.. not in your /home  ;-)

Open the terminal (as user).. and type the stuff from post#11 !

---

### Post by Sharky8U2 on 2010-09-21
IT WORKS!!!!!!! \\:D/

Thank you so much! Now that I have control over my mouse I have very little reason to not use ubuntu full time. I have learnt a lot from this.

Thank you again.

---

### Post by realzippy on 2010-09-21
Cool.Please set thread as "solved"....and have fun!

---

### Post by Sharky8U2 on 2010-09-21
Ok. Thanks again.

As a note to any one who looks back at this. I put sudo in front of each command from post #11, the commands did not work otherwise.

---

### Post by realzippy on 2010-09-21
Arg.MY MISTAKE,SORRY!!

**sudo -i** is wrong,should have been **sudo su**.
Corrected this in post #11,so
no need for "sudo" in front. (but would not do any harm  ;-) )

---

### Post by realzippy on 2010-09-21
The whole bunch summarized:


```
sudo apt-get install libusb-dev python-qt4 cmake git-core
git clone git://git.bu3sch.de/razer.git
cd razer
cmake .            #do not forget the "space" and "dot"
make
sudo make install
sudo ldconfig
sudo su
cp razerd.initscript /etc/init.d/razerd
ln -s /etc/init.d/razerd /etc/rc2.d/S99razerd
ln -s /etc/init.d/razerd /etc/rc5.d/S99razerd
ln -s /etc/init.d/razerd /etc/rc0.d/K01razerd
ln -s /etc/init.d/razerd /etc/rc6.d/K01razerd
exit
sudo reboot


```

Now the razer tool should start with:

```
qrazercfg
```

---

### Post by Sharky8U2 on 2010-09-22
I found that the program would reset DPI every time you restart.

A tip to help with this: instead of using the terminal to open the program every time; add a Startup Application (in preferences if you are using Ubuntu), set the command as "qrazercfg" so the config appears on startup.

---

### Post by realzippy on 2010-09-22
You can try the terminal tool:
```
razercfg
``` instead of qrazercfg;when you figure out the command to set the desired mouse resolution it should be possible to put
this command (or a small script)into autostart,so DPI would be set automatically when logging in.Unfortunately I do not have a razer mouse,so I cannot figure that out.

---

### Post by Sharky8U2 on 2010-10-19
Ok I've taken a while, but I've found the command to set DPI at start up.
Here is a guide on how to do it.

In the terminal type this:
```
razercfg **-s**
```
The "-s" searches for razer mice connected and returns their location. I'll be using my results as examples.

Copy the WHOLE whole location, to specify which mouse the commands are applied to, you put this after "-d"

Next use this command (obviously replace with your mouse's location)

```
razercfg -d Mouse:DeathAdder:USB-004:1532-0016-0 **-R**
```

The "-R" shows you the available DPI settings for your mouse something like this:
```
Profile 1:   1 (450 DPI),  2 (900 DPI),  3 (1800 DPI),  >>4 (3500 DPI)<<,
```

Choose the DPI setting you want (Here I want 900 DPI)

```
razercfg -d Mouse:DeathAdder:USB-004:1532-0016-0 **-r 1:2**
```
The "-r" sets the DPI, the two numbers at the end are "The Profile : The DPI Code" (so if I wanted 1800 DPI, I would have put "1:3")

You can use the check DPI code to make sure it worked.


**To make this happen at starup**: Go to System->Preferences->Startup Applications

Click Add. Then put the code to change the DPI as the command.

Your DPI will now be set at Startup!

Notes:
-Changing the USB Port of your Mouse may change it's Location value, so you would need to get the new one.
-This should also work with Scan Frequency (just use L,l instead of R,r)
-There are more options just type this to see them:
```
razercfg **-h**
```

---

### Post by cosmic_cow on 2012-11-19
This git repository doesn't appear to exist anymore and I haven't been able to find it mirrored anywhere, so I wrote a little script that lowers the mouse sensitivity to something reasonable.

Open up your favorite text editor (vim, gedit, whatever). I named the file fixMouse.sh but you can call it whatever you want as long as it has the .sh extension.

Paste this in as the body:
```
#!/bin/sh

mouse=` xinput | grep DeathAdder | awk '{print $6}' | awk 'BEGIN {FS="=";} {print $2}'`
xinput --set-prop $mouse "Device Accel Constant Deceleration" 5
xinput --set-prop $mouse "Device Accel Velocity Scaling" 1

```

This finds the device number for the DeathAdder automatically and then sets the values for you. Make the file executable and run it and you'll be good to go. I have mine set up to run on boot (it's listed under Startup Applications), but I also have it on my desktop in case I forget to plug in my mouse before I boot.

---

