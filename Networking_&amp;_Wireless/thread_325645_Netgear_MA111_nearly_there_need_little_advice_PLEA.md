---
title: "Netgear MA111 nearly there need little advice PLEASE THANKS!!!"
date: 2006-12-26
forum: Networking &amp; Wireless
---

### Post by Ronni_Mazza on 2006-12-26
First of all i would like to thank this site for helping me with my ubuntu problems as i have used this information to fix my problems.

However :P

I was on these and many other forums looking into the MA111 wireless driver problem that some people are having. I myself am having this problem too!!

I did a few things through ndiswrapper and have my wireless device actually found within the networking section under Administration.

I have successfully entered all the required information (such as SSID, WEP, DHCP) and all seems well. 

This is where it goes wrong

The Wlan1 is down, i enter all info, up it goes about activating it and i set it as the gateway connection.

It thinks and ponders for a while after hitting OK and then after everything closes nothing happens, i cant access the net or ping my router. Any ides of what the problem might be??

Many thanks in advance!!

Ronnie
Perth, West Australia

---

### Post by Crayoneater on 2006-12-26
you should try this:

1. open a terminal
2. type: **sudo ifconfig wlan1 up**
3. type: **sudo iwconfig wlan1 essid xxxxxx**
4. type: **sudo iwconfig wlan1 key xxxxxxx**
5. type: **sudo dhclient wlan1**

(replace xxxx with your information)

you might need to switch step 3 and 4 around, i'm not sure what needs to be done first or if it even matters.

also, make sure that your device actually is wlan1, you can type: **iwconfig **in a terminal and it will display your devices.

anyway, i hope this helps

---

### Post by Ronni_Mazza on 2006-12-26
Hey thanks for the info however everything seems fine untill i do the last command

sudo dhclient wlan1


i get outputs like this:

DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received
No working leases in persistant database - sleeping

Could this be a router problem?

I am runing ubuntu on my laptop and it works fine

One thing i have noticed...

On my desktop there is no network icon at the top with those 2 small computers and no signal strength there too unlike my lappy that has them both.

Im stuck,
Any ideas??

Ronnie
Perth, West Australia

---

### Post by Ronni_Mazza on 2006-12-26
LOL incorrect essid name

haha

Sorry guys when you work at something for so long you seem to lose track of the simplest of things


Thanks

Ronnie

---

