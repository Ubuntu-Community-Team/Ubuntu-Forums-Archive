---
title: "Internet stopped working ubuntu 13.04"
date: 2013-12-02
forum: Networking &amp; Wireless
---

### Post by alyssajesse on 2013-12-02
I'm running Ubuntu 13.04 on a Dell Latitude d430. Have had no problems connecting to internet until this morning, now it says it is connected but I am unable to load any pages in either Chromium or Firefox. I am using a wireless connection. I know the internet connection itself is working as other people are able to connect fine. Please help!

---

### Post by daslinkard on 2013-12-02
Please temporarily hook up the ethernet temporarily and open a terminal and do: 	

 	```
sudo apt-get install linux-firmware-nonfree
sudo modprobe -r b43
sudo modprobe b43 

```

Detach the ethernet...now is it running?

---

### Post by alyssajesse on 2013-12-04
It isn't able to connect even with the Ethernet cable. It installed the packages 'alien librepmbuild3 librepmsign1 libsigsegv2 lsb-core m4 ncurses-term pax rpm' and then asked to install the NEW package linux-firmware-nonfree. It then says 'something wicked happened resolving 'archive.Ubuntu.com:http' I'm on my phone so can't copy and paste everything it says in the terminal but can find another computer if that will help.

---

