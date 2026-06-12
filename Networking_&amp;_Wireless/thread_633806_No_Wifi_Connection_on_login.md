---
title: "No Wifi Connection on login"
date: 2007-12-06
forum: Networking &amp; Wireless
---

### Post by FoxOne on 2007-12-06
I looked and looked, and couldn't find anyone with this issue, so I'm posting my first *hooray* thread here. 

I was able to connect to my wifi connection almost right out of the box with my netgear wg311 pci adapter. Read through some awesome post and got that setup, and it even works with WPA which is rad.

My only beef right now is that when I restart / log off my box and log back in, I have to establish my connection with my router again. Granted it's not terrible because I have to just go to a pull down menu and select my network and I'm back up and running, but can anyone help me with making this happen at log in? 

Thanks in advance! 

I'm using the Ndiswrapper, and wpa_supplicant is installed and being commanded by the default network manager.

---

### Post by FoxOne on 2007-12-07
bump

---

### Post by gemsling on 2007-12-07
I have a similar problem. After a fresh install of 7.10, I easily connected to the Internet via my wireless router that uses WPA. I just entered ESSID and Password in Network Settings and all was good - until I restarted.

I've since saved the settings as a Location in Network Settings, and if I select it, the connection is established. The problem is that the Location is forgotten every time I start, and I can't see a way to make it a default. While it's annoying for me, it's a showstopper for other users on the computer: without admin access, they can't even open Network Settings.

PS. Is "Network Settings" the same as "NetworkManager" which is mentioned a lot in the forums? To add further confusion, the Help screen calls it Network Administration Tool.

---

### Post by FoxOne on 2007-12-07
I think it goes by many names. BTW, I tried using wicd, that as bad times. It locks up the machine at boot and goes down hill from there. I tried soemthing else too, can't recall the name, and it worked, but didn't support wpa.

---

### Post by FoxOne on 2007-12-10
bump

---

### Post by FoxOne on 2007-12-21
bump

---

### Post by joe konda on 2008-01-12
I had a similar problem: at every boot the wireless device was never detected (I've installed some weeks ago Ubuntu 7.10, and my wireless card is Netgear WG311v3), althought I followed the instructions from the community (
[https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3?highlight=%28WifiDocs%2FDevice%29)).
](*,)
Now everything's working well, with a simple trick you could try if you are using ndiswrapper.

Open the console and input the command
sudo gedit /etc/modules

A text editor will be opened, and insert at the end the line 
ndiswrapper
then save and restart.

Hope it works!
:D

---

### Post by FoxOne on 2008-01-15
Sweet, I'll give it a try. Currently I'm running Fedora 8. I just needed some change. I might to go Desktop-BSD and PC-BSD before I make my way back to Ubuntu. But! I have it running on my laptop too, so I'll try it there.

---

### Post by FoxOne on 2008-02-03
Hey, that didn't work for me, but I did find something else. It deals with the keyring, I'll post my findings later

---

