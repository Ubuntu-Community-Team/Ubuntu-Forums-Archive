---
title: "madwifi driver suddenly failed for atheros wireless card"
date: 2008-07-03
forum: Networking &amp; Wireless
---

### Post by bkomar on 2008-07-03
I have an atheros ar5007 wireless card for my new HP.  I downloaded a madwifi driver and my wireless has been great for weeks.  Even this morning it was doing fine.  I boot my laptop this afternoon and I can't get wireless.  I attempted to download the madwifi driver again (a solution in the past) and it did nothing.  Any suggestions?

---

### Post by pytheas22 on 2008-07-03
What exactly is wrong?  Can you see wireless networks but not connect?  Or is there no wireless card recognized by the system?

Did you install any updates before the problem started?

If you reboot the computer does the problem still occur?

Does this help:
```

sudo rmmod ath_pci
sudo modprobe ath_pci
sudo ifconfig ath0 up
```

Also how did you install the madwifi driver--from source?

What does this say:
```

lshw -C Network
```

---

### Post by Bizurke on 2008-07-04
> **pytheas22 said:**
> 

Did you install any updates before the problem started?


 
This can happen when a kernel upgrade takes place. I've had it happen quite a few times over time and have ended up just making myself a script to take care of it. If you have updated please let us know anything that was changed.

---

### Post by hardyn on 2008-07-04
There was a kernel update today Bizirke... you are probably right.

---

### Post by Bizurke on 2008-07-04
I made this script a while back for kernel updates in debian because my wifi always quits. It should install a few apps that are useful and some that may be necessary. Then it will modprobe you card and you should be good to go. I wrote this for use on debian but it should by all means work fine on ubuntu. If there are any issues I'd love to know so I can fix them and make them ubuntu friendly 



```

#!/bin/sh
echo "Madwifi update script by bizurke"
echo "updating apt repositories. This may take a while"
sudo apt-get update
echo "apt repositories have been updated "
echo "if any errors have been reported please read instructions and 
attempt to fix"

	echo "============================================="
	echo
	echo "installing neccesary applications via apt-get"
	sudo apt-get install module-assistant build-essential madwifi-source madwifi-tools kwifimanager wireless-tools


		echo "============================================="

		echo Please, enter your kernel version and architecture, for example 2.6.25-2-686. If you do not know this info please use uname -r
                read kerver
                echo "updating headers to $kerver"
		sudo apt-get install linux-headers-$kerver
		echo 
		echo Headers should be installed, if any errors please check log


echo "============================================="


echo "begining configuration of madwifi"

sudo m-a prepare

sudo m-a a-i madwifi
modprobe ath_pci

echo "If no errors were given then please restart your system. Once you 
have restarted disable your wired connection via 
System>Admin>networking or ifconfig. After that enable your wireless 
connection via System>Admin>networking or iwconfig."


```

if you are not sure how to run this script you need to simply chmod +x madwifi-config.sh (assuming you saved it as that file name) then ./madwifi-config.sh


EDIT: Please be sure you use madwifi and an atheros card before attempting to use this. I am not responsible for your epic failures

---

