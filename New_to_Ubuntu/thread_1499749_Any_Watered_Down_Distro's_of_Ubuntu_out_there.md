---
title: "Any Watered Down Distro's of Ubuntu out there????"
date: 2010-06-02
forum: New to Ubuntu
---

### Post by suomalainen on 2010-06-02
Ubunteros,

I got a real old PC that when bought years ago could only run Windows 95.

I wiped the HDD and tried to install Ubuntu 10.04 to no avail....

I need a watered down distro of Ubuntu but do not know where to get it or if I need to strip the current iso of 10.04 to manually make something.

Your assistance is greatly appreciated.

Thanks!!!!

---

### Post by philinux on 2010-06-02
How much memory has it got.

Peppermint might be ok [http://peppermintos.com/](http://peppermintos.com/) it needs 200 meg.

You could start with the ubuntu minimal cd and then install only what you want. I've just done this using minimal then installing lxde.
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Or there are other ways.
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by bkratz on 2010-06-02
> **suomalainen said:**
> Ubunteros,

I got a real old PC that when bought years ago could only run Windows 95.

I wiped the HDD and tried to install Ubuntu 10.04 to no avail....

I need a watered down distro of Ubuntu but do not know where to get it or if I need to strip the current iso of 10.04 to manually make something.

Your assistance is greatly appreciated.

Thanks!!!!

Well, I just finished downloading Lubuntu, looks promising for older systems.

---

### Post by suomalainen on 2010-06-02
**philinux**

I believe that I'm working with 256 of RAM

Does this hurt or kill me?????


**bkratz**

How do you like Lubuntu???????


**Thank you for your support!!!!**

---

### Post by philinux on 2010-06-02
> **suomalainen said:**
> **philinux**

I believe that I'm working with 256 of RAM

Does this hurt or kill me?????




I'd give peppermint a go then. I tried Lubuntu but preferred Peppermint.

About Peppermint
System Requirements:

    * i386 or derivative processor (AMD64 and x86_64 are fine as well)
    * 256 MB of RAM (possible it works with as little as 192, but not positive)
    * 4 GB hard drive space (this is an overestimate just for good measure)

Iso is only 407 MB Lubuntu is 521MB

---

### Post by bkratz on 2010-06-02
> **suomalainen said:**
> **philinux**

I believe that I'm working with 256 of RAM

Does this hurt or kill me?????


**bkratz**

How do you like Lubuntu???????


**Thank you for your support!!!!**



Just downloaded, will probably be a few hours before I can try it.  Here are the specs.

Intended Audience

Lubuntu is targeted at "normal" PC users running on low-spec hardware. Such users may not know how to use command line tools, and in most cases they just don't have enough resources for all the bells and whistles of the "full-featured" mainstream distributions.

A Pentium II or Celeron system with 128 Mb RAM is probably a bottom-line configuration that may yield slow yet usable system with Lubuntu. It should be possible to install and run Lubuntu with less memory, but the result will likely not be suitable for practical use. 

and a link to look at.

[https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

---

### Post by skompier on 2010-06-02
I like Peppermint and since it's based on Lubuntu, you get that plus more.

---

### Post by lukeiamyourfather on 2010-06-02
While a minimal Linux distribution might install and boot on a machine circa 1995, it will be practically unusable for average tasks (watching videos, browsing the web, editing photos, etc.). Just loading Youtube in Firefox would probably start using swap.

If you must then I'd start with a minimal install of Ubuntu and install Openbox. Cheers!

---

### Post by goseph on 2010-06-02
I have a similar situation 190MB of memory, does anybody know which out of Lubuntu and Peppermint OS is lighter weight?

I know that peppermint says 192MB as absolute bottom line and Lubuntu say 120MB as absolute bottom line. I just wonder if there is a reason for the discrepancy or Peppermint has a little more bloat?

If there is no difference then I will probably grab Peppermint.

---

### Post by goseph on 2010-06-02
Also is there any difference in how easy these two are to use? Ease-of-use is a must! Do they both come with the software centre?

---

### Post by suomalainen on 2010-06-02
And I would like to know if I can use my USB broadband stick from Saunalahti??

I have 10.04LTS installed and Network Manager Applet 0.8 found my stick automatically and I was on the internet within seconds!!!!

So, I'd  like to have exact same results with peppermint or Lubuntu. Which is better choice for me??

I think it's Lubuntu cause it's a copy of Ubuntu 10.04 but can anyone confirm this for sure?????

Thanks again all for your support!!!!

---

### Post by philinux on 2010-06-02
> **suomalainen said:**
> And I would like to know if I can use my USB broadband stick from Saunalahti??

I have 10.04LTS installed and Network Manager Applet 0.8 found my stick automatically and I was on the internet within seconds!!!!

So, I'd  like to have exact same results with peppermint or Lubuntu. Which is better choice for me??

I think it's Lubuntu cause it's a copy of Ubuntu 10.04 but can anyone confirm this for sure?????

Thanks again all for your support!!!!

I'd ask in here. [http://ubuntuforums.org/showthread.php?p=9400070#post9400070](http://ubuntuforums.org/showthread.php?p=9400070#post9400070)
I know peppermint is running the same kernel as lucid.

---

### Post by suomalainen on 2010-06-04
All,

I tried installing:

1. Ubuntu mini to no avail
2. Lubuntu to no avail
3. Peppermint to no avail

All appeared to be going through the install process but then after some time just hung and didn't move further....

Any ideas what can be done to get them going?

---

### Post by wojox on 2010-06-05
Try puppy. It's based of Lucid. [Puppy Linux]("http://puppylinux.org/main/index.php?file=Overview%20and%20Getting%20Started.htm")

---

### Post by 4Orbs on 2010-06-05
The old computer that was running Windows 95... if the BIOS were never updated to something from the year 2000 or newer, then you'll never get any Ubuntu installed because the kernel cutoff date is 2000. Any BIOS older than that will just return a kernel panic error. Maybe try the very oldest version of Puppy or Damn Small Linux.

The other poster... if you're trying to install Ubuntu while using only the USB Wireless receiver: it probably is hanging up when attempting to detect the network connection. You need to install with a wired connection.

In both cases, I could be wrong.

---

