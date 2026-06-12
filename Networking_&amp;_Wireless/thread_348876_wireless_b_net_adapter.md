---
title: "wireless b net adapter"
date: 2007-01-29
forum: Networking &amp; Wireless
---

### Post by dhani99 on 2007-01-29
i have installed ubuntu recently, and i have connected my wireless b network adapter but its not showing any wireless adapter,its showing only ethernet adapter  help needed plz:confused:

---

### Post by tturrisi on 2007-01-29
What make and model# adapter?

---

### Post by dhani99 on 2007-01-29
model no wireless network b adapter , its not showing this device in linux but working in xp . i installed linux today and dont know more about linux help me .

---

### Post by tturrisi on 2007-01-30
> **dhani99 said:**
> model no wireless network b adapter , its not showing this device in linux but working in xp . i installed linux today and dont know more about linux help me .
OK.
What make model# adapter?
This time, physically look at it and read the writing on it.

---

### Post by dhani99 on 2007-01-30
linksys wireless b usb network adapter 2.4 ghz, 802.11b

---

### Post by dhani99 on 2007-01-30
wusb11

---

### Post by dhani99 on 2007-01-30
wusb11v4

---

### Post by tturrisi on 2007-01-30
The Linksys WUSB11 version4 is NOT supported in Linux.
[http://linux-wless.passys.nl/query_part.php?brandname=Linksys](http://linux-wless.passys.nl/query_part.php?brandname=Linksys)
[http://www.qbik.ch/usb/devices/showdev.php?id=3060](http://www.qbik.ch/usb/devices/showdev.php?id=3060)

---

### Post by dhani99 on 2007-01-30
any chances plz?

---

### Post by dhani99 on 2007-01-30
but friend it shows on upeer link will work with ndishwrapper.and i dont know how to install ndishwrapper.thanks its this link
[http://www.qbik.ch/usb/devices/showdev.php?id=3060](http://www.qbik.ch/usb/devices/showdev.php?id=3060)

---

### Post by FrodoB on 2007-01-30
See:

[https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB11v4_%28ndiswrapper%29?highlight=%28Wi%20fiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB11v4_%28ndiswrapper%29?highlight=%28Wi%20fiDocs%2FDevice%29)

---

### Post by dhani99 on 2007-01-30
but i have installed linux 6.10 yesterday, and i dont know anything about it. i dont know where to write that commands and what to do plz need help. i want to access web.thank u

---

### Post by dhani99 on 2007-01-31
help me beginner here, plz

---

### Post by FrodoB on 2007-01-31
Well all of the commands have to be type or cut and pasted into a terminal window. You have to click on the Applications menu in the upper left hand corner to get there:

Applications -> Accessories -> Terminal

All of the items in the instructions that are prefaced with:

user@ubuntu:~$

have to be typed into or pasted into a terminal window.


General help on Ubuntu:

[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

Be patient, and you will get there.

---

### Post by dhani99 on 2007-01-31
thank u very much, if i have any prob ill contact u 
thank u.

---

### Post by dhani99 on 2007-02-01
yes i got that there but they have told that extract ndishwrapper by make , i dont know  what is make? and where can i find it? and another one i cant run exe file they shows that u dont have installed apropriate program like this. thank u very much.

---

### Post by FrodoB on 2007-02-02
make is just a command that you run from a terminal.  Make is the system that tells the compiler what to do to build binary executable programs from software code.

---

### Post by dhani99 on 2007-02-03
first of all when i type ndiswrapper in terminal in window it shows bad command or...like that and then i can successfully build envirnomnet and that things but i cant install ndiswrapper.but i tried lsusb command and that comand shows me details of card, but actually ndiswrapper is not installed ever successfully.

---

### Post by dhani99 on 2007-02-07
help me out plz.................................................
..............................................................
...............................................
....................................
.......................

---

### Post by dmizer on 2007-02-07
you know ... you are going to have a MUCH more pleasant linux/ubuntu experience if you get a wireless adapter that works without configuration.  your usb adapter looks to be one of the most painful i've seen to install.

go here: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
look through the list, find a card that will work without you having to compile the source code of ndiswrapper.

wireless adapters are not prohibitively expensive.

---

