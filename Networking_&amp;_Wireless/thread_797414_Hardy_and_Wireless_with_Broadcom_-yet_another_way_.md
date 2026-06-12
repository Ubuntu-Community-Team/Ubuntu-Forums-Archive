---
title: "Hardy and Wireless with Broadcom -yet another way to do it"
date: 2008-05-17
forum: Networking &amp; Wireless
---

### Post by Dirk_Gently on 2008-05-17
Always see my latest posting to this thread for updated information!


Despite the wealth of How-TOs and Broadcom-related threads already here, none of them seemed to work for me. From the other tutorials I learned that I had to load ndiswrapper (again) after the ssb module. I tried that and got ndiswrapper to take control of my card with no problem. 

My problems started, where all the other threads ended: Trying to associate to my wireless router using WPA2 with wpa_supplicant. Either I couldn't get a successfull authentication or I cold associate successfully but no traffic was possible -not even a ping to the router.  

After days of fiddling around with my Dell D600 notebook which has a BCM4306, Rev. 02 WLAN card, I finally managed to get it to work with ndiswrapper. Here's how I did it so that others may be able to get some hints for their own setup or maybe someone here can offer some advice on how to further refine my method, because as it is it's not very nice, but it works.

I set up my system so that it doesn't load any network drivers on startup not even ndiswrapper! I couldn't prevent the ssb module from getting loaded, though.

After logging in, I have to use 3(!) shell scripts to get the wireless lan working. 

Script No. 1 

```

rmmod ssb
modprobe ndiswrapper && rmmod ndiswrapper && modprobe ndiswrapper

```
For some reason, I have to load ndiswrapper 2 times in a row, otherwise wpa_supplicant from the next script can't successfully associate.

Script No. 2
```

wpa_supplicant -i wlan0 -Dwext -c /etc/wpa_supplicant/wpa_supplicant.conf -dd &

```
The next oddity is, that if I start wpa_supplicant with the -B option it won't work either. So I send it to the background and enjoy the output which is a good means to see if it could associate with the router.
Sometimes a second start of wpa_supplicant is necessary to get a complete handshake, that's why the next script has two optional lines at the beginning.

Script No. 3
```

#killall wpa_supplicant
#wpa_supplicant -i wlan0 -Dwext -c /etc/wpa_supplicant/wpa_supplicant.conf -dd &
ifconfig wlan0 up
ip addr add 192.168.1.42/24 dev wlan0
ip route add default via 192.168.1.1 dev wlan0

```

This sets up the necessary IPs (I never use DHCP) and default route. Of course I tried to have these things and the start of wpa_supplicant in /etc/network/interfaces, but that never worked. 

So there it is. It's tedious, yes, but I've seen more complicated solutions. The most tedious part was finding out the order in which to do things. I'd like to put it all in one shell script, but last time I tried it didn't work. The scripts need to be called separately for some reason. I sure hope that the next release or some update will resolve the situation for Broadcom card users introduced with Hardy.

If anyone can offer suggestions, how to improve my "solution" or how to avoid using it altogether, please reply.  

Cheers

---

### Post by Ph83drus on 2008-05-17
Wow!  I also am having horrible problems with wireless on my dell d600.

I got overwhelmed and frustrated with the amount of information on broadcom wireless on these forums.  I tried all the solutions multiple times, and nothing was working.  

I ended up buying an intel 2200BG wireless card, for $27 and put that in.

And it STILL doesn't work!  It seems closer to working though, because I can now SEE the networks in my neighbourhood, including my own.

However, it will not connect with any of the networks.

Maybe, we have a similar problem?!  Maybe your solution will work with my wireless card with the wpa supplicant stuff??

What does the wpa supplicant stuff do??  Because I am using WPA2 encryption on my wireless.

Thanks!

---

### Post by Ph83drus on 2008-05-17
By the way,  I started a thread asking people for help with my wireless problem.

It can be found at:

