---
title: "How to install Ralink rt3090 drivers"
date: 2011-01-17
forum: New to Ubuntu
---

### Post by carlosmavros on 2011-01-17
Hello there, I've found the drives for my Ralink rt3090 wireless card but I don't know how to install them. Completely n00b to things like this. 
[Here]("http://www.ralinktech.com/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1ERXdMekV5THpFM0wyUnZkMjVzYjJGa09URTJORFF5TWpreU9TNTZhWEE5UFQweU1ERXdYekV5TVRkZlVsUXpNRGt3WDB4cGJuVjRVMVJCWDFZeUxqUXVNQzQwWDFkcFJtbENWRU52YldKdlgwUlFUdz09Qw%3D%3D") is the link to download the .zip , it asks name and e-mail and accepting to download :)
Thanks in advance,
CARLOS

---

### Post by davidmohammed on 2011-01-17
have a read of this [thread]("http://ubuntuforums.org/showthread.php?t=1314747") to see if it helps you.

---

### Post by waqas ajaz on 2011-04-21
You can download this pre-built rt3090-dkms package here:
[http://stat.case.edu/~jrt32/how_to_build_rt3090_for_ubuntu_lucid/rt3090-dkms_2.3.1.4-0ubuntu0~ppa1_all.deb]("http://stat.case.edu/%7Ejrt32/how_to_build_rt3090_for_ubuntu_lucid/rt3090-dkms_2.3.1.4-0ubuntu0%7Eppa1_all.deb")

after downloading :
sudo dpkg -i rt3090-dkms_2.3.1.4-0ubuntu0~ppa1_all.deb
sudo reboot

---

### Post by Sven6210 on 2011-05-09
You can have a look on my how-to at [http://ubuntuforums.org/showthread.p...ghlight=RT3090]("http://ubuntuforums.org/showthread.php?t=1476007&highlight=RT3090")

It also works for the RaLink RT3090, you just need to replace the "[FONT=Verdana, sans-serif]RT2860" with "RT3090".

Disadvantage of this procedure:
[/FONT]
[LIST]
[*]You need to recompile the driver each time you make a  major kernel-update. The backports I have tried so far did not work very  well
[/LIST]
Advantage of this procedure:

[LIST]
[*]On my EeeBox B202 and my friends EeePC 1015 P it works very well and reliable
[/LIST]

The manual should also work for newer releases of Ubuntu, I am still running Ubuntu 10.04 LTS on my systems.

Good luck

Sven

---

### Post by geidorei on 2011-05-12
Hi - been there done that - compiled, installed deb, tried 'Windows Wireless Drivers' - any suggestions?

New laptop - MSI CR620, just purchased from Novatech. Netgear dongle works aok.

Any suggestions greatly appreciated, thanks.

---

### Post by 3rdalbum on 2011-05-12
IIRC, there's been a driver built in for that card for over a year, but it's only worked out of the box since 11.04. In 10.10 and below, you have to blacklist the rt2800usb driver (I believe) in the /etc/modprobe.d/blacklist.conf file and reboot.

Installing ndiswrapper might stop the native driver from working, which is a shame because people seem eager to recommend ndiswrapper at the drop of a hat, when it often doesn't work.

---

### Post by geidorei on 2011-05-12
Hi - thanks for info - still doesnt work and have just upgraded to 11.04.

Did as you have stated in 10.10 but to no affect. Is there any way I can check somehow to see if the hardware is ok, or do I need to install windows to do a check. hope not...

---

### Post by geidorei on 2011-05-18
Update : installed windows XP and all was well, reinstall Ubuntu and then the .deb via synaptic and it now works without any issues. No idea what happened.

---

### Post by carlosmavros on 2011-06-15
Thanks for all the help guys, I had been offline a while , but I really appreciate the help, SOLVED :D

---

### Post by jpsr on 2012-03-15
I downloaded the zip and followed the instructions.
but the make failed the file sta_ioctl_patch.c is not in directory os/linux
Where can i find it

jpsr

---

### Post by gdea73 on 2012-03-15
jpsr: I recommend you follow [url=http://ubuntuforums.org/showthread.php?t=1476007this thread[/url] to figure out how to compile Ralink drivers. If you're not using the RT2860 as in that thread, replace all mentions of it with RT3090.

In case it wasn't mentioned in the tutorial, before you can compile the package with make and make install, you  must run the following command.

```
sudo apt-get install build-essential linux-headers-generic
```

If you get a "Code 2" error, complaining about the lack of a "build" directory inside your latest kernel folder, then install the linux-headers appropriate for your kernel revision. For example, I was running 2.6.35-22, so I installed the package linux-headers-2.6.35-22-generic as well, to get compilation to work.

---

