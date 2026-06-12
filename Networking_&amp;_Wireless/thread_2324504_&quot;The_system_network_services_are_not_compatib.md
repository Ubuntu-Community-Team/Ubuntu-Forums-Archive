---
title: "&quot;The system network services are not compatible with this version&quot;"
date: 2016-05-14
forum: Networking &amp; Wireless
---

### Post by johncroc on 2016-05-14
I rebooted my machine this morning and couldn't make a connection to my network.  My first reaction was to go to the network icon in the the upper right near the clock.  No joy, it wasn't there.  So I went to the general settings app and then to "Network" and got the message in the subject of this post.

I'm running 14.04 LTS.

My current kernel version is 3.13.0-86.

Before this morning, the last time I rebooted was probably a week ago as requested by Updater because of (I assumed) a kernel update.  I'm pretty sure Updater also wanted to do some updates either yesterday or the day before (which I OK'd), but it did not request a reboot.  Other than that there have been no user-initiated changes to my system.

Does anybody have any idea what might have happened and, maybe more importantly, how I begin to troubleshoot and resolve this?

---

### Post by wildmanne39 on 2016-05-14
Is this 14.04 you are using if so then you will need to downgrade your libnl-3 packages:
```
sudo apt-get install libnl-3-200=3.2.21-1 libnl-genl-3-200=3.2.21-1 \ 
libnl-route-3-200=3.2.21-1
```
if you can not install these packages or have trouble making the downgrade you can manually download them from here:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

1. Download the 3 files on another computer.
2. Copy them to a flashdrive.
3. Put the flashdrive into the affected computer.
4. Copy the 3 files into a new folder.
5. Open a terminal in that folder and run

```
sudo dpkg -i lib*.deb
sudo reboot

```
I would put a hold on NetworkManager packages until a fix is released.

```
sudo apt-mark hold libnl-3-200 libnl-genl-3-200 libnl-route-3-200
```

 And after the fix:

```
sudo apt-mark auto libnl-3-200 libnl-genl-3-200 libnl-route-3-200
```
Answer came from here but had an outdated link for downloading the files.
[http://askubuntu.com/questions/727188/the-system-network-services-are-not-compatible-with-this-version-ubuntu-14-04](http://askubuntu.com/questions/727188/the-system-network-services-are-not-compatible-with-this-version-ubuntu-14-04)

---

### Post by johncroc on 2016-05-14
Thank you!  I actually saw the post you referenced (before I posted my original question), but since there was no "green check" for accepted answer, I was hesitant to use the suggested solution.  I will try what you have suggested and report back.

---

### Post by Nosphky on 2016-05-14
This problem has also affected me and many others. It was down to a regression caused by a 'defective' system update we probably all did yesterday. There are many defensive comments saying that this bug only affects those who download and apply 'trusty proposed' updates but that is not true.  Many of us affected do not have 'trusty proposed' selected on our update settings.

There are several proposed solutions but they mostly come down to downgrading the libnl packages. To do that you most likely need internet access on another machine to download the packages (if your package manager cache doesn't have the old versions) and then transfer them via a usb stick to your broken machine.

The procedure outlined in this link under steps 2 and 3 worked nicely for me :

[http://askubuntu.com/questions/727127/last-upgrade-crashes-network-manager-no-internet-connection-no-applet](http://askubuntu.com/questions/727127/last-upgrade-crashes-network-manager-no-internet-connection-no-applet)

I suppose the update record cannot be too bad. In 2 years of accepting all the updates proposed by the system (generally 2 or 3 times each week), this is the first time it has broken my system.

---

### Post by johncroc on 2016-05-14
The answer above, and quoted below, has resolved my network issue.

Thank you, Wild Man!!  Your instructions were clear, to the point, and effective.

JC

> **Wild Man said:**
> Is this 14.04 you are using if so then you will need to downgrade your libnl-3 packages:
```
sudo apt-get install libnl-3-200=3.2.21-1 libnl-genl-3-200=3.2.21-1 \ 
libnl-route-3-200=3.2.21-1
```
if you can not install these packages or have trouble making the downgrade you can manually download them from here:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

1. Download the 3 files on another computer.
2. Copy them to a flashdrive.
3. Put the flashdrive into the affected computer.
4. Copy the 3 files into a new folder.
5. Open a terminal in that folder and run

```
sudo dpkg -i lib*.deb
sudo reboot

```
I would put a hold on NetworkManager packages until a fix is released.

```
sudo apt-mark hold libnl-3-200 libnl-genl-3-200 libnl-route-3-200
```

 And after the fix:

```
sudo apt-mark auto libnl-3-200 libnl-genl-3-200 libnl-route-3-200
```
Answer came from here but had an outdated link for downloading the files.
[http://askubuntu.com/questions/727188/the-system-network-services-are-not-compatible-with-this-version-ubuntu-14-04](http://askubuntu.com/questions/727188/the-system-network-services-are-not-compatible-with-this-version-ubuntu-14-04)

---

### Post by wildmanne39 on 2016-05-14
Your welcome! I am glad it worked.

---

### Post by jkeenan on 2016-05-14
I experienced exactly the same problem as johncroc.  I dutifully update packages when prompted to do so.  I had shutdown my Ubuntu 14.04 x86_64 machine before travel.  When I rebooted -- at a computer language user group meeting I was meeting, no less! -- the Wireless icon was missing from the menu bar and I had no internet access.  Even when I got home and plugged in my Ethernet, I still had no connection.  I had to boot a 12-year-old iMac to get online and found this thread via DDG.  I followed Wild Man's instructions and they worked like a charm!

Thanks to both johncroc for posting and to Wild Man for the quick response.

---

### Post by JamButty on 2016-05-20
Thanks Wild Man for fix and to jkeenan for pointing me here!  Same baffling problem, same effective solution. Note: I could not find those files using the search functions on [http://packages.ubuntu.com/](http://packages.ubuntu.com/), but a general search on each (e.g. libnl-3-200 3.2.21-1)  brought me to the right pages under that url

---

