---
title: "Three Network Cards, NO Network Success"
date: 2007-02-23
forum: Networking &amp; Wireless
---

### Post by Cheekio on 2007-02-23
I've been an ubuntu laptop user since the summer, and I was using a wireless card with ndiswrapper installed. I bought a fancy Atheros wireless card back in the day, and it seemed like a good idea, as it should 'just work'. Well, after it didn't, I assumed maybe it was time to break my laptop again by trying to fix it, so I upgraded from Dapper to Edgy. Updated via my ndiswrapper broadcom card, figured at the very least maybe it would undo any damage I've done, and get my superior atheros card to work.

So when I restarted with a nice new 6.10 Edgy Eft update, my ndiswrapper card didn't work anymore. Device manager says:

Vendor: Broadcom Corporation
Device: BCM4318 [AirForce One 54g] 802.11g
Status: Status
Bus Type: PCI
Device Type: Unknown
Capabilities: Unknown

No problem, I'll plug in my atheros card, and it should just work. It didn't. Reset the machine, still no dice, but now the card blinks once at regular intervals. Well, two wireless cards down. Neither of which show up in System->Administration->"Networking" The atheros card will show up in my Device Manager as "AR5212 802.11abg NIC", recognizing that it is from Atheros Communications, Inc., and the device as labeled above.

Status: Status
Bus Type: PCI
Device Type: Unknown
Capabilities: Unknown

That's a shame. Maybe I need to use synaptic to get some atheros drivers, you know, the madwifi ones or something. So I plug it into the static IP ethernet connection I use on my desktop. After carefully setting up everything, I try to pull up firefox. No internet connection found. So I check the settings again, and again, and again, and give up. Then I bring it over to a router that will give me a nice, easy dynamic IP address. I set the card in "Networking" to "DHCP", hit ok, then test firefox now that it's plugged into a router. No dice. Three different network devices, four different reasonable attempts to connect anything, and absolutely zero success. "Networking" shows my eth0 card, and the modem that came with the laptop, nothing else.

Somewhere along the line I read it would be helpful to edit /etc/network/interfaces, and I went ahead and did as that website told me to. It looks a little like this now:

```
auto lo
iface lo inet loopback

iface ath0 inet dhcp
wireless-essid *****
wireless-key *****



iface eth1 inet dhcp
wireless-essid *****
wireless-key *****



iface eth0 inet dhcp
hwaddress ether *****


auto eth1




auto eth0
```

All that junk in there is old network settings I was trying to set up back when I had a working broadcom card through ndiswrapper, and a working wired connection, back with Dapper. To edit that I use "sudo vi /etc/network/interfaces", which I don't even know how to save my changes or even quit appropriately.

This is the most frustrating ordeal, as my laptop has always been since I've installed Ubuntu. Anyone know how to get it to 'just work'?

---

### Post by Cheekio on 2007-02-23
Sorry for bumping my own thread, but is this really a difficult problem? I expect there's some easy solution, it's a fresh upgrade to Edgy, but I sure don't know what it is.

---

### Post by RomeReactor on 2007-02-23
Hi. What is the output of running

```
iwconfig
```

in the terminal?

---

### Post by Cheekio on 2007-02-24
iwconfig returns:

```

lo          no wireless extensions

eth0       no wireless extensions

sit0        no wireless extensions
```

That doesn't look encouraging.

---

### Post by Floppyjoe on 2007-02-24
looks like you need the line:
```
auto ath0
```
in your /etc/network/interfaces file.

Also check if your /etc/modules file has the word ndiswrapper in it.

If you use WPA encryption make sure your config file(/etc/wpa_supplicant.conf) is not overwritten by the update.

If you are using the gnome gui then sudo gedit /etc/network/interfaces is easier to use for editing purposes.

---

