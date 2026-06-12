---
title: "Can not Connect to Internet"
date: 2010-09-03
forum: New to Ubuntu
---

### Post by 1492 on 2010-09-03
I just downloaded Ubuntu two days ago, and could not connect to the internet.  I went to the network manager, left-clicked on it, and underneath wireless it said, "device not ready". I turned off the wireless, and it said, "wireless is disabled", so I turned it back on and it still showed "device not ready". I tried clicking on configure VPN and nothing happened. I also clicked on "edit connections", but nothing happened. I can't figure out what I need to do. (by the way, I posted this using the same computer with Windows 7). Any help would be appreciated.

---

### Post by zeroseven0183 on 2010-09-03
Hi! I'd like to ask is wireless your only way to connect to the internet? Since, you will probabl have to download the wireless driver (System > Administration > Hardware Driver).

---

### Post by 1492 on 2010-09-04
Okay.  And yes, wireless is my only way to connect to the internet.

---

### Post by juil on 2010-09-04
Here's some troubleshooting tips if there is no wireless connection shown:
[https://help.ubuntu.com/8.04/internet/C/troubleshooting.html](https://help.ubuntu.com/8.04/internet/C/troubleshooting.html)

Following above will help, hopefully.

And here's general info on how to connect wirelessly which i'm sure you've tried:
[https://help.ubuntu.com/8.04/internet/C/wireless-connecting.html](https://help.ubuntu.com/8.04/internet/C/wireless-connecting.html)

---

### Post by 1492 on 2010-09-05
**"Connecting using Network Manager**

                                                                          **Network Manager** (System &#8594; Administration &#8594; Network) supports Roaming mode. This allows you to connect to any available wireless network in range.
                                    
[LIST=1]
[*]                       In the *Taskbar* click the **Network Manager** icon.
[*]                       Select your wireless network from the list.
[*]                       Enter your *Network Key*.
[*]                       Click **Connect**."
[/LIST]
                 
                              
The Network Manager icon disappeared from the taskbar, and there is no System>Administration>Network.  There is a "Network tools", but I haven't been able to get it to do anything .

---

### Post by 1492 on 2010-09-05
Also when I went to the troubleshooting guide it told me to type in "lshw -C network". I did, and it and it told me to become a "super-user".  What does that mean?

---

### Post by 1492 on 2010-09-05
I forgot to put in "sudo", nevermind.

How do I get the Windows wireless driver?

---

### Post by 1492 on 2010-09-05
I think I downloaded the Windows wireless driver, but the trouble shooting guide says I also need ndisgtk which I can get using the Synaptics package manager.  Do I need an internet connection to do that?

---

