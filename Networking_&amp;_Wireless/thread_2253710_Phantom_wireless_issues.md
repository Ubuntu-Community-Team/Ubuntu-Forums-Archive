---
title: "Phantom wireless issues"
date: 2014-11-21
forum: Networking &amp; Wireless
---

### Post by emanmcdow on 2014-11-21
I'm running Ubuntu 14.10 and I have had this issue since 13.04. I can connect to the internet easily, but after 5 minutes it stops working. Notice I said stops working, not disconnected. It says that it is still connected, it's just that websites will load indefinitely, and steam will disconnect. None of my other Ubuntu machines in the house have this problem It "fixes" itself if I disconnect and reconnect. I tried switching to WICD, but it made no difference.

This: [http://pastebin.ubuntu.com/9160549/](http://pastebin.ubuntu.com/9160549/) is the result of:
[COLOR=#000000]> 
 wget -N -t 5 -T 10 [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script) && chmod +x wireless_script && ./wireless_script
[/COLOR][COLOR=#000000][/COLOR]

---

### Post by emanmcdow on 2014-11-23
bump

---

### Post by wildmanne39 on 2014-11-23
Hi, first you have this ```
options rtl8192cu nohwcrypt=1
```parameter set in /etc/modprobe.d/rtl8192cu.conf and in rc.local but according to modinfo that parameter is not an option for your driver so you should remove it from both places, and there is a newer driver we can try that will probably fix your issues.

With an ethernet connection do:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential git dkms
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.9
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot

---

### Post by emanmcdow on 2014-11-23
That first command returned:
> 
emmett@jarvis:~$ sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential git dkms
[sudo] password for emmett: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers-3.13.0-37-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'linux-headers-3.13.0-37-generic' has no installation candidate




---

### Post by wildmanne39 on 2014-11-23
You are using a kernel from 14.04 which had a bug that prevented new drivers from being compiled. You have 14.10 installed so did you choose to keep the old kernel from 14.04? I suspect that is why the kernel headers can not be found but I am not sure.

---

### Post by wildmanne39 on 2014-11-23
Please post the output of:
```
sudo dpkg -s linux-headers-`uname -r`
```
Thanks

---

### Post by emanmcdow on 2014-11-23
Here ya go
> emmett@jarvis:~$ sudo dpkg -s linux-headers-`uname -r`[sudo] password for emmett: 
dpkg-query: package 'linux-headers-3.13.0-37-generic' is not installed and no information is available
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.

---

### Post by wildmanne39 on 2014-11-23
Please answer my questions in post 5.
Thanks

---

### Post by emanmcdow on 2014-11-23
I did not choose to do that, and I just never checked that my kernel was out of date.

---

### Post by wildmanne39 on 2014-11-23
It is strange, it should have upgraded the kernel unless the kernel update was locked to prevent it from upgrading. I am researching to see if we should upgrade the kernel. Did you remove the driver parameters in both the files I listed in my previous post? it is possible to try another parameter but I do not think it will help.

---

### Post by emanmcdow on 2014-11-23
Yeah, went in and deleted those lines.

---

### Post by wildmanne39 on 2014-11-23
Do you know if you have any older hardware that might stop working with the newer kernel? For example my video card is not supported past 12.04.

---

### Post by emanmcdow on 2014-11-23
Eh I don't think so. Everything I have, excluding my hard drive, is only a year or two old.

---

### Post by wildmanne39 on 2014-11-23
I asked my good friend the wireless expert's advice and he suggests a couple of things before upgrading the kernel.

Do:
```
sudo apt-get update
sudo apt-get install linux-headers-`uname -r` 
```
Does it install now?
Let's double check your kernel version:
```

lsb_release -d

```
post results of the last command here.

---

### Post by emanmcdow on 2014-11-23
Installing the headers failed, but here is the result of the last command.

> 
emmett@jarvis:~$ lsb_release -d
Description:	Ubuntu 14.10


---

### Post by wildmanne39 on 2014-11-23
One last check:
```
uname -a
```
post results.
Thanks

---

### Post by emanmcdow on 2014-11-23
Here you go
> 
Linux jarvis 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:28:38 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


---

### Post by wildmanne39 on 2014-11-23
Here are the directions for installing the new kernel, run one command at a time and watch for errors, after each command is done run the next one and they must be ran in order.
```
cd /tmp/

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.16-utopic/linux-headers-3.16.0-031600-generic_3.16.0-031600.201408031935_amd64.deb

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.16-utopic/linux-headers-3.16.0-031600_3.16.0-031600.201408031935_all.deb

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.16-utopic/linux-image-3.16.0-031600-generic_3.16.0-031600.201408031935_amd64.deb

sudo dpkg -i linux-headers-3.16.0-*.deb linux-image-3.16.0-*.deb
```
Before running the last command make sure there are no other .deb files in your tmp folder.
Then reboot and run the commands in my previous post to install the new driver.

---

### Post by emanmcdow on 2014-11-23
To clarify, do you mean these commands?
> 
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get update
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install linux-headers-`uname -r`[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]

---

### Post by wildmanne39 on 2014-11-23
No, I meant these commands:
```
cd /tmp/

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.16-utopic/linux-headers-3.16.0-031600-generic_3.16.0-031600.201408031935_amd64.deb

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.16-utopic/linux-headers-3.16.0-031600_3.16.0-031600.201408031935_all.deb

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.16-utopic/linux-image-3.16.0-031600-generic_3.16.0-031600.201408031935_amd64.deb

sudo dpkg -i linux-headers-3.16.0-*.deb linux-image-3.16.0-*.deb
```
Then reboot and do:
```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential git dkms
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.9
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

---

### Post by emanmcdow on 2014-11-23
> **Wild Man said:**
> 
Then reboot and run the commands in my previous post to install the new driver.
I was talking about this particular statement

---

### Post by wildmanne39 on 2014-11-23
I realized that and I edited my last post to include that answer as well.

---

### Post by emanmcdow on 2014-11-23
I'm pretty sure that fixed it. Thanks a lot dude.

---

### Post by wildmanne39 on 2014-11-23
Your welcome! give it a little while then if it is still working use thread tools at the top of the page to mark the thread solved.
Thanks

---

