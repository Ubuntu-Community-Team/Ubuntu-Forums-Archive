---
title: "BCM43XX/4309 ndiswrapper in Ubuntu 7.04"
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by jakesr on 2007-04-26
I have Dell Latitude 600m with Wireless 1450 (802.11a/b/g) Dual-Band WLAN miniPCI Card Product ID 4309.

I read over a lot of forums found ndiswrapper is the way to go to config my Ubuntu 7.04 for wireless Internet.

Below are various my attempts

I found some script in the forum sites to install the BMC43xx wireless driver using ndiswrapper to automatically configure. But it didn't work. I can't even get the ndiswrapper download successfully.

I tried may time ndiswrapper to install using 'apt-get' and it's not working. It's says ndiswrapper-common doesn't exist some like that.

After that I tried manually downloading the ndiswrapper 1.42 tar file to compile and install. Its throw a lots of errors like  "xxx.h" files not found. If I run the 'make' command inside the directory. 

I really want my move from XP to Ubuntu 7.04. But the ndiswrapper configuration problem with wireless make it very hard and frustrating for me to make this transition.

I checked the community site in ubuntu they don't have a 7.04 pages yet.

So can some one please give me one comprehensive solution in installing my ndiswrapper driver for my wireless card? 

Thanks,
Jakes.

---

### Post by Bergs77 on 2007-04-27
Hi Jack,
I found a guide here [http://ubuntuforums.org/showthread.php?t=340689](http://ubuntuforums.org/showthread.php?t=340689)

I used it for  BCM4303 and it worked. It's also pretty easy to follow.

Good Luck.

---

