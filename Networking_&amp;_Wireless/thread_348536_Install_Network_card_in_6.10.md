---
title: "Install Network card in 6.10"
date: 2007-01-28
forum: Networking &amp; Wireless
---

### Post by maxcooper on 2007-01-28
Hi there,

Im new to ubuntu and was having some trouble installing my dsl usb connection, so i got a cable ethernet connection but im first trying to connect the nic card i bought.

The card is an Advantek Networks 10/100 Mbps Fast Ethernet PCI Adapter and i have 6.10.

Can anyone help?!?

Thanks in advance.

Max

---

### Post by Stemp on 2007-01-29
Hi, 

Your card is not recognized out of the box ? 
Try this code to see if it is installed :
```
lspci | grep eth
```

What is exactly your card model ?

---

### Post by maxcooper on 2007-02-10
I tried that command and got nothig, but I tried just with lspci and was able to see several things but no ethernet card.

The model nr of my Advantek Networks is ALN-101C.

How can I install this??

Thanks for your help!

MAx

---

### Post by Stemp on 2007-02-10
If it's not recognized by default, you probably need to install a driver.

I've found : [http://www.advanteknetworks.com/products/networkadapters/aln101c.html](http://www.advanteknetworks.com/products/networkadapters/aln101c.html)

But I don't see much informations in Google about it.

---

### Post by maxcooper on 2007-02-10
Thanks for replying!

I got it to be recognized now by chaning the PCI slot, but still cannot get online.

Any clues on what shall i need to configure?

Thanks again,

MAx

---

### Post by Stemp on 2007-02-10
Ok, so now your card is recognized ? 
Are you using a modem ? a modem/router ? 
Do you need to enter a user/password ?

---

