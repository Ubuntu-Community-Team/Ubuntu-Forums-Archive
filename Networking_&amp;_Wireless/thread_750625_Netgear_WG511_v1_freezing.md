---
title: "Netgear WG511 v1 freezing"
date: 2008-04-09
forum: Networking &amp; Wireless
---

### Post by groadin on 2008-04-09
Hi guys,
I want to switch to linux (I had used it before, on desktop) but I have a big problem with wifi on notebook. I have DLink PCMCIA card (DWL-G630 E2) which freezes linux when inserted in (or system doesnt boot when card was inserted before). 

I've bought Netgear WG511 (not V2) because I found that it works ok with ubuntu. Actually, it is said on  wifi compatibility list that WG511 works out-of-the-box. Well, not for me.

When none of modules are blacklisted, prism54pci shows an error in dmesg (I dont remember exactly, but it is as trivial as "error: firmware not loaded"). But nothing freezes (there is no wifi neither).

I followed instructions from
[http://brainsnorkel.com/tech/getting-wireless-wpa-psk-working-on-a-dell-inspiron-with-netgear-wg511/](http://brainsnorkel.com/tech/getting-wireless-wpa-psk-working-on-a-dell-inspiron-with-netgear-wg511/)
Actually I had to copy drivers from windows program files because of problem with unshield on x64 (afaik), but the rest (blacklisting, installing driver in ndiswrapper and so on) was done.

After that, system freezes when I insert the card. I've tried to get ctrl+alt+F1 to see some error output (it worked with previous freezes), but now there is no error message at all. 

I really dont know where the problem is. I thought that DLink DWL-G630 E2 just doesnt like linux at all, but I have similar problem (total freeze) with netgear WG511. Maybe the reasons are different (just forget about DLink, I was bothering with it too long). Please help me with getting netgear card working.

Some info (please request any output / logs you need and I will put it asap): tested ubuntu 7.04, 7.10, kubuntu 7.04, linux mint, pclinuxos (freeze everywhere). Notebook model Asus X51R.

---

### Post by chili555 on 2008-04-09
Well, I was shocked to read the instructions you referred to and see *myself* referred to!

I think the module that fights with ndiswrapper on a PCMCIA card is likely *prism54.ko* and probably not prism54pci.ko. You can test this by doing: ```
lsmod | grep prism
```If you see prism54 listed, then you have not blacklisted enough stuff. Then I would add:```
blacklist  prism54
```to your blacklist file. Let us know.

---

### Post by groadin on 2008-04-10
I forgot to add that I had done it too. Should I un-blacklist prism54pci now? I have blacklisted prism54pci, prism54common and prism54, and system still freezes.

---

### Post by chili555 on 2008-04-10
A few questions: is this a 64-bit system? Does:```
sudo cat /var/log/messages | grep ndiswrapper
```or```
sudo cat /var/log/messages | grep wlan0
```tell us anything? Substitute your interface here if it's not wlan0. You can also open a terminal and do:```
sudo tail -f /var/log/messages
```and watch the terminal as you insert the card to see what's happening as the system freezes.

I know you can't really copy and paste from a frozen system, but write down the highlights relating to errors, ndiswrapper and wlan0 and post them here.

With the card not inserted, what is the result of:```
ndiswrapper -l
```Does the card work on a live CD without ndiswrapper, even for a few minutes? If so, I'd love to see, from the live CD, ```
sudo lshw -C network
```I'd like to just verify this is a Prism54 card and not some Beijing re-badge. Again you can just jot down the highlights and skip the data related to ethernet. 

Finally, no need to blacklist more, yet.

---

### Post by groadin on 2008-04-11
> is this a 64-bit system?
Yes. Should I change (I have 64bit Intel Celeron M)?
EDIT: I tried Ubuntu 7.04 64bit, 32bit, Kubuntu 7.04 64bit, and (installed on the hard drive) Ubuntu 7.10 64bit.

> With the card not inserted, what is the result of: "ndiswrapper -l"
netwg511: invalid driver!

> sudo cat /var/log/messages | grep ndiswrapper (without the card inserted)
[Date] [laptopname] kernel: [ 42.992814] ndiswrapper version 1.45 loaded (smp=yes)
[Date] [laptopname] kernel: [ similar double] usbcore: registered new interface driver ndiswrapper
And two more times these two lines (total 6 lines).

I cant test anything with the card inserted. Without it, there is nothing like "wlan0" or "wlan1" in /var/log/messages.

> You can also open a terminal and do: "sudo tail -f /var/log/messages" and watch the terminal as you insert the card to see what's happening as the system freezes.
Nothing, just freeze :-/. About 3 seconds after insertion.

> With "sudo tail -f /var/log/messages" on liveCD (32bit, 64bit, Ubuntu, Kubuntu):
[date] ubuntu kernel: [double] pccard: CardBus card inserted into slot 0
// freeze

Sometimes there is no input at all. Tried with terminal in gnome / KDE, and in "recovery / safe graphics mode". I noticed that it is not freezing on about 1 / 10 tries.

This is what I managed to get:
- after mounting the card, ubuntu 64bit, graphics safe mode, liveCD:
[...] 0000:09:00.0 (prism54pci): cannot boot firmware!
// system still alive

- after mounting again, or during booting with the card mounted in
ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ16
mmcblk0: mmc0: c531 SD01G 10608KiB
mcblk0: p1
pccard: CardBus card inserted into slot 0
PCI: Enabling device 0000:09:00.0 (0000 -> 0002)
ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 21 (level, low) -> IRQ21
p54: LM86 firmware
// freeze

Actually this is strange, I remember I managed to get wlan1 or wlan0 on iwconfig (dont remember exact name), without connection, before installing ndiswrapper, but I dont know on which system it was (I've tested few versions). Maybe 7.10 64bit liveCD. I was happy that system doesnt freeze, but now I dont know what is wrong :-/ Any ideas? Maybe I just was lucky. I think there is no routine when it freezes and when it's not. And this is undependend of system version.

PS: I dont know this is normal, but when booting Ubuntu (liveCD), I spotted something like this:

Configuring network interfaces:
cat: /var/lib/acpi-support/system-manufacturer: No such file or directory
cat: /var/lib/acpi-support/system-product-name: No such file or directory
cat: /var/lib/acpi-support/bios-version: No such file or directory
2x more (I didnt manage to write it all)

I wonder could it be a problem with PCMCIA support (in this notebook)?

Maybe there is a problem with acpi support? How can I turn it off (-noapic, isnt it)?

---

### Post by dstew on 2008-04-11
The problem seems to be with the firmware that p54 loads into the card. When the prism driver tries to interact with the card, you get the errors. Here is a possible solution, involving new firmware: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/90902/comments/10](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/90902/comments/10)

---

### Post by chili555 on 2008-04-11
@groadin
Be cautious; this is mainly aimed at USB devices, although there is a reference to PCI. You want PCMCIA. I am searching for an updated firmware for your WG511.

---

### Post by chili555 on 2008-04-11
> netwg511: invalid driver!This, it seems to me, is the clue we're looking for. I think the firmware issue actually refers to the native module, not really the ndiswrapper process. I think a needed part of the process is the .sys file. Let's remove the driver and try again:```
sudo ndiswrapper -r netwg511
```Then, take a look at wherever you copied netwg511.inf and copy the WG511ICB.sys there, too. Now, let's try re-installing the driver:```
sudo ndiswrapper -i netwg511
```The acid test: plug in the card, hug your penguin doll and see if it freezes.

---

### Post by groadin on 2008-04-12
OK I have good news and bad news. The good news is: the sysem didnt freeze! And the bad news: I don't have a penguin doll ;-(.

OK what I've done.
I followed your last advice chili555 and I noticed that when installing driver like this:
```
sudo ndiswrapper -i netwg511
```
it says "couldnt find file or directory". And actually this is how the driver was "installed" earlier.
I removed it (-e), checked with -l that there is nothing left, and installed driver like this:
```
sudo ndiswrapper -i netwg511.inf
```
Now when listing (-l) it shows "netgear511: driver installed" and no "invalid driver".

OK I plugged my card in, and there is what was displayed:
ndiswrapper: kernel is 64bit, but Windows driver is not 64bit; bad magic 010B
ndiswrapper (board_sys_files:216): couldnt prepare driver 'netwg511'
ndiswrapper loadndisdriver: couldnt load driver 'netwg511'
ndiswrapper (load_wrap_driver:118): couldnt load driver 'netwg511'; check system log for messages from 'loadndisdriver'
0000:09:00.0 (prism54pci): cannot boot firmware

I checked /var/log/messages but nothing here about loadndisdriver. In dmesg there is what is above. But I think this is clear I have to install 32bit system. I will download 32bit 8.04 beta (I really want to check it out :-), especially Kubuntu with KDE4), install and try again. Then I will reply in this topic.

PS: Is the "0000:09:00.0 (prism54pci): cannot boot firmware" line means that prism54pci isnt actually blacklisted?



ADDED:

I installed kubuntu Hardy 32bit, ndiswrapper, blacklisted modules, installed windows driver, and inserted the card. System didnt freeze, ndiswrapper -l said something like "netwg511, card inserted". In lshw the secion with this network card hadnt have logic name (eg "wlan0"). I thought I should restart the system. After reboot, freeze without any output. When inserting the card after booting, sometimes it shows message from prism54 "could not load firmware" (like before) and no freeze, sometimes (more often) it just freeze, without saying anything. I tried to remove modules with modprobe, before inserting, but no help. Please help, I hope you have any ideas how to work it out. :-(

---

### Post by dstew on 2008-04-12
> Now when listing (-l) it shows "netgear511: driver installed" and no "invalid driver".

OK I plugged my card in, and there is what was displayed:
ndiswrapper: kernel is 64bit, but Windows driver is not 64bit; bad magic 010BIf ndiswrapper is working, the message should be "driver installed, hardware present". If it does not mention the hardware, you have a problem.

> But I think this is clear I have to install 32bit system. Often you will need to downgrade to the 32-bit system to get hardware to work. You are right to consider this.

---

### Post by groadin on 2008-04-12
> If ndiswrapper is working, the message should be "driver installed, hardware present". If it does not mention the hardware, you have a problem.

This was the message I've got after inserting the card (32bit Hardy), but only the first time (and also, there was no logic name for this device in lshw, so no "wlan0" or any similar was available). After restart, there was only freezes or "cannot boot firmware" from prim54pci messages.

---

### Post by dstew on 2008-04-12
If you want to keep trying with ndiswrapper, make sure the prism modules are blacklisted. You might also have to blacklist p54, the module that adds the firmware. You need to get the "driver installed, hardware present" message to have any hope of success with ndiswrapper.

---

### Post by groadin on 2008-04-13
I followed your advice **dstew** and blacklisted also p54pci, p54usb, p54common (these three are which I found with "modprobe -l | grep p54"). I also blacklisted prism2_usb, but I think it doesnt matter here.

Now when I insert the card, or boot the system with the card inserted, I get this messages:

> 
ndiswrapper: version 1.52 loaded (smp = yes, preempt = no)
ndiswrapper: driver netwg511 (NETGEAR, 04/06/2004, 2.1.22.0) loaded 
PCI: Enabling device [ID]
ACPI: PCI Interrupt [...] GSI 21 -> IRQ 16
ndiswrapper: using IRQ 16
ndiswrapper: (np_init:216): couldnt initialize device: [ID]
ndiswrapper: (pnp_start_device:439): Windows driver couldnt initialize device (C0000001)
ndiswrapper: (np_halt:259): device f74c7480 is not initialized - not halting
ndisrawpper: device eth%d removed
ACPI: PCI interrupt for device [ID] disabled
ndiswrapper: probe of [ID] failed with error -22
usbcore: registered new interface driver ndiswrapper
// freeze, or this message again and freeze when I put the card second time


I tried win2k and winxp drivers from manufacturer's CD.

Please help.

EDIT: Going to try drivers v3.0 from manufacturer's website...
EDIT2: No luck...

---

### Post by groadin on 2008-04-13
As I said before, I also have DLink DWL-G630 wifi card (E2 version). I tried to run it by ndiswrapper. The driver was installed OK, but during boot I get something like this:
> 
ndiswrapper: version 1.52 loaded (smp = yes, preempt = no)
ndiswrapper: driver netrt61 ([card name and driver version]) loaded
[...]
ndiswrapper: using IRQ 16
// freeze


So as you see, it freezes even earlier than with netgear WG511 card. Am I just unlucky in choosing wifi cards, or is this some bigger problem (I dont know, with PCMCIA slot?)?

Please help if you have any ideas what to do.

---

### Post by tl3000 on 2008-04-13
[http://ubuntuforums.org/showthread.php?t=742630](http://ubuntuforums.org/showthread.php?t=742630)

[http://ubuntuforums.org/showpost.php?p=4251676&postcount=44](http://ubuntuforums.org/showpost.php?p=4251676&postcount=44)

HTH

---

### Post by groadin on 2008-04-13
Do You think this is a Hardy problem? I hope so, I will install Gutsy 32bit asap.

PS: This is what I got when I've uninstalled driver from ndiswrapper, inserted the card, and typed "modprobe prism54":
> 
eth1: no 'reset complete' IRQ seen - retrying
eth1: no 'reset complete' IRQ seen - retrying
eth1: interface reset failure
prism54: Your card / socket may be faulty, or IRQ line too busy :(
// and all above lines 2x or 3x more
// freeze


I've removed SD card to get some IRQ free (actually I just dont have anything more to remove) but still the same.

---

### Post by chili555 on 2008-04-13
If two completely different cards of different chipsets freeze your machine with or without ndiswrapper, I would certainly suspect a systemic problem and not necessarily an operating system, i.e. Linux, problem. Here are some things I suggest looking at:

1. Do you dual boot? Can you get either of these cards to run in Windows? Perhaps on a friends machine?

2. How are IRQ's set up in your BIOS? I have no IRQ issues in my seven computers (seven computers in a home of two people? This guy is nuts.) by selecting 'Auto Detect' in the BIOS for IRQ's.

3. Start the machine without any wireless cards and do:```
cat /var/log/messages | grep IRQ
```Let's see if we get any interesting information. This stuff:```
ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 16 (level, low) -> IRQ 16
```Is not an error, it's just ACPI figuring out who sits where. You are looking for errors or warnings.

4. If your machine has two PCMCIA slots, upper and lower, does it freeze in both?

I am running out of ideas and/or talent.

---

### Post by groadin on 2008-04-13
> 1. Do you dual boot? Can you get either of these cards to run in Windows?
Yes. On Windows Dlink DWL-G630 work OK. Netgear WG511 lists AP's but not connects, but I think I should reinstall the system because I have nice mess here (few programs for wifi deticated for different cards, and so on). Anyway, it is seen by system, diodes are blinking and so on. PCMCIA slot works 100%.

> 2. How are IRQ's set up in your BIOS?

Actually the BIOS in Asus X51R is very poor, but I tried to lock (this option is in menu "security", but works just like "turn off") modem, audio and LAN built-in card. No help.

> 3. Start the machine without any wireless cards and do: "cat /var/log/messages | grep IRQ"
Nothing interesting I think (a lot of ACPI PCI interrupt messages, and information about loading hardware, no errors or warnings).

> 4. If your machine has two PCMCIA slots, upper and lower, does it freeze in both?
Unfortunately I have only one PCMCIA slot (and one Secure Digital Card's slot).

I was wondering Hardy will help because it has something like "asus_laptop" module, which recognizes my poor-supported laptop model (manufacturer doesnt even supports Windows XP, only Vista, which is $#@). I will try Gutsy 32bit, but I doubt it will help.

PS: I also have a problem with miniPCI-E slot. I tested two different wifi cards, which wasnt even seen by Windows. Maybe it is the slot broken (I bought laptop model without wifi, but with a mouse and a bag by mistake, and now I have a problem...) but I'm unlikely to give the laptop for asus support because I need it. Thats why I am using PCMCIA card. I hate Windows and I want to switch to the linux again (I had used Ubuntu on desktop for about half a year and I really like it), but as you can see I cant get the wifi in any way... 

I bought Netgear WG511 v1 (used card) hopefully to get easy linux support. Maybe the problem is located in notebook, not the card. But even if I will take the notebook to the asus support, what can I say? "The PCMCIA doesnt work under linux"? "It doesnt have to" they will say...

The funny thing is, a "wifi on" diode on the notebook front is lighting under Hardy. This should be lighting when miniPCI-E wifi card is on :-). It wasn't even under Vista with all asus drivers installed.

I will post any news if I test Gutsy.

---

### Post by chili555 on 2008-04-13
> I was wondering Hardy will help because it has something like "asus_laptop" moduleSo does Gutsy. From my machine:```
/lib/modules/2.6.22-14-generic/kernel/drivers/misc/asus-laptop.ko
```Is it getting loaded in yours? Please do:```
lsmod | grep asus
```If it is *not* getting loaded, please do:```
sudo modprobe asus-laptop
```If there are no complaints, jam that WG511 in the slot and see if it freezes. I'm running out of ammo (ideas).

---

### Post by groadin on 2008-04-14
OK I installed Ubutnu Gutsy 32bit. The asus_acpi module is loading here instead of asus_laptop. I tried both. No luck with Netgear card (no freezes, but "windows driver couldnt initialize device" messages from ndiswrapper). With DLink, I managed to get wlan0 once (I think it was when I blacklisted both asus_acpi and asus_laptop), but no internet connection (tried wicd, and by-hand in /etc/network/interfaces). After reboot, with modules still blacklisted, the system freezes just after the messages from ndiswrapper:
> 
ndiswrapper: version 1.52 loaded (smp = yes, preempt = no)
ndiswrapper: driver netrt61 ([card name and driver version]) loaded
wlan0: Supports WPA, WEP, [and so on and so on]
[...]
ndiswrapper: using IRQ 16


This messages are displayed every time I have DLink inserted in, but it was just one time when the system didnt freeze (I've tried maybe 5 times in a row). As I said before, it was one single time when it didnt freeze, and I had wlan0 under ifconfig, iwconfig, but no internet connection.

Thank you chili555, dstew, and tl3000 for your help so far. I dont know what to do next. Maybe could you say me what PCMCIA wifi card is guaranted to work with ubuntu, and I will try to buy it?

PS: Is there any way to get more debug info from ndiswrapper, or what is going on in the system before the freeze?

---

### Post by tl3000 on 2008-04-14
> **groadin said:**
> ...  Maybe could you say me what PCMCIA wifi card is guaranted to work with ubuntu, and I will try to buy it?

PS: Is there any way to get more debug info from ndiswrapper, or what is going on in the system before the freeze?

I've been using my Netgear WG511v1 since Dapper without any problems.  However, the configuration setup to get it to work differs slightly in each new version of Ubuntu since then.  Anyway, type the following commands and post your results:

ndiswrapper -l

ndiswrapper -v

The version you're using does not seem to match the latest version for Gutsy.

---

### Post by groadin on 2008-04-15
> ndiswrapper -l
> 
netrt61g : driver installed
netwg511 : driver installed


> ndiswrapper -v
> 
utils version: 1.9
driver filename:       /lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.45
vermagic:       2.6.22-14-generic SMP mod_unload 586 


I also put [dmesg output]("http://groadin.in5.pl/other/dmesg.txt") and [var/log/messages]("http://groadin.in5.pl/other/messages.txt"), maybe you can find something useful here, especially in the end of /var/log/messages.

---

### Post by tl3000 on 2008-04-15
> **groadin said:**
> > ndiswrapper -l

netrt61g : driver installed
netwg511 : driver installed



There are two drivers installed, and they'll be conflicting with each other I think.  I would disable and remove the netrt61g driver.  The ndiswrapper version you're using is OK.  Anyway, the listing of the driver for my WG511v1 on Gutsy is as follows:

```
:~$ ndiswrapper -l
netwg511 : driver installed
        device (1260:3890) present (alternate driver: p54pci)

```

---

### Post by groadin on 2008-04-15
No no, as I said before I am testing two different PCMCIA wifi cards, to get any of them working. The netrt61g is for Dlink DWL-G630, and it is the one which I managed to "run and not freeze" (the "device present" in ndiswrapper -l), but no internet connection. Now it's freezing too (no error messages). I think its very random and very rare to not freeze.

The second card, Negear WG511, should use netwg511 drivers, but it says "Windows driver couldnt initialize device" and freeze.

I also tried to run any card with only one proper driver installed.

---

### Post by tl3000 on 2008-04-15
> **groadin said:**
> ...  (just forget about DLink, I was bothering with it too long). Please help me with getting netgear card working.  ...

> **groadin said:**
> > 1. Do you dual boot? Can you get either of these cards to run in Windows?
Yes. On Windows Dlink DWL-G630 work OK. Netgear WG511 lists AP's but not connects,  ...

> **groadin said:**
> ... No luck with Netgear card (no freezes, but "windows driver couldnt initialize device" messages from ndiswrapper). ...

> **groadin said:**
> ...  The second card, Negear WG511, should use netwg511 drivers, but it says "Windows driver couldnt initialize device" and freeze.  ...

Stop mucking around... work on one card at a time.  You may have a faulty card.  Check to make sure that the card indeed works first.

---

