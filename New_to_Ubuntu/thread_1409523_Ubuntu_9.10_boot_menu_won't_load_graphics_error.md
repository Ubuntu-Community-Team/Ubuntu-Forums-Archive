---
title: "Ubuntu 9.10 boot menu won't load graphics error"
date: 2010-02-17
forum: New to Ubuntu
---

### Post by a-marquardt on 2010-02-17
I have a new hard drive that was preloaded with Ubuntu Super OS and other programs.
It was loaded on a computer that had an Nvidia graphics card. When I try to boot from this hard drive I get a graphics error message saying:

Ubuntu is running in low graphics mode. The following error was encountered you may need to update your configuration to solve this.
(EE)Nvidia: failed to load the Nvidia kernel Module please check your
(EE) Nvidia: systems kernel log for additional error messages
(EE) failed to load module "nvidia"(module specific error 0)
(EE) no drivers available

When you enter OK it gives this window:

What would you like to do?
>Run Ubuntu in low graphics mode for just this session
>reconfigure graphics
>troubleshoot the error
>Exit console login

All options result in black screen crash except troubleshoot the error

That window says:

What would you like to review?
>Review Xserver log file
>Review startup errors
>Edit config file 
>Archive config and log

The first three options lead me to file/logs which are to long to duplicate here as I have no means to screen capture them.

I can reboot from the Ubuntu super OS install DVD and operate Ubuntu without installing it so that I can see Ubuntu files on the new hard drive. I cannot run any of the programs stored on the drive.

My question is there a way to reconfigure my graphics so that I can boot from the already installed Ubuntu on the new hard drive possibly using the install DVD. Or am I forced to reinstall Ubuntu on the new drive destroying everything that is loaded on to it.
Art

---

### Post by kouter on 2010-02-17
it'd be helpful if you could post the config file...

if it's xorg.conf you could try modifying it to use the "vesa" driver.

My ubuntu didn't recognize my nvidia card after fresh install, and I installed drivers via System > Admin > Hardware Drivers.  If you can boot live or with vesa this *should* get it working.

---

### Post by a-marquardt on 2010-02-17
Is there a way I can access the config file through file browser in Ubuntu. As I said before I can see all the folders on the new harddrive using the install disc operating Ubuntu without installing it. I am unsure what folder it would be in, details would be appreciated.:D

---

### Post by kouter on 2010-02-17
```
gedit /etc/X11/xorg.conf
```

I've noticed newer releases of ubuntu don't utilize an xorg.conf, but if it's not there, then you can sudo dpkg-reconfigure xserver-xorg

---

### Post by kouter on 2010-02-17
just reread OP....

what kind of gfx card is in your computer currently? is it not nvidia?

---

### Post by a-marquardt on 2010-02-17
Tried this in terminal but the xorg.conf file came up blank

"Code:
 	gedit /etc/X11/xorg.conf 
I've noticed newer releases of ubuntu don't utilize an xorg.conf, but if it's not there, then you can sudo dpkg-reconfigure xserver-xorg"

This command did not work at all. sudo dpkg-reconfigure xserver-xorg"

I do not have a graphics card I have graphics built into the mother board MSI 6390 VIA Pro SavageDDR KN 266 Chipset ProSavage 8 2D/3D graphic Controller. When I installed Ubuntu on another drive it was not necessary to use any proprietary drivers for the graphics it worked just fine. I think that the drivers in Ubuntu are adequate for the job it is just that it is trying to load something I don't need.

---

### Post by kouter on 2010-02-17
```
sudo dpkg-reconfigure xserver-xorg
```

make sure to move the generated conf file to /etc/X11/xorg.conf

---

### Post by a-marquardt on 2010-02-17
Command does not generate a file. Nothing to move. Could it be that by operating from the install disc in the operate without installing mode that I am unable to access the config file.

---

### Post by kouter on 2010-02-17
my mistake, sudo xorg -configure

that should gen you a new xorg.conf

---

### Post by a-marquardt on 2010-02-17
I rebooted from the new drive and got the error message. Then went to troubleshoot the error, Then edit config file. Here is the config file as it appeared:

Section "Screen"
   Identifier "default screen"
   Default depth  24
End Section

Section "Module"
     Load glx
End Section

Section "Device"
Identifier"default Device"
  Driver "nvidia"
  Option "no logo" "true"

---

### Post by a-marquardt on 2010-02-17
Terminal would not accept "sudo xorg -configure" as a valid command.

---

### Post by JerichoKru on 2010-02-17
> **kouter said:**
> my mistake, ```
sudo Xorg -configure
```

