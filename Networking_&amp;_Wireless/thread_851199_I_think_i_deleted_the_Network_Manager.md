---
title: "I think i deleted the Network Manager"
date: 2008-07-06
forum: Networking &amp; Wireless
---

### Post by Rickyk on 2008-07-06
Ok Hey every one i am new to this forum and i have a problem. I think i have somehow deleted the network manager from my top panel and now i cant connect to my wireless network. so i cant get on the internet. can anyone tell me how i can add the app back to the panel or where i can find the app to open it?


Thanks,
Rickyk

---

### Post by HELLO_science on 2008-07-06
same here! and in terminal it wont come back,,, ricky, if you want a quick and dumb fix make a new admin user and it should be back up at the top.

i hope someone solves this issue

---

### Post by Rickyk on 2008-07-06
Yea i have done that and it worked for awhile then it went away somehow. I think its my 3 yr old bro messin with my comps he likes to tinker.

---

### Post by MacKai on 2008-07-06
Same problem here too... no 2 year old though. it must have been me, but I'm not sure how. I'm also using a new user account right now.... 

Ken V.
ubuntu 8.04

---

### Post by lswb on 2008-07-06
On Main Menu/System/Preferences/Sessions/Startup Programs make sure that Network Manager applet is checked. You may need to logout and log back in again to see changes. (or, open a terminal and type the command nm-applet and press ENTER) 

If that doesn't do it, make sure you have a notification area on the panel somewhere. (By itself the notification area is almost unnoticeable, it just looks like 2 vertical lines of dots, barely distinguishable from the background color. Besides the nm panel icon, this is also where the updates available icon appears and on a laptop where the batter/power icon is shown) Right click on the panel, select Add... then select Notification Area from the list that appears.

---

### Post by HELLO_science on 2008-07-06
problem solved.

---

### Post by MacKai on 2008-07-06
ok looks like i deleted my notification area, no problem getting it back but still no NM... 

it's not on the list under system > preferences > Sessions > start up programs.

if i use the teminal method that was sugested it appearce in the notification area but dissappearse as soon as i close the terminal...


thanks for the help so far....

Ken

---

### Post by wired465 on 2008-07-06
If network manager isn't listed in the startup programs, create a new entry. The command should be "nm-applet". As far as getting the app to run after the terminal is closed, try running "nm-applet &".

---

### Post by MacKai on 2008-07-06
ok... got it added to the list ok, its checked but does not appear in the notification area. switched user accounts but still didn't appear.

used the new terminal method but got the same results (disappears when terminal is closed)

thanks lets keep trying....

Ken V.

---

### Post by wired465 on 2008-07-06
You need to physically log out of that account. If you just switch users, the old user is still logged in. To be safe, just do a reboot.

---

### Post by Rickyk on 2008-07-06
ok i was messing around with it before i read this and i went to add/remove programs and i accidently deleted the network manager app. How can i connect to the internet?? i seen the stickyed post but it went right over my head. Any help??

Thanks,
Ricky

---

### Post by MacKai on 2008-07-06
full reboot didn't work. i made sure nm was checked in the strt up list before i didn't it but ...nothing 


Ken V.

---

### Post by wired465 on 2008-07-06
> **Rickyk said:**
> ok i was messing around with it before i read this and i went to add/remove programs and i accidently deleted the network manager app. How can i connect to the internet?? i seen the stickyed post but it went right over my head. Any help??

Thanks,
Ricky

If you deleted it from add/remove programs... you should be able to select it again from that same window. If not, try "sudo apt-get install network-manager-gnome"

---

### Post by Rickyk on 2008-07-06
i did that and its saying i cant connect to the internet to download the app.

---

### Post by MacKai on 2008-07-06
it looks like your saying to "reinstall" (using the GET command) but it works under the other user account, and if i use the terminal commands it works until i close the terminal.so im no sure thats the answer. let me know if i should "GET" it any way....

got to run to work ill get back to this in the morning ...


thanks for all the help so far....

Ken V.

---

### Post by Rickyk on 2008-07-06
i have accidently uninstalled network manager. I cannot see it on any other user accounts i even made a new one. i nned to know how i can connect to the internet other then useing network manager.

Thanks
Ricky.

---

### Post by lswb on 2008-07-06
If you have a ubuntu cd for your installed distro, open synaptic (Main Menu/System/Administration/Synaptic.

Then from the menu in synaptic, select Settings/Repositories and check the box for the CD. Close that dialog box and search for network-manager, mark it and also network-manager-gnome for installation. The "network-manager-gnome" package is what provides the visible icon in your notification area. Go ahead and "apply" and it should reinstall from the CD.

If you don't have a cd handy, you can use the command line to connect. I'm assuming your system is connected with an ethernet cable to a router or modem that acts as a DHCP server, a pretty common configuration.

Your ethernet interface is likely designated by "eth0" To verify, open a terminal and type the command "ifconfig" 

In the output you shoud see several lines including one something like this:
eth0      Link encap:Ethernet  HWaddr 00:00:00:60:59:00

If you have a wifi adapter or more than one ethernet port you may see additional similar lines, but let's go with the assumption that eth0 is your connected ethernet port (If you're using wireless a few more steps will be needed to connect, it will be much simpler to use a cable if you can)

