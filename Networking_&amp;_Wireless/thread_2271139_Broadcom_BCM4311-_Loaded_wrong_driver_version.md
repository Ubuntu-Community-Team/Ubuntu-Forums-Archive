---
title: "Broadcom BCM4311- Loaded wrong driver version"
date: 2015-03-27
forum: Networking &amp; Wireless
---

### Post by rustybottoms88 on 2015-03-27
I went to [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing_b43.2Fb43legacy_firmware](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing_b43.2Fb43legacy_firmware)
to DL the drivers for my Broadcom BCM4311. I made the mistake of DL the version for Ubuntu 10.04 when I actually have Ubuntu 14.04 now it will not let me uninstal. 
Here is what I get in the terminal: 

rustybottoms88@rustybottoms88-Presario-C500-RQ338UA-ABA:~$ sudo apt-get remove --purge bcmwl-kernel-source
[sudo] password for rustybottoms88: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
rustybottoms88@rustybottoms88-Presario-C500-RQ338UA-ABA:~$ 


it appears to be still trying to install but is unable to. If I run 'sudo apt-get update' it trys to update and tells me the same thing. I am pretty new to Ubuntu so if you need more information let me know and any help with this would be appreciated. Thanks

---

### Post by jeremy31 on 2015-03-27
Do you have Software & Updates open?

---

### Post by chili555 on 2015-03-27
> E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?This generally means that another process, Update Manager, Software Center, apt-get update, et al, is also running. Please close them all and then try again.

By the way, I think bcmwl-kernel-source is wrong altogether. I think you need firmware-b43-installer.

---

### Post by Hadaka on 2015-03-27
hi, please do..
```
sudo rm -rf /var/lib/apt/lists/lock
sudo dpkg -r bcmwl-kernel-source
```
then..
```
sudo apt-get update
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install firmware-b43-installer
sudo modprobe b43
```
thanks.

---

### Post by rustybottoms88 on 2015-03-28
Thank you all very much for your help. 
Hadaka I ran the commands you posted and everything seem to work except until i ran the last command 'sudo modprobe b43' 
After i entered the command it didn't really do anything besides show a blinking curser. I am not near a wireless network at this time to try and see if the wirelss is working but when i push the wifi button on my cmputer it doesn not light up like it should so I am guessing its not working? 
Here is a screen shot ofthe terminal. 
[http://i771.photobucket.com/albums/xx359/rustybottoms88/Screenshot%20from%202015-03-28%20084617_zpsxbjmyfgp.png](http://i771.photobucket.com/albums/xx359/rustybottoms88/Screenshot%20from%202015-03-28%20084617_zpsxbjmyfgp.png)
The last little line there with the ^[[2;3~ is where i tried to take a screen show and hit the wrong buttons.

---

### Post by chili555 on 2015-03-28
Will you please try a reboot?

---

### Post by wildmanne39 on 2015-03-28
Please use thumbnails or url's because a lot of people have slow connections and have trouble loading large images.
Thanks

---

### Post by rustybottoms88 on 2015-03-28
> **Wild Man said:**
> Please use thumbnails or url's because a lot of people have slow connections and have trouble loading large images.
Thanks

Sorry about that. 

 In reply to chili555:
 I went to close the terminal and it told me that closing the terminal will terminate a process. I closed it anyway and rebooted. Upon reboot when the black screen with the word Ubuntu in the middle and the 5 dots that alternate from gray to red came on it remained stuck on that screen. I did not know how to get it from that screen so I unplugged from power source and removed battery and then restarted the computer. Ubunutu loaded this time and now the wireless light will light up when i push it on so it appears to be working. Thank you for your help! I will try it out Monday at work when I will have access to a WIFI network connection. You all have been very helpful and I am very thankful.

---

### Post by chili555 on 2015-03-28
Glad it's apparently working! Post back if you have any trouble.

---

### Post by rustybottoms88 on 2015-04-08
I am posting back but i didn't have any trouble just wanted to let you know it worked great. Thank you.

---

### Post by Vladlenin5000 on 2015-04-08
Nice :p

Now you can use the thread tools to mark this one as Solved, so other can benefit as well.

---

