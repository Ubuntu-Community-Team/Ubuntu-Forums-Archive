---
title: "Another thread about Dell Wireless not working"
date: 2007-02-22
forum: Networking &amp; Wireless
---

### Post by lunchbox_1973 on 2007-02-22
Hello,

Like countless others I can't get my wireless card working. I have a Dell Inspiron 1300 with the broadcom 1470 wireless card.

I've read through many other threads and how to's to fix this and I've done just about everything I can think of.

- I blacklisted the driver it came with
- I installed the windows driver using ndiswrapper

Ubuntu refuses to recognize my wireless card. The only thing it sees is my wired ethernet card.

When I install the driver I get this message (I used the gui version of ndiswrapper)


[IMG]http://img.photobucket.com/albums/v284/rubbief2k1/Screenshot-WirelessNetworkDrivers.png[/IMG]

When I use the terminal it shows the driver is installed, I just don't get the fancy GUI message that "hardware present:no"

"rob@insp1300linux:~$ ndiswrapper -l
Installed drivers:
bcmwl5          driver installed 
bcmwl5a         driver installed "


The device manager lists my wireless card so it is present and ready to be used.

By the way I tried both the BCMWL5A.INF and BCMWL5.INF drivers because even though the latter is newer I read of other people using the "a" version with success. I tried them one at a time and them together like seen above.


Does anyone have any ideas what could be wrong? I'm really getting frustrated here, my wireless dilemma is really the last thing holding me back from ditching Windoze and going Linux full time.

Thanks.

---

