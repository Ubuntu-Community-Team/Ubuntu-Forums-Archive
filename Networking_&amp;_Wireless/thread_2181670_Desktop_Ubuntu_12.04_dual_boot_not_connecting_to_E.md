---
title: "Desktop Ubuntu 12.04 dual boot not connecting to Ethernet or wireless"
date: 2013-10-18
forum: Networking &amp; Wireless
---

### Post by AmyR on 2013-10-18
Hi,
I am very, very new to Linux, and I just installed a dual boot of Ubuntu 12.04 on a windows 7 desktop. I can't seem to get it to connect to any sort of Internet connection, Ethernet or wireless. When I am logged into windows I am able to get the wireless to work using a Belkin USB wireless adapter, but also cannot get the Ethernet to work on windows either. I have installed ndiswrapper on Ubuntu, and according to it I have successfully installed a driver for my wireless USB adapter. Any pointers would be extremely useful. The desktop is a dell optiplex 760.

---

### Post by UltimateCat on 2013-10-18
Welcome to the Ubuntu forums!

It's been a very long time since I used ndiswrapper but when I had a usb adapter I had to blacklist one of the drivers in order for the driver that was installed to work.

As I recall I had a Linksys adapter and I installed a rtl8168 linux driver for it. I had to blacklist the rtl8169 to get the internet working.

To find out what adapter you have you can run:
```
lsusb

```
And post the output here so others can help you. 

I'm not the best with internet connections and configuring the network manager.
I found some webpages that you can read that may be of use.

[http://ubuntuforums.org/showthread.php?t=1482382](http://ubuntuforums.org/showthread.php?t=1482382)
[http://opensource.bureau-cornavin.com/belkin/](http://opensource.bureau-cornavin.com/belkin/)

Hope that helps-

---

### Post by varunendra on 2013-10-19
Hi AmyR,

I saw your other post [post=12820602]here[/post] and you seem to have already fixed your wireless issue with that thread, thanks to dr. chili555. Congrats for that, since it is a really rare chip using a very new driver that not many people can help with :).

Regarding the Ethernet -
> **AmyR said:**
> but also cannot get the Ethernet to work on windows either.
This make me suspect if it is even functional at all.

Did the desktop come with Win7 pre-installed or you installed it yourself?
Did the Ethernet ever work before?
Do you have any indication of it being functional?

Please check your BIOS to make sure it is enabled there, and post back the output of -
```
lspci -nnk | grep -A2 0200
```

While posting the outputs, please use the '**Code**' box. It preserves its formatting and makes your post cleaner, compact and more readable. Follow the "Using Code Tags" link in my signature to see how.

---

### Post by The Cog on 2013-10-19
Moved to Networking and Wireless, where it should reach a better audience and get buried less quickly.

Welcome to the forums, AmyR. I hope we get your problems sorted.

---

