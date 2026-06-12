---
title: "Help configuring my VPN connection"
date: 2007-07-13
forum: Networking &amp; Wireless
---

### Post by gerdt on 2007-07-13
Hello,
After searching around I finally have the option to graphically connect to VPN-servers. But somehow I haven't succeeded in making a successful connection because I can figure out how to configure this specific connection.

I wan't to connect to the VPN of my university, but they only have manuals for Windows and some Linux distro's (commandline configuration), but not Ubuntu. I would like to be able to connect graphically, using the network-manager. I tried to configure VPN on my Feisty using the Debian manual my university provides, but that one doesn't work.

I am using Feisty/Gnome/network-manager.

The manual my university provides is located here:
[http://www.snt.utwente.nl/handleidingen/windows_2k_xp/vpn2_xp_uk.php]("http://www.snt.utwente.nl/handleidingen/windows_2k_xp/vpn2_xp_uk.php")

I was wondering if someone might take a look at this link and tell me how to configure my VPN under Feisty/Gnome. If possible I would like to do this graphically, though a commandline configuration would also be fine.

Thanks in advance!

---

### Post by ReverendJ1 on 2007-07-13
I think I can help you out here. In Edgy Eft, setting up a VPN just involved clicking on the network icon in the system tray and then 'set up vpn' or something like that. I did it before and marveled at how easy it was. I am not sure if they took that out for Fiesty or there is something wrong with the machine I am playing on here at work, but it isn't showing up. Anywho, that isn't our only option. Go to 'Add/Remove' and install kvpnc. Once it is installed it will place a shortcut under 'Applications' -> 'Internet'. 
Open it up and then go to 'Profile' -> 'New File'
'Next'
Select 'Microsoft PPTP', 'Next'
Uncheck 'Require MPPE', 'Next'
Enter your username and password, 'Next'
'Next'
'Next'
'Next'
Enter a profile name and description. Enter 'vpn2.student.utwente.nl' for 'VPN Gateway'
Thats it. Now just try to connect. I tried it out here and it worked fine, it connected (or at least appeared to), but obviously failed the authentication, because apparently there is no one there whose username is 'somebody' with a blank password. :-) Let me know if it works.

---

### Post by llvllarten on 2008-01-29
Thanks, for the advice. 

I also had to install a pptp deamon from:
[http://rpmseek.com/rpm/pptp-linux_1.7.0-2ubuntu2_i386.html?hl=com&cx=0:-:0:3662408:0:0:0](http://rpmseek.com/rpm/pptp-linux_1.7.0-2ubuntu2_i386.html?hl=com&cx=0:-:0:3662408:0:0:0)

Now I'm connected to the UT network!

---

