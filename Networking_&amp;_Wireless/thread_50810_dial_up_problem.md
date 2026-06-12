---
title: "dial up problem"
date: 2005-07-21
forum: Networking &amp; Wireless
---

### Post by swong1 on 2005-07-21
Hi all,

I have a Dell 6000 running dual boot (Windows XP Home + Ubuntu Hoary Hedgehog). I have trouble connecting to my isp via dial up. I ran *pppconfig* to configure the dial up files. I then ran *pon <isp_provider_name>* but nothing happened. Running *plog* gives the following error message:

can't get terminal parameters:  input/output error.

I also tried *wvdialconf wvdial.conf*, but got the following error message:

sorry, no modem was detected.

What gives? I have no problem connecting to isp under Windows. The property manager shows that the modem is a Conexant D110 MDC v.9x running at port COM3 (ttyS2 in Linux). Is it a driver problem? Any ideas? I am a newbie, so a detailed solution would be much appreciated.

---

### Post by jasmuz on 2005-07-21
Extra Extra Read all about Winmodems:

[www.linmodems.org](www.linmodems.org)

---

### Post by swong1 on 2005-07-21
[QUOTE=jasmuz]Extra Extra Read all about Winmodems:

[www.linmodems.org](www.linmodems.org)[/QUOTE]

I have found this website before, for some reason, it only shows the banner and nothing else. Clicking links doesn't work, refresh doesn't work.  :-?

---

### Post by OscarGortez on 2005-07-22
I had this same problem after searching the forums I found winmodems which are basicly all pci modems (from what i hear) basicly make windows do most of the work decrypting data packets and what so this causes a problem under LINUX systems... if you can't view linmodems.com there's a program called scan modem that'll tell you your chipset (which you seem to know already) and tell you where you can get a driver, i have a simaliar chipset in my modem so you should be able to find the driver install it and connect just fine... sorry but the links illude me at this moment...

---

### Post by swong1 on 2005-07-22
[QUOTE=OscarGortez]I had this same problem after searching the forums I found winmodems which are basicly all pci modems (from what i hear) basicly make windows do most of the work decrypting data packets and what so this causes a problem under LINUX systems... if you can't view linmodems.com there's a program called scan modem that'll tell you your chipset (which you seem to know already) and tell you where you can get a driver, i have a simaliar chipset in my modem so you should be able to find the driver install it and connect just fine... sorry but the links illude me at this moment...[/QUOTE]

Thanks OscarGortez, I will continue to look for a solution. Your success at least gives me hope that there is a solution. Thanks for your explanations. It seems that the problem lies with the driver. Where can I find and run (Windows or Linux?) this "scan modem" program? I hope it's Windows, since Ubuntu can't seem to detect it. If you remember the links, please do post them. Thanks!

ps. I can connect to linmodems.org now.  :)

---

### Post by lostinzim on 2005-07-23
I am a complete newbie to Ubuntu and am trying to understand how it works.  I have an NEC Versa P440 laptop which i cant use dial up to connect to the internet.  In network settings it says the modem connection is not active.  When i click on properties and try to autodetect the modem, i get an Information window that comes up which says "Could not autodetect modem device - check thatthe device is not busy and that it is correrctly attached to the computer".  The modem worked fine before while running XP though.  I have tried going through the System administrator to find the problem but have failed.  Any ideas would be appreciated!  

I have downloaded the scan modem program mentioned above and will try that, but if anyone can give me a simpler way forward that would be great.  Thanks

---

### Post by swong1 on 2005-07-23
All right, here's what I've done so far:

1. Downloaded listmodem_app (for Windows XP) from [www.conexant.com/support/md_driverdownload.jsp](www.conexant.com/support/md_driverdownload.jsp)

2. Unpacked the package and ran ListMdm.exe

3. The results showed that I have an HSF modem.

4. Ran *uname -r* under Ubuntu to find out the kernel version (it's 2.6.10_5_386).

4. Went back to Windows. Went to [www.linuxant.com/drivers](www.linuxant.com/drivers) to download the corresponding driver (under HSF solfmodem driver link). They have an Ubuntu 5.04 specific driver, so that's nice. Choose the appropriate version and download it. Unpack it and save it to a CD.

5. Restart the computer and boot it with Ubuntu. Insert the CD and copy the content to my home directory.

6. Run the following command in my home directory:

*sudo dpkg -i hsfmodem*.deb* 

7. It prompts for the region name, email address, license, etc. I want to try for free first, so under license agreement, entered FREE. If everything works out, then I'll fork out for the full version ($15). For the free version, it only allows the modem to transmit at a maximum rate of 14.4kb/s. I had to install hsfmodem twice before it worked. The first time, installation stalled at requesting region name. If it doesn't prompt, run *hsfconfig*.

8. Just as lostinzim, I tried to configure and activate the dial up properties by autodetecting my modem. Before installing hsfmodem, it couldn't detect the modem, now, it detects it at /dev/modem, which is a symbolic link to /dev/ttySHSF0. I ran *sudo wvdialconf wvdial.conf* and this time it detected the modem at /dev/ttySHSF0.

9. Here's the bad news. Unfortunately, running *pon <isp_provider_name>* and *plog* still shows the same error as before: can't get terminal parameters: input/output error.

The fact that now it detects the modem means I did something right, but there is still some nagging problem left. I'm running out of ideas. Please help.

---

### Post by swong1 on 2005-07-23
Good news. I tried reconfiguring the dial up properties:

system->administration->networking

I activated dial up and voila! It works! However, the connection is unstable, and once broken, very difficult to reconnect. At least now I have limited success browsing the web with Linux.

---

### Post by OscarGortez on 2005-07-23
Glad to see you got everything working, I also have some troubles with staying connected and the modem speed is very slow.  it might be a better investment to purchase an eternal modem so you know it's a hardware modem, then linux will have no problems with it and stability is better.  I read somewhere that's something you should do if you're serious about using linux all the time anyway... not sure how much they cost but it can't be that much, right?

---

### Post by OscarGortez on 2005-07-23
[QUOTE=lostinzim]I am a complete newbie to Ubuntu and am trying to understand how it works.  I have an NEC Versa P440 laptop which i cant use dial up to connect to the internet.  In network settings it says the modem connection is not active.  When i click on properties and try to autodetect the modem, i get an Information window that comes up which says "Could not autodetect modem device - check thatthe device is not busy and that it is correrctly attached to the computer".  The modem worked fine before while running XP though.  I have tried going through the System administrator to find the problem but have failed.  Any ideas would be appreciated!  

I have downloaded the scan modem program mentioned above and will try that, but if anyone can give me a simpler way forward that would be great.  Thanks[/QUOTE]

if you can't use dial up to connect to the net what type of modem do you have, and how do you connect?  you're not using a dial-up modem which is the topic in this string, I'm still a newbie so you might want to start a new string on the forums for your problem to get more exposure.

---

### Post by autocrosser on 2005-07-24
As far as external modems go--I use a USB Zoom 2986L Fax/Modem--I don't have serial ports (running a Mac) & all my system is USB2--The Zoom connects FASTER than the internal software modem & is stable for as long as my ISP will allow me to be online. I got this one on eBay for 15us + shipping---I also have heard that the older Supra Express modems work--look for SUP2780 or earlier--To find out about what USB hardware works-- [http://www.qbik.ch/usb/devices/](http://www.qbik.ch/usb/devices/)

I use Gnome PPP to dialout--nice interface & it auto detected the modem right the first time-- USB modems will normally use /dev/ttyACM0--you might also simlink to /dev/modem--some programs would rather call the /modem--

Hope this helps someone!!

Cheers!!
Dean

---

