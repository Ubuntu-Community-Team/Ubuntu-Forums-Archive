---
title: "HOWTO: Get Wireless Card RT61 on Gutsy Gibbon with WPA and dhcp"
date: 2007-10-20
forum: Networking &amp; Wireless
---

### Post by Grafster on 2007-10-20
This DOES NOT WORK in GUTSY.
In fact the card, or at least the version of it that I have, doesn't work at all in Gutsy. For some reason they've "updated" the driver to a nonfunctioning one. I had hopes I'd figure something out but today I reinstalled Fiesty.
It may be the specific implimentation that I have as opposed to a global RT61 thing.

I've left this here just as a record. (this is the best way to get it working on a bog standard fiesty install)


What: How to get your Wireless Card using a Ra-link chip called RT61 working on Gutsy. This will probably only work if you use [dhcp]("http://en.wikipedia.org/wiki/Dynamic_Host_Configuration_Protocol"); if you don't know what it is or aren't sure then it's probable that you use it (the wiki link explains it in more detail if you want to try to think it through for yourself).
Basis: Based totally on the excellent and simple [post]("http://ubuntuforums.org/showthread.php?p=2784369#post2784369") by [takuzinis ]("http://ubuntuforums.org/member.php?u=44153"). The original thread that post is in is also a good resource, but until takuzinis' post everything is too hard to follow for the average user and/or doesn't work.

Note: If you aren't sure what chipset your card uses you can use commands like lsmod to try to figure it out. If you're here I'm assuming you've figured out the chipset of your card (RT61 by Ralink).

Note: I didn't have anything to do for step 2, in gutsy, but you might, so make sure to get rid of anything related to ra0 or ra1 in the etc/network/interfaces file.

Note: I was prompted again for my Wireless Network login password etc when I got connected, so some lines may not be necessary. But I figure... why mess with something that works.

> **takuzinis said:**
>  Mostly peple have dhcp therefore I would suggest ...  you simply:

**Step 1**

```

ubuntu@ubuntu:~$ sudo gedit /etc/network/interfaces

```

Delete everything related to ra0 (or ra1) and around that.

**Step 2**

Add at the beginning of /etc/network/interfaces following:

```

auto ra0
iface ra0 inet dhcp
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwconfig ra0 essid my_essid
pre-up iwpriv ra0 set WPAPSK="my_pass_key"

```

In my case it was:

```

auto ra0
iface ra0 inet dhcp
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwconfig ra0 essid ZEB
pre-up iwpriv ra0 set WPAPSK="zebiekste"

```

*use ra1 instead of ra0 if necessary

**Step 3**

Reboot

**Start browsing**

My System Details
Acer TravelMatt230 (laptop)
Xubuntu [Gutsy Gibbon] 32bit
Card DWL-G630 D-Link AirPlus G (bought in Singapore)

Why am I posting this; Cause it's a bear to get wireless working in ubuntu, and I figure every post helps.

---

### Post by K.Mandla on 2007-10-26
Moved to Networking and Wireless.

---

