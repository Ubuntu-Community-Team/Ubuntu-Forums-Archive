---
title: "WiFi with &quot;Sweex&quot; USB adapter in Edgy Eft, using driver rt2500usb.inf"
date: 2007-01-28
forum: Networking &amp; Wireless
---

### Post by CityTop on 2007-01-28
I am completely new to Ubuntu (and Linux for that matter) - the list of problems seems to be endless...  Here is (another) one: like many others I seem to have trouble getting a WiFi adapter to work.

I have a USB wireless adapter "stick", "Sweex 053":
[http://www.sweex.com/LW053](http://www.sweex.com/LW053)

If I just plug it in, I get two "conncections", one on "wmaster 0" and one on "wlan0", network interface not configured in both cases. But at least the adapter seems to be recognized.

I didn't reckon it would be Linux compatible, since no Linux drivers are available. Then I came across a guide for installing a Belkin USB adapter:
[http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux](http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux)

Interestingly, the (Windows) driver for this device is the same as on my "Sweex" CD, so maybe my adapter will actually work. (I suppose it's some kind of generic driver).

So, I installed ndiswrapper using the Synaptic Package Manager. No problem. I can also  install the driver all right, but I can't get the hardware recognized when I type:

```
sudo ndiswrapper -l
```

I tried to blacklist rt2570, using this guide
[http://www.ubuntuforums.org/showthread.php?t=192588](http://www.ubuntuforums.org/showthread.php?t=192588)
 -  but I don't really know if I should have...

What can I do to make this setup work?

Thanks in advance!

Peter

---

### Post by vaab on 2007-02-07
Same card (LW053 from Sweex) on edgy. Same problem here.
The usb stick is said to use rt2571wf chipset.

Got same wlan0 and wmaster0 devices that pops at plug in.

but none of them accepts a "iwlist <dev> scan", for different reasons :
 
```
wlan0        Interface doesn't support scanning : Network is down **<-- needs a 'ifconfig wlan0 up'**
wmaster0  Interface doesn't support scanning : Operation not permitted

```

Issuing a 'ifconfig wlan0 up', i'm getting access to some commands : 
'iwlist wlan0 scan' - correctly spots my wifi essid


a "lsmod | grep rt" spots the module 'rt73usb' as beiing in charge of the mess.

a "lsusb" gives me this line : 
```

...
Bus 005 Device 004: ID **148F:2573** Ralink Technology, Corps.
...

```

from this source [http://doc.ubuntu-fr.org/materiel/wifi/rt73](http://doc.ubuntu-fr.org/materiel/wifi/rt73) (french), it seems that "rt73usb.ko" provided with edgy is not up to date...

I'm following the path of compiling the right module from source ... this worked perfectly and wasn't so harsh. But it seems messy. I'm looking for a more integrated solution.

---

### Post by nibsa1242 on 2007-02-08
Many others have had difficulty compiling from source. Please inform what sources you are using. Thanks.

---

### Post by satrich on 2007-02-20
The linux kernel headers where updated. So all of a sudden, my wireless connection fell out. I didn't know about the kernel headers update. But I did take a look, and I am using now 2.6.17-11 version. And it was 2.6.17.10.
So I you have to do is re-compile the driver according to : [http://doc.ubuntu-fr.org/materiel/wifi/rt73](http://doc.ubuntu-fr.org/materiel/wifi/rt73)
and all should be ok.

And for the sweex usb stick, you need this source package:
[http://www.ralinktech.com/ralink/data/RT73_Linux_STA_Drv1.0.3.6.tar.gz](http://www.ralinktech.com/ralink/data/RT73_Linux_STA_Drv1.0.3.6.tar.gz)
It works. If you follow the french site, stated above.

* you can forget about editing the rtmp_def.h file. The sweex usb stick is already in there. At least, it worked for me out of the box. All you have to do is ./Configure , make all, and make install. And with Configure take good care of stating the right directory for the new kernel headers. That is somewhat different as stated in that French website.

I also did that blacklisting thing as mentioned earlier.

---

