---
title: "[SOLVED] Activating ATI drivers in 8.10"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by jcats on 2009-01-09
I recently upgraded(?) to 8.10 from 8.04. While it went pretty well, I find that I cannot activate the ATI drivers. They are listed in Admin-Hardware, but no go. I have uninstalled/reinstalled the drivers, tried Envy, been to the ATI site and tried their methods and spent the last 5 hours scouring the web. Nothing has worked.
I have a Radeon 9800 Pro video card. I'd really like to get Compiz running again.
I have seen that there seems to be some conflicts between ATI and 8.10, but if nobody got it to work, there would be a lot more screaming on the web ;)
I have an a copy of the xorg file that worked great in 8.04. Can I just replace the current tone with the old one? If I can, then I need to know how to do that:redface:
I'd appreciate any help
Thanks;
jcats

---

### Post by TANGO! on 2009-01-09
Hi Jcats, I had the same problem and even posted in this forum but nobody seemed to know what was going on.  So after a lot of tinkering I got it working, but only 'cause I found a way around it.  This is what worked for me:

I logged in a console (because I had completely broken xorg after a lot of messing around) and wrote:

```

sudo apt-get remove xserver-xorg
sudo apt-get install xserver-xorg
startx

```

after that, [COLOR="Blue"]**DO NOT**[/COLOR] use the "activate" for the restricted driver in the menus, because it will break it again.

I hope that helps...

---

### Post by TANGO! on 2009-01-09
I just wanted to add: before doing that, I had downloaded and extracted the proprietary drivers straight from ATI, following some guides, and I'm afraid that was what broke down my xorg and why I had to fix it from a command line login.

Just in case it had anything to do with the fix.

---

### Post by markbuntu on 2009-01-09
If you install Intrepid it is absolutely critical to get all the updates and reboot before enabling the restricted driver for an ati card.

If you are upgrading from Hardy you should also remove all fglrx drivers and their kernel modules before upgrading and then get all the updates and reboot before enabling the restricted driver.

If you got the old driver with Envy use envy to remove it completely. if you got it from the repositories or used Hardware Manager, use the Synaptic package manager and remove it completely. If you downloaded it from ati, there are directions for removing the driver in the Install Instructions link from the download page.

---

### Post by jcats on 2009-01-10
Sorry for my late reply-life it gets in the way of playing with computers:tongue:

Tango, I tried your solution, but it didn't help. Actually it crashed my system. But I let Ubuntu roll back/repair the system and for some reason the mesa drivers are now in place:confused:
Markbuntu-thanks for the tips. I wish I had know this before I did the upgrade. Oh well, lesson learned.
I will go back and delete everything out, and try to reinstall. I'll report back what happens.
Thank you both for your efforts.
jcats

Markbuntu-any thoughts on which is the best way to install the ATI drivers?

---

### Post by jcats on 2009-01-10
OK, I'm part way home! Following Matkbuntu's suggestion (thank you), I deleted out the old drivers, and let Envy install new ones. Rebooted and the ATI FGLRX drivers are activated.
But still no Compiz. I deleted it, rebooted and reinstalled Compiz, but no luck.
Also, in Applications-Accessories, listed is the Catalyst Control center. But when I click on it, nothing happens. I don't really care about that, but I would like to get Compiz going.
Any thoughts, anyone?
jcats

---

### Post by Michael.Godawski on 2009-01-10
hi, 
can you please post the output of these commands:

```
sudo lshw -C display
glxinfo | grep rendering
```

---

### Post by jcats on 2009-01-10
OK, here you go;

lshw -C display:

```
 *-display:0             
       description: VGA compatible controller
       product: Radeon R350 [Radeon 9800 Pro]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-3.0 pm bus_master cap_list
       configuration: driver=fglrx_pci latency=255 mingnt=8 module=fglrx
  *-display:1 UNCLAIMED
       description: Display controller
       product: Radeon R350 [Radeon 9800 Pro] (Secondary)
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:02:00.1
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm cap_list
       configuration: latency=32 mingnt=8
```

glxinfo | grep rendering:

direct rendering: Yes

Thank you for your effort Michael

jcats

---

### Post by Michael.Godawski on 2009-01-10
Is it normal to have two entries here? Question to all....
This UNCLAIMED stuff sounds very vague...
This is my output of sudo lshw -C display

```
michael@michael-laptop:~$ sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: RS482 [Radeon Xpress 200M]
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: driver=fglrx_pci latency=255 mingnt=8 module=fglrx
```Your first entry seems ok. Direct rendering is also activated. 
What happens when you go to System > Preferences > Appearance > Visual Effects and select Extra?

---

### Post by jcats on 2009-01-10
SCORE!!! Thank you, Michael. =D> You got Compiz to work for me. I completely forgot about changing the visual effects.. DUH!
As for the double entry, this card has always done that. In all versions of Ubuntu and all versions of Windows. I have no idea why.
Thanks again to all of you for your help
jcats

---

### Post by Michael.Godawski on 2009-01-10
Glad to hear that :).

If you want to customize Compiz further I would install this tool too:
```

sudo apt-get install compizconfig-settings-manager
```Once installed you can run it with this terminal command:

```
ccsm
```

Guide by bodsda:
[http://godawski.oxyhost.com/compiz.html](http://godawski.oxyhost.com/compiz.html)

---

### Post by jcats on 2009-01-10
Thanks Michael. I did install the settings manager. I did a quick look at the link you sent, and when I have a little time, I will definitely be checking that out :cool:

jcats

---

### Post by aireq on 2009-01-12
OK I'm new to Ubuntu and have the same video card.Yet if I go to visual effects and try to change it from Non to Normal or Extra the currently open windows will flash on and off a couple times, but ends in a little  window that says "Desktop effects could not be enabled".

Here's what I get from the same commands.

[I]aireq@aireq-desktop:~$ sudo lshw -C display
  *-display:0             
       description: VGA compatible controller
       product: Radeon R350 [Radeon 9800 Pro]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-3.0 pm bus_master cap_list
       configuration: driver=fglrx_pci latency=255 mingnt=8 module=fglrx
  *-display:1 UNCLAIMED
       description: Display controller
       product: Radeon R350 [Radeon 9800 Pro] (Secondary)
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:02:00.1
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm cap_list
       configuration: latency=32 mingnt=8
[/I]

[I]aireq@aireq-desktop:~$ glxinfo | grep rendering
direct rendering: Yes
[/I]

---

### Post by aireq on 2009-01-12
Here's what i get if I try to run compiz

[I]
aireq@aireq-desktop:~$ compiz
Checking for Xgl: No protocol specified
xvinfo:  Unable to open display :0.0
not present. 
No protocol specified
xset:  unable to open display ":0.0"
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 
No protocol specified
Window manager error: Unable to open X display :0.[/I]


I also tried the install/uninstall commands recomended by tango.

Eric

---

### Post by aireq on 2009-01-12
I should also mention that I have Compiz working now .. .with out FGLX installed. 


Eric

---

### Post by jcats on 2009-01-12
You got Compiz to work, with out fglx installed? Did you install the ATI drivers? I believe (I may be wrong here), but Compiz will only work if you get the Visual Effects to run in Normal or Extra.

---

