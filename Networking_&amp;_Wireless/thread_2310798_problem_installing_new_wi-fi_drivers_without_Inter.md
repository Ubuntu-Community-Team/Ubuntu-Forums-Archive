---
title: "problem installing new wi-fi drivers without Internet connection, Lubuntu 15.10"
date: 2016-01-22
forum: Networking &amp; Wireless
---

### Post by anotherChris on 2016-01-22
I'd like to install 15.10, but on a LiveDVD boot the wi-fi doesn't work.  _**Big problem**_: the only Internet access I have is my current wi-fi connection.   I guess I need to know about downloading the relevant files to a DVD or USB flash drive and installing from there.  Here's what I know so far...


computer: Dell Inspiron 1545 2GB RAM 160GB memory Lubuntu 11.10
wireless: **BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)**
subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]
kernel driver: b43-pci-bridge


I've found the following webpage, which describes installation without Internet access:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)


It looks like I can choose to install STA or b43, and as my current kernel driver says **b43-pci-bridge**, I think I should go with the b43 option.


Next, this webpage uses instructions for 14.04.  The 15.10 LiveDVD does not contain **../pool/restricted/b/bcmwl** or **../pool/main/b/b43-fwcutter/** as mentioned on this page.


I think what I need is found on the following webpage:
[https://launchpad.net/ubuntu/+source/b43-fwcutter/1:019-2](https://launchpad.net/ubuntu/+source/b43-fwcutter/1:019-2)


Now... I've never installed anything on a Linux system before, so at this point I'm starting to really get lost if I'm not already...


Is **b43-fwcutter_019.orig.tar.bz2** (found on last web page mentioned) everything I need to download or is there a separate download for the actual Broadcom firmware?  If there's a separate download, where is it?


Also, what are the correct commands for installing the b43-fwcutter and then the firmware?


I tried following the commands given on the previous web page for the fwcutter, but substituting **b43-fwcutter-019**, and I got the following error:
```
dpkg-deb: error: `b43-fwcutter.1' is not a debian format archive
```

I'm completely lost when I get errors like that.

Please advise.  Thanks.

---

### Post by Hadaka on 2016-01-22
Hi, try this..post #7
[http://ubuntuforums.org/showthread.php?t=2098717](http://ubuntuforums.org/showthread.php?t=2098717)
this is a know working method.
Here is another link for you to verify your [14e4:4315] pcid
uses the b43 driver
[http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)
thanks.

---

### Post by anotherChris on 2016-01-22
Hi Hadaka,
I'm reading the 2098717 thread now to try to understand it.  I saw the 2214110 thread was a sticky.  I guess you're telling me the driver firmware hasn't changed since 14.04.  

This question might be academic, but if the driver firmware hasn't changed, what's with the continual updates on the b43-fwcutter?  Is that completely to do with changes in the "extracting" portions of the Lubuntu software and nothing to do with changes in the b43?  (Sorry if my concepts or terms are muddled.  I'm a newbie.)

---

### Post by Bucky Ball on 2016-01-22
Updates, bug fixes, improvements, security, add new devices. No maintained software remains static. Standstill and become obsolete.

---

### Post by anotherChris on 2016-01-22
> **Hadaka said:**
> Hi, try this..post #7
[http://ubuntuforums.org/showthread.php?t=2098717](http://ubuntuforums.org/showthread.php?t=2098717)
this is a know working method.
Here is another link for you to verify your [14e4:4315] pcid
uses the b43 driver
[http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)
thanks.

OK, I think I understand the thread you recommended.  One poster recommended this...


```

sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
sudo apt-get install linux-firmware-nonfree

```


...but you said it doesn't work because you need an Internet connection.


Then you recommended downloading the zip you attached to your post and doing this...


```

sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43

```


So... you put the driver on your desktop, then copy it into a new directory, then remove all the current drivers from the kernel and add in the b43 driver.  I assume the computer automatically knows to look in a lib/firmware/ directory when adding to the kernel (?).


I will try this, but I have a few questions if you don't mind...


(1) This won't work when I've booted from a LiveDVD, right?  It will only work if I install?
(2) I understand you have to remove all the current drivers, but how do you know what's in there?  Where does "ssb" come from?  And on this other page [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx), they're also removing "wl" and "brcmsmac"--where do those come from, and why don't I have to remove them?
(3) is there a reason to use **rmmod -f** instead of **modprobe -r** ?
(4) I understand that the driver I need is in the zip.  This is so easy.  Why isn't this zip just available for download?  When I Google "b43 driver", I get lots of stuff referring to the b43-fwcutter and other kinds of directories needing extraction...


Sorry about these questions.  I think you know what you're doing; I'm just trying to understand.

Anyway, thanks for your reply.  After I get the driver installed and the wi-fi working, I'll change the prefix to SOLVED!

---

### Post by Hadaka on 2016-01-22
Hi, this method had been used hundreds if not thousands of times.
If you search ubuntu forums it is easy enough to verify.
if you follow the simple instructions..you should have no problems
First drag and drop the zip file to the Desktop, then right click and and choose extract here.
then copy and paste the commands one at a time in the terminal.
the commands do..
1.make a directory in /lib/firmware/b43
2.copy the extracted b43 zip file to the above directory
3.remove modules if they exsist
4. load the b43 driver
You should now have internet access..attach and
Then do..
```
sudo apt-get update
```
to bring your dirver up to date.

^IF you attempted to load the sta driver then first do..
```
sudo apt-get remove --purge bcmwl-kernel-source
```
and 
if you need to remove the b43 driver do..
```
sudo apt-get remove --purge firmware-b43-installer
```
and finally if you are uncomfortable with any of this...then dont load it.

---

### Post by anotherChris on 2016-01-24
Hi Hadaka,
It worked like a charm.  Thank you.  Sorry you seem annoyed, but let me quote from myself...
> **anotherChris said:**
> Sorry about these questions. I think you know what you're doing; I'm just trying to understand.
This is the first time I have used the terminal and unix commands, so I was, literally, just trying to understand.  Thanks.

---

### Post by Hadaka on 2016-01-24
Hi anotherChris, no i was not annoyed at all, I apologize if came I off
that way.I would suggest to anyone to never enter any command or
load any data if they are not feeling secure or are uncomfortable doing
so. Glad that worked for you.

---