### Post by Cheekio on 2007-02-25
Thanks, I added auto ath0 and rebooted, and I got this nice message at the boot-up prompt:
```
loadndisdriver: loadndisdriver: main(638): version 1.7 doesn't match driver version 1.8

*Activating Swap...
*Chekcing root file system...
```
Then it proceeded to check an hvar file (or something, didn't catch it). It rebooted again and still didn't seem to work. The iwconfig ruterned lo, eth0, and sit0 as all "no wireless extensions".

Well, that's a little deturring, so I check out my /etc/modules file, and it does infact have ndiswrapper in it. It has "lp" "psmouse" and "ndiswrapper".

I remember back in the day when I was first trying to use my ndiswrapper card, I tried to set up WPA encryption up, but to no success. So I do probably have a bogus wpa_supplicant.conf file, but it's not necessary anymore.

Does it matter where in the /interfaces file I place the "auto ath0"? Thanks for the help, by the way.

---

### Post by gradedcheese on 2007-02-25
> Maybe I need to use synaptic to get some atheros drivers, you know, the madwifi ones or something.

The latest Edgy kernel (-11) requires a new madwifi (or rather, a recompile).  If you build your own madwifi, it will work fine.  The Broadcom card will continue to not work, of course.  But the Atheros can be made to work.

```

sudo apt-get update
sudo apt-get install build-essential linux-headers-`uname -r`

```

Then follow this guide: [http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)

---

### Post by RomeReactor on 2007-02-25
> oadndisdriver: loadndisdriver: main(638): version 1.7 doesn't match driver **version 1.8**

I'm not sure, but it looks to me like you don't have **ndiswrapper-utils-1.8** installed; do a search for "ndiswrapper" in Synaptic. Five items must show up. Make sure only "ndiswrapper-source" is not installed (you don't need it, unless you have a custom built kernel. If you must download from windows, here's the [link]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fn%2Fndiswrapper%2Fndiswrapper-utils-1.8_1.18-1ubuntu2_i386.deb&md5sum=6ba955830847e6e20282291ff124b34d&arch=i386&type=main").

---

### Post by Cheekio on 2007-02-26
Well I thought downloading the madwifi drivers and manually installing would be prudent, so I got madwifi-0.9.2.1 and played the .tar game, when I tried to 'make' it, I get this error message:```
can't cd to /lib/modules/2.6.17-10-386/build
Makefile.inc:89: *** /lib/modules/2.6.17-10-386/bulid is missing, please set KERNELPATH. Stop.
```

So I searched around a little bit, and I read this might mean I don't have the kernel source installed on my laptop. This is a little bit more challenging a problem than you'd expect, because my laptop still has no internet access. So I USB key'ed over a nice tarball named "linux-2.6.17.10.tar.bz2" and put it in the /Desktop/ folder of my linux laptop. However, now I'm stuck with a good idea what to do next.

If I install my madwifi drivers by following this path, will my wireless card probably work? I still can't even get a cable ethernet connection to work. Any ideas?

---

### Post by Cheekio on 2007-02-26
Success!

I found a friend's USB wireless card, and I plugged it in for immediate success. That was very, very pleasant. So running synaptic, and looking for madwifi, I find this installed:

linux-restricted-modules-2.6.15-26-386

And as my kernel is 2.6.17-10, I go ahead and install the update:

linux-restricted-modules-2.6.17-10-386.

Reboot and my atheros card is blinking like a christmas tree. I go to the System->Administration->"Networking", and there she is, beautiful. I fiddle with those settings for a little while and get my atheros card running on my local network.

The only downside is that the network connection icon on my top panel still says 'no network connection', and there's no way for me to browse local networks, I happened to know the essid and hex passcode for my own house. Is there any way to configure that wireless icon, or a program I should be using to manage wireless networks?

---

### Post by gradedcheese on 2007-02-26
> 
The only downside is that the network connection icon on my top panel still says 'no network connection', and there's no way for me to browse local networks, I happened to know the essid and hex passcode for my own house. Is there any way to configure that wireless icon, or a program I should be using to manage wireless networks?

If that icon is NetworkManager (which is what it sounds like), you simply need to comment out your wireless interface from /etc/network/interfaces and reboot...

---

### Post by Cheekio on 2007-02-26
Here's some more answers to my own questions:

I stopped by network operations today, and they told me that if I used System->Administration->"Networking", it will disable the handy network manager icon in the top right corner of my screen. So don't use it! Now my network manager icon works, and that means I can connect up at school to the school's network, and then again I can connect at home to my own network. Still no solution for the ethernet problem, but I'll have time to solve that issue this weekend.

For now, it looks like a general success. Thanks for the help, and I hope this thread helps other people with the same problems.

---

### Post by gradedcheese on 2007-02-27
> **Cheekio said:**
> Here's some more answers to my own questions:

I stopped by network operations today, and they told me that if I used System->Administration->"Networking", it will disable the handy network manager icon in the top right corner of my screen. So don't use it! Now my network manager icon works, and that means I can connect up at school to the school's network, and then again I can connect at home to my own network. Still no solution for the ethernet problem, but I'll have time to solve that issue this weekend.

For now, it looks like a general success. Thanks for the help, and I hope this thread helps other people with the same problems.

Like I said, it has to do with /etc/network/interfaces -- "Networking" puts any enabled interfaces there, which NetworkManager respectfully ignores so that they aren't multiply-managed.  This is cleaned up in Feisty from what I've noticed, but any NetworkManager howto guide explains it too.

---

