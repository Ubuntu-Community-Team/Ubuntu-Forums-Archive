---
title: "Help, need to know if this will work"
date: 2008-05-22
forum: Networking &amp; Wireless
---

### Post by Enriquecaribe on 2008-05-22
Im pretty sure most of you are tired of hp and broadcom post but, I was wondering if was easier to simply replace the wireless card with an intel 3945ABG card, and would it work on 64bit ubuntu right away? I heard it works out the box, but im not sure if it works on replacement.

I have read through many broadcom post and nothing ever works, so I took out the wireless card and googled "mini pc wireless cards and ubuntu" and intel is known to work default. 

But Im a little hesitant on buying it because my laptop is AMD64 with a broadcom driver, stock. 

Will replacing it work or make it crash, while making me lose money?

BTW, if this works, I'd recommend it as a fix for others, the card only cost $20.


My laptop is a HPdv2000 btw...

---

### Post by Enriquecaribe on 2008-05-22
Bump! seriously need help.

---

### Post by jrusso2 on 2008-05-22
I have not heard of anyone using the Intel wireless on an AMD so I don't know if it would work.

---

### Post by Ayuthia on 2008-05-22
I am not sure if that will work or not.  I just quickly glanced at your threads and it looks like you have a 4310.  I am guessing that you are using NDISwrapper because the b43 drivers do not work for you.  Have you tried this link yet:

