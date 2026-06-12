---
title: "trying puppy linux"
date: 2009-12-30
forum: New to Ubuntu
---

### Post by DarinB on 2009-12-30
I'm trying puppy linux, but can't get it to go online anybody know about this, i do realize this is not an ubuntu issue.

---

### Post by DarinB on 2009-12-30
also will puppy linux triple boot with Jaunty and vista?
i don't want to kill my jaunty install.

---

### Post by thatguruguy on 2009-12-30
As to the "triple boot" issue, just run puppy from a USB drive.  In fact, that's what the puppy linux developers recommend: [http://puppylinux.org/main/index.php?file=How%20NOT%20to%20install%20Puppy.htm](http://puppylinux.org/main/index.php?file=How%20NOT%20to%20install%20Puppy.htm)

As to the "going online" issue, I'd suggest you go to the [puppy linux forum]("http://murga-linux.com/puppy/") and ask there.

---

### Post by DarinB on 2009-12-30
I really knew that was the best option.... I just find the best info here I think the Ubuntu crowd has more talent.

---

### Post by wilee-nilee on 2009-12-30
Puppy if installed will take over the MBR so you might consider running it in a virtual until you have the correct install method.

---

### Post by ajgreeny on 2009-12-30
Don't bother to install it to hard disk but run from CD.  When you shutdown you will be given the option firstly to save your own personal settings and files to a file on the hard disk or flash drive, if connected, and your preferred save destination, and then also to save another file from the CD to allow faster bootup next time.  Accept both, as that is the best way to use it.

As for web connection, more info is needed, particularly if wireless, as everything will depend on hardware and driver availability.

---

### Post by DarinB on 2009-12-30
plane old broadband with a lynksis router. the puppy linux forums are pretty weak on knowledge. 
i didn't see an option for network connection for broadband??? but i cant look at it an be on line at the same time...kinda sucks when that happens

---

### Post by louieb on 2009-12-30
Wired or wireless?

What happens when your run the internet connection wizzard?

---

### Post by DarinB on 2009-12-30
wired when i run Internet connection wizard there is no choice for broadband? and it says no connection found.

---

### Post by DarinB on 2009-12-30
i tried network or wireless lan but i did not find the card there i did autoprobe but then did not find a module for it...
this is my ethernet info from lshw:
*-network
                description: Ethernet interface
                product: 88E8001 Gigabit Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: c
                bus info: pci@0000:06:0c.0
                logical name: eth0
                version: 13
                serial: 00:24:8c:02:b0:cb
                size: 100MB/s
                capacity: 1GB/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.13 duplex=full firmware=N/A ip=192.168.1.100 latency=32 link=yes maxlatency=31 mingnt=23 module=skge multicast=yes port=twisted pair speed=100MB/s

---

### Post by louieb on 2009-12-30
> **DarinB said:**
> i tried network or wireless lan but i did not find the card there... 

That was going to be my next question.   Did it list any cards? 
For a wired connection - all I have ever had to do  is select the card. Then Select auto DHCP. Then I get a connection. 

Sorry I don't have any idea what to try next.

---

### Post by jrusso2 on 2009-12-30
I have a feeling it does not have a driver for that marvel ethernet card.

---