[http://ubuntuforums.org/showthread.php?t=796877&highlight=wireless+d600](http://ubuntuforums.org/showthread.php?t=796877&highlight=wireless+d600)

---

### Post by Ph83drus on 2008-05-17
nope.  The wpa_supplicant thing doesn't work for me.

phaedrus@phaedrus-laptop:~$ sudo wpa_supplicant -i wlan0 -Dwext -c /etc/wpa_supplicant/wpa_supplicant.conf -dd &
Initializing interface 'wlan0' conf '/etc/wpa_supplicant/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant/wpa_supplicant.conf' -> '/etc/wpa_supplicant/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant/wpa_supplicant.conf'
Failed to read or parse configuration '/etc/wpa_supplicant/wpa_supplicant.conf'.
Failed to add interface wlan0
Cancelling scan request
Cancelling authentication timeout
[1] 9122
[1]+  Exit 255                sudo wpa_supplicant -i wlan0 -Dwext -c /etc/wpa_supplicant/wpa_supplicant.conf -dd
phaedrus@phaedrus-laptop:~$

---

### Post by Dirk_Gently on 2008-05-18
Hi 

wpa_supplicant, as the name says, provides the WPA encryption for wireless connections. I omitted the details of setting it and ndiswrapper up, because that's covered in numerous other threads. Please read up on it here or search on Google. 

But I'll be glad to help, too. According to the error message you posted, the config file for wpa_supplicant either doesn't exist, or is not readable. 

Use vi or another editor and create it, containing lines similar to:

```

ctrl_interface=/var/run/wpa_supplicant
ap_scan=2
fast_reauth=1


network={
        ssid="YOURSSID"
        psk=YOURWPAKEY 
        scan_ssid=1
        key_mgmt=WPA-PSK
        proto=WPA
        #pairwise=CCMP TKIP
        pairwise=CCMP
        #group=CCMP TKIP
        group=CCMP
        priority=5
        }

```

Note: YOURWPAKEY is not your WPA passphrase but is created with the command
```

 wpa_passphrase <ssid> [passphrase]

```

After that, please try again.

I checked "your" thread and saw that excellent advice was already given, why don't you just follow that? What I do with my setup is really only useful if you use the integrated wlan card of the D600, but since you've bought an Intel card the route to wireless connectivity should be much easier for you than for me. 
Cheers

> **Ph83drus said:**
> nope.  The wpa_supplicant thing doesn't work for me.

phaedrus@phaedrus-laptop:~$ sudo wpa_supplicant -i wlan0 -Dwext -c /etc/wpa_supplicant/wpa_supplicant.conf -dd &
Initializing interface 'wlan0' conf '/etc/wpa_supplicant/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant/wpa_supplicant.conf' -> '/etc/wpa_supplicant/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant/wpa_supplicant.conf'
Failed to read or parse configuration '/etc/wpa_supplicant/wpa_supplicant.conf'.
Failed to add interface wlan0
Cancelling scan request
Cancelling authentication timeout
[1] 9122
[1]+  Exit 255                sudo wpa_supplicant -i wlan0 -Dwext -c /etc/wpa_supplicant/wpa_supplicant.conf -dd
phaedrus@phaedrus-laptop:~$

---

### Post by Dirk_Gently on 2008-05-23
In case anyone cares, I was able to boil down my 3 scripts into one. After a fresh install of Hardy I found out that I can get my Broadcom 4306 rev. 02 card running with just these lines

```

rmmod b43legacy
rmmod ssb
#modprobe ndiswrapper # loading ndiswrapper 2 times in a row
#rmmod ndiswrapper    # may be necessary, just try for yourself
modprobe ndiswrapper
wpa_supplicant -i wlan0 -Dwext -c /etc/wpa_supplicant/wpa_supplicant.conf -dd &
ip route add default via 192.168.1.1

```

My /etc/network/interfaces is set up according to this guide:

[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)
The default route is still missing after successful association, that's why I set it again manually in the script.


UPDATE: I upgraded to Intrepid Ibex yesterday and this method still works for me. I just used ndiswrapper version 1.53 included with Intrepid which is great, since I had been unsuccessfully trying to compile it with kernel 2.6.27 for weeks.

If this method works for you, please let me know. If it doesn't, send me message and I'll try to help.


Cheers

---