[http://ubuntuforums.org/showthread.php?t=786397](http://ubuntuforums.org/showthread.php?t=786397)

Step 2 is what was needed to get his and a few other 4310 owners to work.

---

### Post by Enriquecaribe on 2008-05-22
> **Ayuthia said:**
> I am not sure if that will work or not.  I just quickly glanced at your threads and it looks like you have a 4310.  I am guessing that you are using NDISwrapper because the b43 drivers do not work for you.  Have you tried this link yet:

[http://ubuntuforums.org/showthread.php?t=786397](http://ubuntuforums.org/showthread.php?t=786397)

Step 2 is what was needed to get his and a few other 4310 owners to work.

This almost worked, but it would not let me save the blacklist. Therefore I have the driver installed but no connection.

---

### Post by Enriquecaribe on 2008-05-22
> **jrusso2 said:**
> I have not heard of anyone using the Intel wireless on an AMD so I don't know if it would work.

Hmph, I would be the guinea pig, but I only have 1 laptop.

---

### Post by Ayuthia on 2008-05-22
> **Enriquecaribe said:**
> This almost worked, but it would not let me save the blacklist. Therefore I have the driver installed but no connection.

Let's not worry about the blacklisting just yet.  Can you post the results of:
```
lsmod|grep -i -e b43 -e ssb -e bcm43xx -e b44 -e ndiswrapper
```

---

### Post by Enriquecaribe on 2008-05-22
> **Ayuthia said:**
> Let's not worry about the blacklisting just yet.  Can you post the results of:
```
lsmod|grep -i -e b43 -e ssb -e bcm43xx -e b44 -e ndiswrapper
```

I got this:
```
rico@rico-laptop:~$ lsmod|grep -i -e b43 -e ssb -e bcm43xx -e b44 -e ndiswrapper
b44                    33552  0 
ssb                    37892  1 b44
ndiswrapper           253016  0 
mii                     7552  1 b44
usbcore               171952  6 ndiswrapper,uvcvideo,usbhid,ehci_hcd,ohci_hcd
rico@rico-laptop:~$ 

```

---

### Post by Ayuthia on 2008-05-22
Can you tell me what happens when you type:
```
sudo modprobe -r b43 b44 ssb ndiswrapper
sudo modprobe ndiswrapper
```
If nothing comes up, can you check the last part of dmesg?  Just type dmesg in the Terminal and look at what it says at the end for ndiswrapper.

I am taking it that you make it through step 2 and was able to add the link without any problem.  If you are not sure, can you post the results of:
[CODE]ls -l /etc/ndiswrapper/bcmwl5*]

---

### Post by Enriquecaribe on 2008-05-22
> **Ayuthia said:**
> Can you tell me what happens when you type:
```
sudo modprobe -r b43 b44 ssb ndiswrapper
sudo modprobe ndiswrapper
```
If nothing comes up, can you check the last part of dmesg?  Just type dmesg in the Terminal and look at what it says at the end for ndiswrapper.

I am taking it that you make it through step 2 and was able to add the link without any problem.  If you are not sure, can you post the results of:
```
ls -l /etc/ndiswrapper/bcmwl5*]

I typed in dmesg and got this for ndiswrapper:
[code][ 1766.674506] usbcore: deregistering interface driver ndiswrapper
[ 1774.545772] ndiswrapper version 1.52 loaded (smp=yes, preempt=rt)
[ 1774.520154] usbcore: registered new interface driver ndiswrapper
```

Then I typed in ```
ls -l /etc/ndiswrapper/bcmwl5*
``` and i got this:
```
rico@rico-laptop:~$ ls -l /etc/ndiswrapper/bcmwl5*
total 1488
-rw-r--r-- 1 root root    913 2008-05-18 16:43 14E4:4311:0007:1028.5.conf
-rw-r--r-- 1 root root    915 2008-05-18 16:43 14E4:4311:0008:1028.5.conf
-rw-r--r-- 1 root root    913 2008-05-18 16:43 14E4:4311.5.conf
-rw-r--r-- 1 root root    965 2008-05-18 16:43 14E4:4312:0007:1028.5.conf
-rw-r--r-- 1 root root    967 2008-05-18 16:43 14E4:4312:0008:1028.5.conf
-rw-r--r-- 1 root root    965 2008-05-18 16:43 14E4:4312.5.conf
lrwxrwxrwx 1 root root     26 2008-05-22 20:28 14E4:4315.5.conf -> 14E4:4311:1363:103C.5.conf
-rw-r--r-- 1 root root    917 2008-05-18 16:43 14E4:4318:0005:1028.5.conf
-rw-r--r-- 1 root root    911 2008-05-18 16:43 14E4:4318:0006:1028.5.conf
-rw-r--r-- 1 root root    919 2008-05-18 16:43 14E4:4318.5.conf
-rw-r--r-- 1 root root    969 2008-05-18 16:43 14E4:4319:0005:1028.5.conf
-rw-r--r-- 1 root root    963 2008-05-18 16:43 14E4:4319:0006:1028.5.conf
-rw-r--r-- 1 root root    971 2008-05-18 16:43 14E4:4319.5.conf
-rw-r--r-- 1 root root    919 2008-05-18 16:43 14E4:4320:0001:1028.5.conf
-rw-r--r-- 1 root root    901 2008-05-18 16:43 14E4:4320:0002:1028.5.conf
-rw-r--r-- 1 root root    917 2008-05-18 16:43 14E4:4320:0003:1028.5.conf
-rw-r--r-- 1 root root    899 2008-05-18 16:43 14E4:4320:0004:1028.5.conf
-rw-r--r-- 1 root root    919 2008-05-18 16:43 14E4:4320.5.conf
-rw-r--r-- 1 root root    971 2008-05-18 16:43 14E4:4324:0001:1028.5.conf
-rw-r--r-- 1 root root    953 2008-05-18 16:43 14E4:4324:0002:1028.5.conf
-rw-r--r-- 1 root root    969 2008-05-18 16:43 14E4:4324:0003:1028.5.conf
-rw-r--r-- 1 root root    951 2008-05-18 16:43 14E4:4324:0004:1028.5.conf
-rw-r--r-- 1 root root    971 2008-05-18 16:43 14E4:4324.5.conf
-rw-r--r-- 1 root root    984 2008-05-18 16:43 14E4:4328:0009:1028.5.conf
-rw-r--r-- 1 root root    984 2008-05-18 16:43 14E4:4328:000A:1028.5.conf
-rw-r--r-- 1 root root    984 2008-05-18 16:43 14E4:4328.5.conf
-rw-r--r-- 1 root root 754688 2008-05-18 16:43 bcmwl564.sys
-rw-r--r-- 1 root root 655034 2008-05-18 16:43 bcmwl5.inf

```

---

### Post by Ayuthia on 2008-05-22
> **Enriquecaribe said:**
> 
Then I typed in ```
ls -l /etc/ndiswrapper/bcmwl5*
``` and i got this:
```
rico@rico-laptop:~$ ls -l /etc/ndiswrapper/bcmwl5*
total 1488
-rw-r--r-- 1 root root    913 2008-05-18 16:43 14E4:4311:0007:1028.5.conf
-rw-r--r-- 1 root root    915 2008-05-18 16:43 14E4:4311:0008:1028.5.conf
-rw-r--r-- 1 root root    913 2008-05-18 16:43 14E4:4311.5.conf
-rw-r--r-- 1 root root    965 2008-05-18 16:43 14E4:4312:0007:1028.5.conf
-rw-r--r-- 1 root root    967 2008-05-18 16:43 14E4:4312:0008:1028.5.conf
-rw-r--r-- 1 root root    965 2008-05-18 16:43 14E4:4312.5.conf
lrwxrwxrwx 1 root root     26 2008-05-22 20:28 14E4:4315.5.conf -> 14E4:4311:1363:103C.5.conf
-rw-r--r-- 1 root root    917 2008-05-18 16:43 14E4:4318:0005:1028.5.conf
-rw-r--r-- 1 root root    911 2008-05-18 16:43 14E4:4318:0006:1028.5.conf
-rw-r--r-- 1 root root    919 2008-05-18 16:43 14E4:4318.5.conf
-rw-r--r-- 1 root root    969 2008-05-18 16:43 14E4:4319:0005:1028.5.conf
-rw-r--r-- 1 root root    963 2008-05-18 16:43 14E4:4319:0006:1028.5.conf
-rw-r--r-- 1 root root    971 2008-05-18 16:43 14E4:4319.5.conf
-rw-r--r-- 1 root root    919 2008-05-18 16:43 14E4:4320:0001:1028.5.conf
-rw-r--r-- 1 root root    901 2008-05-18 16:43 14E4:4320:0002:1028.5.conf
-rw-r--r-- 1 root root    917 2008-05-18 16:43 14E4:4320:0003:1028.5.conf
-rw-r--r-- 1 root root    899 2008-05-18 16:43 14E4:4320:0004:1028.5.conf
-rw-r--r-- 1 root root    919 2008-05-18 16:43 14E4:4320.5.conf
-rw-r--r-- 1 root root    971 2008-05-18 16:43 14E4:4324:0001:1028.5.conf
-rw-r--r-- 1 root root    953 2008-05-18 16:43 14E4:4324:0002:1028.5.conf
-rw-r--r-- 1 root root    969 2008-05-18 16:43 14E4:4324:0003:1028.5.conf
-rw-r--r-- 1 root root    951 2008-05-18 16:43 14E4:4324:0004:1028.5.conf
-rw-r--r-- 1 root root    971 2008-05-18 16:43 14E4:4324.5.conf
-rw-r--r-- 1 root root    984 2008-05-18 16:43 14E4:4328:0009:1028.5.conf
-rw-r--r-- 1 root root    984 2008-05-18 16:43 14E4:4328:000A:1028.5.conf
-rw-r--r-- 1 root root    984 2008-05-18 16:43 14E4:4328.5.conf
-rw-r--r-- 1 root root 754688 2008-05-18 16:43 bcmwl564.sys
-rw-r--r-- 1 root root 655034 2008-05-18 16:43 bcmwl5.inf

```

This portion does not look right.  It appears that the driver you downloaded is not updated here.  The dates in /etc/ndiswrapper/bcmwl5 should be today's date.  If you look at the link, it is not pointing to a file in the directory either.  I am not for sure about how you removed the old driver and installed the new driver.  Did you do these steps in the directory where the new driver is located?
```
sudo ndiswrapper -e bcmwl5
sudo ndiswrapper -i bcmwl5.inf
sudo ln -s 14E4:4311:1363:103C.5.conf 14E4:4315.5.conf
sudo modprobe -r b43 b44 ssb ndiswrapper
sudo modprobe ndiswrapper
```

---

### Post by Enriquecaribe on 2008-05-27
I finally got my wifi working!!!!!!!! YAY!!!!!!!!

I used the ubuntu help wifidocs btw. They should include these docs on the cd... heres the link, if anyone stumbles upon this thread looking for help. BUT BE SURE TO READ CAREFULLY! I made the mistake of not reading, and just posting codes... idiot me...

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

