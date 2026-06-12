---
title: "[SOLVED] Gutsy not detecting Ethernet."
date: 2008-02-08
forum: Networking &amp; Wireless
---

### Post by ashmew2 on 2008-02-08
Hi Everyone , Me and my friends have been using Ubuntu for quite some time. We were using Ubuntu 6.10 ,  Edgy Eft  , But yesterday I thought of upgrading all of our PCs to Gutsy. All of us have Internet Connections ( through Ethernet). Via Edgy , we were able to use the internet without any problems. But on 1 PC  , after upgrading to Gutsy , there is no connectivity. I fail to recognize what the problem is. But the internet was working on Edgy without any problems. I need some help.

The output of the command :
```
 lspci|grep net 
```

is

01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 81)


In Network Tools , Where it lists the Network Device , there is only a LoopBack Interface.


Thanks..

---

### Post by mist on 2008-02-08
yes I have the same problem. with several ubuntu variation OSs
One that works OK is mint.
not working, 7.1, 8.4, Alpha. Zenwalk,Xubuntu. plus more
I will attempt to find out why ubuntu Mint works.
and will post a reply as soon as I find a workaround.
The xubuntu help sugested.
Terminal: sudo ifup etho
but everything i tried so far as not worked.

---

### Post by ashmew2 on 2008-02-08
Well my friend turned on his system and "magically" his Internet started working. Ill get back  to you as soon as we find out what we "did" or "happened" in order to make the internet work.
By the Way , do you have port forwarding ? Try using the Static IP thing in Networking.
Also , try running in terminal , 
```

sudo pppoeconf
```

Although Im pretty sure that you already tried these things but I would like to know the output.


Second Edit :

He has been using a Static IP (for port forwarding) because he keeps Downloading/Uploading stuff using Bit Torrent. For that he needs Port Forwwarding Enabled. So he just went to the Network under Preferences and selected Static IP Address and used the same settings he had been using under windows. And he turned on his system again about 24 hours later to acknowledge that his Internet was working at last.

---

