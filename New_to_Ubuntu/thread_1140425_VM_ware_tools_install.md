---
title: "VM ware tools install"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by Nwwmac on 2009-04-27
I'm a Mac user brand new to Ubuntu. I have it running virtualized on VM Fusion, and it runs fine, if a bit basically: no Unity mode, no video acceleration. Fusion offers some tools that are supposed to enhance what it can do with Ubuntu, but I can't install it after multiple attempts. 

I'm sure it is my fault; I find the Terminal a bit bewildering. I can't seem to get the terminal to find the script I need to run. 

VMware's package says:   

To install/upgrade VMware Tools for Linux, 
  run the program "vmware-install.pl" from a command prompt, either in text 
  mode or from a terminal inside an X session. You must have super user 
  privileges (i.e. be logged as root) to run it.

     ./vmware-install.pl

I can see the file, it's located in a folder called "vmware-tools-distrib", which is in my home folder. 

Can anyone help me with the exact syntax I need to run this script? I've been trying for days, copying the path from the properties tab, but I am always told Terminal can't find the target. 

Many thanks for anyone who can straighten me out!

---

### Post by y_garti on 2009-04-27
hi before you are trying to install the vmware tools let us understand few thing
1 did you install ubuntu from scratch or you have a vmdk that you just mount ?
2 if u have a runing  os is the vmware tools installed or not ?
3 what version do you try to install of ubuntu ?

---

### Post by bodhi.zazen on 2009-04-27
To install the vmware tools see this wiki page :

[VMware/Tools - Community Ubuntu Documentation]("https://help.ubuntu.com/community/VMware/Tools")

---

### Post by Nwwmac on 2009-04-27
Thanks for the quick responses guys. 

I'm running the latest release of Ubuntu (9) as a guest on OS X. I installed Ubuntu with VMware Fusion. 

I tried the first preliminary step suggested on the Forum page for VMware Tools and got the following: 

Reading package lists... Done
Building dependency tree        
Reading state information... Done
E: Couldn't find package headers

What does that mean and what do I do about it?

---

### Post by bodhi.zazen on 2009-04-27
I assume a typo .

what is the exact how to you are following and what command did you enter ?

---

### Post by Nwwmac on 2009-04-27
It looks like that first command - 

sudo apt-get install build-essential linux-headers-`uname -r` psmisc

was not necessary. I succeeded in running the install script after a few more attempts. Terminal navigation is slowly getting better. 

As far as I can tell, only one non critical module failed, that is vmhgfs. This used for sharing folders between the host and the guest. The error message states that: 

"gcc, binutils, make, and the kernel sources for your running kernel must be installed on your machine. These packages are available on your installation CD."

I found gcc on the install CD, but was unable to do anything with it. Any suggestions? 

And thanks again for helping get this far... :)

---

### Post by bodhi.zazen on 2009-04-27
install build essential

```
sudo apt-get install build-essential
```

---

### Post by Nwwmac on 2009-04-28
I have think I have most of the VM Tools working now, wit the exception of the Shared Folders. It turns out that [this feature is not yet supported]("http://blogs.vmware.com/teamfusion/2009/04/ubuntu-904-on-vmware-fusion-2.html") because Ubuntu 9 is still so new. 

The blog post linked to above does [point to a workaround]("http://communities.vmware.com//thread/206772") that I have not looked at or tried yet.

---

### Post by t3ckfr3ak on 2009-05-06
this is a general tutorial to making an ubuntu host work properly with unity and full mouse use, i used the newest ubuntu distro 9.04 jaunty, but this should work with hardy or any of the other newer distros that these complications exist. and it should work with 64 or 32 bit versions. mine was 64

first install your build essentials then open synoptics and check to make sure that gcc (newest available) and your kernel source are installed.  

then unpack the .tar.gz vmware install to the desktop (or anywhere you please, but my commands will be asuming you put it on the desktop modify as needed)

before you go jumping the gun and install it you need to patch it.
this will make the install work properly with no complications.

