---
title: "WiFi card used to not work in Linux, now it ONLY works in Linux"
date: 2008-11-16
forum: Networking &amp; Wireless
---

### Post by Cyber Akuma on 2008-11-16
I have a Toshiba Satellite A215-S7413 Laptop, it's wifi hardware is listed as a Realtek RTL8187B. However, it appears to internally be wired through the USB bus instead of the PCI bus since Vista's device manager has "USB 2.0" at the end of the device's name.

It came wiht Vista preinstalled and WiFI worked perfectly on it since day one.

I have tried Ubuntu since 7.10 and could never get WiFi working.

I installed 8.10 earlier and finally WiFi worked instantly from a default install.

Anyway, after I got it working at last I browsed a few webpages to try it, then downloaded restricted drivers for my video card. Eventually a few reboots later I started the update manager and chose to install all updates, it required a reboot after this.

Once I rebooted........ I found I could not connect to my WiFI network anymore. It kept failing at verifying the WEP key, even though the key is correct and this is THE EXACT SAME PROFILE I USED BEFORE THAT WORKED THROUGH 5 OR SO REBOOTS BEFORE I UPDATED!

I tried deleting and re-creating the profile but no luck, it still fails at verifying the WEP key.

I gave up and booted to Vista........ and noticed that Vista could no longer connect either! It could see all the access points around me but not connect any of them, not even if I disabled the security on mine.

I rebooted to ubuntu to see if I could connect without a WEP key but as soon as it booted it connected.

At this point I have tried everything to get it working in Vista, numerious reboots, attempts to reinstall the WiFi drivers, installs of older versions of the WiFi driver.

Nothing worked. I just cannot get WiFi working in Vista again no matter what I go, but now it works in Ubuntu.

Ethernet works fine but this is a Laptop that I move around a lot, a wired connection is just not feasable. 

Any idea what Ubuntu could have done, if anything, to cause this behavior? I know its not really supposed to be possible for software to mess up hardware like this(usually), but I find it hard to believe Vista's support for my WiFi hardware just happened to mess up within the very hour I got it working in Ubuntu when for the past year it worked flawlessly.

---

### Post by jnorthr on 2008-11-16
for what it's worth, i'd unplug your machine then take out the battery for a few minutes. This should discharge any lingering settings your card may have, then put  it back together again and reboot to see if vista will recognise it that way. On my laptop, i had to take the pcmcia wireless card out of the machine before rebooting then let windows discover the 'new' hardware via plug-and-play.

Does not make sense that ubuntu would zap your wireless card to the point where vista would not 'see' it.:confused:

---

### Post by Cyber Akuma on 2008-11-16
> **jnorthr said:**
> Does not make sense that ubuntu would zap your wireless card to the point where vista would not 'see' it.:confused:

No no, Vista sees it, and it can even detect my wireless network and others around me.

However, it can no longer CONNECT to my wireless network, even though all my settings are correct.

I even tried resetting my router to factory defaults and upgrading its firmware, but it still could not connect.

In fact, its not even bringing up a dialog box to enter my WEP address when I attempt to connect even though it can tell that its a WEP protected network (even though I am certain I wiped all my WiFi profiles so it shouldent be able to remember it).

I tried connecting to another network around me and the WEP/WPA passphrase dialog appeared.... but I doubt its my router since I have about 10 Wireless devices connected to this router and ALL of them are working fine, I even had my cousin bring his laptop and it was able to form a new WiFi connection just fine with my router.... not to mention my laptop while its running Ubuntu.

---

### Post by jnorthr on 2008-11-16
Ok, well at least that's some good news that vista can 'see' your network. This just sounds like all the bits are working together ok, but something stops the actual connection, so i'd start to look into the security issues here involving WEP/WPA security. As a temporary measure could your turn off security in both your router and the laptop to see how far it will go in connecting ? Yes, all your other devices will complain, but you can re-enable it after this test. 

this just 'feels' like a password or security mismatch issue rather than an o/s or hardware conflict. I think you are almost there - sorry - that's all i can think of at the mo. :confused:

---

### Post by Cyber Akuma on 2008-11-16
I already tried that.

I tried turning off security, and nothing happened.

Then I tried resetting the router to factory settings, which also resetted it's password as well as everyting else, and it still couldent connect.

---

### Post by abhinavg90 on 2008-11-16
I have a similar problem - same card. Toshiba A210
Sometimes after using the wifi on Ubuntu, if I restart into XP, the wifi just won't connect to the network (WPA). But if at this point, I shut down XP and let it be for 5-10 minutes and boot back into XP, it works.

---

### Post by Cyber Akuma on 2008-11-16
No matter how much I reboot, it won't fix it.

I tried older and newer drivers too, didnt work.

---

### Post by Cyber Akuma on 2008-11-26
I had my cousin bring his laptop over, its a very similar model to mine but slightly different, it could connect to my network.

I brought my laptop to his home and it could connect to his network.

So now.... ever since I installed Ubuntu 8.10 and got WiFi working in it.... the laptop will refuse to connect to only MY network but will connect to others, and it ONLY does this under Vista.

This... makes no sense...

---

### Post by Cyber Akuma on 2008-11-30
A friend recommended something that fixed it, disabling IPv6 in Vista. Apparently he works at an ISP and it was a common problem there.

First time I heard of such a crazy thing though.

---

