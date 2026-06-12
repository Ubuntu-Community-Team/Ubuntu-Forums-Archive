---
title: "help me setup my intel220BG wireless network please or i will lose my girlfriend"
date: 2007-08-16
forum: Networking &amp; Wireless
---

### Post by threeonethree on 2007-08-16
i made my girlfriend install ubuntu , she messed up her windows but managed to install ubuntu. but the problem is that she cant connect to the internet. she cant talk to me and is very angry about it she might leave me please help me..

i have tried to get her network working.. she has a intel 220BG network card which is detected and installed automatically by ubuntu. she has dhcp enabled in the router and her brothers computer is connected via wired connection to same router is is connected to the internet..

the problem is that she cant seem to get an ip address via dhcp (when she puts the wireless connection on roaming mode) she gets an ip like 169. something ... she cant even ping her 192.168.2.1 it says destination unreachable.  but her bro gets an ip automatically.. 

when she clicks on the two computers on right top side of her screen, it gives her all networks in her area , she can see hers too . but when she puts her keyword , it just asks her to give her keyword again and again. it doenst say ur connected or that keyword is wrong .. it just asks again .(mayb because of the 169. somethin ip she got?)

i tried to tell her to put the ip etc manually.. she gave it an ip like 192.168.2.4 , gave gateway address , put her essid , passowrd etc,, when she rebooted she was able to ping the router now.. but was not able to ping google.com .. i thought this was dns problem so i gave her ip adddrss or google and still coudnt ping .. coudnt open any sites etc.. whats wrong..


