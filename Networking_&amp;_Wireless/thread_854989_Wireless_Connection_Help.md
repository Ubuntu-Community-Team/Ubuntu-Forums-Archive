---
title: "Wireless Connection Help"
date: 2008-07-10
forum: Networking &amp; Wireless
---

### Post by racie on 2008-07-10
Okay, I have an Atheros AR5007 wireless network card in my Compaq F756NR laptop.  I have tried numerous how-to's with MadWiFi, Ndiswrapper, etc.  Nothing has worked so far.  In Network Settings, wireless connection is not even an option on the list.  I have also tried going into BIOS to enable the wireless connection at boot.  I have heard that you have to disable Atheros HAL, but after I disable it in the Hardware Settings, it still says "in use," even though it is unchecked.  I have looked throughout the forums and tried many things.  This is different from my Xubuntu problem because I am now running Ubuntu, however, it didn't make a difference in the wireless connection.  Please help.  Thanks.

---

### Post by Prefix100 on 2008-07-10
[http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html)

Have you tried that?

---

### Post by chalewa on 2008-07-10
well i mean if you have tried a bunch of how-to's and nothing has worked, maybe a clean boot and then trying to reinstall the madwifi drivers might be in order. 

wait to see if someone else has a less drastic approach, but i have the same card in my laptop, and it can be a pain in the ***. 

have you never gotten wireless to work at all on it? 
i just have a feeling that you are just going to get more links to more how-to's in this thread.

---

### Post by racie on 2008-07-10
> **Prefix100 said:**
> [http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html)

Have you tried that?

Yes.  I even tried the 64-bit how-to after the 32-bit one didn't work.  (My computer is a 32-bit)

> **chalewa said:**
> well i mean if you have tried a bunch of how-to's and nothing has worked, maybe a clean boot and then trying to reinstall the madwifi drivers might be in order. 

wait to see if someone else has a less drastic approach, but i have the same card in my laptop, and it can be a pain in the ***. 

have you never gotten wireless to work at all on it? 
i just have a feeling that you are just going to get more links to more how-to's in this thread.

