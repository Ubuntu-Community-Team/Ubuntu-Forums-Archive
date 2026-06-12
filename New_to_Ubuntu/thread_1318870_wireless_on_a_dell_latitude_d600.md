---
title: "wireless on a dell latitude d600"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by dlewis187 on 2009-11-07
windows IT pro giving ubuntu a try and I ran across my first problem, well actually I have not done a single thing yet.
Under system > preferences > network connections > wireless I added my home wireless with ssid & wpa password
How do I tell what my ip address is?
ifconfig does not give me an ip
How do I tell if my wireless is connected or if ubuntu even reconizes my wireless card?
I have an identical d600 running XP and wireless is working properly.

First issue and ubuntu is not as simple as I hoped?

---

### Post by PRC09 on 2009-11-08
I think you just need to connect your cable and do the updates first and then just activate the drivers..

[http://ubuntuforums.org/showthread.php?t=931178&highlight=dell+d600](http://ubuntuforums.org/showthread.php?t=931178&highlight=dell+d600)

---

### Post by dlewis187 on 2009-11-08
ok plugged in, ran system > update manager
installed a bunch of updates
In system > network connections my wireless is configured and its set to connect automatically
but in system > administration > network tools the network device wireless interface has a state of Inactive

a lspci -v shows a network controller
Broadcom 802.11b/g wireless lan controller

So it seems that ubuntu can see the wireless nic but I have no idea how to enable it?

---

### Post by PRC09 on 2009-11-08
You can check in System--Admin---Hardware drivers and see if the drivers are in use or available, if not enable them and try again.You can right click on your connection icon in the task bar and edit your connections from there.Hope this helps,I have a couple of those dells and dont remember anything strange during the set-up other than installing the driver....Post back and let us know.....

---

### Post by anewguy on 2009-11-08
With the lspci -v, what is listed after "module" on the lines for your wireless adapter?

Dave :)

---

### Post by dlewis187 on 2009-11-09
[PRC09]("http://ubuntuforums.org/member.php?u=774899")
very nice, I had no idea installing drivers was so easy
Ok I got the driver installed from the hard wire
If I right click on the system tray it has checked
Enable Networking and Enable Wireless
If I left click on the connections tray it says Wireless Networks > device not ready

lspci -v
Kernel modules: ssb

Not sure what else to do here?

---

### Post by PRC09 on 2009-11-09
I think you will also have to add a file from System -Admin- Synaptic Package Manager..Search for b43-fwcutter,mark for install and apply,when thats done I cant remember if I did a reboot or not but it wouldnt hurt anyway...Post back...

---

### Post by dlewis187 on 2009-11-09
wohoo!   Sucess!
b43-fwcutter was already installed but I marked it for reinstallation, hit some button about download firmware or something, rebooted and its working

Stupid question:   With windows I just install XP, go to dell's web site and download and install the hardware drivers.   How is the typical users supposed to know to do the above tasks to get a wireless device to work?

I'm not trying to pick on ubuntu, just trying to understand.

---

### Post by PRC09 on 2009-11-09
I just started with Ubuntu myself and found the learning curve a little different than windows.These forums and Google do get used alot for me.If you really want to learn the system and the basics(I am just winging it) there is a Pocket Guide that is free (see link).I am sure there are some formal training and certification sites as well... I am no expert at this but just happen to have the same machine..and someone helped me sort it out so I am just doing the same...Welcome to the forums by the way.......

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

---

### Post by bowtie350_428 on 2010-04-06
I had been trying for a while, then I found this post...  I tried it and YES!  It worked.  
 
I marked b43-fwcutter for reinstallation then rebooted and it work. 
 
I think Im gonna like this forum.

---

### Post by sseelbinder on 2010-06-06
Where is the "easy" button?!  I too had issues with the internal wireless network card with the Dell Latitude D600, but the above instructions for b43-fwcutter was the solution.  Thanks all!

---

