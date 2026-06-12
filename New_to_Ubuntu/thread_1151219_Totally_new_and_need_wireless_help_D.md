---
title: "Totally new and need wireless help D:"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by urbackdoor on 2009-05-06
OKay, If your reading this. thank you for thinking about helping me!
I only just set-up ubuntu 9 yesterday, so yes. im still learning. 
Right now I have a LAN connection, but its important i set-up my wireless. My wireless card is a Trendnet 423PI b1.1r
Ive looked though every tutorial and it always seems to get a little messy and not work. I know it would be a lot to type to answer me how, but perhaps you know a link? any help is greatly appreciated.

---

### Post by mick8985 on 2009-05-06
Unfortunately it appears your wifi card is a bit of a bitch to get working
[URL="https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_(ndiswrapper)?highlight=(WifiDocs%2FDevice)"]
https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_(ndiswrapper)?highlight=(WifiDocs%2FDevice)[/URL]

---

### Post by albinootje on 2009-05-06
> **mick8985 said:**
> Unfortunately it appears your wifi card is a bit of a bitch to get working
[URL="https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_(ndiswrapper)?highlight=(WifiDocs%2FDevice)"]
https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_(ndiswrapper)?highlight=(WifiDocs%2FDevice)[/URL]

Thanks for that link. It's good to know for the OP that it can work, and that Ndiswrapper can be used.

However, the good news might be that the howto looks outdated.
It talks about ndiswrapper-1.29 while this :
[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=ndis](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=ndis)
talks about version numbers higher than 1.29 so I would like to suggest to the OP to try and install Ndiswrapper packages, instead of compiling as the howto suggests.
See here : [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