and why isnt she getting an ip with dhcp? does she need to ifconfig /flush dunno somethign like that? please help or she might leave me for ******* her computer up :( ,, i will post the result of ifconfig etc commands later cus she doesnt have internet access to post em yet

---

### Post by dannyboy79 on 2007-08-16
well you don't want roaming mode. uncheck that. also, are you sure there is no security for the router? WEP or WPA or WPA-PSK? I will need to see the following items to be able to help you.

First I need to triple check that you do indeed have the wireless chip you say you do. Do you mean the intel 2200bg? What does this command return?
lspci -vv

Immediately after booting up fresh, open a terminal and from the command line, type in
dmesg
and hit enter. Look through it for anything that's related to eth0, eth1, wlan0, wlan1, or anything about your wireless interface.
next please let me see what modules are loaded. these are drivers. that command is
lsmod
then let me see the output of these commands
iwconfig -a

also, are you aware of this [http://ubuntuforums.org/showthread.php?t=242418](http://ubuntuforums.org/showthread.php?t=242418)
if you have the intel 2200gb that is.

---

### Post by threeonethree on 2007-08-16
lspci says its a intel 2200BG wireless card..

dmesg says something about link not up

lsmod says ip2200 something driver is loaded

please help.. cant post iwconfig cus there is no network on that pc how can i?

---

### Post by kevdog on 2007-08-16
When you type iwlist scan, do you get anything???

Also when you type lshw -C network, is the device enabled or disabled?  What is the logical name?

---

### Post by dannyboy79 on 2007-08-16
> **threeonethree said:**
> lspci says its a intel 2200BG wireless card..

dmesg says something about link not up

lsmod says ip2200 something driver is loaded

please help.. cant post iwconfig cus there is no network on that pc how can i?
well, you either use a floppy drive, a usb stick, or just write it down. we need to see this info in order to help. if the wireless card is being seen, then have you gone into System, Admin, Network and tried to configure it for your setup. meaning the ESSID, security and what not?

---

### Post by threeonethree on 2007-08-16
> **kevdog said:**
> When you type iwlist scan, do you get anything???

Also when you type lshw -C network, is the device enabled or disabled?  What is the logical name?

i reinstalled fiesty right now.. its a fresh install.. when i type iwlist scan i get all the networks around the house.. her philips one comes too. it says its secured with a key.. i know its wep .. 128 bit. but it doesnt show IE  thingy where it shows if its wep /wpa or w.e .. 

when i type lshw -C network . i see her myson wired lan card and also her wireless.. her wireless says its unaccociated.. logical name is eth1  ..


also on a fresh install of feisty i cant ping 192.168.2.1 .. says unreachable.. it is secrued with wep

---

### Post by kevdog on 2007-08-16
Try the following at command line

This is assuming wlan0 is your interface name.  You can find your interface name by typing lshw -C network and by looking under your wireless section, look for logical name.

```

sudo dhclient -r wlan0
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "<ESSID_Of_Network_in Quotes>"
sudo iwconfig wlan0 mode Managed
sudo iwconfig wlan0 key HEXKEYHERE <------or you can put s:ASCII_KEY
sudo dhclient wlan0

```

Hopefully that will work for right now!

Just caught that your interface name was eth1.  So put eth1 in place of wlan0.

---

### Post by lambophil on 2007-08-16
should be able to help you here.

I just got my wireless working today and ive got a 2200BG Intel wireless card.
Ok, i had the same prob as you - i had WEP encryption going and it kept asking for the passphrase. I then went and told my Airport Extreme to use WPA encryption, and just like that it seemed to ask the passphrase to remember and just work. I dont think these wireless cards like WEP... but i hope that helps cause it was frustrating me as well. Also WPA is much more secure anyway.

---

### Post by threeonethree on 2007-08-16
> **kevdog said:**
> Try the following at command line

This is assuming wlan0 is your interface name.  You can find your interface name by typing lshw -C network and by looking under your wireless section, look for logical name.

```

sudo dhclient -r wlan0
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "<ESSID_Of_Network_in Quotes>"
sudo iwconfig wlan0 mode Managed
sudo iwconfig wlan0 key HEXKEYHERE <------or you can put s:ASCII_KEY
sudo dhclient wlan0

```

Hopefully that will work for right now!

Just caught that your interface name was eth1.  So put eth1 in place of wlan0.

tried this .. cudnt still ping 192.168.2.1 cant connect nothing.. im tryin to use wpa instead now .. how do i roll back these settings which were made by thse commands?

---

### Post by threeonethree on 2007-08-16
hey .. it worked .. she just waited and then after some time clicked networks and slected her network put pass and it connected.. mayb the dhcp thing did the trick? will she able to stay connected when she restarts?

---

### Post by lambophil on 2007-08-16
> **threeonethree said:**
> hey .. it worked .. she just waited and then after some time clicked networks and slected her network put pass and it connected.. mayb the dhcp thing did the trick? will she able to stay connected when she restarts?

Yep definately should do.. It should just reconnect automatically i think. Its strange but, hey at least it works!

---

### Post by kevdog on 2007-08-16
Sometimes it takes like 30 seconds or so to get a dhcp lease.

To roll back what you typed:
sudo dhclient -r wlan0

If you want to bring down the interface (dont really need tooo):
sudo ifconfig wlan0 down

Thats it!

If all this works, let me know.  We can then proceed to WPA, and then installing WICD.

---

### Post by threeonethree on 2007-08-16
its wroking now so no need to roll back .. but what the .... why didnt it just worked out of the box .. i am very confused what happened and how it got fixed.. she wanted to give up many times but i made it work.. these kinda stuff should be fixed in ubuntu so that newbs dont get pissed off and ditch it

[www.knb.phpnet.us/forum](www.knb.phpnet.us/forum)

---

### Post by dannyboy79 on 2007-08-17
from what you described, you weren't ever configuring it with the password for your security and you didn't select the network. Also, you said it was in roaming mode, which I don't think works unless you have a correctly filled in /etc/network/interfaces file. I believe roaming mode will roam around and try to connect to any ap that you have setup within yoru interfaces file, i may be wrong here just a guess as I don't use it. So I think it just boiled down to the configuring it and the roaming mode. Glad you got it and glad another guy didn't have to lose his love over coding/linux. he he he he

---

### Post by kevdog on 2007-08-17
Another solution for you -- this time one that use a GUI -- no typing -- WICD.  Try it, you will like it, and your girlfriend will love you even more :)

---

