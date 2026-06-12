---
title: "Internet slow or doesn't work"
date: 2014-05-20
forum: Networking &amp; Wireless
---

### Post by gijs2 on 2014-05-20
Hello,

Since today i've acquired Ubuntu and it has been great, but there is one problem that has really been bugging me.
My internet is either verry slow or my laptop won't connect with ANY wireless network, wich is verry annoying.

Hopefully anyone would be able to help me with my problem, thanks :)

---

### Post by wildmanne39 on 2014-05-20
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz)depending on the size of the file and it will be placed in your home folder. The wireless information will help to diagnose your wireless issue, the Mac address, WPA key and WEP key are removed for your security, then reply back, click on the paper clip and attach the (wireless-info.txt, or wireless-info.txt.tar.gz) file as a zip file. 

If you do not have ethernet connection then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385).
Thanks

---

### Post by gijs2 on 2014-05-20
Thanks for the quick reply, i've put the .tar.gz in the attachements.

---

### Post by wildmanne39 on 2014-05-20
There are issues with the driver your device uses since it is still a fairly new device, but you also have a second driver loaded ath9k, I suggest we blacklist it unless you are using it for some reason.
```
echo "blacklist ath9k" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Thanks

---

### Post by wildmanne39 on 2014-05-20
Also you should try channel 1 or 11 in your router.

Your driver is not loaded automatically so do:
```
sudo su 
echo rtl8188ee >> /etc/modules 
exit
```
we may have to try a parameter, but this is the first time I have worked with this driver and I am short on time because work just come up so if someone else with experience would like to jump in that would be great.
Thanks

---

### Post by gijs2 on 2014-05-20
Alright i've pasted that in my terminal and i've restared my laptop, any other advice since it still isn't as fast as it was when i used windows.
And it isn't the problem with my router because i experience the same problem at work.

---

### Post by wildmanne39 on 2014-05-20
Did you reboot? is there any improvement?

---

### Post by gijs2 on 2014-05-20
> **Wild Man said:**
> Did you reboot? is there any improvement?

I did reboot, and there is no improvement.
And it is not the channels of my router since the same problem occurs on my work.

---

### Post by wildmanne39 on 2014-05-20
>  And it is not the channels of my router since the same problem occurs on my work. If you are not willing to do what is ask of you then I have no further suggestions.

---

### Post by gijs2 on 2014-05-20
> **Wild Man said:**
> If you are not willing to do what is ask of you then I have no further suggestions.

It's not that i'm not willing to do what you suggest but I use this laptop the most on my work and I can't go snooping around on the router at my work.

---

### Post by wildmanne39 on 2014-05-20
I am doing research to see what parameters might help, but we are limited not being able to change router settings.

Did this driver come with ubuntu 14.04 or did you manually install it?

---

### Post by gijs2 on 2014-05-20
> **Wild Man said:**
> I am doing research to see what parameters might help, but we are limited not being able to change router settings.

Did this driver come with ubuntu 14.04 or did you manually install it?

When I first bought this laptop it contained Windows 8, but last night I used Darik's Boot and Nuke to wipe my hard drive and then I manually put Ubuntu 14.04 LTS on a USB stick and booted my laptop from my usb and then I installed Ubuntu 14.04 LTS.

Hopefully this information may be of any service.

---

### Post by wildmanne39 on 2014-05-20
From what I read you can install kernel 3.14 and that fixes the issues you are having.

Do:
```
sudo apt-get install linux-headers-generic linux-headers-$(uname -r) build-essential
```
Then download the needed packages:
```
wget kernel.ubuntu.com/~kernel-ppa/mainline/v3.14.4-utopic/linux-headers-3.14.4-031404_3.14.4-031404.201405130853_all.deb
 
wget kernel.ubuntu.com/~kernel-ppa/mainline/v3.14.4-utopic/linux-headers-3.14.4-031404-generic_3.14.4-031404.201405130853_amd64.deb

wget kernel.ubuntu.com/~kernel-ppa/mainline/v3.14.4-utopic/linux-image-3.14.4-031404-generic_3.14.4-031404.201405130853_amd64.deb

```
Then install the kernel:
```
sudo dpkg -i linux-image-3.14.4*.deb linux-headers-3.14.4*.deb
```
Cross fingers and reboot.

---

### Post by gijs2 on 2014-05-20
> **Wild Man said:**
> From what I read you can install kernel 3.14 and that fixes the issues you are having.

Do:
```
sudo apt-get install linux-headers-generic linux-headers-$(uname -r) build-essential
```
Then download the needed packages:
```
wget kernel.ubuntu.com/~kernel-ppa/mainline/v3.14.4-utopic/linux-headers-3.14.4-031404_3.14.4-031404.201405130853_all.deb
 
wget kernel.ubuntu.com/~kernel-ppa/mainline/v3.14.4-utopic/linux-headers-3.14.4-031404-generic_3.14.4-031404.201405130853_amd64.deb

wget kernel.ubuntu.com/~kernel-ppa/mainline/v3.14.4-utopic/linux-image-3.14.4-031404-generic_3.14.4-031404.201405130853_amd64.deb

```
Then install the kernel:
```
sudo dpkg -i linux-image-3.14.4*.deb linux-headers-3.14.4*.deb
```
Cross fingers and reboot.


I think that did the trick!
Thank you so much for you time!

Have a good one :)

---

### Post by wildmanne39 on 2014-05-20
Your welcome! I am glad it worked.

---

