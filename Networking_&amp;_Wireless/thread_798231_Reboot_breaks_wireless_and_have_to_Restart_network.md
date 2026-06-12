---
title: "Reboot breaks wireless and have to Restart network services"
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by linuxology on 2008-05-18
I am running DHCP and everytime I restart the linux box I lose my wireless connectivity and have to run this command to get.  My wireless works fine after I run the command sudo /etc/init.d/networking restart  

Is there anyway to fix this ?  I have a linksys wmp5g wireless card.  One of my ideas is to put the command  sudo /etc/init.d/networking restart in a startup script, but I do not know how to do this.  Anyone have suggestions?

Here's a copy of my /etc/network/interfaces

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid test
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk psk

---

### Post by Cap'n Skyler on 2008-05-18
> **linuxology said:**
> I am running DHCP and everytime I restart the linux box I lose my wireless connectivity and have to run this command to get.  My wireless works fine after I run the command sudo /etc/init.d/networking restart  

Is there anyway to fix this ?  I have a linksys wmp5g wireless card.  One of my ideas is to put the command  sudo /etc/init.d/networking restart in a startup script, but I do not know how to do this.  Anyone have suggestions?

Here's a copy of my /etc/network/interfaces

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid test
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk psk

the place you re start the wireless connection has a place to save the settings on one of the tabs.
that should hold after reboot.
so re connect the wireless
then save those settings
then re boot and see if it worked.

---

### Post by linuxology on 2008-05-18
I tried to save in System->Admin->Network  This did nothing I am having to type the command into the terminal window to get my wireless card to grab an ip.

---

### Post by linuxology on 2008-05-18
Bump to the Top

---

### Post by Valloric on 2008-05-18
Ok, I had the same problem, and solved it today. 

This will be a lengthy post on running commands as root during boot without a password so others searching the forums can find this (there doesn't seem to be a similar post, and believe me, I looked). Linuxology, you should follow method three for your particular problem. Also, apologies if this guide hand-holds too much, I'm writing it with newbies with similar problems in mind.

There are basically three ways to run a command as root during startup: **method one** concerns editing the "sudoers" file so Ubuntu doesn't ask for the sudo password for the command you execute with sudo. You can find more info on that [here]("https://help.ubuntu.com/community/Sudoers") and [here]("http://ubuntuforums.org/showthread.php?t=779902"), but I really don't recommend that method. 

**Method two** is using root's crontab. More info on using crontab in general can be found [here]("http://ubuntuforums.org/showthread.php?t=102626"). But take notice, if you just add a command to your crontab with "crontab -e", those commands will NOT run as root, because that is your crontab, and you are not root. You need to run "sudo crontab -e", and edit root's crontab. This will be a completely different file altogether. Commands in here run as root. To get crontab to run a command during boot, you need to use "@reboot" instead of the number sections. More info on that [here]("http://www.debian-administration.org/articles/372"). Crontab with "@reboot" is not good *for this particular problem*, as it runs before any user logs in.

**Method three** (and the one I used to fix this problem) involves putting those necessary commands in a script, and calling that script from "/etc/init.d/rc.local". That file is the last one to run during boot, so* put the full path to your script at the end of this file*. You don't need sudo, rc.local runs as root.

If you need step-by-step instructions for method three and this problem, well... here they are:

Create a folder in your home directory. Let's call it "scripts".

```

mkdir scripts

```Now, you need to create a shell script with that restart command.

```

gedit scripts/net_restart

```Now put this in the script:

```

#!/bin/bash
echo "net_reset attempt" 
/etc/init.d/networking restart

```Close it and save it. Now change permissions so it can be run:

```

chmod +x scripts/net_restart

```Ok, now edit "/etc/init.d/rc.local"... 

```

 sudo gedit /etc/init.d/rc.local
 
```...and add the *full path* to your script *at the end of the file*:

```

# run my script to restart wireless after boot
/home/<YOUR USERNAME>/scripts/net_restart
  
```And that should be it. Granted, you could have just added the restart command to "/etc/init.d/rc.local", but I was trying to make a point. The adage about "teaching a man how to fish" comes to mind... scipts are nicer if you have more that one command to execute (even though this isn't that case :D).

EDIT: I think this solution for the net restart causes my computer to pause for like 10 seconds during boot at "Starting MTU...". It could be unrelated, and it could be specific to my computer, but anyway, it continues booting after that pause. Just thought I should give a heads-up just in case.

EDIT2: For the solution to the "Starting MTA..." pause, look [here]("http://ubuntuforums.org/showpost.php?p=4532555&postcount=4").

---

