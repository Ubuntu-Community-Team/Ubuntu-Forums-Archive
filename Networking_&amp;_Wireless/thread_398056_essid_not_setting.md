---
title: "essid not setting"
date: 2007-03-31
forum: Networking &amp; Wireless
---

### Post by n00bd00d on 2007-03-31
Please help, I have been trying this on my own for too many weeks now.

I have a bcmwl5 wireless card.  I have had this working in dapper, but upgrading to edgy broke me and I can't seem to get working.

I blacklisted the card, installed ndiswrapper and loaded the windows driver using ndiswrapper.

ndiswrapper -l hows the driver installed and hardware present.

dmesg shows ndiwrapper being loaded, finding the card and drivers and aliasing the card to eth1.

sudo iwlist eth1 scan shows my network and others around me.  This means I still have everything working hardware wise, yes?

sudo iwconfig shows my eth1 settings with no essid set.

trying a sudo iwconfig eth1 essid <myessid> and then sudo iwconfig shows the essid is not being set!  I tried every combination I could think of with iwconfig eth1 key, managed, ifconfig eth1 up, etc... nothing enables me to set the essid.

dhclient fails in the normal way... no DHCP offers received after trying 5 times or so.

I have looked through dmesg, /var/log/messages and syslog.  Nothing seems out of the ordinary (comparing with others posts of these logs who have working systems).  Consistently, however is reported that eth1: link is not ready.  No more clues, however.

Why wouldn't I be able to set the essid?  I am assuming this is the reason why I can't get an address...

Thanks for any help.

---

### Post by chili555 on 2007-03-31
> I still have everything working hardware wise, yes?Yessir!

Sometimes, wireless cards will be knocked into action with the MAC address of the router, like this:```
chili@LAPTOP60:~$ sudo iwlist eth1 scan
Password:
eth1      Scan completed :
          Cell 01 - Address: **99:13:19:62:8D:F7**
                    ESSID:"GBR1"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=78/100  Signal level=-56 dBm  Noise level=-56 dBm
                    Extra: Last beacon: 52ms ago

chili@LAPTOP60:~$ sudo iwconfig eth1 ap **99:13:19:62:8D:F7**
```Then do *sudo dhclient eth1* and let us know.

---

### Post by n00bd00d on 2007-03-31
Wow!  Awesome!

That was all it took!

Unbelievable, I didn't even think of trying that.  In all of the posts and blogs I read I didn't come across that idea but that was what it wanted.

Any idea why this makes a difference?  Is this a bug with the edgy kernel?  Since this wasn't required with dapper and is with edgy, it seems the logical conclusion but not absolutely conclusive.  Maybe it's calling a different method within ndiswrapper or even the windows driver that dapper wasn't calling?


Anyway, you have no idea how much time I wasted on this, so thank you very much...

---

### Post by chili555 on 2007-03-31
I don't think it's a bug, I think drivers, ndiswrapper and, for that matter, routers are complex. What works effortlessly for one won't work, ever, for another. Different strokes...etc.

This morning I did a reinstall, and I connected my wireless in three commands: iwconfig essid, iwconfig key and dhclient. It took all of one minute. Yet I see posts here where people do the exact same thing and can't connect in two weeks! You just have to hit the right combination.

Glad it's working. If it doesn't survive a reboot, you can fix it in /etc/network/interfaces:```
wireless-ap <whatever_u_found>
```But that will slow you down a bit if you roam. I roam, but only from the family room to the bedroom.

---