that should gen you a new xorg.conf

Make sure the X in the command is uppercase.

---

### Post by kouter on 2010-02-17
=X ...

you know I was thinking this really demonstrates why you should have a separate /home partition.  Because ever since I did it, I have no issue with popping in an install cd and doing a clean install.  Great when you get those bugs that you can't figure out how to fix and just need to get back to square one.

---

### Post by a-marquardt on 2010-02-17
This is the response I got from the command 
sudo Xorg -configure

ubuntu@ubuntu:~$ sudo Xorg -configure

Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.


Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 

 ddxSigGiveUp: Closing log
ubuntu@ubuntu:~$

---

### Post by Johnny19734 on 2010-02-17
Goto Ubuntu's Software center and install envy. This utility will upgrade your kernel and graphics drivers.
:P

---

### Post by theozzlives on 2010-02-17
```
sudo rm /tmp/.X0-lock
```

---

### Post by a-marquardt on 2010-02-17
Goto Ubuntu's Software center and install envy. This utility will upgrade your kernel and graphics drivers.
:razz:
Tried this running from install disc without installing.  EnVy installed and appeared in Applications under system tools but did nothing, wouldn't load. Is there another way to install envy other than going to the software options under applications. Remember I cannot boot from the drive that has all my applications and Ubuntu on it that gives me a graphics error and no boot menu.


Terminal would not accept this command
sudo rm /tmp/.X0-lock

---

### Post by Johnny19734 on 2010-02-18
> **a-marquardt said:**
> Goto Ubuntu's Software center and install envy. This utility will upgrade your kernel and graphics drivers.
:razz:
Tried this running from install disc without installing.  EnVy installed and appeared in Applications under system tools but did nothing, wouldn't load. Is there another way to install envy other than going to the software options under applications. Remember I cannot boot from the drive that has all my applications and Ubuntu on it that gives me a graphics error and no boot menu.


Terminal would not accept this command
sudo rm /tmp/.X0-lock



That wont work....the live disc is for that session. At this point you will need to do one of the following.

1) Boot to the live disc (hopefully you can connect to the internet) and download the latest nvidia drivers.

[http://www.nvidia.com/Download/index5.aspx?lang=en-us](http://www.nvidia.com/Download/index5.aspx?lang=en-us)

Tip: I alway re-name the .run file to nvidia.run. Easier for command line.

Once this is done, place the nvidia.run in the old home directory.(original jacked up install) 

After you complete this boot into the messed up install and boot up. 

Go into command line mode. 

You will need to "CD" or Change Directory to the location of the "nvidia.run" file. 

Once this is done, type in the command "ls" this will give you the list of folder and files in the folder that you are in. If nvidia.run is there your good to go for the next step.

Now, just type "sudo sh nvidia.run"

This should install the new most current driver. But remember if you do it this way. Every time a new kernel comes out you may have to reinstall the driver. If this doesn't work you'll have to do it the other ways listed below.

or 

2) Edit the .xorg. (No thanks) 

or 

3) Back up everything and do a fresh install.


I hope this helps. Please feel free to ask any more questions.

-JJ

---

### Post by a-marquardt on 2010-02-18
Thanks for your advice, the only question I have for now is how will downloading Invidia drivers help me since I don't have an Invidia graphics card? 

This whole debacle started when a friend downloaded for me on his computer a bunch of programs and ubuntu onto this new drive. He has Invidia so he had to set it up for Invidia to get it to work. Now I am afraid that the original drivers that are normally installed with Ubuntu have been wiped out. On previous installs the drivers worked just fine for my current system no need to upgrade to a proprietary driver. 

I have another drive with Ubuntu installed on it that works fine when I boot from it. Is it possible somehow to remove a driver file from the working version and add it to the non working version? Note I can use the working drive to boot from and see the folders from the non functioning Ubuntu install on the new drive. Will that work?

---

### Post by Johnny19734 on 2010-02-18
> **a-marquardt said:**
> Thanks for your advice, the only question I have for now is how will downloading Invidia drivers help me since I don't have an Invidia graphics card? 

This whole debacle started when a friend downloaded for me on his computer a bunch of programs and ubuntu onto this new drive. He has Invidia so he had to set it up for Invidia to get it to work. Now I am afraid that the original drivers that are normally installed with Ubuntu have been wiped out. On previous installs the drivers worked just fine for my current system no need to upgrade to a proprietary driver. 