Ugh... no, I haven't.  In "Network Settings" I have always had only two options-- wired or ppoe.  I've reinstalled the madwifi driver a bunch of times (different how-to's) and still nothing. :(  And what do you mean by a clean boot?

---

### Post by Prefix100 on 2008-07-10
I think he means reinstall ubuntu

---

### Post by racie on 2008-07-10
That wouldn't do any good.  I installed Xubuntu before that and I didn't try a lot of things, but none worked.  Then I installed Ubuntu and still no luck.

---

### Post by chalewa on 2008-07-10
well my reason for suggesting the clean boot is because you have tried so many times to install the madwifi driver, and the ndiswrapper that i can almost guarantee that something is conflicting with something somewhere.

my suggestion is that if you do a clean boot with a fresh copy of ubuntu and try to install the madwifi drivers, that you might have better luck.

---

### Post by Prefix100 on 2008-07-10
Are you certain of your card number?

It is possible you are trying to use incorrect drivers due to mistaken identity of the card.

---

### Post by chalewa on 2008-07-10
> **Prefix100 said:**
> Are you certain of your card number?

It is possible you are trying to use incorrect drivers due to mistaken identity of the card.

oh yea good call...i forgot to mention that. lscpi incorrectly identified my card, try the ar5006eg drivers.

---

### Post by racie on 2008-07-10
Yeah, I know what you mean.  Linux detected my card as an Atheros AR242, BUT Vista detects it as an Atheros AR5007.  I know the Vista one is right because my WiFi works on my Vista OS.  Well, I guess I'll just try reinstalling it.  *sigh*  It'll take about 3-4 hours since I don't have a LiveCD.  I used Wubi to install it.  Wish me luck.  :)

---

### Post by chalewa on 2008-07-10
> **racie said:**
> Yeah, I know what you mean.  Linux detected my card as an Atheros AR242, BUT Vista detects it as an Atheros AR5007.  I know the Vista one is right because my WiFi works on my Vista OS.  Well, I guess I'll just try reinstalling it.  *sigh*  It'll take about 3-4 hours since I don't have a LiveCD.  I used Wubi to install it.  Wish me luck.  :)

why not just download the install disc in vista and then use that...

---

### Post by racie on 2008-07-10
Because I don't have a CD to burn the .iso file to.

---

### Post by racie on 2008-07-10
Okay, I've reinstalled Ubuntu and it still doesn't show "wireless" in "Network Connections."  Shall I try [this](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html) again?

---

### Post by racie on 2008-07-10
You know, I think I may have found my problem.  The first step is to disable HAL and reboot the system.  I did that, but it still says "in use."  How can it be in use if it's disabled?
Pic:
[img]http://img362.imageshack.us/img362/4617/screenshothardwaredriveiv6.png[/img]

---

### Post by Prefix100 on 2008-07-10
When you get past that HAL hurdle, if it doesn't work, try using a howto for the card model that linux outputs.

---

### Post by racie on 2008-07-10
The how-to's that I am finding for AR242x (as Linux thinks it is) are the same for my actual driver (AR5007).  Should I try blacklisting HAL?

---

### Post by Arthur Archnix on 2008-07-10
I can't test this myself as i'm not on ubuntu, but try:

sudo apt-get install sysvconfig
sudo sysvconfig

Then, find hal and uncheck it. Save. Quit. Reboot.

Do you still show hal as "in use"?

It's possible that your setup is such that after boot hal is loaded anyway, by gnome. If you boot into single user mode that's any easy way around this. Just print the instructions, boot into single user mode, follow the instructions (without sudo, since you're root. Be careful!), and then reboot.

Guesses I'm afraid, as I've not the same chip nor OS as you.

---

### Post by racie on 2008-07-10
> **Arthur Archnix said:**
> 
sudo apt-get install sysvconfig
sudo sysvconfig

Then, find hal and uncheck it. Save. Quit. Reboot.

Do you still show hal as "in use"?

It's possible that your setup is such that after boot hal is loaded anyway, by gnome. If you boot into single user mode that's any easy way around this. Just print the instructions, boot into single user mode, follow the instructions (without sudo, since you're root. Be careful!), and then reboot.

Okay, that REALLY scared me for a minute there.  After I did it and rebooted, my internet stopped worked even though it's plugged in by a chord.  So apparently HAL is needed to use the internet.  So why am I trying to disable it.  Wouldn't this just screw everything up like it did five minutes ago?

*edit*  And would this patch be useful to me? --> [http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679)  I have an Atheros AR5007 that is detected on Ubuntu as an Atheros AR242x.

---

### Post by Arthur Archnix on 2008-07-11
> **racie said:**
> Okay, that REALLY scared me for a minute there.  After I did it and rebooted, my internet stopped worked even though it's plugged in by a chord.  So apparently HAL is needed to use the internet.  So why am I trying to disable it.  Wouldn't this just screw everything up like it did five minutes ago?

First, if you installed sysvconfig, disabled hal, then restarted and found something bad happens, there's no need to be scared. Just run sysvconfig again, put a checkmark back in hal, and restart. Back to normal. 

Second, perhaps hal is required for your wired connection to start automatically when using network-manager. But it will certainly work without hal. Look for the network manager process by doing "ps -ax" in a terminal, kill the network-manager process by doing "kill -9 processid#" where you replace processid# with the four digit number in front of network-manager. Then, while still in a terminal bring up your ethernet connection manually. Something like "ifup eth0 dhcp" may do the trick. Or "ifup eth0" followed by "dhclient eth0". There are plenty of how-to's on the forum that can give you much better instructions. And again, if anything goes wrong there's no need to panic. Restarting the computer will make everything go back to default. 

As to why you're disabling hal, I haven't the foggiest idea. I was simply responding to the fact that you're trying to get wireless working, it tells you to disable hal to follow the instructions, and you couldn't disable hal. I thought I'd let you know how I thought you might achieve that. 

> *edit*  And would this patch be useful to me? --> [http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679)  I have an Atheros AR5007 that is detected on Ubuntu as an Atheros AR242x.The fact that you were a bit freaked out by your internet not working briefly leads me to recommend you NOT try to patch your system. That's something that is usually much more difficult to fix than by simply restarting, or re-checking a check-box. 

Assuming you haven't yet been able to follow the original instructions, the safest and easiest approach at the moment would be to disable hal as per the instructions, bring up your ethernet connection (wired) manually, and then continue on.

If that fails, then perhaps others can advise you about applying the patch or other things you might try.

Best,
AA

---

### Post by quanumphaze on 2008-07-12
You could try to compile the latest MadWifi drivers from source. It fixed the driver from locking up my system with my AR5005G.

Kajaste made a very nice script that automatically downloads the source, uninstalls the old driver, and compiles and installs the new one.
[http://ubuntuforums.org/showthread.php?t=798485](http://ubuntuforums.org/showthread.php?t=798485) Follow instructions carefully

It shouldn't make things any worse than you have it now.

And leave the Hal thing installed when you do this. It may not have any effect but when I did it it was active.

A useful command to see the card:
```
sudo lshw -C network
```
I get:
```
  *-network
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 3
       bus info: pci@0000:0a:03.0
       logical name: wifi0
       version: 01
       serial: 00:16:cf:c8:8e:20
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.0.41 latency=96 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g

```
If you get something like *-network UNCLAIMED and most of the stuff under configuration then Ubuntu hasn't loaded it up right.
It may also be useful to run this before you try the script to see if Ubuntu is in fact loading up the drivers correctly and it's Network Manager that is failing.

Another funny thing I find with my chip is that you sometimes (usually when I take the battery out) have to flick the wireless switch after GRUB but before the boot splash so that it's active and Ubuntu picks it up.

---

### Post by crazyness003 on 2008-07-12
I dont have any direct help but it would be useful to upgrade to the latest kernel. 

Tell us what kernel you have by doing this in the tenminal 
```
uname -r
```

The latest supported Ubuntu kenrel (2.6.24-19) fixed my wireless problem. It could do the same for you.

And dont feel bad, it took me 2 months to get my wifi working.

---

### Post by DonaldJ on 2009-02-05
One little thing that can cause weird data problems is if your hardware's AC power wires are crossing data wires...  Clean-up that horrid tangled mess of wires...  Power wires on one side.. Data wires on t'other...  I'm not saying it'll fix your prob, but it will help to eliminate future such probs.. and it might even increase your internet speed...

---

