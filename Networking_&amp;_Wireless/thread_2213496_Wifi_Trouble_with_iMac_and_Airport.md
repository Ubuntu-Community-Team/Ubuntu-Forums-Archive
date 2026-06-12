---
title: "Wifi Trouble with iMac and Airport"
date: 2014-03-26
forum: Networking &amp; Wireless
---

### Post by Ryan_J_Kingkade on 2014-03-26
I am very new with linux and ubuntu and I am having a hard time getting the wifi to work.

I have Ubuntu 13.10 installed and working on a partition of my iMacs HD.  

Everything seems to be working great expect the wifi.  I have tried most everything I have found on the internet and even youtube.  Nothing seems to be working.

I have not given up yet!  Does anyone have a simple answer or work around for my problem?!

Thank you!

---

### Post by Hadaka on 2014-03-26
Hi please do .

```
sudo apt-get install linux-firmware-nonfree
```

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by Ryan_J_Kingkade on 2014-03-28
> **Hadaka said:**
> Hi please do .

```
sudo apt-get install linux-firmware-nonfree
```

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)


Thank you for the quick reply.  I tried this and it did nothing.  I should mention I have NO internet connection what so ever.  I am not hardwired so I cannot download anything.  Is there another way around this?

---

### Post by Hadaka on 2014-03-28
hi, no internet huh...fun stuff...
lets try a couple things..please do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo modprobe -r wl

```
boot...any improvement?
also do..
```
lspci -nnk | egrep '0200|0280'
```
just post back the [14e4:XXXX] numbers..thanks/

---

### Post by Ryan_J_Kingkade on 2014-03-28
Here is what I get:

sudo apt-get remove --purge bcmwl-kernel-source
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

What could that be?!

---

### Post by Ryan_J_Kingkade on 2014-03-28
I should mention that I have now hardwired my iMac to my internet.

---

### Post by Ryan_J_Kingkade on 2014-03-28
11ab:436a

---

### Post by Ryan_J_Kingkade on 2014-03-28
Sorry, here is what you wanted...

14e4:4328

---

### Post by Hadaka on 2014-03-28
ok..progress...please do..
From a wired connection to the internet
*Removes incorrect driver
Ignore any offer of proprietary or additional driver offers
```
sudo rm -rf /var/lib/apt/lists/lock
sudo apt-get update
sudo apt-get upgrade
sudo dpkg -r bcmwl-kernel-source
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo modprobe -rf wl
```
then do..
*Installs correct wireless driver
```
sudo apt-get install linux-firmware-nonfree
sudo modprobe -v b43
```
boot..disconnect your wired connection
wireless working?

---

