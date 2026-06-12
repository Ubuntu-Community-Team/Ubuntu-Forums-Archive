---
title: "How do I get my Ip number, gateway number and mask number?"
date: 2011-06-21
forum: New to Ubuntu
---

### Post by s1baker on 2011-06-21
Hi, 
In Windows XP there is a command that one can run in a "cmd" window
that will give you your ip number, the mask number and gateway number and other stuff about your internet connection. I think the command is "ipconfig" and "ipconfig /all" to get everything.

Is there a similar command for Ubuntu that one can type into the terminal that will give you the same things?

Thanks

---

### Post by AlphaLexman on 2011-06-21
```
ifconfig
```

---

### Post by nzjethro on 2011-06-21
[Here]("http://ubuntuforums.org/showthread.php?t=76078") is a link to a thread that may help you.

I'm not sure if there is a single command that is equivalent, but this thread has a script that will give you equivalent information.

---

### Post by Gremlinzzz on 2011-06-21
just right click network icon and choose connection information:)

---

### Post by dFlyer on 2011-06-21
> **s1baker said:**
> Hi, 
In Windows XP there is a command that one can run in a "cmd" window
that will give you your ip number, the mask number and gateway number and other stuff about your internet connection. I think the command is "ipconfig" and "ipconfig /all" to get everything.

Is there a similar command for Ubuntu that one can type into the terminal that will give you the same things?

Thanks

You can also use:

ip addr

---

### Post by AlphaLexman on 2011-06-21
Or here is a fancier (function) version

```
	netinfo ()

	{

		echo
		echo -e "--------------- Network Information ---------------"
		/sbin/ifconfig | awk /'inet addr/ {print $2}'
		/sbin/ifconfig | awk /'Bcast/ {print $3}'
		/sbin/ifconfig | awk /'inet addr/ {print $4}'
		/sbin/ifconfig | awk /'HWaddr/ {print $4,$5}'

		MYIP=`lynx -dump -hiddenlinks=ignore -nolist http://checkip.dyndns.org:8245/ | sed '/^$/d; s/^[ ]*//g; s/[ ]*$//g' `

		echo "${MYIP}"
		echo -e "---------------------------------------------------"

	}

```

**EDIT:** You may need to install '**lynx**'
```
sudo apt-get install lynx
```

---

### Post by s1baker on 2011-06-21
Would the "Broadcast Address" that shows up by right clicking the little network icon and selecting "connection information" be what is considered the gateway, or is the gateway the "Default Route"?

---

### Post by crispy_420 on 2011-06-22
I think what is listed as the default route is the same as the gateway, just a different way of saying it. As far as the broadcast address, not sure how to best explain this but here are some reads:

[http://en.wikipedia.org/wiki/Broadcast_address](http://en.wikipedia.org/wiki/Broadcast_address)
[http://learn-networking.com/network-design/how-a-broadcast-address-works](http://learn-networking.com/network-design/how-a-broadcast-address-works)

It is always the last address in the network.

---

### Post by mcduck on 2011-06-22
> **s1baker said:**
> Would the "Broadcast Address" that shows up by right clicking the little network icon and selecting "connection information" be what is considered the gateway, or is the gateway the "Default Route"?

The "Default Route" is same as gateway, "Hardware Address" is same as MAC address and "IP address is, well, IP address. :)

You can also run "*sudo ifconfig -a*" in a terminal, that would be the closest equivalent of running "*ipconfig /a*" on a Windows system.

Broadcast address is used for sending data to all systems on a network instead of just a specific system. And of course to receive such messages as well.

---

### Post by s1baker on 2011-06-22
so what would be the Ubuntu equivalent to these XP commands:

```
ipconfig  /renew_all
ipconfig  /release_all
```

---

### Post by alphacrucis2 on 2011-06-22
> **s1baker said:**
> so what would be the Ubuntu equivalent to these XP commands:

```
ipconfig  /renew_all
ipconfig  /release_all
```


Check out dhclient.

---

### Post by jtarin on 2011-06-22
```
route -n
```caveat...will not give IP number. Got to [whatismyip.com ]("http://www.whatismyip.com/")to see what your IP is from the outside world.

---

