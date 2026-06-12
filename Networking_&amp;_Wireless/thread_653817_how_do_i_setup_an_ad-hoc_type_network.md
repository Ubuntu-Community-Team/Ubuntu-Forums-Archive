---
title: "how do i setup an ad-hoc type network?"
date: 2007-12-30
forum: Networking &amp; Wireless
---

### Post by svtfmook on 2007-12-30
i have a wired connection.  i installed a wifi card.  i want to be able to connect my wifi devices to my wifi card to use the wired connection.

the card shows up in lspci:
04:07.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

i installed ndiswrapper

where do i go from there?

---

### Post by MrFSL on 2007-12-30
I think you actually have three questions here (correct me if I'm wrong)

**1)** How do I get my wireless card to work: 04:07.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

**2)** How do I setup and adhoc network

**3)** How do I implement ICS **I**nternet **C**onnection **S**haring (or IP forwarding)

As far as 1) goes - I don't have that card and am not familiar with its usage or the requirement for ndiswrapper. I can say the following. The output of:```
iwconfig
``` should give you an idea if your wireless network card is detected. I suggest installing ndisgtk for a graphical interface for ndiswrapper: ```
sudo apt-get install ndisgtk
``` Then you can access this too by going **System > Administration > Windows Wireless Drivers** Lastly, if you require ndiswrapper then you will need to get the Windows ndis driver for your card. Check the manufacturers website

As far as 2) I have had nothing but issues getting adhoc networks setup using any graphical tools. (Seems to not be a priority in the linux community) So I have had to edit files to get this working. It isn't too difficult really. You have to edit the /etc/network/interfaces file to start. More information can be found by typing (from a terminal):```
man interfaces
``` If you are looking for a more "flexible" solution you can write a script (or several scripts) that dynamically set your network settings. The main command in the script will be iwconfig. More information can be found by typing: ```
man iwconfig
```After your network connection is up and running THEN add your encryption. (For all Linux wireless issues please add encryption last.) You will have to manually set it by adjusting wpa_supplicant. More information can be found by typing:```
man wpa_supplicant
```and also ```
man wpa_supplicant.conf
```

Lastly for 3) I find it easiest to share you network connection by installing firestarter. Firestarter is a gtk graphical frontend for iptables (you firewall). There is a easy to use graphical interface for setting up ICS. It should be as easy as checking a box or two. It can be installed by typing:```
sudo apt-get install firestarter
```

I know you were probably hoping for a more direct answer - but as you can see it is an involved question. Do some reading and when you get stuck repost.

---

### Post by svtfmook on 2007-12-30
well, i guess my biggest problem is getting network manager to recognize the card.

it shows up in lspci, but not in iwconfig

so i guess i need to know how to get network manager to recognize the card.

---

### Post by MrFSL on 2007-12-30
According to this site: [http://hardware4linux.info/component/17424/](http://hardware4linux.info/component/17424/)

... there are mixed reviews on this hardware. 

ACTUALLY! This site might definitely help you! 
[https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)

Ah search - how easy you make life ;)

---

### Post by svtfmook on 2007-12-30
> **MrFSL said:**
> According to this site: [http://hardware4linux.info/component/17424/](http://hardware4linux.info/component/17424/)

... there are mixed reviews on this hardware. 

ACTUALLY! This site might definitely help you! 
[https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)

Ah search - how easy you make life ;)
ok, i followed the doc, i got everything setup per the guide.

but iwconfig still does not list "wlan0"
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      no wireless extensions.


john@cpe-76-188-8-111:~$ ls /etc/ndiswrapper
mrv8335

john@cpe-76-188-8-111:~$ cat /etc/modprobe.d/ndiswrapper
alias wlan0 ndiswrapper


now, when i did this command:
john@cpe-76-188-8-111:~$ sudo ndiswrapper -m

i got:
module configuration already contains alias directive

idk...

---

### Post by svtfmook on 2007-12-30
ok, i was able to get the card working using a different driver.  now, i'm able to view networks that are available, but i cannot get any of my wifi devices to connect to the network and use the internet connection.

---

