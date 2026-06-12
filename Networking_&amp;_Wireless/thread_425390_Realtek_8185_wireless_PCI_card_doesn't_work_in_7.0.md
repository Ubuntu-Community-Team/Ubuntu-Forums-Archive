---
title: "Realtek 8185 wireless PCI card doesn't work in 7.04"
date: 2007-04-27
forum: Networking &amp; Wireless
---

### Post by chucktx on 2007-04-27
Does anyone know why a realtek 8185 PCI card doesn't even show up in 7.04 but worked fine in 6.10?  Now the airlink AWL3025 shows up but I can't get it to associate.  The airlink card didn't show up in 6.10.

---

### Post by nancy0779 on 2007-04-27
I have same card and had same problem  and still having wireless problems. You have to comment the realtek driver information in restricted drivers file. Search on this form and u should see the steps to enable the drivers and than ur wireless card will be recognized.
I am still struggling to get wep work on my laptop.

---

### Post by jstone00 on 2007-04-27
Luke411 said:

There are some other posts on here about this but I'll add in my two cents worth since I had the same problem and managed to get mine working again.

1) You have to comment out the drivers in the black-listed file.

/etc/modprobe.d/blacklist

#blacklist r818x
#blacklist r8187

2. You have to add a 'dummy' character to your ESSID after you reboot and the modules load. I used a " for mine at the end. I guess some bug makes the last character of your ESSID leave the building and you have to do that in order to connect.

Good luck,

---

### Post by _tomcio on 2007-05-07
Well it doesn't work for me. I have the same chip in my wireless card and I also made this workaround (dummy sign, editing blacklist etc). However it still doesn't work for me :cry: 

Here is what I see, when I'm trying to turn on wmy network interface:
```
tomek@tomek-desktop:~$ sudo ifdown wlan0 
tomek@tomek-desktop:~$ sudo ifup wlan0 
RTNETLINK answers: File exists 
run-parts: 
/etc/network/if-up.d/avahi-autoipd exited with return code 2 
tomek@tomek-desktop:~$ 
```

'ping' to my access point and router says, that destination hos in unricheable?! On the other hand Ubuntu sees this accesspoint, because Network Manager detects few wireless network in my street.

Connection works fine under (forgive me God) under MS Vista with static IP address. Of course I configured the same static IP under Ubunto too.

HELP!

---

### Post by luke411 on 2007-05-07
I had to follow the instructions above after I upgraded from Edgy but I just decided to reformat and do a clean install and once I commented the drivers out of the blacklist, everything works great. I didn't even need to add the special character after my network name. Maybe it's an upgrade thing. Also I noticed it is much easier to connect to wireless networks as the network monitor automatically detects them now and ask you which one you want to connect to. Something else that didn't happen until I did a new install. I see what they meant now by adding laptop wireless support to this distro.

---

### Post by duojet on 2007-05-12
Thanks! I've waiting for a fix so could install ubuntustudio, and that worked perfectly!

Interestingly, in the blacklist file it says the driver is "buggy", but I've been using what I'm pretty sure is the same driver in dapper, and never had an issue.

---

### Post by lsalminen on 2007-05-15
Hi,

I'm new to Linux (completely)...

I have the Realtek RTL 8185L chipset, and I tried to use the
 /etc/modprobe.d/blacklist

#blacklist r818x
#blacklist r8187

commands in terminal (including sudo ...), but it didn't work.

Can someone explain to me what I have to do step by step??

I've been searching for days on google etc.

Thanks,
Lee

---

### Post by andytx on 2007-05-15
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6) &Conn=5&DownTypeID=3&GetDown=false&Downloads=tr ue

Download the windows xp version of net8185.inf

Extract the file into a directory of your choice.

install the driver
ndiswrapper -i net8185.inf
update the driver with the PCI ID
ndiswrapper -a 1799:700f net8185
restart the computer.
then ndiswrapper -l should show that it exists.
net8185 : driver installed
device (1799:700F) present
then configure it through System>Admin>Networking

---

### Post by lsalminen on 2007-05-15
Thanks! The wireless is now working! :)

---

### Post by anywebloco on 2007-05-29
I've tried blacklisting and adding an extra character to ESSID.

My problem is that whenever I try to activate the connection via System Settings->Network Settings my system hangs!

Any thoughts greatly appreciated!

---

### Post by renato treder on 2007-06-07
hi too all.. well I am beginner with linux ubuntu and I've got RTL8185 pci card, but I can't to connect with internet. first, I am brazilian and my english isnt very good, so please write step by steap what I need to do, I checked  one link on this page about the the windows xp version of net8185.inf, but this link doesnt work, remember that I had used ubuntu just for this week, I have search for all these days for the pci's driver but I couldnt find on the brazilian topics. Please help me, once again, I dont know nothing about linux.. please step by steap.. thx a lot. renato treder. you can email me. [email]spamcare-outros@yahoo.com[/email]

---

