---
title: "script for connecting to wireless networks"
date: 2008-03-07
forum: Networking &amp; Wireless
---

### Post by kaiwan on 2008-03-07
Hi! I would like to write a script named "wlan" that would do this:

miroslav@miroslav-desktop:~$ sudo wlan
Enter SSID: some_essid
Enter ENC: 1234567890
You are connected!
miroslav@miroslav-desktop:~$

So what I want is to use the inputs from terminal for inputs to iwconfig command,
in this example it would be:
---- 
iwconfig wlan0 essid some_essid enc 1234567890 &&
dhclinet &&
ifup wlan
----

and if I  dont enter the ENC, script should assume that there is no encryption:
----
iwconfig wlan0 essid some_essid &&
dhclinet &&
ifup wlan
-----

And it would be nice if I could run a scan of available networks before enterning SSID and ENC!

I could do it easier using GUIs, but I would like to learn how to write scripts.
Thanks

---

### Post by SpaceTeddy on 2008-03-07
just stumbled accross [this]("http://ubuntuforums.org/showthread.php?t=717260") thread posted 7 hours before yours. i think the dude does exactly what you want to do :)

---

### Post by kaiwan on 2008-03-07
maybe...not sure....looks unfinished

---

### Post by kaiwan on 2008-03-07
Here it is:

----------------------------------------------------------------
#! /bin/sh

nokey="";

echo 'You must be root to run this script!';
echo 'Scanning for avaliable networks ...';

sudo iwlist wlan0 scanning

echo 'Enter network SSID: ';
read ssidName
echo 'Enter network key: '
read netKey

if ["${netKey}" == "$nokey"];
then 
	sudo iwconfig wlan0 essid ${ssidName}
else 
	sudo iwconfig wlan0 essid ${ssidName} enc ${netKey}
fi 

#iwconfig wlan0 essid ${ssidName} enc ${netKey} &&

sudo dhclient wlan0
sudo ifup

echo 'All done, you are connected!'
echo 'To disconnect type: sudo ifdown wlan0'
----------------------------------------------------------------

If bugs are found please let me know, thanks :)
p.s. it works with WEP, if someone knows how to make it work with WPA let me know ....thanks again

---

### Post by SpaceTeddy on 2008-03-07
i have no idea how bash scripting works (i am a perl/python junkie), but you might want to acctually check if you are root instead of just printing it. otherwise, it looks fine :)

---

### Post by kaiwan on 2008-03-07
> **SpaceTeddy said:**
> i have no idea how bash scripting works (i am a perl/python junkie), but you might want to acctually check if you are root instead of just printing it. otherwise, it looks fine :)

dont know how to check it, for now, when I find out I will implement it...

---