I have another drive with Ubuntu installed on it that works fine when I boot from it. Is it possible somehow to remove a driver file from the working version and add it to the non working version? Note I can use the working drive to boot from and see the folders from the non functioning Ubuntu install on the new drive. Will that work?

What kinda card do you have? If intel, you will have to edit the .xorg (PIA)

---

### Post by a-marquardt on 2010-02-18
I do not have a graphics card I have graphics built into the mother board MSI 6390 VIA Pro SavageDDR KN 266 Chipset ProSavage 8 2D/3D graphic Controller. When I installed Ubuntu on another drive it was not necessary to use any proprietary drivers for the graphics it worked just fine. I think that the drivers in Ubuntu are adequate for the job it is just that it is trying to load something I don't need. I have trouble editing the Xorg. It doesn't seem to work from the live disc.

---

### Post by Johnny19734 on 2010-02-18
> **a-marquardt said:**
> I do not have a graphics card I have graphics built into the mother board MSI 6390 VIA Pro SavageDDR KN 266 Chipset ProSavage 8 2D/3D graphic Controller. When I installed Ubuntu on another drive it was not necessary to use any proprietary drivers for the graphics it worked just fine. I think that the drivers in Ubuntu are adequate for the job it is just that it is trying to load something I don't need. I have trouble editing the Xorg. It doesn't seem to work from the live disc.

The location of the xorg file is:

"/etc/X11/xorg.conf"

I'm not sure if you can edit it from a live cd. If you can,  find the location of the original UBUNTU install and use a utility called "gedit" (gnome editor)

SO.....You will need to do something like this,

Sudo gedit /etc/X11/xorg.conf in terminal.

Now!! before you just copy and paste this into terminal you will need to find the location of the xorg for the original install. It wont be in /etc/X11/xorg.conf on the live CD. Hopefully the live CD mounts the HD for you and you can browse to find it.

So it would be:

Sudo gedit /(path of original xorg.conf file)/



Once this is done, I would start by changing :

Section "Device"
Identifier"default Device"
Driver "nvidia" <------------ to VESA 
Option "no logo" "true"

Again, I hate this process. but its a start. Hopefully you can find the original xorg file. 

For more XORG info check out:


