---
title: "Vodafone Huawei K3565 Problems"
date: 2010-05-16
forum: New to Ubuntu
---

### Post by Envious on 2010-05-16
Im new to Linux so go easy on me.

Yesterday I decided to take the plunge and wipe my laptops hard drive clean and install Ubuntu, however my only way of connecting to the internet is by using the above 3g modem, but I was sure it would work with Ubuntu after I found a few forum posts with people saying they got the same modem working with no problems.

After Ubuntu had installed I plugged the modem in and completed all the steps in the networking wizard, but the modem did not even attempt to connect when I told it to.

I then tried the drivers I downloaded from Betavine onto a blank CD before I installed Ubuntu, but it told me that python-twisted was missing, even though when I looked it seemed to be installed.

Sorry about the long post, I've had to install Windows again but I really want to make Ubuntu work, so does anyone know of a driver I could download to a blank CD before I install Ubuntu again?

Thank you everyone.

---

### Post by arochester on 2010-05-16
Someone brought one of these to me last week. It should work "out of the box" with 9.04 onwards. It worked fine with Crunchbang Linux (an Ubuntu derivative). Which version are you using? 

Don't turn on the computer and then plug in. Plug in first and then turn on.

---

### Post by Envious on 2010-05-16
> **arochester said:**
> Someone brought one of these to me last week. It should work "out of the box" with 9.04 onwards. It worked fine with Crunchbang Linux (an Ubuntu derivative). Which version are you using? 

Don't turn on the computer and then plug in. Plug in first and then turn on.

I'm using Ubuntu 10.04 LTS, I tried plugging it in first when the computer was turned off but it still did not work, after I did the network wizard to set up the modem and tried to connect it took less that 1 second from me clicking connect for it to say 'GSM Disconnected'.

---

### Post by Envious on 2010-05-16
If this modem is not that compatible with Ubuntu does anyone know if there is a 3g modem that works with Ubuntu without any problems?

---

### Post by philinux on 2010-05-16
See the sticky in General Help forum.

---

### Post by 3g modem on 2010-05-31
[COLOR=#000][SIZE=5]Have any questions please contact:[http://www.3gmodem.com.hk/ZTE/K3565Z.html](http://www.3gmodem.com.hk/ZTE/K3565Z.html)  [/SIZE][/COLOR]
[COLOR=#000]:popcorn:[/COLOR]

---

### Post by mrsi on 2010-05-31
Hi, I was having the same problem. It turned out I had the wrong apn, my one is ppbundle.internet. The ubuntu mobile broadband wizzard gave me pp.internet.

I have a vodafone top up and go k3565 (rev 2).

The easiest way to tell what apn you should be using is set up the modem on a windows machine. Then run regedit and look under HKEY CURRENT USER>SOFTWARE>VODAFONE.

One of they keys under that (I'm in ubuntu right now so can't remeber which one) says APN and tells you the apn you should be using.

---

### Post by gandaran on 2010-05-31
> **mrsi said:**
> Hi, I was having the same problem. It turned out I had the wrong apn, my one is ppbundle.internet. The ubuntu mobile broadband wizzard gave me pp.internet.

I have a vodafone top up and go k3565 (rev 2).

The easiest way to tell what apn you should be using is set up the modem on a windows machine. Then run regedit and look under HKEY CURRENT USER>SOFTWARE>VODAFONE.

One of they keys under that (I'm in ubuntu right now so can't remeber which one) says APN and tells you the apn you should be using.
or even easier, go to the properties window of the modem microsoft windows setup, that's how I found out everything I needed, the APN and authentication method for my Ubuntu setup!

---

