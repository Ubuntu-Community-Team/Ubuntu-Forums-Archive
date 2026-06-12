---
title: "Problems with integrated Broadcom"
date: 2006-10-12
forum: Networking &amp; Wireless
---

### Post by Erkkimon on 2006-10-12
Has anyone got Broadcom 4311 working? My mum just bought HP NX 6310 and I should make Ubuntu work on it. I won't give up coz I'm not gonna let her use stupid Winblows on his laptop.

The problem is that I can't find the interface anywhere. I can't set it up coz I can't get any contact to the card. Or maybe I just am too n00b. :S Anyway, I've messed around the Internet and read through dozens of forums and failed every time. What to do?

---

### Post by joergenlie on 2006-10-12
I have 4311 working on a hp pavilion 9074.
get ndiswrapper 1.25 source and unwrap it
uninstall ndiswrapper from repositories

Got to the directory where you have ndiswrapper 1.25 and type in terminal:

sudo make distclean
sudo make
sudo make install

then 
sudo ndiswrapper -i "your".inf 
sudo ndiswrapper -l (driver present, hardware present)
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m

echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo rmmod bcm43xx
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper

if ndiswrapper doesn't load at startup, add "ndiswrapper" to the bottom of your /etc/modules
works fine. 

If you choose to try out network manager to admin your networks and get it to work let me know. My network manager sees all wireless but won't connect so i have to stick with the default one. not so cool though.


hope this helps

Jørgen
Norway

---

### Post by Erkkimon on 2006-10-14
I installed NdisWrapper succesfully from the sources but my connection doesn't work. So I think that I have the drivers for my card now but how can I take the connection in use? Anything like wlan0 isn't listed in the list of interfaces in my network settings. When I open my NdisGTK, under bcmwl5 reads "Hardware present: No". What is wrong? The card is surely connected coz it's integrated and works fine with Winblows.

---

### Post by joergenlie on 2006-10-14
what do you see when you type "iwconfig" in terminal?


Jørgen

---

### Post by Erkkimon on 2006-10-14
> leena@korvajalka:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

ra0       RT2500 Wireless  ESSID:"WLAN"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:02:72:4D:18:E9
          Bit Rate:54 Mb/s   Tx-Power:0 dBm
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=65/100  Signal level=-62 dBm  Noise level:-197 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


This. This ra0 is my A-Link's PCMCIA card that I'm connected with.

---

### Post by joergenlie on 2006-10-14
strange

I have never tried the gtk for ndiswrapper, but I would stick to terminal.

When you install the bcmwl5.inf remember to have the other files from your windows driver directory present as well. I believe ndiswrapper uses some .sys files too. (if you forgot)


 your interface isn't necasserily called wlan0 either. It might as well turn up as eth1.

if you have a wireless button on your lap try to press it and see if somethings happening.

try searching the forum as well, theres loads of treads about bcm cards.

When you foolow the steps I have mentioned earlier in this tread, do you get any errror messages?

Jørgen

---

### Post by gvgerman on 2006-10-14
this worked for me:  [Howto: Broadcomm Wireless]("http://www.ubuntuforums.org/showpost.php?p=1071920&postcount=1")

---

### Post by Erkkimon on 2006-10-14
I've wandered through dozens of howtos and everyone has the same problem: no interface can be found. And I can't spot wireless button in my laptop. I got no errors except when compiling the NdisWrapper as the path of the $KBUILD variable was wrong.

---

### Post by Erkkimon on 2006-10-14
About the .sys files u talked about; where are they and where should they be put about?

PS. I spotted the wireless button but nothing reacts when I push it. There seems to be a led light it but it keeps dark even if I hit it with a hammer.

---

### Post by joergenlie on 2006-10-15
Find the windows directory that holds your bcmwl5.inf file. there's alot of other files there as well. Copy the entire folder and put it somewhere u like in your ubuntu filesystem. cd to that directory in terminal and install it from there. Be sure you have uninstalled the bcmlw5.inf first before you reinstall it otherwise ndiswrapper tells u it's already installed.


Jørgen

---

