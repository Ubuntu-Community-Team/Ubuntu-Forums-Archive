---
title: "Ubuntu Wireless on Packard Bell"
date: 2009-08-16
forum: New to Ubuntu
---

### Post by KyleRickards on 2009-08-16
Hi All

I have installed Ubuntu 9.04 on a couple of machines now with no problem.

However, when I try it on my old Packard Bell Easynote R1004, I do not seem to have any wireless options (although wired connections work). I have tried using the Madwifi solution and also using the Windows .inf file but still am getting nowhere : (

Please could anyone help?

Thanks
Kyle

---

### Post by LewRockwell on 2009-08-16
```
lspci -C network
```

output please

.

---

### Post by KyleRickards on 2009-08-17
Hi Lew

I tried the command but it said -C was an invalid switch argument?

Kyle

---

### Post by jrothwell97 on 2009-08-17
If that doesn't work, just run

```
lspci
```

and tell us what that puts out.

---

### Post by KyleRickards on 2009-08-17
Hi

That worked - and I got:

00:00.0 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 CPU Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:06.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN400/PM800/PM880/PN800/PN880 [S3 UniChrome Pro] (rev 02)


If I plug in either of my two USB Wireless adaptors, I can get straight on, seems to be the internal bit there is an issue with.

Kyle

---

### Post by mapes12 on 2009-08-17
Hi Kyle

Your wifi isn't showing in the list. If it's a USB device then ```
lsusb
``` and post the output.

---

### Post by HotShotDJ on 2009-08-17
> **mapes12 said:**
> Your wifi isn't showing in the list.
Yes, it is in the list.
> **KyleRickards said:**
> 00:06.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
Unfortunately, I've had little luck finding a solution to your problem.  Hopefully somebody with some experience with this card will happen along.

---

### Post by tarps87 on 2009-08-17
Just a quick thing to check, is the driver listed under system -> admin -> restricted drivers?

---

### Post by KyleRickards on 2009-08-17
Hi tarps87

Cannot see Restricted Drivers option under the menu?

Kyle

---

### Post by tarps87 on 2009-08-17
Sorry it is called hardware drivers

---

### Post by KyleRickards on 2009-08-17
Hi

Yes, it appears, should I post a screengrab?

Kyle

---

### Post by tarps87 on 2009-08-17
You should be able to select the driver and click activate. You may need to reboot before it is listed as in use.
If you have any difficulty post the screen shot and I'll try and make it clearer

---

### Post by mapes12 on 2009-08-17
> Yes, it is in the list.
Quote:
Originally Posted by KyleRickards View Post
00:06.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
Unfortunately, I've had little luck finding a solution to your problem. Hopefully somebody with some experience with this card will happen along.Good spot.................. I must get some stronger glasses.

I read somewhere that Atheros adapters need [madwiifi]("https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi") to get them going.

---

### Post by KyleRickards on 2009-08-17
Well I have a screengrab but cannot work out how to post here - should I just give up?

---

### Post by KyleRickards on 2009-08-17
I think I am just annoyed as I used EEEbuntu on my Asus and everything just worked, including Flash, Iplayer, etc. Is there another version of Ubuntu similar to EEEbuntu where there's not as much messing around?

---

### Post by tarps87 on 2009-08-17
I don't know if any other distros will be  any better as it is likely to be the same situation, the difference is that your Asus card was supported out of the box where as this one is not.

To attach the screen shot click the go advanced button then on the paper clip you can attach the image to the post

---

### Post by KyleRickards on 2009-08-17
Here you go.

---

### Post by 3rdalbum on 2009-08-17
Try removing "madwifi" and installing the "linux-backports-modules-jaunty-generic" package - it contains later drivers for various things, including wireless cards.

---

### Post by KyleRickards on 2009-08-17
Hi 3rdAlbum

Sorry, but you would have to walk me through it- new to all this, sorry!

Kyle

---

### Post by tarps87 on 2009-08-17
It looks like the driver is enabled, if your wireless is not working you should try 3rdalbums suggestion, deactivate the current madwifi on and type 
this into a terminal
```
sudo apt-get install linux-backports-modules-jaunty-generic
```

But before you do this could you post the output of
```
iwconfig
```

---

### Post by KyleRickards on 2009-08-17
Hi - as per below.

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Mr Smith"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0F:B5:D0:0E:0C   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=31/100  Signal level:64/65  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

---

### Post by tarps87 on 2009-08-17
> **KyleRickards said:**
> ```
Hi - as per below.

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

[B]wlan0     IEEE 802.11bg  ESSID:"Mr Smith"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0F:B5:D0:0E:0C   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=31/100  Signal level:64/65  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/B]

pan0      no wireless extensions.
```

It is working, it is registered as wlan0 and is connected to a network called "Mr Smith". Is this your network?

Edit: Do you have the networking icon? If you do and you can't see any wireless interfaces listed try wicd
```
sudo apt-get install wicd
```
it is an alternative network manager which may be more successful.
It appears we were missing the simple problem and solution

---

### Post by KyleRickards on 2009-08-17
Hi

I did that test with my USB wireless adapter in... Should I run the same test with it unplugged and post?

Kyle

---

### Post by KyleRickards on 2009-08-17
Hi

Connected using ethernet cable, same test now gives me:

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

---

### Post by tarps87 on 2009-08-18
Oh, in that case it isn't working. I suggest trying 3rdalbums suggestion.

---

### Post by KyleRickards on 2009-08-18
Hi tarps87

Have disable Madwifi and downloaded the other drivers package but am unsure what to do next?

Thanks
Kyle

---

### Post by tarps87 on 2009-08-18
> **tarps87 said:**
> ...
```
sudo apt-get install linux-backports-modules-jaunty-generic
```

Did you follow this step? If so they are installed, now try iwconfig

---

### Post by KyleRickards on 2009-08-18
Hi

Ran the command, removed USB adaptor and ran Iwonfig - still says no wireless connections. Looks like I may be stuck with this one.

Kyle

---

### Post by tarps87 on 2009-08-19
I sounds like you have tried everything, not having that device I can't do any testing so the only thing I can suggest is try using the live cd of Ubuntu 8.04 LTS (long term support). This is reported to support your wireless card. I am surprised the backports module did not work.

---

### Post by mapes12 on 2009-08-19
> Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)You mention taking a USB device in and out of your machine. Is your wifi adapter built into the machine or a USB device please?

---

### Post by tarps87 on 2009-08-19
> **mapes12 said:**
> You mention taking a USB device in and out of your machine. Is your wifi adapter built into the machine or a USB device please?

My understanding is that the non-working card (the Atheros one) is internal and the op is using and external usb adapter to connect to the wireless and the internet through that. Please correct me if I am wrong

---

### Post by mapes12 on 2009-08-19
> **tarps87 said:**
> My understanding is that the non-working card (the Atheros one) is internal and the op is using and external usb adapter to connect to the wireless and the internet through that. Please correct me if I am wrongThank you.

That answers what I was about to suggest i.e. using a known, supported USB or PCMCIA card.

---

### Post by KyleRickards on 2009-08-19
Hi both

That's correct.

Kyle

---