In the terminal, type these commands, enter you password if prompted:

sudo ifconfig eth0 up
sudo dhclient eth0

You'll see some output, hopefully without errors, and get an ip address assigned.

Then you can start up synaptic or whatever package manager you are comfortable using and reinstall NM.

---

### Post by MacKai on 2008-07-07
[COLOR="Blue"]OK I'm fixed, this is what I think happened and how I fixed it:

I deleted my Notification area, not sure how but it was gone.

I found this thread and posted 

I followed the directions from the fist reply:[/COLOR]

 “On Main Menu/System/Preferences/Sessions/Startup Programs make sure that Network Manager applet is checked. You may need to logout and log back in again to see changes. (or, open a terminal and type the command nm-applet and press ENTER) 
If that doesn't do it, make sure you have a notification area on the panel somewhere. (By itself the notification area is almost unnoticeable, it just looks like 2 vertical lines of dots, barely distinguishable from the background color. Besides the nm panel icon, this is also where the updates available icon appears and on a laptop where the batter/power icon is shown) Right click on the panel, select Add... then select Notification Area from the list that appears.”    

[COLOR="Blue"]thanks lswb...

what I learned here was that that NM was checked in the start up list and I didn't have a notification area. What I did was follow the directions for putting a new notification are on the panel. Except I “logged out” by changing users instead of rebooting. Needless to say it didn't work. While I'm waiting for more input from the community I poke around and unchecked the box for NM on the start menu planing to log off and recheck it. When I went back NM was gone from the startup list. I used the instructions to use the terminal program and it did indeed start NM in the notification area but closed as soon as I closed the terminal.

next step was Wired465's instruction to add NM back to the menu :[/COLOR]

”If network manager isn't listed in the startup programs, create a new entry. The command should be "nm-applet". As far as getting the app to run after the terminal is closed, try running "nm-applet &".

[COLOR="Blue"]thanks Wired465.

I followed these instructions and NM was back on my start up list.  But not in the notification area.

I next tried Wired465's instructions to use the terminal and type "nm-applet &". with no different results (NM launched but closed with the terminal)[/COLOR]

[COLOR="Blue"]tried full rebooting and didn't work.

Next was Wired 465's instruction to "sudo apt-get install network-manager-gnome" I wasn't sure I needed to do this because NM seemed to still be installed (It worked from the terminal) but I did it any way... no change

ok here is the embarrassing thing... again while waiting for more input from the community I looked over all the steps I had done and realized that when I had added NM back to the start up list I made a typing error and typed “nm-apple” missing the “T” 
as soon as I fix this every thing worked.. 

so if this has happened to you:

	1.  Make sure you still have your notification area. Look for the two lines made up of small 	dots. Look close there hard to see. Add it if u don't have it by right clicking on the panel, select 	Add... then select Notification Area from the list that appears. 

	2.  Check that NM is checked on the start up list Menu/System/Preferences/Sessions/Startup 	Programs

3.then reboot

4.  if that doesn't work try the reinstall in the terminal type"sudo apt-get install network-manager-gnome"

5.  then reboot

if still no go, try repeating steps 1>2>3 

thanks to the Ubuntu community

I hope that by admitting to my dumb and recapping the steps someone else can fix their machine.....[/COLOR]

---

### Post by Rickyk on 2008-07-07
i couldnt connect to the internet useing your meathod lswb. And i am useing a wireless connection (a neighbors). Can you post the meathod to connect to a wireless connection?

Thanks,
Ricky

---

### Post by lswb on 2008-07-07
How are you posting to this forum? You can go to the web site [http://packages.ubuntu.com](http://packages.ubuntu.com), and find network manager for hardy. Download it, copy to your linux system via usb stick or whatever, cd to the directory where the package is and type

sudo  dpkg -i networkmanagerpackage,

substitute the correct name for what I used above, and do the same for the nm-applet package.

If you want to take a shot at connecting with wifi, you can try this but there are a lot of ifs and buts. No guarantee that it will work without some finessing and cussing. 

First determine what your wireless interface is. Turn on or insert the wireless adapter. Open a terminal and enter the command 

iwconfig

There will be several lines of output something like this:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:""  
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:1F:90:E0:E9:CE   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:41  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

See the block of lines I've posted that start with 
eth1      unassociated  ESSID:""  

This shows that eth1 is the wireless interface. It could have a different name on your system, wlan0, ath0 are common. Whatever it is, substitute it where I use eth1 from here on.

OK, now do you know the name (essid) of the network? if not, type 

  sudo iwlist eth1 scanning

(enter password if prompted)

look for a line something like 

 ESSID:"neighbor" 

If you see any lines in the output like " Encryption key:on" or anything about WPA, you will need the key or passphrase. I'm continuing from here as if the network is open/unencrypted/insecure. 


Substitute the correct essid (network name) where I use "neighbor" below and try this line:

sudo iwconfig eth1 mode managed essid "neighbor" 

Now this line:

sudo dhclient eth1

Hopefully you will see a few lines of output and a line near the end about an ip address being assigned, If so, go ahead and try synaptic & see if you can download.

Unfortunately there are often quirks or "gotchas" in connecting this way. You can check the long but helpful sticky thread at the start of the forum networking section for more help. Good luck.

---

