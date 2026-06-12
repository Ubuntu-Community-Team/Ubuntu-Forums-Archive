---
title: "Broadcom BCM 4322 on Mac"
date: 2013-11-27
forum: Networking &amp; Wireless
---

### Post by cobymaggs on 2013-11-27
Hello

Yesterday we installed Lubuntu on our old mac. We performed a full clean-up and the installation succeeded. There's only one issue that we have, we can't use the airport anymore to make a wireless internet connection (or use the wireless mouse as other example). We don't think it's WIFI setting related, the available wireless connections only don't show up on the old mac device.

To be sure we installed Lubuntu on our laptop in the same way and everything works, wireless internet was ok. 

Because we couldn't make an internet connection on the pc, we were going to install the mac os again, but while doing this, the device automatically recognized the available networks again. So could it be a drive issue then?

We don't know how to solve this, in the weekend we will check to see if we can connect the computer via cable and to find a solution. Maybe someone can help us already? It must be something stupid but we couldn't figure it out yet.

---

### Post by heir4c on 2013-11-27
Post the output of the command:
```
lspci | grep 'Network controller'
```
Than we can see what wireless card you have.
ThanX

---

### Post by cobymaggs on 2013-11-27
aha, in one of the first steps during the installation we were asked:

- i don't want to connect to a wifi-network...
- connect to this network: 
and then we could select Broadcom corporation BCM 4322 802.11a/b/g/ Wireless LAN controller (rev01)

that's what we see now when using lspci as network controller

---

### Post by heir4c on 2013-11-28
You must install the driver for the Broadcom. But I have not one here, so I can't help you with a howto, so search on this forum (Google is easier and more possibility).
Sorry.

Edit:
Here a link to help with the Broadcom:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by Bucky Ball on 2013-11-28
*Thread moved to **Networking & Wireless**.*

If you can get online with a network cable there's a good chance this will be fixed quickly. The Broadcom cards are well supported but the catch 22 is it's difficult without the cable connection sometimes.

Could you please give us the output of these two commands. Copy them onto a USB dongle perhaps:

```
sudo lshw -C network
iwconfig
```

Do you know the details for your wifi network/router/access point?

If you can get online follow the instructions at '49' down the page here:

[http://askubuntu.com/questions/55868/how-to-install-broadcom-wireless-drivers-bcm43xx](http://askubuntu.com/questions/55868/how-to-install-broadcom-wireless-drivers-bcm43xx)

---

### Post by cobymaggs on 2013-11-30
all right, we found a solution, I can use internet again via a power line adapter :-)

and yes, we followed the instructions at '49'

[http://askubuntu.com/questions/55868...rivers-bcm43xx]("http://askubuntu.com/questions/55868/how-to-install-broadcom-wireless-drivers-bcm43xx")

and WIFI is working again.

Thanks a lot!!! :D

---

### Post by Bucky Ball on 2013-11-30
Good news. Please mark thread as solved by following the instructions in my signature. ;)

---

