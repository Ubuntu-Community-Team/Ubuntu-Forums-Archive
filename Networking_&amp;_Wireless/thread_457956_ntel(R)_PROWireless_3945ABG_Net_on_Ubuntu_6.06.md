---
title: "ntel(R) PRO/Wireless 3945ABG Net on Ubuntu 6.06"
date: 2007-05-29
forum: Networking &amp; Wireless
---

### Post by cleoandra on 2007-05-29
I just install Ubuntu and Im a big noob in here, so I would like to know how can I config my wifi connection on Toshiba if dont recognise my wireless card, I mean the most easyer and explicit way cos i tryed lot of way in forums and still cannot make it work :( So I was thinking to post this and maybe with ur help I can start use it.. Thx

---

### Post by Bigdog60 on 2007-05-29
Tell me what exactly what you want to do with the wireless.

---

### Post by wieman01 on 2007-05-29
Run this from command line and we will see if your card is working or not:
> iwlist scan
Please post the output. And please keep in mind: You cannot use Ethernet and wireless at the same time. When you try to connect via wireless, pull the cable.

---

### Post by cleoandra on 2007-05-29
sure! i was not connected in cable if i could do my work with cable it was easyer :) I just need wifi connection and I guess need help step by step Im too n00b maybe for it... actually not for long...:)

---

### Post by chili555 on 2007-05-29
Please open a terminal (Applications -> Accessories -> Terminal) and type:```
iwlist eth1 scan
```Press enter. Jot down the result and post it here. While you are there, please also do:```
iwconfig
```Please post the result here. Thanks.

---

### Post by wieman01 on 2007-05-29
> **cleoandra said:**
> sure! i was not connected in cable if i could do my work with cable it was easyer :) I just need wifi connection and I guess need help step by step Im too n00b maybe for it... actually not for long...:)
Alright then... Do you know how to use the terminal? That's the quickest way of resolving your problems. Please execute all the commands that chili555 & I have posted here. It's a good start.

---

### Post by cleoandra on 2007-05-29
yup so as i said lo(probs opening port on router)interface dont support scan/no wireless ext; eth0 same; eth1 scan complete/unassociate(cos no cable just), sit0 interface dont support scan/no wireless ext....
guess thats all ive got.. what should i do next? :p

---

### Post by chili555 on 2007-05-29
> what should i do next?You could give us enough information to work with.

There was a lot more information associated with eth1 than just this:> eth1 scan complete/unassociateWe need those details in order to know if your wireless interface, eth1, is working or not. Please help us help you.> lo(probs opening port on router)lo is the loopback interface and has nothing to do with your router or ports.

---

### Post by wieman01 on 2007-05-29
You probably cannot post this information because you have got no wireless access. What you can do though is...

a. open a text editor that comes with Gnome
b. highlight the output of the scan command with the mouse pointer (click & drag)
c. then paste it in the text editor windows by clicking both touchpad buttons at the same time. 
d. save the file on a USB device
e. then post it using any other PC that is hooked up to the Internet.

Could you do that? It will help a lot.

---

### Post by cleoandra on 2007-05-29
Im sry about that didnt know is imp and thx for loopback, somebody just laugh of my unknowledge...
I have  here what you need ... ;)   [http://cpt901.free.fr/ubuntu/eth1.rtf](http://cpt901.free.fr/ubuntu/eth1.rtf)
Thx for other option im just back in front of pc and ill not move anymore..:)

---

### Post by wieman01 on 2007-05-29
> **cleoandra said:**
> Im sry about that didnt know is imp and thx for loopback, somebody just laugh of my unknowledge...
I have  here what you need ... ;)   [http://cpt901.free.fr/ubuntu/eth1.rtf](http://cpt901.free.fr/ubuntu/eth1.rtf)
Thx for other option im just back in front of pc and ill not move anymore..:)
Mate, good news is that you adapter seems to work just fine. Please do me another favor and post the results of this command:
> iwconfig
Then the contents of this file:
> sudo gedit /etc/network/interfaces
Also let me know what your network name is (ESSID) and whether you are using WEP (encryption) or not. You are close.
[U][B]
EDIT:[/B][/U]
Need to go to bed now... it's kind of late here. I'll check on you tomorrow.

---

### Post by cleoandra on 2007-05-29
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"Livebox-1928"
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:16 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:818   Missed beacon:0

sit0      no wireless extensions 
cannot open gedit/etc/network/interfaces

---

### Post by chili555 on 2007-05-29
I notice the access point Livebox-1928 is using WPA encryption. To set up WPA, please follow wieman01's link in his signature. Also, it is not> gedit/etc/network/interfacesRather, it is> gedit /etc/network/interfacesThat little space is crucial.

---

### Post by cleoandra on 2007-05-29
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid Livebox-1928
wireless-key B"F'ÀDADA"--È"B'"É-"ÇÀÀÉÉ

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

### Post by cleoandra on 2007-05-29
just another question.. ;p how do i reset the sudo pass he ask me even if i never set one before? it still work in root but if i want to change i cannot...

---

### Post by wieman01 on 2007-05-30
> **cleoandra said:**
> just another question.. ;p how do i reset the sudo pass he ask me even if i never set one before? it still work in root but if i want to change i cannot...
First of all, chili555 is right... your router is set to WPA which makes matters a bit more complicated than they ought to be. Is there a way you can turn off all security or change to **WEP** instead of WPA? Then it will be much easier for us to help you.

Second, the password the system is asking for should be your standard user password I believe. Please try it out.

Once you have disabled WPA on the router, please send us a note. It is a lot easier to get you hoooked up that way.

---

