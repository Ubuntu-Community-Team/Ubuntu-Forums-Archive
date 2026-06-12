---
title: "[SOLVED] Wireless in Tecra A4 doesn't work"
date: 2008-04-17
forum: Networking &amp; Wireless
---

### Post by linuxbeak on 2008-04-17
Hello,

I've got a bit of an issue here. Yesterday morning I formated my Toshiba Tecra A4 which besides needing a general rebuild was working more or less fine (ie wireless was working.) I installed Ubuntu when it was Edgy and updated it to Feisty and eventually Gutsy.

Yesterday, I installed Gutsy directly and it went more or less without a hitch. Networking was broken, however, and that's because the Tecra A4 needs the kernel options "lapic" and "irqpoll" added to boot. After adding that to GRUB, wired ethernet works but wireless (ipw2200) does not. I did a ton of searching online and it appears that a lot of people are having the same problems with the ipw2200.

When you do dmesg | grep ipw2200, it shows that the driver is indeed there (version 1.2.0, I think... it's not the 1.2.2 one) but it says that it failed to send TX_POWER five times and then stops.

I have no idea what the heck is wrong. It worked fine beforehand (besides being finicky with sometimes picking up a WEP or WPA enabled network) but it's totally useless now. It goes without saying that this defeats the purpose of the laptop.

A few key notes:

[LIST]
[*]As stated beforehand, the boot options "irqpoll" and "lapic" need to be present in menu.lst (or whatever the GRUB config file) in order for networking to work.
[*]The laptop (a Toshiba Tecra A4, submodel S211) has a hardware switch that enables or disables the wireless controller.
[*]The driver for the wireless controller is ipw2200. The version is 1.2.0. I have tried manually building 1.2.2 with the same result.
[*]dmesg shows that the card is detected and module is loaded, but "failed to send TX_POWER" five times and then stops.
[/LIST]

I will provide as much info including dmesg and log outputs when I can/asked. Any help would be appreciated, as this laptop without wireless is really annoying.

EDIT: Another annoying thing to note: There is no splash screen when booting Ubuntu. It's a black screen and it stays that way for at least three to five minutes, and then it goes to the login screen. I have no idea if it's related, but it's certainly annoying and is the next thing that I must fix after wireless.

SECOND EDIT: Here's some information.

Kernel: 2.6.22-14-generic

Output of dmesg involving ieee80211 and ipw2200:

ieee80211_crypt: registered algorithm 'NULL'
ieee80211: 802.11 data/management/control stact, 1.2.18
ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>

ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2
ipw2200: Copyright(c) 2003-2006 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
ipw2200: Failed to send TX_POWER: Command timed out.
ipw2200: Failed to send TX_POWER: Command timed out.
ipw2200: Failed to send TX_POWER: Command timed out.
ipw2200: Failed to send TX_POWER: Command timed out.
ipw2200: Failed to send TX_POWER: Command timed out.
ipw2200: Unable to initialize device after 5 attempts.
ipw2200: failed to register network device
ipw2200: probe of 0000:06:04.0 failed with error -5

---

### Post by linuxbeak on 2008-04-17
Alright, now I'm even more confused. I saw something online saying to boot into Windows with the hardware switch set to "off", and then reboot into Linux with the switch still off. I did this and now the wireless card is properly detected. What the hell is going on?

I'm going to reboot with the switch still on and will report back the findings.

---

### Post by linuxbeak on 2008-04-17
My findings are a little less bizarre now, but still confusing.

[LIST]
[*]The wireless card works. However, in order for Ubuntu to be happy, the hardware switch needs to be turned off at boot time. An annoyance, but one that I can live with in the short term. I will be filling out a bug report to extrapolate on this.
[*]You do not need to go into Windows to make this work. It works as long as the hardware switch is off at boot time.
[/LIST]

Very weird indeed. For now I'm resigned to having to live with this new quirk and will focus on getting the rest of my laptop working, such as the unacceptably long boot time and lack of splash screen.

EDIT: I think I found the answer to the long boot time and black screen problems here: [http://ubuntuforums.org/showthread.php?t=579684&highlight=long+boot](http://ubuntuforums.org/showthread.php?t=579684&highlight=long+boot)

---

### Post by linuxbeak on 2008-04-17
Well, what do you know? I installed StartUp-Manager, fixed the resolution and voila, splash screen, considerably faster boot and (get this) the wireless works perfectly fine, even with the switch on at boot time (I'm using it right now!).

Marking as solved.

---

### Post by randomsearch on 2008-07-01
You are a genius.

I have been struggling with this problem for weeks, and stumbled across this post whilst trying to get this working for an urgent Skype call!

Fantastic.  I installed the Startup Manager, and changed the display resolution.  Then I rebooted and wireless worked!!!! wtf???  I have rebooted about 30 times tonight trying to get the thing working, so I can safely say this was the solution that fixed the flipping thing.

NB I also have problems with this wireless card in Windows.  It seems to me that this is a hardware problem and that this fix somehow convinces the hardware to work properly...

Woo!

RS

---

