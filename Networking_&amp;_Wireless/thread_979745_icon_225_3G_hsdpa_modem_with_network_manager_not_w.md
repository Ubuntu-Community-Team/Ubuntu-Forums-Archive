---
title: "icon 225 3G hsdpa modem with network manager not working"
date: 2008-11-12
forum: Networking &amp; Wireless
---

### Post by wabre on 2008-11-12
hi everybody.

i need some help with the 3G HSDPA modem icon 225 running on 8.10 32bit.

i followed this tutorial [http://www.pharscape.org/content/view/66/75/](http://www.pharscape.org/content/view/66/75/)

to install the HSOconnect tool. I can connect this way and use the connection, although I do not like this way of connection, especially since it's necessary to connect and disconnect it this way and since the modem is not recognized by the network manager, firefox for example starts in offline mode.

since 8.10 SHOULD be an improved distro mainly concerning GSM/3G wireless connections, i'm not satisfied with this workaround. According to this>

[https://wiki.ubuntu.com/NetworkManager/Hardware/3G](https://wiki.ubuntu.com/NetworkManager/Hardware/3G)

"using hso-1.6.tar.gz and udev.tar.gz from pharscape. All now working with network-manager"

it should work. I used both hso-1.6.tar.gz and udev.tar.gz. i was able to install the first tar, but i had problems installing udev.tar.gz so i could not continue.

these are the files i used:
udev.tar.gz: [http://www.pharscape.org/component/option,com_forum/Itemid,68/page,viewtopic/t,545/](http://www.pharscape.org/component/option,com_forum/Itemid,68/page,viewtopic/t,545/)
hso-1.6.tar.gz:
[http://www.pharscape.org/component/option,com_forum/Itemid,68/page,viewtopic/t,544/](http://www.pharscape.org/component/option,com_forum/Itemid,68/page,viewtopic/t,544/)

Does anybody know how to proceed with this and how to install? which outputs are needed from my machine?

Appreciate the help.

---

### Post by TpyKv on 2008-11-12
I'm also struggling with 8.10 - the first thing I always install (after a fresh Ubuntu install) is this Icon225 - I need it to be able to get everything else to work...

I followed the normal set up guide (from previous threads) and I get to the ./install.sh part - 

mkdir option
cd option
wget [http://asuseee.free.fr/tuto/01/icon225.tar.gz](http://asuseee.free.fr/tuto/01/icon225.tar.gz)
tar zxf icon225.tar.gz
mkdir /lib/modules/2.6.21.4-eeepc
mkdir /lib/modules/2.6.21.4-eeepc/extra
sudo ./install.sh

 - and here it says - 

./install.sh: 6: udevcontrol: not found

 - I can't believe that everytime I upgrade the the latest and "greatest" - that I find new problems that didn't exist before. I probably spend more time tinkering with the system than actually using it. 

If anyone can suggest a fix, I will owe you, big time!

---

### Post by wabre on 2008-11-12
> **TpyKv said:**
> I'm also struggling with 8.10 - the first thing I always install (after a fresh Ubuntu install) is this Icon225 - I need it to be able to get everything else to work...

I followed the normal set up guide (from previous threads) and I get to the ./install.sh part - 

mkdir option
cd option
wget [http://asuseee.free.fr/tuto/01/icon225.tar.gz](http://asuseee.free.fr/tuto/01/icon225.tar.gz)
tar zxf icon225.tar.gz
mkdir /lib/modules/2.6.21.4-eeepc
mkdir /lib/modules/2.6.21.4-eeepc/extra
sudo ./install.sh

 - and here it says - 

./install.sh: 6: udevcontrol: not found

 - I can't believe that everytime I upgrade the the latest and "greatest" - that I find new problems that didn't exist before. I probably spend more time tinkering with the system than actually using it. 

If anyone can suggest a fix, I will owe you, big time!

i'm not sure about eeepc and it's kernel, though try to follow the procedure from this link:

it says for 8.04, but i did it in 8.10 and it works. anyway, for me this entire HSOconnect thing is only a workaround, the icon 225 should be recognized by the network manager whatsoever:

[http://www.pharscape.org/content/view/66/53/](http://www.pharscape.org/content/view/66/53/)

---

### Post by TpyKv on 2008-11-12
Thank you, I'm going to try that this evening. I am hardly ever at home which is why I have this ICON225 in the first place, so having to go home and just to be able to get online, outside again, is hassle. 

The other problem is that network manager is awful and doesn't like working with the aircrack-ng - patched madwifi (wireless) driver. So I've been using WiCD and it's great... I don't think the HSO connect app is going to like WiCD but I'll have to wait and see... no doubt ten fresh install's later it will all be working again :)

Edit - damn good job I love Ubuntu otherwise I'd have smashed my laptop up into 750 little one pound pieces!

---