the patch is located here [http://ubuntuforums.org/showthread.php?t=975084&page=2](http://ubuntuforums.org/showthread.php?t=975084&page=2)

then put the patch on the desktop

run this command (replacing User with your user name)

sudo patch /home/USER/Desktop/vmware-tools-distrib/binvmware-config.pl /home/USER/Desktop/vmware-config.pl.patch

if the patch applied successfully then your good to go on to the next step
if not retrace your steps check for your error this is VERY IMPORTANT!!

then run the installer (again replacing the user name with your user name)

sudo /home/USER/Desktop/vmware-tools-distrib/vmware-install.pl

just say yes to everything, near the end you will need to say yes the default is no

if everything worked right and you had no errors then go on to the next step, otherwise retrace your steps figure out where you went wrong, the vsock should now be working properly but not necessarily running

now you need to add the vmware toolbox and the vmware user app's to the startup

click on settings then sessions or startup programs at the top (depends on the ubuntu version)

add the following (separately label as you please)

/usr/lib/vmware-tools/bin/vmware-user

and

/usr/lib/vmware-tools/bin/vmware-toolbox

reboot

you should now be able to use unity but you may be having an issue where in the standard vm (not using unity) the mouse is trapped in the screen, this will make the mouse work incorrectly in unity

go back to the standard vm

open synoptics

search for "vmmouse" the top result (of the two) is an xorg mouse app, you need this, it will almost fix your issue. add both of the two apps because i wound up having both, so if you don't have both get them.

then search for vmware and find the mouse app get it too

now your almost done

find your xorg.conf

either in /etc/x11/xorg.conf
or in /etc/xorg.conf

open with  sudo gedit /etc/xorg.conf

before you go on read this page [http://ubuntuforums.org/showthread.php?t=1126696](http://ubuntuforums.org/showthread.php?t=1126696)

my xorg was blank i dont know why, but that page shows you what you need to do if it isnt.
but either way
make your configuration file look like this

 # VMware SVGA

Section "Module"
    Load        "dbe"  	# Double buffer extension
    SubSection  "extmod"
    EndSubSection
    Load        "type1"
    Load        "freetype"
#    Load       "glx"
EndSection

Section "Files"
    RgbPath	"/usr/X11R6/lib/X11/rgb"
#    FontPath   "/usr/X11R6/lib/X11/fonts/local/"
    FontPath   "/usr/X11R6/lib/X11/fonts/misc/"
    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
    FontPath   "/usr/X11R6/lib/X11/fonts/Type1/"
    FontPath   "/usr/X11R6/lib/X11/fonts/Speedo/"
    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/"
    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/"
#    ModulePath "/usr/X11R6/lib/modules"
EndSection

Section "ServerFlags"
#    Option NoTrapSignals
EndSection

Section "InputDevice"
    Identifier	"VMware Keyboard"
    Driver	"keyboard"
    Option "AutoRepeat" "500 30"
    Option "XkbRules"	"xfree86"
    Option "XkbModel"	"pc104"
    Option "XkbLayout"	"us"
    Option "XkbCompat"	""
EndSection

Section "InputDevice"
    Identifier	"VMware Mouse"
    Driver	"vmmouse"
	Option "CorePointer"
Option "AlwaysCore"
    Option "Protocol"    "ps/2"
    Option "Device"      "/dev/input/mice"
    Option "ZAxisMapping"	"4 5"
#    Option "Emulate3Buttons"
#    Option "Emulate3Timeout"    "50"
#    Option "ChordMiddle"
	Option		"Emulate3Buttons"	"true"
EndSection


Section "Device"
    Identifier  "VMware SVGA"
    Driver      "vmware"
EndSection

Section "Screen"
    Identifier  "Screen 1"
    Device      "VMware SVGA"
    Monitor     "vmware"
    # Don't specify DefaultColorDepth unless you know what you're
    # doing. It will override the driver's preferences which can
    # cause the X server not to run if the host doesn't support the
    # depth.
    Subsection "Display"
        # VGA mode: better left untouched
        Depth       4
        Modes       "640x480"
        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       8
        Modes       "1024x768"
        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       15
        Modes       "1024x768"
        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       16
        Modes       "1024x768"
        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       24
        Modes       "1024x768"
        ViewPort    0 0
    EndSubsection
EndSection

Section "ServerLayout"
	Option "AllowEmptyInput" "off"
    Identifier  "Simple Layout"
    Screen "Screen 1"
	InputDevice	"VMware Keyboard"	"CoreKeyboard"
	InputDevice "VMware Mouse"	"CorePointer"
EndSection


Section "ServerFlags"
	Option "AutoAddDevices" "False"
EndSection


Section "Monitor"
    Identifier      "vmware"
    VendorName      "VMware, Inc"
    HorizSync       1-10000
    VertRefresh     1-10000
EndSection

save it
restart the vm
your done

again my os was ubuntu 9.04 64 bit

i did not add the tutorial on making the printer functions work, but you will find them if you google enough

---

### Post by Pedroparamo on 2009-05-11
I can not copy and extract the tar.gz file--i get the message that no such file or directory exists.  I cannot seem to find the tar.gz file.???

Thanks.

Pedro

---

### Post by t3ckfr3ak on 2009-05-23
did you tell vmware to "install vmware tools" (in the vmware menu under vm) then it made a cd called vmware in your guest operating system? note you will need to copy the file from the cd before attempting to extract it

---

