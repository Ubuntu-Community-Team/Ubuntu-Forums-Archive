---
title: "no drivers for Allied Telesyn"
date: 2007-02-26
forum: Networking &amp; Wireless
---

### Post by cannabis on 2007-02-26
Hello community!

I just installed Ubuntu and im new for unix systems. It looks pretty good, but I cant listen to music or connect to the Inet in Ubuntu. I have cable connection with switcher DES-1005D (Inet on 2 computers). Connection is using password and login. Questions:

Network card is Allied Telesyn 2501TX, Ubuntu couldnt detect network device. So what I can do with this problem? It couldn detect Floppy and AudioCard too ... 


Where I can find program, so it would be possible to format harddrive from floppy?




Thank you!

---

### Post by cannabis on 2007-02-26
[http://www.alliedtelesyn.com/products/detail.aspx?pid=238&lid=71](http://www.alliedtelesyn.com/products/detail.aspx?pid=238&lid=71)


My network card is here, plz people, I really need your help!

---

### Post by chili555 on 2007-02-26
Please open up a terminal and do sudo lspci -vv | grep Network and see if your card shows up. I think it uses the Realtek RTL8139D chipset. If you can confirm this, you might just do sudo modprobe 8139too and see if your card fires up (appears in System -> Admin -> Networking. If so, enable the card, mark it with DHCP and you sould be all set!

If not, search this forum for RTL8139 and see if there are posts about getting it going.

---

### Post by cannabis on 2007-02-27
> **chili555 said:**
> Please open up a terminal and do sudo lspci -vv | grep Network and see if your card shows up. I think it uses the Realtek RTL8139D chipset. If you can confirm this, you might just do sudo modprobe 8139too and see if your card fires up (appears in System -> Admin -> Networking. If so, enable the card, mark it with DHCP and you sould be all set!

If not, search this forum for RTL8139 and see if there are posts about getting it going.

Hi!

I tried to run 
```
sudo pppoeconf
```
but it write that card couldnt be detected, so there is nothing to do. I looked out that Im using Ubuntu 5.10, maybe I need newer version to get it work? 

Thank you!

---

### Post by cannabis on 2007-03-03
Here is my:

```
lspci
```



[http://img215.imageshack.us/img215/4761/dsc043586rg5.jpg](http://img215.imageshack.us/img215/4761/dsc043586rg5.jpg)

---

