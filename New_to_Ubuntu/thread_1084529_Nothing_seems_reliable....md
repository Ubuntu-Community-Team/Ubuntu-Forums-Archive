---
title: "Nothing seems reliable..."
date: 2009-03-02
forum: New to Ubuntu
---

### Post by kilgore9 on 2009-03-02
Not sure if there is a solution to this, but it is getting really irritating.  I'm using Ubuntu 8.04 32bit on an Acer Extnesa 5630Z laptop.  

Wether things work or not seems dependent on chance alone.  My video players were working all fine, then yesterday suddenly every video i tried to play would crash the system.  I was able to fix it by changing some settings, but why would it work and then stop working without me changing anything?

Today it's my sound that randomly stopped working.  don't know why or how to fix it.  

I also have had similar problems connecting to the internet.  Although I don't change the settings, sometimes it just stops working.  Wireless worked for about a minute, but I have never been able to get it back. 

Several normal programs (skype, evolution mail) sometimes save my preferences, and sometimes don't.  Things I change will stay changed, or not, but I can't figure out why.

I thought Ubuntu was supposed to be very stable... but it seems to be extremely moody, only working when it feels like it.  I have no prior linux experience.  Generally, I like it, but this is the most annoying thing...

---

### Post by diablo75 on 2009-03-02
Sorry to hear about the troubles you are having, but you didn't really give us much information to go off of (e.g., verbatim error messages if any, the actually settings that you said you changed/adjusted, etc.).

Have you by chance installed Ubuntu Restricted Extras (so that you have the proprietary video/audio decoders for the more popular video/audio formats)?  Have you applied any updates recently; specifically, kernel updates?  What programs are you using to play back videos and/or audio files, and do the crashes persist if you attempt to play the media in an alternative program (for instance, instead of using the default "Movie Player"(totem) to play back video, you could try vlc instead)?

---

### Post by kilgore9 on 2009-03-02
thanks for the reply diablo!

I don't know many specifics... but as for video, it worked when changing video output to x11.  The only player I can't get to work is the default totem player, can't find where to change it to x11 output.  But I have three others (VLC, mplayer, smplayer) that I was able to adjust and change.  As long as I avoid totem things work fine.

Just don't understand why it would work one minute and then stop the next.  I do have the restricted extras, but haven't updated anything in the kernel (wouldn't even know how to do that).  

My audio is back now, a simple reboot did the trick (always my first solution!).  I wasn't getting an error, sound just stopped playing.  The microphone also comes and goes.  Last night I got it working again, now I can't get it back.  For example, using Fmit (Free Musical Instrument Tuner) the mic was working fine, now it just doesn't work.  Can't get any input into the program. 

Connecting with ethernet (wired) works fine (for now).  Wireless does not, it recognizes my card, shows the network, but it just can't connect.  Sometimes it says it is connected but it really isn't.  It appears to accept my WEP key (which Ubuntu 8.10 would not) but doesn't let me put in my PPP usrname and password.  The PPPoE settings in Network Manager do not allow me to use wireless (ra0) as a connection option, just ethernet (eth0).  Strangely, I had the wirless working for a fleeting minute or two.  It seemed fine, then it just stopped.  No error, nothing.  

I would like to give more specifics but I don't really have any.  Things just seem to work/not work randomly.

---

### Post by mkvnmtr on 2009-03-02
I don't know if this will help you but two things come to mind. Hardware problems like bad solder joints or heat. The hardware I have no idea how to check but you should be able to tell if the unit is getting hot.

---

### Post by kilgore9 on 2009-03-02
Well the laptop doesn't get very hot, and the fan works just fine.  It doesn't turn on all the time and definitely stays cooler than my aging ibook...I could cook an egg on that thing!

---

### Post by mikechant on 2009-03-02
As far as your wireless network issue, one thing that seems to help some people is to use an alternative network manager. You could try installing 'wicd', which is in the repositories.
You might like to search these forums (and elsewhere) to see what people have to say about this.

---

### Post by johnjohn2 on 2009-03-02
Wicd is what i had to use on the other halfs lappy.

8.10 may help you out here as UBUNTU is always maturing and this release is rather good. Don't get me wrong UBUNTU 8.04 was reliable for me alas i like the bleeding edge aspect.

Wireless issue also sounds like you have not set the router up correctly also WEP can be cracked very easily and WPA is not totally secure but does offer better protection.

What happens when you acess the router and takethe password of i.e. no encryption?

You system specs would also help us alot.

Regards John

---

### Post by kilgore9 on 2009-03-02
About the Wireless..

I found and installed wicd, but it is even less helpful than my network manager.  I can't connect at all with wicd, gives me nowhere to put in my PPP username and password.  Wireless also won't connect, same problem there.  Anyone know how to get my network manager back?

I don't have a router...I have a Wireless DSL Modem.  Usually I give in the WEP key to connect to the Modem, then a usrname and password to connect to the internet.  It says it is connected to the modem but keeps asking for the WEP key, as if it is not accepted.  I had the same problem in 8.10. 

System Specs?  Sorry I'm a total noob and don't know really what you need...

Ubuntu 8.04 32bit on Acer Extensa 5630Z laptop
Wireless card: Acer Nplify 802.11b/g/Draft-N WLAN

Does that help?

---

### Post by edhawk2 on 2009-03-04
I have exactly the same problem.  I just got an overhauled Dell Latitude laptop (P3 - 1.2 Ghz, 512 m RAM, 20 gig HD) and I did a fresh load of Ubuntu 8.1 and every time I get an upgrade alert I do the upgrades, as late as today.  Totem wouldn't play DVDs even after downloading the extras it suggested.  I downloaded smplayer and it worked great for one DVD and wouldn't play another, even after several reboots.  

I came here to forums so see if anyone could help.

---

### Post by sandyd on 2009-03-04
could both of you post the result of running

```

lspci

```
in the terminal?

---

### Post by edhawk2 on 2009-03-04
Here's what I got when I ran "lspci:"

ed@jethro:~$ lspci
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:01.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:01.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
ed@jethro:~$

---

### Post by kilgore9 on 2009-03-05
kilgore@kilgore-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe (rev 10)
03:00.0 Network controller: RaLink Unknown device 0781
0d:06.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 01)
0d:06.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
0d:06.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 03)

---

