---
title: "strange problem and stranger solution"
date: 2008-10-01
forum: Networking &amp; Wireless
---

### Post by tyk on 2008-10-01
Hi all,
Although this is related to a [previous thread]("http://ubuntuforums.org/showthread.php?t=914780"), I feel this merits a new one. This is my setup:
box 1 - q6600; xubuntu 8.04; adsl wired etc.
box 2 - ibm t23 thinkpad; xubuntu 8.04; adsl wired etc.

For weeks I have been trying to figure out why internet simply does not work on the older thinkpad, or is painfully slow; pinging gave on an average 80-85% packet loss. While transferring stuff from box 1 to 2 with a usb stick (standard something or the other..) **I realized that internet works perfectly when the usb stick is plugged in.** 
This is completely reproducible. I am updating the thinkpad right now and if I eject the usb stick, download (and internet) speed falls to 500B/s or mostly 'unknown'. Plug it back in and it zips at 30-40 kb/s which is normal for my connection.

*What gives??*

---

### Post by vniksic on 2008-10-01
> **tyk said:**
> Hi all,
For weeks I have been trying to figure out why internet simply does not work on the older thinkpad, or is painfully slow; pinging gave on an average 80-85% packet loss. While transferring stuff from box 1 to 2 with a usb stick (standard something or the other..) **I realized that internet works perfectly when the usb stick is plugged in.** 
This is completely reproducible. I am updating the thinkpad right now and if I eject the usb stick, download (and internet) speed falls to 500B/s or mostly 'unknown'. Plug it back in and it zips at 30-40 kb/s which is normal for my connection.

*What gives??*

Sounds like buggy or strange hardware to me. Can you see the same results on another distribution, or another OS completely?

---

### Post by tyk on 2008-10-01
I actually tried ubuntu, dsl and knoppix on the thinkpad but it always had internet problems. I feel it is by chance that I noticed this while running xubuntu... 
now i keep the usb plugged in all the time. will try this with some other usb device like a mouse or webcam.

--edit= yes its true. removed usb storage and net went down. plugged in usb camera and we're back. i am foxed. but happy that i have a solution of sorts.

---

