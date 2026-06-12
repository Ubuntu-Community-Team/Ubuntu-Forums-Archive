---
title: "log msg &quot;PUK required&quot; already after 1x PIN asked (3G/Vodaphone)"
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by stephanvaningen on 2008-11-07
I havea 3G datacard, and I am not able to accesss any broadband networks. Whenever I insert it into my laptop, it once asks for a PIN-code, and directly after that the network-icon in the right-top of the gnome-screen starts animating, but the two grey circles never turn green.

After checking the system logs, I see repetitive messages 'PUK required' 'status 4 -> 6', 'status 6 -> 4', ... every few seconds.

I then eject the card, [unlock the SIM-card (using my mobile phone)]("http://ubuntuforums.org/showthread.php?p=6055411"), and retry: same result. PIN code is correct, since I changed it a few seconds ago in my mobile phone and there it is accepted.

---

### Post by jekkil on 2008-11-26
Does your linux install (on a laptop I suppose) support well your datacard ?

Have you also tried with the usb modem that you can have too from Proximus ?

Thanks for the info

---

### Post by stephanvaningen on 2008-11-27
> **jekkil said:**
> Does your linux install (on a laptop I suppose) support well your datacard ?

Have you also tried with the usb modem that you can have too from Proximus ?

Thanks for the info
1: No, since it immediately re-prompts for PIN code combined with immediate logging of 'PUK required', it doesn't

2: I have only tried this 3G PCMCIA-card which is in my possession, nothing else (it's a company-card)

---

### Post by Macchi on 2009-01-17
I have a similar problem not being able to use a Huawei E600 ( recognized as E620) on Ubuntu 8.10 with the latest updates.

Network Manager 0.7 ask for a PIN and PUK on an unlocked card.
It never goes further since the question for the Personal Unblocking Key (PUK) on the Network-Manager-Gnome shows a limited frame and seems to acquire only four digits. But PIN and PUK keys can have from 4 to 8 digits!

(It is bad to experiment with this since after ten wrong attepts with the PUK the SIM card is permanently blocked.)

I am looking into the code for NM and search more before filing a bug.

---

### Post by ubulette on 2009-02-08
did you file a bug for that? either upstream or in launchpad?

---

### Post by asac on 2009-02-08
> **stephanvaningen said:**
> 
After checking the system logs, I see repetitive messages 'PUK required' 'status 4 -> 6', 'status 6 -> 4', ... every few seconds.


Could you please paste more context from your syslog?

---

### Post by asac on 2009-02-08
also to debug this we need the serial log. for that do:

```

$ sudo su
$ export NM_SERIAL_DEBUG=1
$ killall NetworkManager
$ NetworkManager --no-daemon 2>&1 | tee /tmp/nm.log.txt

```

Now reproduce your issue (try to connect multiple times).

Then file a bug with the nm.log.txt file attached (sanitize your PIN/PUK which might show up in the log first) and give us your bug id.

---

