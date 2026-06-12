---
title: "Linksys wirless B usb adapter"
date: 2008-02-19
forum: Networking &amp; Wireless
---

### Post by Badbrad on 2008-02-19
I have just got done installing the ubuntu 7.1 and everything is amazing on it except one thing. I can't seem to get the internet to work. I select my wireless network and it actually connects and give me the strength of the connection in percent. The only problem is i'm still not getting internet even after being connected to the network. I have other computers on the network that are able to use internet so i know its not my network. I was just curious if theres something i'm doing wrong?

specs:
Linksys wireless B USB adapter
model #: WUSB11 2.4 GHz.

I'm brand new to linux so please try to dumb down your terms. Thanks in advance.

---

### Post by Badbrad on 2008-02-19
bump...

---

### Post by Hightide on 2008-02-19
HI Bradbrad

can you post output from

```
 sudo iwconfig
```



```
 sudo ifconfig
```


regards
:)

---

### Post by Badbrad on 2008-02-19
Here you go:

ifconfig:
[IMG]http://i14.photobucket.com/albums/a324/Dewane/fdfef.jpg[/IMG]

iwconfig:
[IMG]http://i14.photobucket.com/albums/a324/Dewane/fdlf.jpg[/IMG]




Thanks for all your help

---

### Post by jhetrick62 on 2008-02-19
You are not getting an address via dhcp for your card.  Is your network wireless connection set to "roaming" mode when you check it?

If so, you have wireless driver issues it seems.  You many need to build new wireless drivers from the windows driver using ndiswrapper and then blacklist your current driver.  

OR, you may be able to search the forum to learn how others have dealt with your same wireless adapter.

Jeff

---

### Post by Badbrad on 2008-02-19
My wireless network is setup on a PPPoE. I have it set to roaming and it picks up my network and actually acts like it connects, but it doesn't. 

I guess i will have to read up on ndiswrapper seeing as how i have no idea what that is :) 


thanks for all your help

---

### Post by jhetrick62 on 2008-02-19
Here you go, take a look at this.  
[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

Don't do the SVN stuff, but follow this and make sure to blacklist your current driver.

Goodluck,
Jeff

---

