---
title: "Any Decent GUI Wireless Manager?"
date: 2007-02-16
forum: Networking &amp; Wireless
---

### Post by telovoyagarcar on 2007-02-16
It sucks to have to type 20 commands to get the wifi card connected to a wireless network, each time i turn on the computer.

I found kwifimanager, kwirelessmonitor, the gnome network tool and a few others that didn even start, to be really useless.
Is there any soft to manage wireless networks able to scan, connect, and save different profiles for different locations (ex: home - office - starbucks). Being able to tell me the AP mac, channels, type of security, range, and all those important details is a plus. 

Do you have experience with a nice wifi manager?

Thank you.

BTW.. im using an Atheros card, madwifi-ng drivers. Just in case



..

---

### Post by futz on 2007-02-16
NetworkManager Applet
[http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)

It comes with Ubuntu. All you have to do is enable it. Works perfect. I have two Atheros cards and have never had to type anything to make them work. With NetworkManager it's all automatic.

I also use NM in Fedora and Sabayon. Works perfect there too.

---

### Post by pebo on 2007-02-16
network-manager should do what you want. It needs a bit of setting up though - read the documentation in /usr/share/doc.

---

### Post by dashnak on 2007-02-16
I've found that wifi-radar works a lot better for me than network-manager, you could try that....

---

### Post by telovoyagarcar on 2007-02-20
ok.
i installed wireless-manager and there is no option to save any profiles here... every time im on a different location i have to do everything manually. Wireless-manager is so basic. Useless for me.
What is the difference between this and the conection properties applet that came with ubuntu?

Wifi radar did not work in my laptop. Kwifimanager also sucks, it just shows networks around but still does not have the simple options i need.

Is there anything else a little more ¨advanced¨ able to keep safe a few profiles for a couple of different locations?

Thank you

---

### Post by computerjunkie on 2007-02-20
wireless assistant is decent

---

### Post by telovoyagarcar on 2007-02-22
> **computerjunkie said:**
> wireless assistant is decent

Thank you...

It looks very decent great!

The bad thing is that it just ¨LOOKS¨ good.. but it does not work.
I click on the network i want and follow the small wizard asking for the basic stuff like DHCP, KEY, etc, then click OK and the thing does nothing...  the settings on the wireless card just stay the same as they were before.

Why is this getting so complicated!! ???? :( 

is it possible to write scripts with the commands i use each time in the terminal to connect to each of those networks, so i just run the one i need when i need it? i can waste anymore time with this.

Thanks.

---

