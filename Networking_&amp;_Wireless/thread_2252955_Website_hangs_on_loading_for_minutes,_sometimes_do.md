---
title: "Website hangs on loading for minutes, sometimes doesn't load."
date: 2014-11-16
forum: Networking &amp; Wireless
---

### Post by Kevin_Hernandez on 2014-11-16
I've recently installed Ubuntu 14.04 LTS (64-bit) on a Lenovo Z585 laptop running an A8-4500M APU w/ AMD 7640G.
I'm fairly new to ubuntu and linux so bare with me.

Websites randomly don't load using FF. I'll visit facebook.com and it'll stay loading and I'll have to close browser and try again until it loads. This happens with other sites too. Sometimes facebook will load but wont load the entire page. On windows, everything seems to be running normal so I don't think it's my connection. 
This is a wired connection with wireless disabled. 

Need some help address this issue

---

### Post by shibu_sawyer on 2014-11-16
Sounds like you are hitting a bug, i had this issue long back where webpages dont load, and i got to reload the webpage.

Anyway here is the work around :

Run the resolvconf command in terminal (never mind whatever output you get sometimes you get error,sometimes you might get package not exist, just issue this command to check)


"sudo dpkg-reconfigure resolvconf"


Just agree/ok and then restart your networking (or just restart your
computer). 

You might also need to clear out your browser caches.


bug report :
[https://bugs.launchpad.net/ubuntu/+s...f/+bug/1000244](https://bugs.launchpad.net/ubuntu/+s...f/+bug/1000244)

---

### Post by Kevin_Hernandez on 2014-11-16
Ok I've ran resolvconf on command and restarted. It seems to have done somewhat of a job on facebook... but sometimes it still hangs. I overid my cache management to 1024, and it also helped a bit. I've uninstalled Flash as I thought that would play a big role in being slow. 

All this has helped, but I still get the problem every now and then. This is a new install of Ubuntu, and I've tried about 3 Installs all the same. 

Specs: 
AMD A8-4500M APU w/ AMD 7640G
6 GB of Ram
128 GB Samsung Evo SSD

---

### Post by coldraven on 2014-11-16
I'm getting this problem as well using FF 33.0 on Ubuntu 12.04. I just press the stop button (the small X) then reload the page but it is annoying. I thought that it might be a wifi problem but while a page is hanging if I open a new tab it will load a different site in an instant. 
It might be caused by one of my add-ons. I use NoScript and a bunch of others.

---

### Post by Kevin_Hernandez on 2014-11-16
Only addon I use is adblockplus...

---

