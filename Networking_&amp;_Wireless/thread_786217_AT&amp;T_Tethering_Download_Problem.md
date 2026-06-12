---
title: "AT&amp;T Tethering Download Problem"
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by quickwitt on 2008-05-07
I live in a rural area with no broadband but we do have a strong 3G signal from AT&T. As a result we tether cell phones for internet connectivity. Using wvdial and a USB cable I got my connection set up to my Motorola Razr V3xx with no problem using standard AT commands. The connection is much faster under Ubuntu 8.4 than XP or Vista. The problem is every download stalls after just a few hundred kilobytes. It isn't the connection because I can download fast and furious under Windows. I am posting from this connection. The problem is specific to the Linux environment. Any ideas?

here are the contents of wvdial.conf

Init1 = ATZ 
Init2 = AT+CGDCONT=1, "IP", "WAP.CINGULAR"
Init3 = AT+CGATT=1 
Init4 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
Modem = /dev/ttyACM0 
Modem Type = USB Modem 
ISDN = 0 
Baud = 921600 
Stupid mode = 1 
New PPPD = yes 
Phone = *99# 
Password = test
Username = test

Again, there are no connectivity issues. I can browse and even stream content at a pretty good speed. The problem is only with downloads.

Thanks in advance!

---

### Post by quickwitt on 2008-05-08
Help? Anyone?

---

### Post by quickwitt on 2008-05-10
O.K. Thanks for all of the help!:):confused:

I found a link in an unrelated post to this guide

[http://davestechsupport.com/blog/2008/02/28/how-to-connect-linux-to-your-cellular-internet/](http://davestechsupport.com/blog/2008/02/28/how-to-connect-linux-to-your-cellular-internet/)

which suggest using the command [COLOR="Red"]wvdialconf[/COLOR] to probe your phone and create a default wvdial.conf file.

Next I played around with the commands until I came up with this

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1, "IP", "WAP.CINGULAR"
ISDN = 0
Modem Type = USB Modem
New PPPD = yes 
Phone = *99#
Modem = /dev/ttyACM0
Username = user
Password = pass
Baud = 460800

I am now able to download at up to 230 KB/sec! Not bad and almost twice as fast as under Vista.

Someone who has a better understanding of AT commands might be able to make a more elegant solution. If so, I am all ears. 

I hope this info might help someone else.

Cheers!

---

### Post by Casey Timm on 2008-05-10
I am having the same problem, all of my downloads stop at random points of just a few hundred KB, but the above solution didn't help. Any ideas?

---

### Post by Darrena on 2008-05-10
I as searching for my old PPP script but I couldn't find it since I had this same problem and eventually solved it but forgot how I did it!   In the meantime you may want to consider taking a look at GPRSEC (See my signature for packages) or UMTSmon ([http://umtsmon.sourceforge.net/](http://umtsmon.sourceforge.net/)).

The good news is that Network Manager 0.7 has VERY good support for aircards but the bad news is that it is still under some pretty heavy development.   I am running a snapshot on one of my laptops and it works impressively well.

---

### Post by quickwitt on 2008-05-11
Casey Timm: Give some more details. Who is your carrier, what is your phone, how do you connect the phone to the computer, which version of Ubuntu, etc.

Also, post the contents of your wvdial.conf file.

-----------------------------------------------------


I added 2 lines that make the PPP connection occur much faster:

Stupid Mode = 1
Auto DNS = 1

The entire wvdial.conf looks like this

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1, "IP", "WAP.CINGULAR"
ISDN = 0
Modem Type = USB Modem
New PPPD = yes 
Stupid Mode = 1
Auto DNS = 1
Phone = *99#
Modem = /dev/ttyACM0
Username = user
Password = pass
Baud = 460800

---

### Post by Casey Timm on 2008-05-11
I am using a Motorola Krzr K1, and my carrier is ATT, and for wvdialconf I have tried a direct copy yours, and just the default, all have let me get online, but the download problem still exists. I have tried on ubuntu 7.10 and 8.04. Also I have used pon, vwdial, GPRS Easy Connect, and Umtsmon. Here is my current vwdialconf

[Dialer Defaults]
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1, "IP", "WAP.CINGULAR"
Modem Type = USB Modem
New PPPD = yes
Phone = *99#
ISDN = 0
Username = WAP.CINGULAR
Init1 = ATZ
Password = Cingular1
Modem = /dev/ttyACM0
Baud = 460800

---

### Post by Casey Timm on 2008-05-15
I am still having this issue, and would rather not switch to windows where, it works. Anyone one have any ideas?

---

### Post by tobiasly on 2008-06-06
I just got tethering working beautifully on my Eee PC using usb-rndis-lite instead of wvdial. My Eee isn't running Ubuntu (yet! but that's another story...) but apparently many have gotten it working in Ubuntu as well.

Don't think this one is in the Ubuntu repo (but it definitely should be, how do we suggest it?) so you'll need to compile from source. And since it's a kernel driver you need the kernel sources for your current version (and you'll need to recompile when upgrading the kernel).

Anyhoo, once it's working, all you do is connect your phone and type "dhclient rndis0" in Ubuntu, no modem commands to mess with since it just uses the settings that are already in your phone.

Here is the link to the Eee instructions (there's even a note or two for Ubuntu users): [http://wiki.eeeuser.com/howto:install_synce_usb_rndis_lite_drivers](http://wiki.eeeuser.com/howto:install_synce_usb_rndis_lite_drivers)

Here's similar instructions for Ubuntu, although not as detailed: [http://ubuntuforums.org/showthread.php?p=3588717#post3588717](http://ubuntuforums.org/showthread.php?p=3588717#post3588717)

Both of these involve getting the driver from a Subversion repo using "svn" so you'll need subversion package installed (and usual build-essential of course).

If this were added to the Ubuntu repo, than anyone could simply plug in their cell phone and it would work instantly! How do we suggest new packages for the repo?

---

### Post by quickwitt on 2008-06-23
Strangely, my downloading issue has returned. I would suspect that AT&T was thwarting my efforts but it works fine in Vista. I don't know enough about networking protocols to troubleshoot the issue. I can connect and surf fine. All downloads stall after 10-20MB. If I pause/resume the download it picks up rather quickly to 200+ KB/s then slowly crashes until it stalls out again. I have tried everything that I can think of including adjusting the baud rate, turning hardware/software flow control on and off, and tinkering with the AT commands (although I know nothing about them). Nothing solves the problem. 

I know that there is someone in the Ubuntu community that has the answer! 

Thanks!

---

### Post by Casey Timm on 2008-06-25
The problem is still persisting for me also. Except it appears in vista for me now. The only os that handles the connection is XP, and here is a strange one, if I set up forwarding any XP client will work fine, while I still can't maintain a connection, along with any Ubuntu clients. Any body get this working correctly?

---

### Post by jvain2005@gmail.com on 2008-08-18
I think, this is AT&T problem. I read in terms and condition that 3G networks are optimized for internet browsing but not for downoads.

---

