---
title: "multi-card reader doesnt work on AA1 and similar computers"
date: 2010-09-03
forum: New to Ubuntu
---

### Post by the-penguin on 2010-09-03
I recently came in contact with a computer whos' Multi-Card Reader doesn't work, I've looked around for some time and found some dead forum posts in this and similar forums.
I hope to renew some interest in this topic by posting this thread.

I read somewhere that the issue originally lies with the BIOS but I can't confirm this.

I hope you can help,
regards
jason

---

### Post by davidmohammed on 2010-09-03
if you can supply more detail then maybe someone here can help.

Can I suggest, type 

lsusb

in a terminal session - post the contents here in the reply.

also have a look in the kernel log (System --> Administration --> Log File Viewer) and post the bits that correspond to the multi-card-reader.

---

### Post by the-penguin on 2010-09-05
alright so i finally found the time, sorry for keeping you waiting.

the lsusb command shows the follow:
```
Bus 005 Device 002: ID 15d9:0a33 Dexon Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 5986:02c1 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by the-penguin on 2010-09-05
running the command tail -f /var/log/messages will show these three lines when an SD card is inserted and removed again

```
[ 1549.824178] usb 1-3: new high speed USB device using ehci_hcd and address 9
[ 1549.959173] usb 1-3: configuration #1 chosen from 1 choice
[ 1551.050550] usb 1-3: USB disconnect, address 9
```the syslog section shows this

```
[ 1815.200062] new high speed USB device using ehci_hcd and address 13
[ 1815.333663] usb 1-3: configuration #1 chosen from 1 choice
[ 1820.998271] usb 1-3: USB disconnect, address 13
```and last but not least ( probably the most important ;) ) the kern.log shows this

```
[ 2047.740151] usb 1-3: new high speed USB device using ehci_hcd and address 19
[ 2047.874042] usb 1-3: configuration #1 chosen from 1 choice
[ 2049.942614] usb 1-3: USB disconnect, address 19
```

---

### Post by QLee on 2010-09-05
> **the-penguin]running the command tail -f /var/log/messages will show these three lines when an SD card is inserted and removed again

```
[ 1549.824178] usb 1-3: new high speed USB device using ehci_hcd and address 9
[ 1549.959173] usb 1-3: configuration #1 chosen from 1 choice
[ 1551.050550] usb 1-3: USB disconnect, address 9
```the syslog section shows this

```
[ 1815.200062] new high speed USB device using ehci_hcd and address 13
[ 1815.333663] usb 1-3: configuration #1 chosen from 1 choice
[ 1820.998271] usb 1-3: USB disconnect, address 13
```and last but not least ( probably the most important  said:**
>  usb 1-3: new high speed USB device using ehci_hcd and address 19
[ 2047.874042] usb 1-3: configuration #1 chosen from 1 choice
[ 2049.942614] usb 1-3: USB disconnect, address 19
```

I'm not sure what you think you're illustrating with your post but the three different log entries you posted are from three different events, not the same event. Since you stated it was a BIOS problem, wouldn't it take a BIOS update to correct?

---

### Post by davidmohammed on 2010-09-05
> **the-penguin said:**
> alright so i finally found the time, sorry for keeping you waiting.

the lsusb command shows the follow:
```
Bus 005 Device 002: ID 15d9:0a33 Dexon Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 5986:02c1 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

Sorry in advance if I'm misinterpreting this, but none of the above appears to correspond to a multi-card reader.  The first is obviously a mouse. The "Linux Foundation" are just slots on the usb hub and the "Acer, Inc" is a webcam.

Assuming that I have read this correct, your multicard reader needs to be "switched" on either physically, or via a bios option.
Second thing to check, is your SD card actually working?  Can you try in another device, or try another SD card that you definitely know is working?

---

### Post by the-penguin on 2010-09-05
Alright. i know that the SD card is definetly working because I use it on my netbook constantly, the card reader is not broken because it works on the windows partition.
I can't confirm that it is a BIOS problem and therefore performing a BIOS update would be taking an uneccecary risk.

---

### Post by the-penguin on 2010-09-05
I don't know anything about the lsusb command, I was told to post the output and thats what I did.

---

### Post by davidmohammed on 2010-09-05
OK,
  so you've confirmed that it is working when you dual boot into windows - correct?

Therefore, the linux kernel is not recognising your netbook card-reader.  Is your netbook relatively new in terms of - has it just been released?  Possibly, a newer kernel will work.

Just for the record - what is the netbook (manufacturer, model, version etc)?

If you want to try a newer kernel - see the advice [here]("https://wiki.ubuntu.com/KernelTeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds").  Suggest download the latest maverick kernel (2.6.35).  The download consists of 3 deb files which you install.

---

### Post by QLee on 2010-09-05
[QUOTE=the-penguin]I recently came in contact with a computer whos' Multi-Card Reader doesn't work, I've looked around for some time and found some dead forum posts in this and similar forums.
I hope to renew some interest in this topic by posting this thread.
...[/QUOTE]

Is it one of the old ones and, if so, do any of any of the suggestions in this thread work?
[http://ubuntuforums.org/showthread.php?t=974525](http://ubuntuforums.org/showthread.php?t=974525)

For example, does it function if a card is inserted when booting?

Are you running netbook edition?

Edit: You should detail what you have actually tried from the old threads you reviewed, what you have tried and the errors you received can help to troubleshoot.

---

### Post by krimzonstarr on 2010-09-05
There have been some issues with the AA1. I have a zg5 model and see some improvement with the right-sided card reader using the instructions at [https://help.ubuntu.com/community/AspireOne/110L]("https://help.ubuntu.com/community/AspireOne/110L") under "Card Readers."

The left-side SD card port has always worked fine for me, hot-plugging works too. The right-side has been a continual problem though.

---

### Post by the-penguin on 2010-09-05
Alrighty.. it's a MSI Wind L1300 netbook that I'm trying to fix right now ( sorry for the wrong computer type in the title of the thread), but the same problem is happening on the Acer Aspire One, sorry for not posting this info earlier.

---

### Post by the-penguin on 2010-09-05
> **krimzonstarr said:**
> There have been some issues with the AA1. I have a zg5 model and see some improvement with the right-sided card reader using the instructions at [https://help.ubuntu.com/community/AspireOne/110L](https://help.ubuntu.com/community/AspireOne/110L) under "Card Readers."

The left-side SD card port has always worked fine for me, hot-plugging works too. The right-side has been a continual problem though.

The AA1 I'm working on is the exact same model and has the exact same issues ( hmmm maybe there's a connection here ;) ) I haven't tried that thread yet.. but maybe that threads suggestions apply to my MSI netbook too.

EDIT: sorry for all the double posts.. im just very very unorganized :(

---

