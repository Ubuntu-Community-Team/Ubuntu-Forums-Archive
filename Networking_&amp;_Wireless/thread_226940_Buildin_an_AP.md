---
title: "Buildin an AP"
date: 2006-07-31
forum: Networking &amp; Wireless
---

### Post by Tomas Galli on 2006-07-31
SORRY MY ENGLISH. CHEERS FROM ARGENTINE!



 Ok, i´m trying to build an AP with the mini-distro Voyage-Linux (Debian based). The PCI wlan card have an Atheros Chip, so i can work with Madwifi. This Driver is included in the Linx-Voyage Ditro and i installed the last version of it. i installed the buid-essential pack, and another packs.
 
when i do iwconfig the list show´s 



	lo					no wireless extension

	Sit0					no wireless extension

	wifi0 					no wireless extension

	Ath0   					    IEEE ....   
					    Mode "Master"...Channel 0.....	Access point: Not-Asociated
					    bit rate........	
					    ETC ETC

	eth0					no wireless extension






then i do



	iwpriv ath0 mode 3
	
	ifconfig ath0 192.168.2.1  (and the wlan card go up)

	iwconfig ath0 essid xxx channel x rate auto 




at this moment, i can connect to the AP from another Computer and a USB STICK.

It´s all ok. isn´t it?

NO

When i reboot the system, i must enter those cods again in order to bring up the Wlan card again
(Sorry about the questions i´ll going to make, it can be stupid, but believe me, i´m a little bit stupid too..)



1) How can i make the system to bring up the wlan during the booting?

1.2) Must i type 	$make
	       		$make install 
     from the madwifi directory and, THEN, enter the codes?

1.3) if that, where is the madwifi directory, because i really can´t find it making $dir /anything i puted $dir /madwifi
$dir /madwifi-ng $dir /a lot of patchs/madwifi ... and notjing, i can´t find it to do this $make install



2) it´s about to make a Script. In that case, how can i make a Script? 

2.1) what i need to type on it to solve my problem?

2.3) where must i copy the Script in? what directory?

3) I´t something relation to "ECHO" ((((((sorryyyyyy i don´t know what "ECHO" is. But i trying so hard to get in linux planet 
   and i like it very much.))))))


Another data



I have the 2.6.15-486-voyage directory in /lib/modules
but i have nothing in /usr/src

i´ll study, believe me, but help me with this...

---

