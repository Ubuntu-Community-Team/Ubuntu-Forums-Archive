---
title: "USB Adapter disconnecting"
date: 2007-07-16
forum: Networking &amp; Wireless
---

### Post by tprzepiorka on 2007-07-16
Hello. I tried searching about this and only found one thread, with no helpful replies. So hopefully someone now can help.

I am using a DWL-G122/B1 USB wireless adapter. I installed the rt2x00 drivers (only ones I could find) and finally got internet working. It was great until about 2 hours later the lights on the dongle stopped and I no longer had internet. I had to restart my computer in order for them to work again. Since then the frequency has varied from hours to 10 minutes. 

If there are no solutions could someone recommend some Ubuntu compatible USB wireless adapters so I can buy a more reliable one? (I am using a G network). 

Thanks for the help in advance :D

---

### Post by MyR on 2007-07-16
here's the community documentation for the card. it was tested under dapper but it *should* work for feisty
[https://help.ubuntu.com/community/WifiDocs/Device/DWL-G122_(Rev_B)](https://help.ubuntu.com/community/WifiDocs/Device/DWL-G122_(Rev_B))
good luck!
peace

P.S. I recommend this card:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16833315067](http://www.newegg.com/Product/Product.aspx?Item=N82E16833315067)

---

### Post by MyR on 2007-07-16
actually it looks like it could be a problem with the device itself. :/

---

### Post by tprzepiorka on 2007-07-16
Thanks for the recommendation. I'll try check it out. Sadly living outside the US newegg.com doesn't ship outside the US. I guess I will have to put up with this until I can get a good enough adapter. 
Thanks once again.

---

### Post by MyR on 2007-07-16
heres a list of compatible usb cards. many of them work "out of the box"
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
peace

---

### Post by tprzepiorka on 2007-07-26
I managed to find a way to fix and restart the adapter with out having to completely restart Ubuntu. By running these commands:
```
sudo ifdown eth0
sudo ifup eth0
```
Is there someway to periodically run these commands so that I can download without interruptions or create a button for my top panel that I can click when my USB adapter disconnects?

Thanks

---

### Post by MyR on 2007-07-27
I think you can create a launcher.. you will probably need to enter your password each time. for the command put
```
sudo ifdown eth0 && sudo ifup eth0
```
hope this helps!
peace

---

### Post by Guitar John on 2007-07-29
> **MyR said:**
> 

P.S. I recommend this card:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16833315067](http://www.newegg.com/Product/Product.aspx?Item=N82E16833315067)

Did the this device work for you *out of the box* in Feisty?

-John

---

### Post by MyR on 2007-07-29
> **Guitar John said:**
> Did the this device work for you *out of the box* in Feisty?

i haven't bought that card yet (although i will buy that one if i end up getting one). the aircrack team recommends it and i know the chipset is well supported. it also got great reviews on newegg.
sorry, maybe i should have kept my mouth shut ;]

check the other link i posted for a list of cards supported out of the box

peace

---

### Post by Guitar John on 2007-07-30
> **MyR said:**
> i haven't bought that card yet (although i will buy that one if i end up getting one). the aircrack team recommends it and i know the chipset is well supported. it also got great reviews on newegg.
sorry, maybe i should have kept my mouth shut ;]

check the other link i posted for a list of cards supported out of the box

peace

I checked the [website]("http://www.edimax.us/").  If you click on the *downoads* icon, there is some info listed as * Linux Open-Source Code*.   Hey, at least there's some Linux recognition out there.

---

### Post by MyR on 2007-07-30
nice sig

---

### Post by Guitar John on 2007-07-30
[-o<

---

### Post by tprzepiorka on 2007-07-30
> **Guitar John said:**
> Did the this device work for you *out of the box* in Feisty?

-John

The card does not work out of the box :( I picked it up hoping it would. In fact it wouldn't even let me start up Ubuntu if I had it plugged in and froze Ubuntu if I put it in after startup. I wouldn't recommend it though. 

I ended up taking back the Edimax adapter and got this one instead:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16833150021&Tpk=wg111v2](http://www.newegg.com/Product/Product.aspx?Item=N82E16833150021&Tpk=wg111v2)
It worked great out of the box with no configuration needed and I haven't had any problems with it at all.

---

### Post by Guitar John on 2007-09-22
I finally found my solution with [the  BELKIN F5D7050]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833314011").  I ordered one, and it worked "out of the box."  I configured the wireless connection on both computers with the same device just to make sure.  Once that was done, I ordered a second one.  All I had to do when it arrived was plug it into the computer and I was surfing away.

Hope this helps.

---

