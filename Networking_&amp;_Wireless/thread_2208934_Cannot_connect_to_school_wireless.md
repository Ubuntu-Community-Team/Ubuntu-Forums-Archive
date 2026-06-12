---
title: "Cannot connect to school wireless"
date: 2014-03-03
forum: Networking &amp; Wireless
---

### Post by Inoki on 2014-03-03
Hey everyone,

this problem in general affects every ubuntu derivative,

thing is I cannot connect to our school's wireless, which uses the following method:

[http://www.nowiressecurity.com/articles/configure_8021x_authentication_in_linux.htm](http://www.nowiressecurity.com/articles/configure_8021x_authentication_in_linux.htm)

I've tried most of what is written there but to no avail, even installed a few certificates, although this connection is without a certificate.

The interface when I'm trying to connect is exactly the same as shown in the picture. I'm also attaching our configuration for Windows machines, MACs work also: [https://drive.google.com/file/d/0B02pgs8EZtbcaEFEVTlDWXlGLVk/edit?usp=sharing](https://drive.google.com/file/d/0B02pgs8EZtbcaEFEVTlDWXlGLVk/edit?usp=sharing)

---

### Post by varunendra on 2014-03-04
Terribly slow speed here (1 KB/s or less !!), so couldn't open your google drive link. But let's take an overall setup of your wireless settings and related stuff.

Please follow the "Wireless Script" link in my signature, download and run the script as per instructions in the linked post, and post back the report it generates.

---

### Post by Inoki on 2014-03-06
A temporary fix has been suggested here: [https://plus.google.com/+InokiSakaeru/posts/QB8M8gpzWju](https://plus.google.com/+InokiSakaeru/posts/QB8M8gpzWju)

---

### Post by Inoki on 2014-03-13
> **varunendra said:**
> Terribly slow speed here (1 KB/s or less !!), so couldn't open your google drive link. But let's take an overall setup of your wireless settings and related stuff.

Please follow the "Wireless Script" link in my signature, download and run the script as per instructions in the linked post, and post back the report it generates.
Hey,

had to re-open, as I experience a few disconnects, now on Xubuntu. Please see the attached.

Important to mention I had to use my phone (Galaxy S4 using CM 10 Android 4.3.1) to connect to the school's WiFi, plug and use it as a modem.

---

### Post by varunendra on 2014-03-13
Hi,

I may be a bit busy today, maybe even a couple of days, so posting my general recommendations pertaining to your card/driver all at once. Please check/try them one at a time, move on to next if the current one does not work.

Try them in the sequence given here, regardless of what you have tried before.

**First,** check if your connection file contains a line "system-ca-certs=.." -
```
sudo grep 'ca-cert' "/etc/NetworkManager/system-connections/UCN"
```
The above command assumes that the Access-point(s) you want to connect have SSID "UCN", and the connection "KeyFile" is saved with the same name. Change it if it's a different one. I have enclosed the file address within double-quotes, so that it doesn't return error if the name contains blank spaces.

Do you see a line "**system-ca-certs=[COLOR="#FF0000"]true[/COLOR]**" in the above output? If yes, try deleting the line, either by opening it with your GUI text editor (with root privileges), or with the following command -
```
sudo sed -i '/system-ca-certs/ d' "/etc/NetworkManager/system-connections/UCN"
```

Then try to connect. Can you? Sometimes, this line gets automatically re-generated, in that case, try changing its value to **[COLOR="#006400"]false[/COLOR]**, again either using your text editor, or the following command -
```
sudo sed -i '/system-ca-cert/ s/true/false/' "/etc/NetworkManager/system-connections/UCN"
```
Of course change the name of the KeyFile to whichever it is. Its name would be same by which it appears in Network Manager's menu.

**Second option -** If the line does not exist, or deleting/changing its value does not help, try a few driver parameters as suggested here (change "**rtl8192[COLOR="#FF0000"]ce[/COLOR]**" to "**rtl8192[COLOR="#006400"]se[/COLOR]**") : [http://ubuntuforums.org/showthread.php?t=2180314&p=12815912#post12815912](http://ubuntuforums.org/showthread.php?t=2180314&p=12815912#post12815912)

As mentioned in the linked post, the changes would be temporary, so test the connection without rebooting after applying them. If any of them seems to help, make them permanent as mentioned in the later posts of the same thread (or simply ask here).

**Third option -** If the above two don't help, try a newer driver as mentioned in this post (the commands and procedure will be exactly same, nothing to change here) : [http://ubuntuforums.org/showthread.php?t=2203443&p=12926946#post12926946](http://ubuntuforums.org/showthread.php?t=2203443&p=12926946#post12926946)

Please try these for now, and post back how it goes. I hope one of these should solve the problem, but if not, I'd be ready to dig deeper.

---

### Post by Inoki on 2014-03-14
The first two changes didn't help, connectivity was lost after a very short while, attaching logs.

It is important to mention, that when I connect my phone and distribute the connection through it it's perfectly stable and fast. When I connect with my Win7 x64 machine, the connection remains, but it's not so fast as via my Android device and it also sometimes drops, so it's quite vague where the issue lies, since it works sometimes and sometimes it doesn't, is it the network configuration (quite frankly our IT isn't very reliable), but I also know that for many Windows machines it works perfectly well, there are times when it also works on mine, our teachers mostly use MACs and for them it's stable, so it might be a driver issue in the end.

I've had this problem with every Ubuntu version, as well as its derivatives like Linux Mint going back to older releases, like Mint 9 I think it was, as there are many old, unaddressed bugs. My laptop overall always had connectivity issues, but as Ubuntu distros got upgraded with newer driver versions the overall connectivity improved, yet sometimes I still encounter connectivity issues with certain HW/network configurations.

Atm. every network with the exception of the one at school works (thankfully, as I'm struggling for years already and frankly am tired of it), hence my question: updating to those backports I have a few doubts. I just hope it won't do more harm than good and would like to hear your sincere opinion whether I should rather go with my phone, connect it as usual, have the connection working without any configuration alterations and hope that the next LTS to which I plan to stick will improve. Frankly, not having my phone with me I'm doomed, as even Windows 7 has connectivity issues from time to time, on the same laptop.

I've also seen a lot of people using their phones as routers because the connection doesn't work for them either regardless of the OS, thus I believe the root cause may be related to our IT and how they've set up the connection.

What do you suggest, should I try to build the new driver even so or rather stick to using my phone as a modem where everything works without tinkering with the installation.

**Are there any risks associated with building the new driver?**

---

### Post by Inoki on 2014-03-18
Bumping this topic, as assistance would be needed.

---

### Post by varunendra on 2014-03-18
Updates/new requirements should be posted in new posts, not by changing the contents of existing posts. It causes confusion or wrong impression later.

> **Anathaen said:**
> What do you suggest, should I try to build the new driver even so or rather stick to using my phone as a modem where everything works without tinkering with the installation.

**Are there any risks associated with building the new driver?**

I think you *should* try upgrading the driver to the one I proposed. It has been tested many times by now and so far it has *always* proved to be working better.

I don't think there is any risk in trying the backported drivers, or I'm not aware if there is any. Even if it didn't work, removing it is as easy as executing a single command from the same directory where you installed it from *(it may be worth noting that it would be a good idea to keep that directory safe after installing, in case you need to update or remove it later. Although even that is not necessary)*. The package seems to have scripts that do backup of existing driver and restoring them if you choose to remove it later, however, I haven't personally tested how good or reliable they are at doing that. Please see this post if you need a 'guaranty' ;) : [http://ubuntuforums.org/showthread.php?t=2210322&p=12955264#post12955264](http://ubuntuforums.org/showthread.php?t=2210322&p=12955264#post12955264)

---

### Post by Inoki on 2014-03-19
Hey **Varun**,

I think I made it to work with the driver you suggested adding the following parameter as permanent:

```
echo "options rtl8192se ips=0" | sudo tee /etc/modprobe.d/rtl8192se.conf
```
So far it seems to be working, I'll do some more testing and should everything run smooth I'll mark this one as solved.

Thanks a ton for your assistance, it's highly appreciated and would be great if in the future release this driver would be included by default, as you also claim it helped a lot of people.

---

### Post by varunendra on 2014-03-19
No problem! I'd be curious to see your update, hopefully a positive one but I'm not holding my breath to it.

The driver I proposed was from kernel 3.12, while the next LTS (14.04) will come with kernel 3.13 by default (or even newer, I'm not sure on that). Let's hope it lives up to our expectations.

And thanks for the feedback. It's great to have users who experiment themselves and let us know what works the best - that helps us greatly to offer better advice next time. :)

---

### Post by Inoki on 2014-03-20
Hey,

hate to bear bad news, but the connection is still weak. Disconnects occur regularly, although it improved a bit.

Any suggestions?

---

### Post by varunendra on 2014-03-21
Not suggestions yet, only a few more output requests - Please post these -

1) A fresh report of "wireless_script"
2) Output of -
```
grep [[:alnum:]] /sys/module/rtl*/parameters/*
```

---

### Post by Inoki on 2014-03-24
Hey Varun,

I'll mark this as solved since I came to the conclusion, that the internet issues at my campus aren't caused by neither Ubuntu or my hardware, but it's our ITs fault who, simply put, cannot establish a network properly.

I came to the conclusion based on the many complaints rising at our campus towards our IT guys recently, when we're about to petition them to do something about it.

Thank you very much for your assistance.

---

### Post by varunendra on 2014-03-24
Interesting. :)

Let's hope it gets fixed automatically when they upgrade hardware or reconfigure the network.

---

