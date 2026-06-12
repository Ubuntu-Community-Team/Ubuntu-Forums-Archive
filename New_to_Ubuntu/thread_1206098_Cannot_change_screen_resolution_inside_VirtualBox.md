---
title: "Cannot change screen resolution inside VirtualBox"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by philk949 on 2009-07-06
Hi,
On a Windows Vista Ultimate SP2 platform, I am running Ubuntu 9.0.4 in Sun VirtualBox.
The problem I am having is in changing my screen resolution within the virtual machine. In System>Preferences>Display, I am offered only 2 resolution choices, 600x800 and 640x480.
I have installed available updates but cannot access more choices.
Could someone please help me with this?

---

### Post by juanoleso on 2009-07-06
You need to install the guest additions, if you haven't already.

start your virtual machine and then let Ubuntu boot up
click devices => Install guest additions
it will mount a cd
install build-essentials using apt-get
open a terminal and cd to the cdrom usually /media/cdrom
run the VBox script for linux
restart

---

### Post by philk949 on 2009-07-06
Thanks for the response, Juan.
Unfortunately, when I tried to install Guest Additions I received the attached error message.
I have given myself the necessary permissions for access to the Sun folder but still cannot install.

Phil

---

### Post by philk949 on 2009-07-06
I have managed to mount the disc after installing Guest Additions.
Could you please give DETAILED instructions on how to proceed from here in order to change my screen resolution?
Thanks,
phil

---

### Post by Sky Pixie on 2009-07-07
Edit the Xorg.conf file directly using the command line.

At the gdm login screen, choose the terminal/console login option from the drop down menu.

Enter your username.  Enter your password.

Backup the existing file:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf~
```

Open the file using nano:
```
sudo nano /etc/X11/xorg.conf
```

Scroll down using the arrow key.  No key combinations are necessary to enter text.

Create a SubSection in the Section "Screen"
```

Section "Screen"
    Identifier    	"Default Screen"
    Device        	"NVIDIA"
    Monitor      	"Monitor"
SubSection "Display"
	Depth		24
        Modes      	"???x???"
EndSubSection
EndSection

```
Replace the ??? with an acceptable resolution for your monitor such as 1024x768 or 1280x800.

Save the file with Ctrl X.  Press Y to overwrite the existing file.

Start X.
```
startx
```

That should do it.

If you mess up, restore the original config file:
```
sudo cp /etc/X11/xorg.conf~ /etc/X11/xorg.conf
```

---

### Post by philk949 on 2009-07-07
HI Pixie,
Thanks for the reply.
But gdm login screen? When I power up the virtual machine, I'm given the GUI login screen. Can I simply open a terminal from there and enter the codes?
Thanks,
Phil

---

### Post by The Cog on 2009-07-07
> **philk949 said:**
> HI Pixie,
Thanks for the reply.
But gdm login screen? When I power up the virtual machine, I'm given the GUI login screen. Can I simply open a terminal from there and enter the codes?
Thanks,
Phil
Ctrl-Alt-F1 through Ctrl-Alt-F6 will give you six console login prompts that don't rely on the GUI. Very handy! When done, Ctrl-Alt-F7 (though sometimes F8 or F9 instead) will return you to the GUI.

Though before fannying around with the script from the Vbox ISO, check in synaptic. I think I saw the guest additions in there, which should make for an easier install altogether. Go System->Administration->Synaptic Package Manager, then search for and install virtualbox-ose-guest-utils. You may need to reboot before they work though.

If those guest utils from Synaptic don't work, then you will have to install the utils from the CD. Your error message looks like you were trying to run the wrong script (or the script itself is in error) because Linux doesn't have a C:.

Sorry I can't help in more detail, I've never run Ubuntu in VB under Windows, only ever the other way round.

---

### Post by Sky Pixie on 2009-07-07
> **philk949 said:**
> HI Pixie,
Thanks for the reply.
But gdm login screen? When I power up the virtual machine, I'm given the GUI login screen. Can I simply open a terminal from there and enter the codes?
Thanks,
Phil

gdm = Gnome Display Manager

Gnome is the graphical user interface for Ubuntu.  There should be a drop down menu to start a text-only console session.  Alternatively, a console session can be started with Alt N.

---

### Post by philk949 on 2009-07-07
There should be a drop down menu to start a text-only console session > 
A drop-down where, please?
I am not an experienced Ubuntu user, so I need a bit of spoon feeding. Sorry.
phil

---

### Post by philk949 on 2009-07-07
Thank you all for your help. I managed to get the job done through the Synaptic Package Manager.
Phil

---

### Post by Sky Pixie on 2009-07-07
> **philk949 said:**
> There should be a drop down menu to start a text-only console session 
A drop-down where, please?
I am not an experienced Ubuntu user, so I need a bit of spoon feeding. Sorry.
phil

There should be a menu somewhere on the login screen.  Near the username and password boxes or at the bottom of the screen.  Perhaps it's labeled "Sessions" or similar.

---

### Post by philk949 on 2009-07-07
Thanks Pixie,
Found it under Options, bottom left corner. I restored my resolution through Synaptic, but I'm going to check this out anyway. I need the practice.
Thanks,
Phil

---

