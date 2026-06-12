---
title: "Newbie trying to install linux printer driver"
date: 2010-03-26
forum: New to Ubuntu
---

### Post by johnfrith on 2010-03-26
Hello, looking for some assistance, if anyone can help. I'm trying to set up with Ubuntu for the first time. It's taken me a long time to get my wireless network, and the sound to work, now the last thing is the printer! I have an old Samsung ML4500, and no sign of recognition on booting with the device connected. I've download the tar file for the linux i386 driver from [http://www.samsung.com/uk/support/detail/supportPrdDetail.do?menu=SP01&prd_mdl_cd=&prd_mdl_name=ML-4500&prd_ia_sub_class_cd=P](http://www.samsung.com/uk/support/detail/supportPrdDetail.do?menu=SP01&prd_mdl_cd=&prd_mdl_name=ML-4500&prd_ia_sub_class_cd=P) 

I've copied the readme text at the bottom of this message.

So my questions are:
1) The printer didn't work "out of the box", does that mean that I have to use the driver from Samsung or could the correct driver be in Ubuntu somewhere, but I have to install it? (I can't even tell what the driver is called at the moment).
2) If I do need to install the Samsung version, do I fulfil the 3 "requirements" from the installation notes (below). I'm using a fresh version of 32 bit Karmic?
3) Does it matter when the installation files are? Currently I've extracted them to directory /home/John/Downloads, and inside there there is a  folder called "image" which has the setup.sh file which I'm supposed to run. 
4) It says I need  to be "logged in as the super-user (root)". Is this satisfied if I cd to "image" and enter sudo setup.sh? Probably not as I get a message "command not found" when I do this. Does using "sudo" fulfill the super user bit? Does being in /home/john/ count as the root bit?

Sorry to ask such basic questions. 

Regards, John

SUPPORTED CONFIGURATIONS
------------------------

- Linux distributions : Redhat 6.x, Mandrake 7.x, SuSE 6.x, Debian 2.2, 
  Caldera OpenLinux 3.x, TurboLinux, Slackware 7.x, Linux/PPC, Yellow Dog,
  and newer versions.
- Linux kernel 2.2 and up
- GNU Libc version 2.1 and up

Requirements :
- GTK+ 1.2 libraries ; these usually come with the GNOME desktop environment,
  but if your distribution didn't install those by default, you will need to
  install them before you can use the graphical tools from this package.
- A working Ghostscript installation
- CUPS 1.1.x is the preferred printing system for this package, but the
  Linux Package will accommodate any other printing system based on LPD.
  CUPS 1.1.14 packages are provided as a convenience with this program, and can
  be installed or upgraded from the installer. However, users of Debian and
  Slackware distributions should make sure they have an active printing system
  (such as LPD) before proceeding with the installation.

INSTALLATION
------------

You need to be logged in as the super-user (root) to be able to install this
package.

- Run the 'setup.sh' script on the CDROM to launch the installation program, 
  if the installer didn't start automatically upon insertion of the CDROM in
  your drive.

- You may choose either the "Recommended" or "Expert" types of installation.
  "Recommended" is fully automated and won't require any interaction on your
  part. It will install the product under /usr/local/linuxprinter.
  The "Expert" installation allows you to fine-tune these settings and choose
  where the package will be installed.

- Once the installation is done, you will be offered the option to start the 
  Configuration Tool, which allows to install and configure new Linux printers
  into your Linux system.

- The configuration tool can later be launched by using the 'linux-config'
  command, or through the menu item that may have been added to your Gnome / KDE
  menus.

---

### Post by roger_1960 on 2010-03-26
Hi
In answer to question 4, Yes, sudo should give you root privileges.  It is all case sensitive - could that be the problem?  ie is it SETUP.sh?

---

### Post by patchwork on 2010-03-26
If the directory the script is in is not in a PATH directory, you will need to run ```
sudo ./setup.sh
```.  This simply tells bash to look in the current directory to find the script.

