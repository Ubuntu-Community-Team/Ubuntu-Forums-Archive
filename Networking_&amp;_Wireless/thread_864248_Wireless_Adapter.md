---
title: "Wireless Adapter"
date: 2008-07-19
forum: Networking &amp; Wireless
---

### Post by Sepher on 2008-07-19
Hi all,

I've just installed Ubuntu and cant get my wireless adapter to work. I've googled it, and have tried various things. But with all this being new to me I'm really struggling to understand it.

My wireless adapter is a WG111v2. 

Could anyone explain in the most simplist terms on how to get this wireless adapter running? I have never used Linux before, and its a completely new experience lol.

I have typed lsusb into the terminal which has produced 0846:6a00 for my wireless adapter. So its def v2 right? I know I have to install ndiswrapper or something, but I don't no how to? I had located eventually in the terminal and did make install but it failed creating directorys or something. It's all too confusing for me!

Thanks

---

### Post by HokeyFry on 2008-07-19
If you haven't successfully installed Ndiswrapper, try the Wireless howto in my sig. It outlines how to install it both from Synaptic and from source, as well as how to set up your driver. Also, are you using 32 or 64 bit linux? Also keep in mind that Vista drivers do not yet work with Ndiswrapper.

---

### Post by Sepher on 2008-07-19
Thanks for the fast reply I'll check that out.

I am using 32 bit linux.

---

### Post by Sepher on 2008-07-19
Hi,

I've spent hours on it lol. I've got the driver installed, which is the XP version. Could anyone confirm the name of the INF file to check I'm using the right driver?

The dongle still doesnt connect to my router. I can now get internet access via ethernet. Static IP doesnt work on ethernet but I wasn't bothered by that at the moment.

I dont want to take any security off of my router although I do admit I'm using a heavy encryption which is WPA-PSK [TKIP] + WPA2-PSK [AES]. Would this encryption work with Linux?

Thanks

---

### Post by Sepher on 2008-07-20
I have now tried WG111v2 driver 1.3 for XP and Windows 98 and still no joy =(

I don't get response from "sudo modprobe ndiswrapper" am I suppose to?

Thanks

---

### Post by JagDragon on 2008-07-20
If my memory serves me correctly, to install a driver using ndiswrapper, one has to go
```

sudo -s
modprobe -r ndiswrapper
ndiswrapper -i [driver inf file here].inf
ndiswrapper -ma
ndiswrapper -mi
ndiswrapper -m
modprobe ndiswrapper
exit
```

---

### Post by aimwin on 2008-07-25
hi

Have you read this 
[http://ubuntuforums.org/showthread.php?t=850120&highlight=wg111v2](http://ubuntuforums.org/showthread.php?t=850120&highlight=wg111v2)

In my opinion.

Try clean install of Ubantu 8.04 and install wg111v2, 
Don't update anything.

It should work.
If it did not work, read further on that thread.
If my experience did not help then

try to PM phytheas22

Good Luck

good luck

---

