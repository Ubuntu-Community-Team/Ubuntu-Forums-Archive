---
title: "Help with my microsoft mn-510 wireless card"
date: 2007-07-02
forum: Networking &amp; Wireless
---

### Post by acast2003 on 2007-07-02
hello, i am new to ubuntu 7.04 and basically have no idea how to use it but i am trying to run my microsoft mn-510 wireless adapter. i have downloaded the linux-wlan-ng program, but i have no idea on how to use it. If someone could please provide me with advice on how to make my adapter work with ubuntu using the linux-wlan-ng program i would greatly appreaciate it. thanks

---

### Post by jpl80 on 2007-07-02
go to the command line and type in this:

sudo lsusb -v

post the output (should be about 5 lines) that starts with something that looks like this:

02:03.0 Network controller...

This will tell us what chipset you have. Then [go here to see if that chipset is supported]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported").

---

### Post by jpl80 on 2007-07-02
You should also read the readme file that is included in linux-wlan-ng. I think you have to build it and there are instructions on how to do that in the README.

---

### Post by acast2003 on 2007-07-02
ok, i wil try what you have suggested. thank you

---

### Post by acast2003 on 2007-07-02
i did not work, i have looked all over the net for programs to make the adapter work on fiesty fawn, such as ndiswrapper and wlan-ng, i have ndis wrapper, but i just think i am installing ndis wrapper the wrong way, can anyone tell me how to get ndis wrapper to work, remember, i am a total noob at linux

---

