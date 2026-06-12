---
title: "VMware Server: causes IP/net problem on host"
date: 2008-08-17
forum: Networking &amp; Wireless
---

### Post by xSauronx on 2008-08-17
I searched around a bit but im not exactly sure what I need to do to change something. 

This is a new problem to me, Ive installed/run vmware server a few times and havent run into this, so I dont know if its something funky I did or not during setup. 

Problem: when vmware services are running, vmnet8 has an address of 192.168.1.1

That IP shouldnt be used, as its the IP of my cable modem. That means the guest in vmware can get on the net fine, but the host cant. 

I tried changing it manually with ifconfig but it was a nogo, so what do i do to change this? 

Thanks :)

---

### Post by darco on 2008-08-17
Which ver of vmware do you have? I have build 1.06-91891...Is Ubuntu the Host?
Also under your Guest setting what do you have for Network Settings, Bridged  or NAT? Bridged  allows the  guest to have its own IP rather than piggy backingin on the Host IP...
You can try the Virtualization forum here...
Try this thread
[http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934)

good luck
darco

---

