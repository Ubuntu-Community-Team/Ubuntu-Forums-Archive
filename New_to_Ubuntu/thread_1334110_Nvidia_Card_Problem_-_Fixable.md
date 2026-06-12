---
title: "Nvidia Card Problem - Fixable?"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by XIOV on 2009-11-22
**All Problems Have been resolved, thank you all for your time and assistance.**
[s]Okay so I have a dell xps m1530 with a GeForce 8400M GS.  Ubuntu recommended I install the proprietary driver then restart.  The restart resulted in a blank screen.  I can't do anything to solve the problem.  

I know how to get to the console (ctrl+alt+f1) and I've tried about everything I can think of.  

 lspci | grep -i nvidia tells me that I have a 01:00.0 VGA compatible controller: nvidia corporation geforce 8400mgs (rev a1)

I can't run the uninstall command because I dont know the path to the driver.
I looked when I installed the program and the driver was Nvidia-gix-new; but a simple sudo sh nvidia-gix-new --uninstall naturally doesn't work.
I also found someone used sudo sh nvidia-linux-driver-129.12.x86.sh --uninstall; this didn't work either.
I can't use GUI to solve the problem because the screen blanks after the splash.

Moreover, when running sudo nano /etc/X11/xorg.conf I get to the xorg.conf but I have no idea where the heck to find the properties I need to change.  I tried ctrl+r then ctrl+t to search files, but I can't find 'screen' to change resolution nor can I find 'devices' to disable the change I made (IE Turn off the evil proprietary driver).

After I type the sudo nano /etc/X11/xorg.conf command it brings up a screen that looks like this:

GNU nano 2.0.7            File: /etc/x11/xorg.conf





^G Get Help ^O WriteOut ^R Read File ^Y Prev Page ^K Cut Text ^C Cur Pos
^X Exit ^J Justify ^W Where Is ^V Next Page ^U UnCut Text ^T To Spell

There is no information regarding where to find the devices.  I looked through man xorg.conf but it didn't help me.

This is a real pain in the *** and I need this computer monday for college and work (its now sunday morning 5am, I've been screwin with it all night)

If anyone can assist at all it would be greatly appreciated.[/s]

---

### Post by waspbr on 2009-11-22
It should be fixable,your xorg should be there, though I noticed that at your nano line it read

```
/etc/x11/xorg.conf

```

instead of 

```
/etc/X11/xorg.conf

```

If even that fails, what you can do is on select the recovery option on you grub screen, this will take you to the recovery menu, there select the fix video option.

---

### Post by themusicalduck on 2009-11-22
Not too sure what would cause the blank screen, but do you remember what version of driver it is you installed?

Looking in synaptic, there are 3 different version, nvidia-glx-96, nvidia-glx-173 and nvidia-glx-185.

You could use ```
sudo apt-get remove nvidia-glx-*version*
``` to remove the driver and hopefully get back into your desktop.

The blank screen problem is probably fixable, but at least you can get back into a working computer for now.

---

### Post by pbrane on 2009-11-22
you can always try this in a terminal:

**sudo dpkg-reconfigure -phigh xserver-xorg**

should set your /etc/X11/xorg.conf back to a default state. for your nvidia driver you want something like this in your xorg.conf file:

[B]Section "Device"
	Identifier     "Device0"
	VendorName     "NVIDIA Corporation"
	Option	"NoLogo"	"True"
	Driver	"nvidia"
EndSection[/B]

---

### Post by XIOV on 2009-11-22
Awesome thank you guys so much! [s]I got the nvidia driver working now by going into sudo nano /etc/X11/xorg.conf and adding Option "UseDisplayDevice" "DFP" into Section "Screen".

Now however, I get an error that says "Ubuntu is running in low-graphics mode: Your screen and graphics card could not be detected..." and it displays a resolution that is so low my monitor barely recognizes it.

Edit:
Going back into sudo nano /etc/X11/xorg.conf I changed my Section "Screen" settings again:
Section "Screen"
   Identifier     "Default Screen"
   Monitor       "Configured Monitor"
   Device         "Configured Video Device"
                   Subsection "Display"
                              Virtual 1280 800
                    EndSubSection
   Defaultdepth     24
   UseDisplayDevice     "DFP"
EndSection

I saved and typed sudo /etc/init.d/gdm restart
Then I get a Blue Screen with a gray box that says:
"There already appears to be an x server running on display :0. Should another display number by tried?  Answering no will cause GDM to attempt restarting the server on :0 again. (You can change consoles by pressing Ctrl-Alt plus a function key, such as Ctrl-Alt-F7 to go to console 7.  Xservers usually run on consoles 7 and higher.)
<Yes> <No>

If I press Yes it takes me back to what I suspect is the splash screen (with too low of a res to see anything other than the error message telling me I have a low resolution), if i press no it does nothing.
Needless to say, Im stuck again :/[/s]

Edit:
Typed the reset command
sudo dpkg-reconfigure xserver-xorg
Then ran a reboot via sudo reboot

Everything is working, but I still need to install an Nvidia video driver so my 3d apps work.  Any suggestions on how to do this rather than the GUI (System -->Administration-->Hardware Drivers)

---

### Post by waspbr on 2009-11-22
well if the standard method is giving you trouble, you could try installing the package called envyng, (namely envyng-core and envyng-qt, look up on synaptic). This should give you an alternative to the usual method.

---

