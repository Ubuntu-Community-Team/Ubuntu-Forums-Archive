---
title: "Intel wireless recognizing, but not connecting. AA 17.10"
date: 2017-11-24
forum: Networking &amp; Wireless
---

### Post by pointy2 on 2017-11-24
[I]I have read other threads and searched for a remedy, however, my prob is not mentioned.
[/I]
dell 5378 w/Intel wireless interface 3165. There is a warning in the terminal as I ran lshw -C network....output may be incomplete or inaccurate, you should run this program in super-user. [I](I think the warning has to do with running this command in sudo.)

New re-install of AA 17.10 on i7 KabyLake archetecture, with the above mentioned Intel wireless, firmware updated. 
Wireless was working for about an hour before reboot. After reboot, the network manager shows available wifi networks, and connects (?) to a selected network. It's there, that all wifi terminates in the sense that the icon shows a "?", and no traffic is recorded. Cannot access a site or even repository through wifi. 
[/I]Settings panel shows airplane mode = off, wifi = on, and various networks as mentioned before. 
AirVPN client is installed, but not connected. 

UFW has been re-set to default. 

This post is being written on my backup laptop running XX 16.04. It is sitting right next to the affected dell. So wifi is working through the router. 

Is there an error in the config? if so, where and what should I search for?

---

### Post by pointy2 on 2017-11-25
I'm beginning to understand that it's a bug during the update process. I'm finding alot of different solutions to the many inquiries of this issue. 
> iwconfig wlan0 outputs "wlan0  No such device.

I've found solutiuons in Arch and other flavors, but nothing yet for Ubuntu 17.10. This is going on day 3 in finding a solution....please help. 

All comments and suggestions are welcomed.

---

### Post by him610 on 2017-11-26
pointy2:

Recommend you read and follow instructions in this post, [https://ubuntuforums.org/showthread.php?t=370108]("https://ubuntuforums.org/showthread.php?t=370108")
then maybe you will get some help.

---

### Post by pointy2 on 2017-12-01
Thanks for this link, him610.

Following the instructions as I understand them, I'm running in to a problem executing the script.

#1 Download the script to my desktop on XX 16.04 LTS machine, to transfer to AA 17.10 machine.
#2 Right click on script to pull up "properties".
#3 Highlight permissions tab, select "Alloe executing file as program". Close box.
#4 Double click on script to select "Run" in the dialogue box. (This is where the conflict arises...script opens with gedit, no dialogue box opens).

OK, So I read [I][COLOR=#800000][**NOTE 1:** Since Ubuntu 13.04, Text Files open up in text editor even if they are made executable. To change this-

Open any folder > go to **Files > Preferences > Behavior tab > select "Ask each time"** option under "Executable Text Files" section.]
[/COLOR]
Here, I open a random folder (desktop) and right click or search for file permissions/preferences to select Behavior tab.[B] I cannot find this 

[/B][/I]***I'm stumped. Who has guidance for my confusion?***

---

