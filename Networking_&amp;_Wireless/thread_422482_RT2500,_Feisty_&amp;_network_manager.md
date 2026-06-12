---
title: "RT2500, Feisty &amp; network manager"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by davince on 2007-04-25
Hi,

I have an RT2500 compatilbe network card, and I want to use the network manager properly. 

Symptoms:
- It shows the available networks in roaming mode, but no signal strength
- When I select my network, I can enter the network details
- When I click connect it keeps on connecting for a while
- For that time waconfig actually is correctly configured. If I give DHCP a kick I can use internet
- After the time-period passes (timeout?) it deconfigures my wireless network

I can connect by configuring the wireless network manually with iwconfig.

So, where should I submit a bugreport? There are 3 possible locations:

- here, its ubuntu in which it goes wrong
- at the network manager site. Its their software which isn't working
- at the rt2x00 site which provides the driver, cause maybe it's the driver

As I have figured out the network manager should support the rt2500 except for WPA support. I have WEP, so that should not be a problem. So, it is something in feisty? Where should I go to get help?

---

### Post by k1001001 on 2007-04-25
I have the same card and the same problems. Getting it to work on Dapper was hard, and it looks like Feisty is going to be just as difficult. How do you connect wirelessly using iwconfig?

---

### Post by davince on 2007-04-25
Hi k1001001,

Here is my interfaces file, its located in etc/networks/interfaces:

--
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto ra0
iface ra0 inet dhcp
wireless-essid <my wirelessnetwork id>
wireless-key <my hex key>
--
I removed all redudant devices (wlan, eth1, etc...)

What I first did to try this was the following in a console:

sudo iwconfig ra0 -essid <myid> -key <my key>
sudo dhclient

If that works, the above configuration should work after a restart. Note that your network should be up and running before you start ubuntu, else you can restart the network with:

sudo ifdown

after that

sudo ifup

Well, I hope it helps, good luck! There are many other posts about this adapter, try to search for rt2500

---

### Post by radeonboy on 2007-04-25
I have the same problem!  Boy there goes my hopes of having a triple boot system...I might just uninstall Ubuntu because this sucks.

I have an ASUS WL-130g wireless card based on the Ralink 2500 series.  I just installed Ubuntu 7.04 and it sees the networks around my neighbourhood.  I select my router and put in my WEP and it searches, then it dies because it cant connect to it somehow.

I go into manual mode and it sees my network again but it says 0% for each network seen.

:mad: 

I guess I should go back to Windows where I dont have this problem...

---

### Post by Supercross on 2007-04-25
From what I've heard, RT2x00 chipset cards do not work under network manager nor do they support WPA encryption out of the box.  Therefore those using these cards are going to have to use ndiswrapper, following the same procedure you followed in previous ubuntu releases.  I have also heard of other programs that will work but from experience I know ndiswrapper works perfectly.

---

### Post by AirRaven on 2007-04-25
> **Supercross said:**
> Therefore those using these cards are going to have to use ndiswrapper, following the same procedure you followed in previous ubuntu releases.  I have also heard of other programs that will work but from experience I know ndiswrapper works perfectly.

Which is strange, since my RT2500 card's had absolutely no problems with every Ubuntu Release since Breezy- I'm connecting from it from the Edgy LiveCD at the moment trying to sort out the problem I've got with Feisty.

It's perfectly well supported- I never had *any* problems with it until Feisty appeared on the scene. Something in the update's broken RT2x00 support completely.

---

### Post by AirRaven on 2007-04-25
> **davince said:**
>  here, its ubuntu in which it goes wrong
- at the network manager site. Its their software which isn't working
- at the rt2x00 site which provides the driver, cause maybe it's the driver

I'd suggest posting the bug reports in that order, in answer to your question. First Ubuntu, then Network-Manager, then RaLink.

---

### Post by AirRaven on 2007-04-25
Alright- I've run across a simple solution for the problem. It's a bit of an ugly hack, but it works- and to top it all, you don't even have to fuss around with WiCd or the like.

All you'll need is a LiveCD of a previous version of Ubuntu- I used my old Edgy install CD, but I assume a Dapper Install LiveCD would do just as well so long as it fully supports the RT2500.

All that you need to do is start up, boot into the LiveCD OS, and then set up your network card via the standard System->Administration->Networking method using the old network-admin tool. 

Now you'll need to mount your Feisty Partition to be accessible from the LiveCD. In my case, it's hdb1, so I used the following command:

```
sudo mount /dev/hdb1 /mnt/feisty
```

Once this has been done, you'll need to open up Nautilus with Root access. 
```
gksudo nautilus
```

Now, navigate to /mnt/feisty/etc/network, and delete the contents of that folder. Replace the contents of the folder with the contents of /etc/network/interfaces in your LiveCD's file system. 

Then replace /mnt/feisty/etc/resolv.conf with /etc/resolv.conf.

Reboot, and your Feisty Networking should be fully functional- or at least it is for me. I'd advise against touching the Feisty Network configuration tools- I've not touched them yet, and I'm not particularly keen on watching them mangle the working configuration tools.

Like I said- it's not a particularly graceful solution. But it works.

---

