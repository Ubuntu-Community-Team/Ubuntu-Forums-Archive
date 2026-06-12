---
title: "Wireless troubles"
date: 2015-04-19
forum: Networking &amp; Wireless
---

### Post by cosmin4 on 2015-04-19
Hello, i have the latest version of lubuntu, but i have some troubles with my wireless connection. 
I have a Medion MD6200 and a netgear wireless pc card wg511v2. 
So I need some help to make wireless network working on my netbook.
Thanks in advance.

---

### Post by praseodym on 2015-04-19
Hi,

please run the wireless script from the sticky-thread and show the outputs here.

Thx

---

### Post by cosmin4 on 2015-04-20
[http://pastebin.com/LzHwyxV4](http://pastebin.com/LzHwyxV4)
Thanks.

---

### Post by Topsiho on 2015-04-20
I just fixed this or a similar problem using:

[https://help.ubuntu.com/community/NetworkManager0.7/](https://help.ubuntu.com/community/NetworkManager0.7/)  :

 d. Why won't Network Manager manage my Networks?

===> If your network connection is listed in /etc/network/interfaces, it is unavailable to NetworkManager <=== with its default setup (read this to see how to change it to manage these connections: [http://wiki.debian.org/NetworkManager](http://wiki.debian.org/NetworkManager) ). The best option for a standard setup is to open the file using

sudo gedit /etc/network/interfaces 

and comment out (ie put a # in front of) or delete every line in the /etc/network/interfaces file except the two with lo in them- they read

auto lo
iface lo inet loopback 

Now my new lubuntu works perfectly!!

In stead of gedit use leafpad though

Topsiho

---

### Post by praseodym on 2015-04-20
You need this driver using Ndiswrapper:
```

sudo apt-get install --reinstall linux-headers-generic build-essential dkms ndisgtk ndiswrapper-dkms
wget http://media.cdn.ubuntu-de.org/forum/attachments/19/38/1888522-marvel_8335_X32.tar.gz
tar xvf 1888522-marvel_8335_X32.tar.gz
sudo ndiswrapper -i marvel_8335XP/mrv8335.inf
sudo ndiswrapper -ma
sudo modprobe -v ndiswrapper
```
Check:
```
ndiswrapper -l
iwconfig
lspci -nnk | grep -iA2 net
lsmod
sudo iwlist scan
```

---

### Post by cosmin4 on 2015-04-20
You saved my life, [**[COLOR=#000000]praseodym[/COLOR]**]("http://ubuntuforums.org/member.php?u=1411497"). Wi-fi is working now on my lubuntu, and... i can now remain on it. Thanks a lot, you really helped me ! ^.^

---