[http://www.x.org/wiki/](http://www.x.org/wiki/)

---

### Post by a-marquardt on 2010-02-18
Here is an update on what has happened When I first go to boot from the drive that has the graphics problem it gives error messages one window option is to troubleshoot the problem. In this window there is an option to edit config file.

"I rebooted from the new drive and got the error message. Then went to troubleshoot the error, Then edit config file. Here is the config file as it appeared:

Section "Screen"
   Identifier "default screen"
   Default depth  24
End Section

Section "Module"
     Load glx
End Section

Section "Device"
Identifier"default Device"
  Driver "nvidia"
  Option "no logo" "true"  "

I replaced "nvidia" with "VESA"
I was then able to launch to the desk top I did not get a menu for boot though. I am now able to get internet and have access to all programs that were loaded with Ubuntu on this drive.
  
The graphics were not good initially so I had to increase resolution and tweak the settings on the monitor to adjust position and size of frame. 

My next question, in the section "Module" are there better options than "glx", and why didn't my boot menu appear?

---

### Post by Johnny19734 on 2010-02-19
> **a-marquardt said:**
> Here is an update on what has happened When I first go to boot from the drive that has the graphics problem it gives error messages one window option is to troubleshoot the problem. In this window there is an option to edit config file.

"I rebooted from the new drive and got the error message. Then went to troubleshoot the error, Then edit config file. Here is the config file as it appeared:

Section "Screen"
   Identifier "default screen"
   Default depth  24
End Section

Section "Module"
     Load glx
End Section

Section "Device"
Identifier"default Device"
  Driver "nvidia"
  Option "no logo" "true"  "

I replaced "nvidia" with "VESA"
I was then able to launch to the desk top I did not get a menu for boot though. I am now able to get internet and have access to all programs that were loaded with Ubuntu on this drive.
  
The graphics were not good initially so I had to increase resolution and tweak the settings on the monitor to adjust position and size of frame. 

My next question, in the section "Module" are there better options than "glx", and why didn't my boot menu appear?

You dont have correct the driver installed for that graphic card. You are running a generic graphic mode.  Didn't you say you had a SAVAGE card? Old!!! but it should be compatible. 

Check this link out!

[http://manpages.ubuntu.com/manpages/hardy/man4/savage.4.html](http://manpages.ubuntu.com/manpages/hardy/man4/savage.4.html)

Okay, I believe you will need to edit you xorg file once more and replace these values with this, thats if you card is savage!

     Section "Device" <------------
     Identifier "devname"<---------
     Driver "savage" <---------
         

Remember:

Sudo gedit /etc/X11/xorg.conf 

Save it and reboot and you should have full video acceleration !!!

---

### Post by halitech on 2010-02-19
> **Johnny19734 said:**
>    

Remember:

Sudo gedit /etc/X11/xorg.conf 

Save it and reboot and you should have full video acceleration !!!

if using graphical apps, you should use GKSUDO not sudo to launch them

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by a-marquardt on 2010-02-19
I was able to get the graphics to work although I don't think 100% I had to tweak the monitor some but it was than running under VESA.
 The thing I don't understand now is why I can't get the boot menu to appear, it just goes to Ubuntu splash screen directly, and Ubuntu will not shutdown or restart it just goes to black screen while the computer stays on.

---

### Post by Johnny19734 on 2010-02-21
> **halitech said:**
> if using graphical apps, you should use GKSUDO not sudo to launch them

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Why is it an issue?
Well, to be perfectly honest, most of the time it isn't. For a lot of applications, you can run them the improper way—using sudo for graphical applications and see no adverse side effects.

Okay....so if it didn't work then use "GKSUDO" but, I have never had an issue in my life...

---

### Post by Johnny19734 on 2010-02-21
> **a-marquardt said:**
> I was able to get the graphics to work although I don't think 100% I had to tweak the monitor some but it was than running under VESA.
 The thing I don't understand now is why I can't get the boot menu to appear, it just goes to Ubuntu splash screen directly, and Ubuntu will not shutdown or restart it just goes to black screen while the computer stays on.

Dude, replace "VESA" with "Savage" and it will fix your issues.

---

### Post by halitech on 2010-02-21
> **Johnny19734 said:**
> Why is it an issue?
Well, to be perfectly honest, most of the time it isn't. For a lot of applications, you can run them the improper way—using sudo for graphical applications and see no adverse side effects.

Okay....so if it didn't work then use "GKSUDO" but, I have never had an issue in my life...

most of the time you probably won't but isn't it better to get in the habit of doing it correctly instead of risking that something breaks and you have to try and resolve an issue?

---

### Post by a-marquardt on 2010-02-21
I replaced VESA with Savage and the graphics appeared to work better but then after a few tries I realised I had created a new problem I have no sound. The sound control is completely missing from the menu bar. I went to switch back the next day to VESA which sorta worked and had sound only to find that Terminal rejects the command SUDO. Using gedit /etc/X11/xorg.conf I can get the file but when I try to edit it, it says I am not authorised to do so. So I can't change the settings. I am going to install a graphics card so that I have more graphics memory hopefully this will solve some of my problems. Oh GKSUDO didn't work either same problem?

---

### Post by Johnny19734 on 2010-02-22
> **a-marquardt said:**
> I replaced VESA with Savage and the graphics appeared to work better but then after a few tries I realised I had created a new problem I have no sound. The sound control is completely missing from the menu bar. I went to switch back the next day to VESA which sorta worked and had sound only to find that Terminal rejects the command SUDO. Using gedit /etc/X11/xorg.conf I can get the file but when I try to edit it, it says I am not authorised to do so. So I can't change the settings. I am going to install a graphics card so that I have more graphics memory hopefully this will solve some of my problems. Oh GKSUDO didn't work either same problem?

Not sure how the video detection would effect your sound but let me know what card you get. You should stick with nvidia. If this is an old PC which it sounds like you can get a good PCI card from NEWEGG.com for cheap. 9400's/9500's are good work station cards that you can use with a newer computer if that old one craps out. 

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010380048%201069609642%20106792522&name=GeForce%209%20series](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010380048%201069609642%20106792522&name=GeForce%209%20series)

---

### Post by a-marquardt on 2010-02-24
Got a Ge Force Nvidia Graphics Card 5200 256MB PCI Type. Of course the install disc will not work with Ubuntu. When I went into Hardware Drivers It gave me suggestions for drivers and said that the driver needed to be activated. When I went to Activate it, it said I was not authorised. I went to authorisations and set everything to yes and still I was not authorised. I reloged in using my password and still I was not authorised. What am I doing wrong?

---

### Post by a-marquardt on 2010-02-24
I Installed  Envy and tried updating that way. According to Envy the 9.1 Driver is incompatible with Nvidia and not recommended. The Ubuntu5.0 driver was so I installed it. How can I get the latest driver.

---

