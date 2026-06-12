---
title: "Connection Ad-Hoc between Windows 7 and Lubuntu"
date: 2015-04-04
forum: Networking &amp; Wireless
---

### Post by balubeto on 2015-04-04
Hi

I have Lubuntu 14.04 with an Internet connection via USB stick and I have a computer with Windows 7.

 Since both computers have wireless chips, I would like to create a wireless Ad-Hoc to share Internet.

 So, how do I do this so that Windows 7 did not create a "undefined network"?

Thanks

Bye

---

### Post by Vladlenin5000 on 2015-04-04
Why don't you connect Windows directly to the same AP? Is your router limited to only one wireless client?

---

### Post by balubeto on 2015-04-05
> **Vladlenin5000 said:**
> Why don't you connect Windows directly to the same AP? Is your router limited to only one wireless client?

Because I do not have an access point.

 So having the internet stick connected to the notebook with Lubuntu, how do I make a wireless Ad-Hoc connection with the notebook with Windows 7 so that both notebooks have Internet?

Thanks

Bye

---

### Post by Vladlenin5000 on 2015-04-05
Which one has internet connection and how?

---

### Post by balubeto on 2015-04-05
> **Vladlenin5000 said:**
> Which one has internet connection and how?

The notebook with Lubuntu acts as host and is connected to the Internet via a USB internet stick.

 Now, I have a notebook with Windows 7 that needs an Internet connection and I thought to share the Internet connection with that of the notebook with Lubuntu.

 So how should I configure the two notebooks (which have wireless chips) to share the Internet connection?

Thanks

Bye

---

### Post by Vladlenin5000 on 2015-04-05
What is that "USB internet stick"???
A WiFi dongle? If so you must be connected to an wireless access point (AP) already so my first question stands. Besides, if you're already using such WiFi device you can't simultaneously share that, you'd need a second WiFi card/dongle. Or you can bridge the wireless connection to the Ethernet and connect the other laptop by cable.
Please clarify the first point, we can't proceed otherwise.

---

### Post by balubeto on 2015-04-05
> **Vladlenin5000 said:**
> What is that "USB internet stick"???
A WiFi dongle? If so you must be connected to an wireless access point (AP) already so my first question stands. Besides, if you're already using such WiFi device you can't simultaneously share that, you'd need a second WiFi card/dongle. Or you can bridge the wireless connection to the Ethernet and connect the other laptop by cable.
Please clarify the first point, we can't proceed otherwise.

The notebook with Lubuntu acts as host and is connected to the Internet via a USB internet key (as [http://www.ondacommunication.com/it/prodotti/o/289/TM201?id_cat=2](http://www.ondacommunication.com/it/prodotti/o/289/TM201?id_cat=2)).

 Now, do you understand? So, could you help me?

Thanks

Bye

---

### Post by Vladlenin5000 on 2015-04-05
So it's USB 3G modem dongle...
Provided your WiFi card works in Lubuntu and is a relatively new one it should be possible. In standard  Ubuntu you would go to system settings > Network, select the WiFi and toggle the option to use as a hotspot. There's also the often recommended Firestarter: [http://www.svsarana.com/share_3G_data_internet_over_wifi.php?redirect=1](http://www.svsarana.com/share_3G_data_internet_over_wifi.php?redirect=1)

---