You may have to make the script executable if you haven't done so already:```
sudo chmod +x ~/Downloads/image/setup.sh
```

---

### Post by johnfrith on 2010-03-27
Thanks for posting roger_1960, setup_sh is in the correct case.

patchwork thanks for that. I've just got to the permissions section of the ubuntu pocket guide, so hopefully no-one will have to explain that to me again.

I did get setup_sh to run finally by using gksu (used instead of sudo to run graphics package) in root:

root@jf:/home/john/Downloads/image# gksu setup.sh
root@jf:/home/john/Downloads/image# 

No error messages, and no output, and no worky. Unless anyone reading has any suggestions, perhaps I'll try the "Installations and Upgrades" board.

J.

---

### Post by s_ø on 2010-03-27
I havent checked the instructions out. But look at this link [http://www.openprinting.org/printer/Samsung/Samsung-ML-4500](http://www.openprinting.org/printer/Samsung/Samsung-ML-4500)
The say it works perfectly.

---

### Post by coffeecat on 2010-03-27
> **johnfrith said:**
> 1) The printer didn't work "out of the box"

But it is supported out of the box. I've just checked. The driver for the ML-4500 is included. 

I was surprised to see you say this because my ancient Samsung ML-1210 works out of the box and has done so with every distro I've tried since 2005. There is a huge range of Samsung printers supported in a default install.

Let's go back to basics. You say "no sign of recognition on booting with the device connected". It's not necessarily auto-recognised. Boot up, connect the printer and switch it on and go to System > Administration > Printing. If the printer is not already configured, click on 'add' and follow the wizard.

If that fails for some reason, open firefox and type 'localhost:631" in the address box. Click on the "Administration" tab and then "Add Printer" and see where that takes you.

---

### Post by johnfrith on 2010-03-27
> **coffeecat said:**
> Boot up, connect the printer and switch it on and go to System > Administration > Printing. If the printer is not already configured, click on 'add' and follow the wizard.
If I run this, and click "New", it searches for a printer, but doesn't find anything. It does present a screen where I can enter a URI, but I don't know what the URI is. I have searched but all the explanations go over my head.

> **coffeecat said:**
> If that fails for some reason, open firefox and type 'localhost:631" in the address box. Click on the "Administration" tab and then "Add Printer" and see where that takes you.

This gives me a screen:
**Add Printer**

           Local Printers:   SCSI Printer 
 HP Printer (HPLIP) 
 HP Fax (HPLIP) 
    Discovered Network Printers:   
   Other Network Printers:   AppSocket/HP JetDirect 
 Internet Printing Protocol (http) 
 Internet Printing Protocol (ipp) 
 LPD/LPR Host or Printer 
 Windows Printer via SAMBA 
 Backend Error Handler 
    

This doesn't mean much to me. I tried SCSI printer, which takes me to:
**Add Printer**

         Connection:    
Examples:     [http://hostname:631/ipp/](http://hostname:631/ipp/)
    [http://hostname:631/ipp/port1](http://hostname:631/ipp/port1)

    ipp://hostname/ipp/
    ipp://hostname/ipp/port1

    lpd://hostname/queue

    socket://hostname
    socket://hostname:9100
 See ["Network Printers"]("http://localhost:631/help/network.html") for the correct URI to use with your printer.
     

Network Printers takes me to:
**Using Network Printers**

   **Using Network Printers**

  This help document describes how to discover, configure, and use TCP/IP network printers with CUPS.
  **Getting the IP Address**

****

.................................................etc.

Well, first thing is that it's not a networked printer, but ignoring that, in the middle of this page there is a table of common URI's, but no mention of Samsung.

I'm lost and my head is spinning. I'm sure this is obvious to someone, but I'm putting in a lot of hours trying to climb this learning curve. Any help appreciated.

Regards, John

---

### Post by johnfrith on 2010-03-27
> **s_ø said:**
> I havent checked the instructions out. But look at this link [http://www.openprinting.org/printer/Samsung/Samsung-ML-4500](http://www.openprinting.org/printer/Samsung/Samsung-ML-4500)
The say it works perfectly.

Thanks s_ø.

I did have to buy a new (usb) cable for the printer. Maybe that's not working.

---

### Post by johnfrith on 2010-03-27
Just tried my new cable with my old laptop, and it works, so it's not a problem with the cable.

---

### Post by coffeecat on 2010-03-28
It's likely that Ubuntu is not detecting the printer, not that it doesn't have the drivers. Which may be a hardware issue.

Question: are you able to detect any other usb device in the port you're using? Have you tried a different usb port for the printer. You're not, by chance, using a usb to parallel converter between the printer and usb cable?

Try this. Boot up with the live CD so that you're getting a completely default, albeit live, Ubuntu system. Plug in and switch on the printer. Is it detected? Can you configure it and print a test page? If so, there's something wrong with your installed version of Ubuntu which we need to look into. If not....

Boot up the live CD on the laptop (assuming that the laptop can run it) - or on another machine - and do the same. If the live CD can detect and configure the printer, but not the original machine, then you have a hardware problem.

By the way, running the CD live does not in any way affect any installed OS, **unless** you mount the hard drive and edit/change any files on it. So running the live CD should not damage whatever's on the hard drive. If you manage to configure the printer in the live session, all this is lost when you power down, so that won't solve the issue, merely be useful diagnostically.

---

### Post by johnfrith on 2010-03-28
> **coffeecat said:**
>  You're not, by chance, using a usb to parallel converter between the printer and usb cable?

Many many many thanks coffecat - I am indeed using usb to parallel cable! When you posted the above, I looked on the forum for problems with usb / parallel connections and found:
[http://ubuntuforums.org/showthread.php?t=1436079](http://ubuntuforums.org/showthread.php?t=1436079)    & 
[http://ubuntuforums.org/showthread.php?t=894223](http://ubuntuforums.org/showthread.php?t=894223)

In these, using a URI of **parallel:/dev/usblp0 **is suggested. I manually added the printer using System > Admin > Print, and entered the above URI, and now the printer works!

This is a workaround, though. I don't know why the system didn't recognise the printer automatically.

---

### Post by johnfrith on 2010-03-28
I thought I'd be a good citizen and report the problem, but found it was already being dealt with. See:

[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/436495?comments=all](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/436495?comments=all)

Apparently since Karmik usblp module has been blacklisted. Sounds like without this system won't autodetect parallel printers. So perhaps a better solution would be to remove usblp from blacklist, but as I'm now working and maybe it's blacklisted for a good reason, I'm going to "move on".

It's only taken me just under 3 months to get Ubuntu working on my laptop! Shows how much I dislike Microsoft. Now I can finally start transferring off my old system.

Thanks for everyone's help.

---

### Post by coffeecat on 2010-03-28
> **johnfrith said:**
> It's only taken me just under 3 months to get Ubuntu working on my laptop! Shows how much I dislike Microsoft.

A man after my own heart! :)

When I started with Linux in 2005 (mostly Fedora then) I couldn't get an internet connection reliably for at least three months. Sometimes I could browse the internet; mostly I got nothing at all. At the time I understood and knew the square root of very little at all concerning networking - which didn't help. Eventually, I managed to get reliable connections by using a static local network IP address and manually setting my ISP's DNS servers in resolv.conf (which got splattered every time I rebooted). Exceedingly long story short - the firmware in my router whose manufacturer shall be nameless (cough - DLink - splutter! :wink:) was over a year old and unable to deal with IPv6 addressing. Updated the firmware and Robert has been my Uncle ever since. More especially since I moved onto a Linksys router and more recently a Netgear one.

I persevered for over three months and learnt something about networking in the process. It was very frustrating but I was motivated by my desire to free myself of the Microsoft shackles. Which is why I have little sympathy for those coming to these forums, complaining that they've wasted all of a few hours trying to get wireless working and threatening to go back to Windows. :rolleyes:

Good luck with your Ubuntu-ing!

---

