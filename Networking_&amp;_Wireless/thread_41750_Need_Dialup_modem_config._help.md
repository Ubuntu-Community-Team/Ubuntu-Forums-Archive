---
title: "Need Dialup modem config. help"
date: 2005-06-14
forum: Networking &amp; Wireless
---

### Post by retsel on 2005-06-14
Delete

---

### Post by conall on 2005-06-14
At first, you'll need to know what modem is installed onto your PC. Winmodems are sightly different to configure, cus you have to install a "driver" to get them running. I'm installing a Smartlink winmodem, and can post a how-to when successfully installed it.

---

### Post by retsel on 2005-06-14
It is a Winmodem, and the Ubuntu Device Manager has correctly identified it as a Conexant HSF 56K HsFi Modem. From the information I could get from the W98 connection it is connected to Com3 port. I've gone to System>Admin>Networking and tried to figure out how to at least try it, but I can't seem to get past there.

---

### Post by az on 2005-06-14
[http://test.wiki.ubuntu.com/forum/hardware/Conexant](http://test.wiki.ubuntu.com/forum/hardware/Conexant)

Sorry.

---

### Post by retsel on 2005-06-14
Thanks for the information about the modem, however I'm not concerned about the modem itself (I'll get another one if need be), my concern is that I can't figure out how to configure a dialup modem on Ubuntu. I've tried several times to put the info into what I think is the right screen, but nothing seems to happen. I think I need step by step leading by the hand (so to speak).  Thanks.

---

### Post by TeeJay on 2005-06-14
[QUOTE=retsel]Thanks for the information about the modem, however I'm not concerned about the modem itself (I'll get another one if need be), my concern is that I can't figure out how to configure a dialup modem on Ubuntu. I've tried several times to put the info into what I think is the right screen, but nothing seems to happen. I think I need step by step leading by the hand (so to speak).  Thanks.[/QUOTE]

You can download "[gnomeppp](http://www.gnome-ppp.org/download/0.3/gnome-ppp-0.3.21.tar.gz)" a gnome based dialer that uses a similar interface to the way windows does. It fits on a floppy so you can transfer it to Ubuntu from Win98.

---

### Post by retsel on 2005-06-14
Thanks for the hint! That sounds good. I'll see if I can find it and download it. I've, of course never loaded a program into Ubuntu and run it, so this will be interesting. Do you have any hints about how to do that?

---

### Post by TeeJay on 2005-06-15
[QUOTE=retsel]Thanks for the hint! That sounds good. I'll see if I can find it and download it. I've, of course never loaded a program into Ubuntu and run it, so this will be interesting. Do you have any hints about how to do that?[/QUOTE]

I'm by no means a expert but I can usually work thing out with the help of the forum and google.

This might be a better option.

Download the deb file from here:
[http://linux.org.by/debian/pool/main/g/gnome-ppp/gnome-ppp_0.3.11-2_i386.deb](http://linux.org.by/debian/pool/main/g/gnome-ppp/gnome-ppp_0.3.11-2_i386.deb) 

Then in a terminal ( applications : systems tools : terminal ) write in 
 sudo dpkg -i gnome-ppp_*something*.deb. ( with the actual path to the deb file)

eg. sudo dpkg -i /home/retsel/desktop/ gnome-ppp_0.3.11-2_i386.deb

It should show up in menu :applications: internet.

You will also need wvdial, ppp and pppconfig which can be install from the Ubuntu CD from Synaptic.

To finnish type sudo pppconfig in the terminal and setup account information in the configuration utility.


Someone probaly has a better/different way, but there isn't much help for us users in the stone age still on dialup.

---

### Post by retsel on 2005-06-15
Thanks for the input! I'm really going to show how newbie I am here: I was able to download the deb (which I assume means debian) file, and get it over onto Ubuntu. I have not done the sudo dpkg command yet because I don't understand what you mean about the wvdial, ppp, and pppconfig files. What is their purpose? Are they executable files? If I can find them on the CD and get them onto Ubuntu, where do I put them, and what do I do to/with them?

I really appreciate your efforts to help!

---

### Post by TeeJay on 2005-06-15
They are executables of sorts, think of them more as software that install in the background that work with gnomeppp rather than programs you acually need to run.
sort of like the drivers that come on a CD when you by a new modem.

They may already be installed, but the easiest way to check is to type these commands in a terminal one by one.

sudo apt-get install wvdial
sudo apt-get install ppp
sudo apt-get install pppconfig

enter your password at the promps and answer y to any questions. Once those 3 are installed you won't need to worry about where they go or what they do, Ubuntu will put them in all the right places.

To finish off in the terminal again type.

pppconfig

"I will also direct you to  here [http://ubuntuguide.org/](http://ubuntuguide.org/) it's a great Ubuntu guide that has helped me out tremediously.

Good luck with it

---

### Post by retsel on 2005-06-15
I'll see if I can do it. Thanks very much for taking the time to help!

---

### Post by flyboy_2003 on 2005-06-19
By the way, I have Gnome PPP installed, but I am having some issues with permissions. If I try to dailup it fails and tells me that I do not have sufficient permissions.

So, I added myself to the dialout group. Then I went into the /dev directory and did a chown on both the /dev/modem symbolic link, and also to the correct character device for my modem, which is /dev/ttySHSF0. The owner and group for both of these was root and root, so I changed it to root and dialout.

This worked just fine, and I was able to use Gnome PPP.

Here is the problem: when I reboot my machine, those two entries that I changed to root and dialout, have been changed back to root and root again. Now I am back to square one!

Anyone know why this is happening? How can I keep /dev/modem and /dev/ttySHSF0 with the owner root and the group dialout?

Thanks.

---

### Post by norman_h on 2005-07-11
[QUOTE=flyboy_2003] How can I keep /dev/modem and /dev/ttySHSF0 with the owner root and the group dialout?

Thanks.[/QUOTE]

You have to change the udev permissions.  Edit this file:
/etc/udev/permissions.d/ude.permissions

---

