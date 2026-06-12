---
title: "bridge wireless to ethernet"
date: 2007-10-06
forum: Networking &amp; Wireless
---

### Post by madandbad on 2007-10-06
hi, i have ubuntu feisty and its running great with my linksys wireless-busb network adapter, however i would like to bridge that connection to ethernet so that i can connect a cable from my ubuntu pc into my hub and then into my laptop, im complete noob please help

---

### Post by pheeror on 2007-10-06
Buy wireless-ethernet "adapter" insted of wireless-usb

---

### Post by pheeror on 2007-10-06
Of course, there is workaround. You could make your ubuntu box works as bridge (package bridge-utils, command brctl). Now you can find good howto. But it's only a workaround.

---

### Post by kevdog on 2007-10-06
Can you draw or describe what you want to do better??

Is this what you want??

Internet---->Router or hub----->Desktop PC (has 2 network cards in place)---bridge--->LaptopPC

---

### Post by madandbad on 2007-10-06
router (wireless connection)-----------------ubuntu---------ethernet hub------------------windowslaptop

---

### Post by kevdog on 2007-10-06
Hmm Im a little bit confused

Wireless router (has only 1 ethenet port?????) ----- Ubuntu Pc (Has two networking cards??? ---- Hub -- windows

I dont know the specifics of your network but you can't do:

Wireless router ------ Hub ----- Ubuntu
...............................----- Windows PC

---

### Post by pheeror on 2007-10-06
His wireless router can be connected only by USB port. The best he can do is to be wireless router with switch.Of coures, madandbad also can type "ubuntu briding howto" in google search box.

---

### Post by kevdog on 2007-10-06
Ok lets start

sudo aptitude install bridge-utils

Can you post the following 
lshw -C network
ifconfig

Then we will be able to set up the bridge interace with something like the following:
 # ifconfig eth0 0.0.0.0
 # ifconfig eth1 0.0.0.0
 # brctl addbr mybridge
 # brctl addif mybridge eth0
 # brctl addif mybridge eth1 
 # dhclient mybridge

---

### Post by madandbad on 2007-10-09
NO, i HAVE MY ROUTER DOWNSTAIRS, AND THIS UBUNTU PC UP HERE;
i wish to also be able to connect an Ethernet cable to my ubuntu pc to my hub and then to my laptop, instead of buying one of these.
[http://www.amazon.com/gp/product/B00008WMBT/ref=s9_asin_image_1/104-1289705-5419958?pf_rd_m=ATVPDKIKX0DER&pf_rd_s=center-2&pf_rd_r=1EBMEJSTV4A6BFFETA2Z&pf_rd_t=101&pf_rd_p=278240301&pf_rd_i=507846](http://www.amazon.com/gp/product/B00008WMBT/ref=s9_asin_image_1/104-1289705-5419958?pf_rd_m=ATVPDKIKX0DER&pf_rd_s=center-2&pf_rd_r=1EBMEJSTV4A6BFFETA2Z&pf_rd_t=101&pf_rd_p=278240301&pf_rd_i=507846)

---

