---
title: "Can't connect to Wireless network"
date: 2008-03-16
forum: Networking &amp; Wireless
---

### Post by PongApp on 2008-03-16
Hey there, 

I am having troubles connecting to my wireless network even though I know everything is working. I'm running Wubi so I can choose between windows vista or Linux ubuntu 7.04 upon start up and my windows connection is fine. I also ran a Boot of Ubuntu 7.10 off a CD and the connection worked as well. For some reason when I choose to boot Ubuntu form my hard disk however using Wubi and I try and connect even though I know im putting in the right key and i have a fine setup it says it can not connect. I'm sorry for sounding really stupid but I just cant figure out what to do.

---

### Post by cmnorton on 2008-03-16
For starters, look at your /etc/network/interfaces file. I am assuming your Ubuntu installation is set to get its IP from your wireless router via DHCP and you Network Manager icon is on (usually is on) the upper right of the top toolbar.

Assuming that is correct, my interfaces file had to be set up -- other than comments -- like this

auto lo
iface lo inet loopback

for wireless networking to work. When I put this same PC into a wired network, no changes were required to interfaces. Wired just worked. I have not yet tried working this all out with static IP addresses.

---

### Post by PongApp on 2008-03-16
Thank you for the reply,

I am pretty new to Linux so I'm not exactly sure what you want me to do. I checked the file and it has exactly what you said (the comments and then the two lines). I don't know if you want me to edit something or add those lines, because if so they are already there. I still can't connect to my network. Any additional help would be much appreciated.

---

### Post by cmnorton on 2008-03-16
Select the Network Manager icon, and try to select your wireless network. If you've protected it with encryption, Network Manager is sophisticated enough to let you enter the network passphrase that your wireless router translated for you. 

That is in the router, if your passphrase is maryhadalittlelamb (which your router translates into hex byttes), NetworkManager is kind enough to let you enter maryhadalittlelamb, and translate it for you. 

What happens when you select "your network" from what may be a list of available networks?

---

### Post by PongApp on 2008-03-16
It shows up on the list and I select it then I suppose what is the "Network Manager" screen comes up prompting me to enter a passphrase or key. I change it from passphrase to HEX since I have a WEP key for my network, enter it, and then it trys to connect for awhile then says connection failed even though I know everything is right, and my equipment is working since im connected on the same PC as windows.

---

### Post by cmnorton on 2008-03-16
It should work if you choose WEP 128-bit Passphrase and use exactly the same passphrase you used when you set up the router. To see all this in the router, you may have to take an ethernet cable and connect your PC to the router, and then access your routers interface, which is usually web-based.

---

### Post by PongApp on 2008-03-16
I don't have a passphrase; I have a Hex key. I switch it from passphrase to Hex Key, put it in, it looks for it, and yes although it SHOULD be working, it doesn't. Hence my problem =/

---

### Post by cmnorton on 2008-03-17
Your HEX key was generated from a pass phrase. It may be the selection you are chosing. I remember finding the selections a bit confusing, and had to try a couple of them. For testing purposes, you could remove the wirless encryption temporarily just to see if you can connect. Then, put in a new passphrase.

Newer Linksys routers would not accept the length of the passphrase I used on an older Linksys Wireless G router I have. Could that be it? How old is your router and what length passphrase does it accept?

---

### Post by PongApp on 2008-03-17
Here's what my router looks like:

[It's a Verizon GT704WG]("http://onlinehelp.verizon.net/consumer/bin/images/Modems/ActiontecGT704WG_Vz200.jpg")

I don't see the word "passphrase" anywhere in my router settings. Heres is the what the security page looks like for WEP security.

~~~~~~~~~~~~~~~
~~~~~~~~~~~~~~~

4. Click on the button next to WEP

(We recommend using WEP because it encrypts your wireless traffic.)

WEP :  (on is selected)


O   on                 O   Off 
 
5. Select a WEP Key

NOTE: To create a WEP Key, you need to enter a combination of 10 digits. You can choose any letter from A-F or any number from 0-9.
Sample WEP Key: 0FB310FF28

select a WEP Key: (64-bit selected)

O   64-bit WEP key     O   128-bit WEP key    O 256-bit WEP key 

Key Code:
[**********]    (obviously i rather not show my key)

~~~~~~~~~~~~~~~~~
~~~~~~~~~~~~~~~~~

so yeah, I just enter whatever key I want and I don't know if that's the "passphrase" or not but i select 64-bit HEX key when the network thing comes up since that is what I have. I still don't know what's wrong.

---

### Post by PongApp on 2008-03-17
As well for further information, when I turn my WEP key to the "Off" position I disconnect from my network all together (On windows Vista). Luckily my other computer that is directly connected via Ethernet cable was still online and i was able to change my settings back to WEP key "On"

---

