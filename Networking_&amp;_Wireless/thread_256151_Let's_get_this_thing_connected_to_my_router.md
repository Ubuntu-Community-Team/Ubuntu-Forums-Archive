---
title: "Let's get this thing connected to my router"
date: 2006-09-12
forum: Networking &amp; Wireless
---

### Post by cjax1 on 2006-09-12
OK. I just installed 6.06. I cannot get wireless working. I did in the last release with WEP encryption. Got it down to a science. So I figured no problem this time. Yeah right.
I have turned off encryption with the same results.
 I used the exact same method I used in the last release in terminal and configuring the network. I think the last release was called Breezy?
 I got the windows driver installed. Before that I found out the ndiswrapper utils was not even copied during the install. I read someone elses post that said the same thing. I found it on the CD and copied it to my home folder. In terminal I CD'd to that directory and got it installed.

Here is what I typed in terminal to show what I'm getting in return,
```
chris@Ubuntu-desktop:~$ sudo ndiswrapper -l
Password:
Installed ndis drivers:
bcmwl5            driver present,  hardware present
chris@Ubuntu-desktop:~$ depmod -a
FATAL: Could not open /lib/modules/2.6.15- 23- 386/modules.dep.temp for writing: Permission denied
chris@Ubuntu-desktop:~$ sudo -i
root@Ubuntu-desktop:~# depmod -a
root@Ubuntu-desktop:~# modprobe ndiswrapper
root@Ubuntu-desktop:~# sudo ndiswrapper -m
modprobe config already contains alias directive
root@Ubuntu-desktop:~# exit
logout
chris@Ubuntu-desktop:~$ iwconfig
lo                no wireless extensions.

eth1            IEEE 802.11/g    ESSID:off/any  Nickname:"Broadcom 4306"
                   Mode:Managed   Access Point: Invalid    Bit Rate=1Mb/s
                   RTS thr:off          Fragment thr:off
                   Link Quality:0  Signal level:0  Noise level:0
                   Rx invalid nwid:0  Rx invalid crypt:0 Rx invalid frag:0
                   Tx excessive retries:0  Invalid misc:0  Missed beacon:0

eth0            no wireless extensions

sit0             no wireless extensions

chris@Ubuntu-desktop:~$
```

Edit, I did have my ssid set correctly with the same exact results. I try using DHCP and activating the card. It activates but I get no connection. If I try a static ip it will not activate, I get an error and tells me to check the settings. I've use a static IP in Breezy with no problem. If I click OK and close the window and check again it is not active.

Any help will be appreciated. I feel like I've moved a couple steps backwords in 6.06 not forward. Why the ... do I have to spend all my time trying to research all this again? I have actually used the exact same methods in one other distro and got it working. What has changed so much in 6.06? This is crazy.:mad:

---

### Post by spd106 on 2006-09-12
Basically, since the bcm43xx project to create an open source driver from broadcom chipsets became useable this was prefered to ndiswrapper. However the downside is that the bcm43xx driver needs the firmware from your windows cd and is limited to 11Mbps. 

Have a look at this wonderful community docs page. [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper)

---

### Post by cjax1 on 2006-09-12
Thanks for the link. I'm checking it out now. I still say it's crazy. I see you posted your reply 41 minutes ago. I've been trying and trying to get back here and I usually get a time out and page can not be displayed. I can get to any other website so I know it's not my connection. And when I click Submit I have to log in again. I'm already logged in. I'm sorry if I have an attitude but if I keep having trouble even getting on the Ubuntu forum I won't be back. So far I love Ubuntu and would like to make it my OS of choice but I have to have wireless no matter what. I had it in Breezy. And I just wanted to say now just in case I can't or decide not to get back here that I did not like it when I did not have a choice in where to install Grub. What if I didn't want to put it in the MBR. Luckily I did but I may have wanted to chainload it.

I do thank you for your reply.

---

### Post by cjax1 on 2006-09-12
OK. This isn't going to work. I'm in a building several yards away from my router. I would have to lug this desktop over there and wire it to my router. I can not download anything using aptget because wireless is not working. If I knew where to get these packages with windows I would download them that way. I'm not going to bother. But it still would probably not work. I'm not going through moving my desktop when I can get wireless working in other distros. Besides, I'm reading where others have tried those methods and still not worked. It looks like one command after another. Scripts scripts scripts. I've been playing arount with Ubuntu since Hoary, didn't need wireless then, and I keep coming back. I think I found the best distro there is, at least for me. I finaly got my neighbor interested in Linux and invited them over to try 6.06 installed with wireless once I get it going. Now I'm going to look like an idiot after ranting and raving about Ubuntu. I'm nuking Ubuntu right now. You have no idea how sick that makes me feel. I fell in love with Ubuntu. If I cant show them how well it works on my computer how am I going to convince them to put it on their computer. I have no clue if it'll work on theirs. They need wireless too and as far as I know wireless can't be set up with a live CD. Maybe I should've said this somewhere else but I had to get it off my chest and I'm not coming back.

---

