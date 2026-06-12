---
title: "Getting wpa_supplicant to load at boot"
date: 2007-02-03
forum: Networking &amp; Wireless
---

### Post by tictacman on 2007-02-03
I have followed this guide  to set up my ralink wifi card with wpa using
[http://ubuntuforums.org/showthread.php?t=263136](http://ubuntuforums.org/showthread.php?t=263136).  However I can't figure out how
load up the wpa_supplicant automatically in xubuntu.  One posts recommended adding a script to /etc/init.d/ but I'm not sure what I should put in the script.

Here's my configuration in /etc/network/interfaces:

auto lo
iface lo inet loopback

iface ra0 inet dhcp
wireless-essid MYGROUP
pre-up wpa_supplicant -Bw -Dwext -i ra0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
auto ra0

#iface eth0 inet dhcp

#auto eth0


To get the wifi card to access the router this is what I'm doing at the moment:

Waiting for the system to load up

sudo ifdown ra0

sudo wpa_supplicant -Bw -Dwext -i ra0  -c/etc/wpa_supplicant.conf

sudo ifup ra0

---

### Post by phansiizwe on 2007-02-03
I have:

```
pre-up sleep 5
```

under:

```
pre-up wpa_supplicant -Bw -Dwext -i ra0 -c/etc/wpa_supplicant.conf
```

in order to give wpa_supplicant some time to load before the interface comes up.

---

### Post by tictacman on 2007-02-03
OK my interface settings now looks like this:

auto lo
iface lo inet loopback

auto ra0
iface ra0 inet dhcp
essid MYGROUP
pre-up wpa_supplicant -Bw -Dwext -i ra0  -c/etc/wpa_supplicant.conf
pre-up sleep 5
post-down killall -q wpa_supplicant



#iface eth0 inet dhcp

#auto eth0

Unfortuneatly it still doesn't boot up into the network - i have shut ra0 down and the bring it back up again to get on the net.  I tried variants of sleep 5 by lengthening the time but this has not helped either. Does anybody have any other suggestions.

---

### Post by tictacman on 2007-02-04
Ok, after much trial and error and countless reboots I solved the problem.  I went back to the idea of running a script at startup.  Here's what I did altogether:

I stripped out the wpa_supplicant line in /etc/network/interfaces so it read like this:

auto ra0
iface ra0 inet dhcp
essid MYGROUP

Then I loaded up nano from the terminal and created a file called ra6.sh writing in the commands I was typing manually from the command line so it looked like this:

#!/bin/sh
wpa_supplicant -Bw -Dwext -i ra0 -c/etc/wpa_supplicant.conf
sleep 15
ifdown ra0
ifup ra0

made it executable:
chmod +x ra6.sh

added it to the startup scripts:
 sudo update-rc.d -f ra6.sh start 99 2 3 4 5 .

rebooted and now it works!!.  This was my first script :)

---

### Post by whawes on 2007-10-25
From Edgy onwards, the easiest way to load wpa_supplicant at boot is via the /etc/network/interfaces file rather than editing init scripts. Just follow the procedure described here:

