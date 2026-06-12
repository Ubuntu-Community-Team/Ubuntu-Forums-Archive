---
title: "Help!"
date: 2007-09-24
forum: Networking &amp; Wireless
---

### Post by tsnell on 2007-09-24
I switched my Toshiba sattelite A105 from Vista to Ubuntu 6.1 Dapper Drake and now my wi-fi won't work. what do i do?

---

### Post by uxe1 on 2007-09-24
if you can find a way to, download the latest ubuntu. i never tryed dapper, but the one after it (edgy efft) was kinda week on the  wireless frount. the current (fiesty fawn) is working fine on alot of wireless cards. gutsy gibbion is due out some time in october so what ever you do youll be doing a lot of updating. 
im sure there are lots of ppl here who could offer better more experianced advice; but with just "Help!" in the subjcet line they may pass over your post unawares that they could offfer you assistance. try "dapper drake wifi not found" or " not responding", or whatever its doing and in the body of the note list what you have tried and puter specs. im a n00b as well but i have found that if you post that way you usualy get more qualifyed help (and sooner).
good luck!

---

### Post by harty83 on 2007-09-24
Give some info on your card.  Who is the manufacturer and what model do you have?

---

### Post by bmartin on 2007-09-24
Post the output of the following two commads. After that, we should be able to direct you on how to get it working:
```
sudo lshw -C network
lsusb
```
The first one is useful for non-USB sticks and the second is useful for USB.

---

### Post by tsnell on 2007-09-25
:confused:OK it's built in not USB or 1394 IEEE, so those commands won't work. It is an Atheros® Wireless LAN (802.11b/g) I hope this helps!

---

### Post by bmartin on 2007-09-25
MadWiFi might work, but just to be sure, let's see which Atheros chipset you have. Post the output of the following:
```
sudo lshw -C network
lspci -nn
```

---

### Post by tsnell on 2007-09-25
root@shin-chan:/home/tsnell# lshw -C network
*-network UNCLAIMED
          description: Ethernet controller
          product: Atheros Communications, Inc.
          vendor: Atheros Communications, Inc.
          Physical id: 0
          bus info: pci@02:00.0
          version: 01
          width: 64 bits
          clock: 33MHz
          capabilities: cap_list
          resources: iomemory:d0100000-d010ffff  irq:233

root@shin-chan:/home/tsnell# lspci -nn
0000:00:00.0  0600:   1002:5a31  (rev 01)
0000:00:01.0  0604:   1002:5a3f
0000:00:06.0  0604:   1002:5a38  
0000:00:12.0  0101:   1002:4379  (rev 80)
0000:00:12.0  0c03:   1002:4374  (rev 80)
0000:00:13.1  0c03:   1002:4375  (rev 80)
0000:00:13.2  0c03:   1002:4373  (rev 80)
0000:00:14.0  0c05:   1002:4372  (rev 82)
0000:00:14.1  0101:   1002:4376  (rev 80)
0000:00:14.2  0403:   1002:437b  (rev 01)
0000:00:14.3  0601:   1002:4377  (rev 80)
0000:00:14.4  0604:   1002:4371  (rev 80)
0000:01:05.0  0300:   1002:5a62
0000:02:00.0  0200:   168c:001c   (rev 01)
0000:09:04.0  0607:   1524:1410  (rev 01)
0000:09:06.0  0200:   10ec:8139  (rev 10)

That's the output hope it helps!

---

### Post by bmartin on 2007-09-25
> **tsnell said:**
> 0000:02:00.0  0200:   168c:001c   (rev 01)
Yep... that's an Atheros 5007EG; try [this thread]("http://ubuntuforums.org/showthread.php?t=512828").

---

### Post by bmartin on 2007-09-25
Is your computer an Acer laptop? If so, when your computer isn't plugged in, does Ubuntu detect that your computer's no longer plugged in? My girlfriend has an Acer laptop and it doesn't detect the fact that it has a battery.

I ask because you have a lot of similar hardware to what she has.

---

### Post by tsnell on 2007-09-25
thnx bmartin I'll try that!

---

### Post by tsnell on 2007-09-25
no it's toshiba satellite A105 I think I'll try installing 7.01 ans see if it works then, if not I'll be back!

---

### Post by bmartin on 2007-09-25
> **tsnell said:**
> no it's toshiba satellite A105 I think I'll try installing 7.01 ans see if it works then, if not I'll be back!
It won't. My girlfriend runs 7.10 on the same chipset and it didn't work OOTB.

---

### Post by tsnell on 2007-09-26
ok well i couldn't get it to install! it froze at 54% :(
I'll try that wcid first, if that don't work I'll let u know.

---

### Post by bmartin on 2007-09-26
What froze at 54%? The **wget** command? That's a file download.

---

### Post by tsnell on 2007-09-26
no my iso of 7.10 i burned it to cd and well, it froze @ 54% :(

BTW I checked the disk and it said that 1 file was corrupted what could i do???

---

### Post by bmartin on 2007-09-26
You checked the CD after burning and it said 1 file was corrupted? I'd either burn another disc or download a new ISO; it depends on whether the ISO is bad or the burn is bad.

Or do you mean that your hard disk had 1 file corrupted?

---

### Post by tsnell on 2007-09-26
not the hard disk, it was the cd. and I tried checking the 

MD5SUM (spelling)? but I couldn't get it to check it

(I'm downloading to WinXP Home)

---

