---
title: "Kernel -11 breaks wireless"
date: 2007-03-12
forum: Networking &amp; Wireless
---

### Post by eppoh on 2007-03-12
I read where many people had thier wireless broken after upgrading to the latest -11 kernel( mine included)
-10 still works fine.
Is this going to be fixed or not?

Any newbie downloading the latest and (greatest)? ubuntu is going to have a broke wireless right out of the box.

It "just worked" before the upgrade

---

### Post by gradedcheese on 2007-03-12
Try updating your restricted-modules package and see if that fixes it.  If not, tell us what chipset you have (ex: Atheros) and we'll find a way to make it work.

---

### Post by whfilho on 2007-03-15
I am having the same problem. Already updated restrictedmodules ( 2.6.17.7-11.2) and still not working.  Any suggestions? I'm using a Toshiba notebook with Atheros AR5006EG

---

### Post by gradedcheese on 2007-03-15
I just downloaded (boot into 2.17-10 if needed) the [latest madwifi source]("http://madwifi.org/wiki/UserDocs/GettingMadwifi") and built the driver for -11 (boot into -11 to do it).  It's very easy:

1) uncompress the archive and cd to it
2)
```

make
sudo make install
modprobe ath_pci

```

You need a couple packages first:
```

sudo apt-get install build-essential linux-headers-`uname -r`

```

If you have svn (apt-get install subversion) you can just get the driver via svn as their page explains instead of doing step 1.

---

### Post by whfilho on 2007-03-16
Thank you for your help, but still not working. I made all steps but "modprobe ath_pci"  give me an error.

WARNING: Error inserting ath_rate_sample (/lib/modules/2.6.17-11-generic/net/ath_rate_sample.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting ath_pci (/lib/modules/2.6.17-11-generic/net/ath_pci.ko): Unknown symbol in module, or unknown parameter (see dmesg). Using madwifi 0.9.2.1

---

### Post by BenWilson on 2007-03-16
I have a similar problem with the rt2500 chipset. The problem manifest itself for me _yesterday_. All previous Fiesty updates were working swimmingly (if I ignore the four hours without printing because of a bad cupsys that an update fixt).

I have kernel 20-9 and 20-11 on one system, but only 20-11 on another. The only way for me to use wireless is to boot into 20-9. Even when that happens, however, I have to manually start the network connection---auto ra0 seems not to be working as expected.

Both systems have run for some time under Edgy. I thought I'd contribute to the alpha phase this time and am experiencing heart ache.

The specific problem I am encountering is the kernel, so says Google and these forums, is splitting the wireless PCI card into two devices: ra0 and wmaster0. According to my research, this problem occurred in December, 2006 for those who were using rt2x00.serialmonkey.com sources. The "working" driver was called the "legacy" driver, which leads me to wonder "if it ain't broke, don't fix it."

The advice was to capture the CVS source and recompile rather than use the released build, which leads me to think the problem has a standing remedy. However, I would rather know this was fixed via an update than me having to recompile a kernel. (I come from Gentoo, so recompiles do not scare me; I'm just lazy.)

Regards,
Ben Wilson

---

### Post by gradedcheese on 2007-03-16
> 
WARNING: Error inserting ath_rate_sample (/lib/modules/2.6.17-11-generic/net/ath_rate_sample.ko): Unknown symbol in module, or unknown parameter


This usually means that you built it for the wrong kernel.  madwifi's scripts detect the kernel you are running about build for that.  So, did you:
1) get the source code
2) boot into the -11 kernel
3) build and modprobe the driver

---

### Post by eppoh on 2007-03-19
> **gradedcheese said:**
> Try updating your restricted-modules package and see if that fixes it.  If not, tell us what chipset you have (ex: Atheros) and we'll find a way to make it work.

Thanks, I appreciate it. It is a Prism 2.5

Is the latest kernel working for anyone else with this card? Mine was working fine before I did the recommended updates. 

Do I perhaps have the wrong repositories or is it just the kernel?

If so, why not just fix the kernel so it works again?

---

### Post by chili555 on 2007-03-19
eppoh-
Please sudo gedit /etc/modprobe.d/blacklist to add:```
#chili sez no to prism2
blacklist prism2_cs
```Then do:```
sudo rmmod -f prism2_cs
```Reboot and post back to let us know.

---

### Post by eppoh on 2007-03-20
> **chili555 said:**
> eppoh-
Please sudo gedit /etc/modprobe.d/blacklist to add:```
#chili sez no to prism2
blacklist prism2_cs
```Then do:```
sudo rmmod -f prism2_cs
```Reboot and post back to let us know.

Where do I add that code? Not sure what I am doing.

I tried in the folder modprobe and blacklist. there is no blacklist folder

I tried rmmod but it would not run- got an error "no such file or directory"

Thanks for the offer to help. I wish I had the time and abililty to be on OS tester, but I don't. I need something that just works and doesn't break when it is updated. That is why I came to Ubuntu- plus I hate windowz.

I'll just use the other kernel , like the other Prism card users.

Thanks

---

### Post by chili555 on 2007-03-20
I thoght I explained it pretty well:> sudo gedit /etc/modprobe.d/blacklist
Just copy and paste that into a terminal and a text editor, Gedit, comes up with a file to edit:```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801
```Then simply add the text mentioned at the end, save and close.

> I wish I had the time and abililty to be on OS tester, but I don'tThere is no perfect operating system; not linux, not BSD and certainly not Windows. The wonderful part about linux and Ubuntu in particular, is that you can make it more perfect all by yourself, and you will have the support of a community that, I dare say, is unmatched in Windows.

FWIW, the laptop I am posting from right now is running a 2.6.20 kernel, a Prism 2 card, with prism2_cs blacklisted. I responded because I know it works.

---

### Post by whfilho on 2007-03-21
There is a new release of madwifi (0.9.3). For me it works just fine. My wireless is :lolflag:

---

### Post by eppoh on 2007-03-21
> **chili555 said:**
> I thoght I explained it pretty well:
Just copy and paste that into a terminal and a text editor, Gedit, comes up with a file to edit:```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801
```Then simply add the text mentioned at the end, save and close.


FWIW, the laptop I am posting from right now is running a 2.6.20 kernel, a Prism 2 card, with prism2_cs blacklisted. I responded because I know it works.

Okay, I did that. 

When I issued, sudo rmmod -f prism2_cs

I get   : ERROR: Removing 'prism2_cs': No such file or directory

There is still no wireless card showing in the network, only 2 Wired  connections, 
Wlan0 and Eth0

---

### Post by chili555 on 2007-03-21
Please issue the command:```
lsmod | grep prism
```Is this a PCMCIA card or a PCI card or...? If the command produces a result, blacklist it, without the .ko extension and reboot. Let us know.

---

### Post by eppoh on 2007-03-22
> **chili555 said:**
> Please issue the command:```
lsmod | grep prism
```Is this a PCMCIA card or a PCI card or...? If the command produces a result, blacklist it, without the .ko extension and reboot. Let us know.


It is a pci. When Ilsmod I get: prism2_pci               74752   0

prism2_pci is already blacklisted as "blacklist prism2_cs, so I changed it to _pci...

Success!

I wish I understood what happened and what we ( you) did to fix it.
How can it work if we blacklist the driver for that card?

---

### Post by chili555 on 2007-03-22
Because there are already drivers called orinoco and hostap that work with Prism 2/2.5 cards. These drivers work and play well together. Prism2_whatever loads and fights with the others. You have to give it an F for the day and expel it from school. Harmony returns!

Fixed in Feisty, as far as I can tell.

---

