---
title: "Some questions (before I'm forced back to m$)"
date: 2007-02-17
forum: Networking &amp; Wireless
---

### Post by wej1971 on 2007-02-17
After a week of attempting to get wireless networking working on my machine, I'm just about at the stage where I give up and go back to m$. Before I do, I have some questions (a list ditch attempt to get some success): -

1. If iwlist wlan0 scan shows my access point correctly, and iwconfig wlan0 shows all the settings correct, why would I not get a connection consistently? Sometimes it works, sometimes it doesn't, sometimes it works then gets disconnected.

2. Why does iwlist wlan0 scan sometimes say no scan results immediately after showing my access point on a previous scan

3. Why do I need to specify my ap's mac address for connection to work at all? To get a connection I have to do the following: -

sudo iwconfig wlan0 ap <mac_address>

Most of the time this doesn't work, then I have to do lots of iwlist wlan0 scan, ifdown and ifup to get it working.

4. Why does downloading cause my connection to die within 2 minutes?

5. Why aren't my settings working at startup, despite the fact that ndiswrapper has the correct driver and the appropriate settings are in /etc/network/interfaces?

6. Could my disconnection/connection problem be usb 2.0 or nvidia related, despite the fact that I'm using ndiswrapper (I understood that the usb 2.0 problem didn't affect ndiswrapper) and my nvidia is the motherboard (nForce2) rather than the graphics card?

7. Is there *anything* else I can try - I'm getting really really depressed with all this. I'm willing to forgo m$ and embrace Linux but I need wireless networking to work.

Someone please help! You're my only hope...

---

### Post by highneko on 2007-02-17
This is a long shot maybe but if you're using sudo iwconfig then you are still a super user for a longer time like maybe two minutes? So maybe try changing your user to root "sudo su" then getting the wireless working? Good luck, I hope you don't have to make a change to m$.
 :lolflag:

---

### Post by wej1971 on 2007-02-17
Are you saying that if I enable the interface with sudo iwconfig it won't stay configured?

---

### Post by [L2G] Slapshot on 2007-02-17
Hi Wej

 I use a troublesome wireless usb stick from belkin. My vendor id which you can find by doing lsusb 

Bus 005 Device 003: ID 050d:705a Belkin Components

the bit of interest is this 050d:705a    it tells you what driver it needs and if it will ever work copy yours here and we can see what it needs. I'm a noob so we can only try our best mate. We'll try one step at a time

Jacko

---

### Post by maniacmusician on 2007-02-17
> **wej1971 said:**
> Are you saying that if I enable the interface with sudo iwconfig it won't stay configured?
that doesn't sound right at all.

it may be that your driver is of low quality. You probably have a device that is not well supported. As Slapshot says, you can try and find out the level of support for your card. 

In case that doesn't pan out, are you willing to buy a wireless card that will definitely work with Linux? I believe this is a list of compatible cards [http://www.linux-wlan.org/docs/wlan_adapters.html.gz](http://www.linux-wlan.org/docs/wlan_adapters.html.gz)  or you can just ask around on the forums as well.

---

### Post by wej1971 on 2007-02-19
You know I'm beginning to think I should buy another device, but the problem is that it works a dream with XP (it's a dual boot PC) and I'm loathe to spend more money.

Still, things are starting to get desperate so I'm not sure what other options I have.

---