[https://help.ubuntu.com/community/WifiDocs/WPAHowTo#head-19b0a03ec0e66fadc9426778724825dd585178a5](https://help.ubuntu.com/community/WifiDocs/WPAHowTo#head-19b0a03ec0e66fadc9426778724825dd585178a5)

This will start and stop wpa_supplicant automatically every time you call ifup or ifdown on the relevant interface.

Works fine for me using Feisty.

---

### Post by Hero of Time on 2007-10-25
This is what I have in my interfaces file and works just fine.
```
iface eth1 inet static
	address 192.168.1.252
	gateway 192.168.1.254
	dns-nameservers 192.168.1.254
	netmask 255.255.255.248
	wpa-driver wext
	wpa-ssid <ssid>
	scan-ap-scan 2
	wpa-proto WPA RSN
	wpa-pairwise CCMP
	wpa-group CCMP
	wpa-key_mgmt WPA-PSK
	wpa-psk <wpa key from wpa_passphrase>
	post-down killall -q wpa_supplicant

```

Something that is also possible, is the following:
```
iface eth1 inet dhcp
	pre-up wpa_supplicant -Dwext -ieth1 -Bw -c/etc/wpa_supplicant/wpa_supplicant.conf
	post-down killall -q wpa_supplicant

```
And the wpa_supplicant.conf file:
```
network={
	ssid="<ssid>"
	scan_ssid=1
	proto=WPA RSN
	key_mgmt=WPA-PSK
	pairwise=CCMP
	group=CCMP
	psk=<psk from wpa_passphrase>
}

```

So what you had, should have worked, if you removed the association with the ssid, prior to starting wpa_supplicant.

---

### Post by alphacrux on 2008-03-24
Thanks to tictacman for his post. I was having the same problem and his instructions finally got my wireless automated. I would like to add that the command used to load the script: > sudo update-rc.d -f ra6.sh start 99 2 3 4 5 . does not need the -f parameter as this is only used when forcefully removing a script when the actual script file has not been deleted first. You can use man update-rc.d to check it out for yourself.

Personally I have tried using wpa-roam as well as adding pre-up and post-down commands to /etc/network/interfaces and none of it seems to work. I have even tried using large numbers for the pre-up sleep command but still no luck. I think it might have to do with the fact that the firmware in my prism 2.5 wavelan card is pretty old. Also Ive noticed that everyone uses the wext driver when calling wpa_supplicant but I have to use hostap for it to connect to my university's peap connection properly. Regardless when I run wpa_supplicant from the command line AFTER boot-up then I never have any trouble connecting. I don't see any point wasting anymore time on /etc/network/interfaces when this is such a easy workaround.

---

### Post by kevdog on 2008-03-24
Can you better explain this line for me and others??

```
sudo update-rc.d -f ra6.sh start 99 2 3 4 5 .
```

---

### Post by alphacrux on 2008-03-25
> **kevdog said:**
> Can you better explain this line for me and others??

```
sudo update-rc.d -f ra6.sh start 99 2 3 4 5 .
```

This code takes a script from /etc/init.d/ and sets it up so that it runs at startup "man update-rc.d" will tell you more about it than I can.

"start" tells it how to load at startup, all the numbers are parameters for "start". "99" is a number which tells the computer when to execute the script at startup with 0 being first and 99 last, with this number you are letting everything boot up first before executing this script. "2 3 4 5" are each runlevels, I don't know what a runlevel is but I do know "2 3 4 5" is the default, I believe thats why he chose them. The period separates start from stop, stop being how the script is stopped and in what order upon shutdown. stop is not required although the period is. In fact another way to do this would be to use the code: ```
sudo update-rc.d ra6.sh defaults 99 00
``` This code tells the computer to load the script last and stop it first although it is now recommended that you use multiuser instead of defaults: ```
sudo update-rc.d ra6.sh multiuser 99 00
```

In fact this last piece of code is probably the best way to load a script to run at startup.

---

### Post by kevdog on 2008-03-25
So you prefer the following:
sudo update-rc.d ra6.sh multiuser 99 00 

over
sudo update-rc.d -f ra6.sh start 99 2 3 4 5 .


They both work however?

---

### Post by alphacrux on 2008-04-05
Essentially yes, however the start and stop parameters are meant for customizing which runlevels the script runs and is shut down on. Because I don't know too much about runlevels I personally would stay from using them (less chances for a detrimental typo :)). Using just start doesn't tell the computer how to stop the script properly so I don't think this is the best way to go about this, especially if you're using more complicated scripts. Here is the reason for using multiuser over defaults from the manual:
> NOTES
       The multiuser option is an  Ubuntu-extension  intended  to  reduce  the
       amount  of time spent stopping services during shutdown and reboot that
       have no particular requirement to be explicitly stopped.

       Unless your init script does something in the stop command that is more
       than  just  sending the TERM or KILL signal to the running process, you
       should strongly consider using multiuser instead of defaults.

Also to note, you can actually just use defaults or multiuser without the two digit sequencing numbers: "defaults XX XX" -> "defaults" If you use this command the script with start and stop on 20. Ideally its better to use two corresponding sequencing numbers:
> As a rule of thumb, the sequence number of the  stop  link  should  100
       minus the sequence number of the start link; this causes services to be
       stopped in the opposite order to that in which they are started.  Obvi&#8208;
       ously,  therefore,  the  default  stop  sequence  number  should be 80.
       Defaulting to 20, as update-rc.d does, is an old  bug  that  cannot  be
       fixed because of the risk of breaking things.

---

