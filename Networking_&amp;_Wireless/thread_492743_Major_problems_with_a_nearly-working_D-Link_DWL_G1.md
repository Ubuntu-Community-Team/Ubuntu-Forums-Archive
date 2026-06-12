---
title: "Major problems with a nearly-working D-Link DWL G120 USB card"
date: 2007-07-05
forum: Networking &amp; Wireless
---

### Post by Momotombo on 2007-07-05
I tried asking for help before, but I guess I did something wrong, as nobody replied to my topic. Here it is again, with a better topic title.

I've been looking through tutorials and following directions for a couple of weeks in order to get my G120 working. The most I've gotten it to do is scan for wireless APs. I know it's still scanning because I can watch the signal strength for the APs go up and down, but when I try to connect to one, it doesn't work. I can never get online.

When I look in ndisgtk, it says there's no hardware present, but the driver is installed. When I look using ndiswrapper -l, it says it's installed and that it's using the driver. I've used the blacklist so that it won't look for other drivers. I finally found out that I have to activate the ndiswrapper module, and I did, and that led me to where I am now.

The power light on the device blinks on and off, and the internet activity light doesn't blink at all. Usually the power light is always on, but the internet light blinks.

Can anyone help me get the internet actually working in Ubuntu? It's frustrating because I have to keep rebooting into two different OSes to look up new information. I don't have any other wireless cards. Obviously my card works right, because I'm using it right now.

Thanks in advance.

---

### Post by sj3fk3 on 2007-07-05
> **Momotombo said:**
> I tried asking for help before, but I guess I did something wrong, as nobody replied to my topic. Here it is again, with a better topic title.

I've been looking through tutorials and following directions for a couple of weeks in order to get my G120 working. The most I've gotten it to do is scan for wireless APs. I know it's still scanning because I can watch the signal strength for the APs go up and down, but when I try to connect to one, it doesn't work. I can never get online.

When I look in ndisgtk, it says there's no hardware present, but the driver is installed. When I look using ndiswrapper -l, it says it's installed and that it's using the driver. I've used the blacklist so that it won't look for other drivers. I finally found out that I have to activate the ndiswrapper module, and I did, and that led me to where I am now.

The power light on the device blinks on and off, and the internet activity light doesn't blink at all. Usually the power light is always on, but the internet light blinks.

Can anyone help me get the internet actually working in Ubuntu? It's frustrating because I have to keep rebooting into two different OSes to look up new information. I don't have any other wireless cards. Obviously my card works right, because I'm using it right now.

Thanks in advance.
paste some more info, start with dmesg, iwconfig ifconfig etc

---

