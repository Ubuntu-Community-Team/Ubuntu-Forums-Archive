---
title: "Ubuntu won't detect my Blanc wireless b/g router"
date: 2008-01-30
forum: Networking &amp; Wireless
---

### Post by Rippy on 2008-01-30
I've got a Dell D400 laptop with a Broadcom 1300 NIC. It dual-boots windows as well, and windows connects to my AP just fine, so it's not a hardware issue. The AP is a Blanc 802.11.b/g wireless router.

I've installed the bcm43xx driver and I can now see a couple of my neighbour's [protected] APs: so it CAN see access points. However, it can't see mine, even though windows sees it just fine.

And here's the kicker: I've gotten it to see my AP before. I don't know how I did it, but it worked. Then I had to try again due to some issues with the driver installation, and I've never gotten it to detect the AP since.

So the hardware is good, the driver is good, and I briefly got Ubuntu to detect my AP, so it should be possible. Does anyone know what gives? I did tweak some settings on the router after I got Ubuntu to see it, so maybe it's to do with my router's settings? Or is it incompatible with Ubuntu somehow? (I got it essentially for free due to rebates)

Any help is appreciated,

Rippy

---

### Post by dannyboy79 on 2008-01-30
did you make your router not broadcast it's ESSID? if so, a scan won't see it. you can hardcode the info into your /etc/network/interfaces file if that's the case. Here's an example of mine (althought I use WEP), my Belkin wifi adapter doesn't even support scanning when I try iwlist wlan0 scan so I had to do it this way.

auto wlan0
iface wlan0 inet static
address 192.168.0.6
netmask 255.255.255.0
network 192.168.0.1
gateway 192.168.0.1
        pre-up ifconfig wlan0 up
        pre-up iwconfig wlan0 essid YOURESSIDHERE
        pre-up iwconfig wlan0 mode Managed
        pre-up iwconfig wlan0 key YOURHEXKEYHERE

then you would issue, 
sudo ifdown wlan0
sudo ifup wlan0
NOTE: use the interface name for yours not wlan0.

---

### Post by Technophobia on 2008-01-30
You could try downloading Wifi radar. This program has been said to work with wireless networking better than Ubuntus default. Having the ability to rescan for APs makes this program worth it. For some odd reason Network Manager (Ubuntu's default "network manager") doesn't give the user the ability to rescan for APs.

[http://packages.ubuntu.com/gutsy/net/wifi-radar](http://packages.ubuntu.com/gutsy/net/wifi-radar)


good luck

---

### Post by dannyboy79 on 2008-01-30
i believe that wifi-radar is just a gui for wireless tools in linux. just try this

sudo iwlist interfacenamehere scan

example:
sudo iwlist wlan0 scan

---

### Post by Rippy on 2008-01-31
No, it definitely broadcasts its ESSID, because I can see it just fine in windows. I'm gonna try wifi-radar because, whether it solves my problems or not, it sounds like something I'd like to have when I get wireless working. I've also gotten my hands on a spare AP that I can try out and see if Ubuntu likes it any better, and switch 'em out if it works.

---

### Post by dannyboy79 on 2008-01-31
it has nothing to do with ubuntu liking your router. router's are standardized items. did you try to the scan using the command I posted?
you installed the module per this?
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy)

---

### Post by Rippy on 2008-01-31
Yeah, that's roughly what I did to install the module. It comes up in the restricted drivers list and everything. As for the command, I've been using it thoroughly, and it does succeed in displaying everything about the APs it's detecting

And now, guess what. I started ubuntu up, and it DETECTED MY AP in the network manager! Then I tried to connect and it didn't work, after several more tried I did a scan via the terminal and it only detected one unwanted network. Then I scanned again, and my network was detected! Then after a few more scans, nothing was detected. But now it's been detecting my AP for a good 5 minutes.

So, long story short, I don't know why the listed networks have been fluctuating so wildly (this is all without moving the laptop at all), but right now it sees the network I want it to see.

[5 minutes later] ..Nevermind. I've studied my scanning more carefully, and what happens is this: It detects my AP, but as I keep re-scanning, the "Last beacon" number eventually starts to climb, from a reasonable ~400ms all the way to 10 or 13 seconds, and then finally it just drops out and isn't detected anymore. I have a feeling this is not what I want.

Thanks for the help by the way. I'm king of in over my head with all this wireless configuration.

---

### Post by dannyboy79 on 2008-01-31
it sounds like you are getting interference from other electronics and the other ap's. you could try to change the channel. have you tried wifi-radar? have you tried to manually edit your interfaces file and just put in the info there and ifup your interface?

---

### Post by Rippy on 2008-01-31
Tried doing it manually, tried wifi-radar, still nothing. There are 3 access points in the building, on channels 1, 6 and 11 (mine's on 1), so there shouldn't be any interference.

Now it's being consistently inconsistent: it'll detect the AP, then after a few seconds it'll start to time out, and by about 15 seconds it times out completely and is no longer detected. 30-ish seconds later, it repeats.

---

### Post by dannyboy79 on 2008-02-01
does dmesg show any output or errors? it sounds like your module (driver) for your wifi card isn't working right. which driver are you using, are you using ndiswrapper?

---

### Post by Rippy on 2008-02-01
I am now, and it WORKS! :D I just found a guide that worked especially well for me. I'd tried ndiswrapper before, don't know what I did this time to make it work, but it did. Anyway, thanks for sticking with this thread, I appreciate it.

---

### Post by dannyboy79 on 2008-02-01
glad you got it working

---

