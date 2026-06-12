---
title: "Can't get WEP to work for anything! Going crazy!!!!!! Toshiba Laptop"
date: 2008-05-23
forum: Networking &amp; Wireless
---

### Post by mechanicalmetal on 2008-05-23
Hey guys,

I have looked all over the forums and internet and nothing is helping me. I have a Toshiba Satellite a205-s5800 with a Realtek 8187b driver installed (yes its the one that everyone says to install and it worked, yaaay :mad:)everytime I connect to an open wireless network everything works flawless, but whenever I attempt to connect to my network at home or at work that has WEP encryption I cannot get jack. Getting really annoying not being able to have internet access =( 

Thank you so much and please note that any and all suggestions are to the highest of attention.

-Brandon

---

### Post by Bubba64 on 2008-05-24
> **mechanicalmetal said:**
> Hey guys,

I have looked all over the forums and internet and nothing is helping me. I have a Toshiba Satellite a205-s5800 with a Realtek 8187b driver installed (yes its the one that everyone says to install and it worked, yaaay :mad:)everytime I connect to an open wireless network everything works flawless, but whenever I attempt to connect to my network at home or at work that has WEP encryption I cannot get jack. Getting really annoying not being able to have internet access =( 

Thank you so much and please note that any and all suggestions are to the highest of attention.

-Brandon

Have you set the configuration correctly in the network settings. When I get disconnected I can't get back on unless I run roam with my own network or due a restart with manual configuration. Have you also turned off your router to let it reset then tried the wep setup with the correct configuration set then due a restart. once you have it working you can save it on the networks page after unlocking it for access. Also can you plug in and get it to work

---

### Post by nick_jones on 2008-05-24
i have the same exact problem, i turned off my WEP encryption and it works fine, but when it's on nothing

---

### Post by nick_jones on 2008-05-24
okay, i got mine to work. i was using the default WEP 128 bit passphrase option, i instead picked the WEP 64/128 bit hex key option, that did the trick. maybe it'll work for you too :)

---

### Post by pgroover on 2008-05-24
I just ran into the same problem and after a lot of frustration, I removed network-manager and my keyrings.  I then reinstalled both of them, started nm-applet manually, recreated the keyring for my network and now things are back to "normal".  There may be some residual issues I might have to contend with later, but for now everything is running fine.

---

### Post by mechanicalmetal on 2008-05-24
> **pgroover said:**
> I just ran into the same problem and after a lot of frustration, I removed network-manager and my keyrings.  I then reinstalled both of them, started nm-applet manually, recreated the keyring for my network and now things are back to "normal".  There may be some residual issues I might have to contend with later, but for now everything is running fine.

Hey man, please let me know what you did exactly so that I can try it. Im a linux noob so kinda post your reply in dummy terms. Thanks man!!! 

And for bubba64's reply, yes I can get online if I plug in via lan or if I connect to an open wireless network but no wep or wpa. I work for an internet company so I have tried my laptop on like 20 different routers.

Please advise :(!!

---

### Post by pgroover on 2008-05-25
> **mechanicalmetal said:**
> Hey man, please let me know what you did exactly so that I can try it. Im a linux noob so kinda post your reply in dummy terms. Thanks man!!! 

And for bubba64's reply, yes I can get online if I plug in via lan or if I connect to an open wireless network but no wep or wpa. I work for an internet company so I have tried my laptop on like 20 different routers.

Please advise :(!!

Sorry about the delay, but I've been pretty busy today.

Here are the steps I took (within a terminal):

sudo apt-get remove network-manager (Remove network-manager)
cd .gnome2
Follow one of the following to remove your keyrings:
1. (safer option since any previous keyrings are saved) cd keyrings, mv default.keyring default.keyring.bak, mv default default.bak
2. (more volatile since keyrings are deleted) rm -Rf keyrings (remove ALL keyrings)
sudo apt-get install network-manager (reinstall network-manager)
sudo apt-get install kwalletmanager (reinstall kwalletmanager)

Close the terminal, and run each of the following, in succession, using Alt-F2:
kwalletmanager (starts kwallet)
nm-applet (start network manager)

After you've started nm-applet, configure your wireless as you normally would (ESSID, encryption key, etc.), click OK and you should then be prompted by kwallet for a password to encrypt the new keyring.

Good luck

---

