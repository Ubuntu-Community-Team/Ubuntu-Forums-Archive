---
title: "Mobile web browsing blocked"
date: 2010-05-25
forum: New to Ubuntu
---

### Post by bluebelly30 on 2010-05-25
Hello, 

I am new to the Ubuntu and Linux world and have overcome most of my issues (apart from this one) using this and other forums (thanks everybody). The problem I have now is that I can not browse the internet using a mobile broadband connection.

I am using Ubuntu 10.4, have Firestarter installed and use the chromium browser. 

From what I can tell the dongle is connected to the internet. The dongle is a 'ZTE Incorporated ZTE WCDMA Technologies MSM' USB device.  The network connections manager seems to connect to it with out issue. 

When the wireless connection is used at home everything works fine, its just the mobile broadband that is a issue.

My questions are:

1.How can I test that the dongle really is connected to the web and working fine?

2.If the dongle is working do I need to add a policy in to firestarter to let chromium browse the web? It is set to permissive by default, blacklist traffic.

3.What else needs to be looked at/ configured to fix this?

Thanks in advance

---

### Post by 3rdalbum on 2010-05-25
> **bluebelly30 said:**
> 

1.How can I test that the dongle really is connected to the web and working fine?

Try pinging an IP address that you know is available, such as:

```
ping 208.67.222.222
```

If pinging works, and web browsing doesn't work, then you have a DNS problem that you can solve by my instructions here: [www.chrislees.info/ubuntu/opendns.shtml](www.chrislees.info/ubuntu/opendns.shtml)

> 2.If the dongle is working do I need to add a policy in to firestarter to let chromium browse the web? It is set to permissive by default, blacklist traffic.

I'd advise turning Firestarter off, and removing it. Ubuntu doesn't listen to any incoming ports by default, so you don't need a firewall for an individual computer.

If you do really want a personal firewall and you know why you want it (there are a couple of rare use cases), then make sure it's not blocking any outgoing connections, only incoming connections.

---

### Post by bluebelly30 on 2010-05-25
Thanks for the very fast response, I did the following:

Disconnected wireless network, connected to the mobile connection, and then in terminal:

david@david-laptop:~$ ping 208.67.222.222 
PING 208.67.222.222 (208.67.222.222) 56(84) bytes of data. 

[then nothing, so reconnected the connection to the wireless router and:]

ping: sendmsg: Operation not permitted 
64 bytes from 208.67.222.222: icmp_seq=109 ttl=48 time=17.7 ms 
64 bytes from 208.67.222.222: icmp_seq=110 ttl=48 time=16.0 ms 
64 bytes from 208.67.222.222: icmp_seq=111 ttl=48 time=16.5 ms 
etc...
etc...

I think that means the dongle isn't working as it should, is that right?

Firestarter is now gone, following the instruction given by  jerome1232  in post 2 here:
[http://ubuntuforums.org/showthread.php?t=890858](http://ubuntuforums.org/showthread.php?t=890858)

---

### Post by philinux on 2010-05-25
> **bluebelly30 said:**
> Hello, 

I am new to the Ubuntu and Linux world and have overcome most of my issues (apart from this one) using this and other forums (thanks everybody). The problem I have now is that I can not browse the internet using a mobile broadband connection.

I am using Ubuntu 10.4, have Firestarter installed and use the chromium browser. 

From what I can tell the dongle is connected to the internet. The dongle is a 'ZTE Incorporated ZTE WCDMA Technologies MSM' USB device.  The network connections manager seems to connect to it with out issue. 

When the wireless connection is used at home everything works fine, its just the mobile broadband that is a issue.

My questions are:

1.How can I test that the dongle really is connected to the web and working fine?

2.If the dongle is working do I need to add a policy in to firestarter to let chromium browse the web? It is set to permissive by default, blacklist traffic.

3.What else needs to be looked at/ configured to fix this?

Thanks in advance

Try this, open a terminal Apps>access>

```
sudo apt-get install usb-modeswitch 
```

Not certain if a reboot is necessary.

See the General Help forum stick re usb dongles.

---

### Post by bluebelly30 on 2010-05-25
Thanks philinux, 

I have already installed the usb-modeswitch. I tried again just to double check and it was ok.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
usb-modeswitch is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

Do I need to do anything with it once it has installed?

---

### Post by bluebelly30 on 2010-05-25
> If pinging works, and web browsing doesn't work, then you have a DNS problem that you can solve by my instructions here: [www.chrislees.info/ubuntu/opendns.shtml](www.chrislees.info/ubuntu/opendns.shtml)

I have changed the setting open DNS ip addresses as per the instruction in the link, still nothing.

Nice looking site by the way.

---

### Post by gandaran on 2010-05-25
hi, I use mobile internet and I can say I spent a full day trying to make it work with Ubuntu!, I couldn't find any information on how to set up my ISP mobile internet! I had to figure it all out by comparing the same set-up in a windows computer!
can you describe what you have done so far, is the dongle recognised? do you know the APN and authentication details? if your dongle is recognised then all you need is the APN and authentication method which you can easily obtain by checking the properties on the same windows mobile install if you have one.
also you you need to reboot after the set-up for it to start working.

---

### Post by 3rdalbum on 2010-05-25
If you didn't get pings coming back, then your dongle isn't working on Linux (or you haven't paid your Internet bill!). Unfortunately I don't know how to get it working. You may be able to use this command:

```
lsusb
```

(that's a lowercase L, not a One)

to find out the exact chipset of your USB device, and then search on Google for "<chipset name> ubuntu 10.04". If anyone has reported the same problem and a solution, you should be able to find what to do.

BTW thanks for the compliment about my site. I appropriated the design from a freely-available template, and the orange background came from a copyleft wallpaper. :-)  The only thing that's mine is the content!

---

### Post by bluebelly30 on 2010-05-25
Thank you everyone for you help, my questions have been answered so its marked solved.

> 1.How can I test that the dongle really is connected to the web and working fine? = > ping 208.67.222.222 

In this case it isn't.

> 2.If the dongle is working do I need to add a policy in to firestarter to let chromium browse the web? It is set to permissive by default, blacklist traffic. = > I'd advise turning Firestarter off, and removing it. Ubuntu doesn't listen to any incoming ports by default, so you don't need a firewall for an individual computer.

If you do really want a personal firewall and you know why you want it (there are a couple of rare use cases), then make sure it's not blocking any outgoing connections, only incoming connections.

> 3.What else needs to be looked at/ configured to fix this? = > is the dongle recognised? do you know the APN and authentication details? if your dongle is recognised then all you need is the APN and authentication method which you can easily obtain by checking the properties on the same windows mobile install if you have one.
also you you need to reboot after the set-up for it to start working.

When/ if I get this working I will do a quick write up and post it here.

Thanks again everyone

---

### Post by gandaran on 2010-05-25
bluebelly30
you said you believed the dongle was connected to the internet, does network manager display a message that internet is connected or disconnected after you try to manually connect?

---

### Post by bluebelly30 on 2010-05-26
Hi gandaran,

sorry for the sluggish response I had to log off yesterday.

 > does network manager display a message that internet is connected or disconnected after you try to manually connect?

The network manager pop up tells me it has connected. But the ping command tells a different story.

---

