---
title: "Wireless internet problems 9.10"
date: 2010-03-22
forum: New to Ubuntu
---

### Post by iamsuperman420 on 2010-03-22
I am running ubuntu 9.10 on an acer aspire one netbook. I am running a dual boot setup with windows 7. On system startup my comp connects to my wireless network and I can use firefox,frostwire,etc. with no problems. After a while (25-30 mins) I disconnect and i am unable to reconnect. Any help would be greatly appreciated.

---

### Post by admiralspark on 2010-03-22
Hello,
Would you please go into a terminal and post the output of
```
lspci | grep Network
```
back here? That'll tell us specifically which wireless card you have.

Second, please post the output (in a similar manner as above) of:
```
iwconfig
```
Please do that both while you have internet and, if possible, get a copy of it after the internet drops/save to text file/reboot/post here.

Does internet work fine in Windows?

Also, what exactly do you mean "it won't reconnect afterwards"? Will it attempt to or will the wireless card actually shut down?

I'll get to potential problems and fixes after we have more information.

---

