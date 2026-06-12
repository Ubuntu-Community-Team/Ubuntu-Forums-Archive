---
title: "wifi problem with SiS chipset"
date: 2006-09-13
forum: Networking &amp; Wireless
---

### Post by vargadanis on 2006-09-13
Hi all,

I know that there are plenty of threads like this but I need some help to get my wlan card working.
I have just now bought my computer (Acer notebook) and it has SiS chipset. The system can see the wifi card, there is an eth1 enty for iwconfig. But when trying to bring it up nothing happens. Do I have to install... what is its name? ndiswrapper to get everything work? If I have to do so do I have to recompile the whole kernel? How can I install the source package of this program that I found on the packages.ubuntu.org? 

I am sorry but I could not find the answer for these questions. It took me 3 days to change the resolution to 1280x800 so U can imagine how much time it is gonna take the learn everything in connection with linuxes. ^_^

Dani

---

### Post by vargadanis on 2006-09-13
Ok...

I had some progress. I installed ndiswrapper. Not the ndiswrapper-utils deb package, but I relcompiled the kernel source, I have make essetials installed so lots of thing that are needed to get my card working. Ndiswrapper seems to be working properly but there is something strange. When I load the module there should be a wlan0 in iwconfig, am I right? 

So whats next after loading the .inf driver? It sais that everything is ok, but I do not know the next step. Pls help...

---

### Post by vargadanis on 2006-09-13
Bahh...

I am loosing my patence. I have been trying to bring wlan up without any success.
In the install howto of the ndiswrapper it was written that I should see a wlan0 something. I cannot see it. Why is that? 
Under windows I have to turn on the wlan to get it working but I cannot do this under linux. I push the button but nothing happens. 
Any ideia? I have got an acer 5003WLMi

Edit:
I get an error when trying to give this command: ifup wlan0
The error message is there is no such device

---

