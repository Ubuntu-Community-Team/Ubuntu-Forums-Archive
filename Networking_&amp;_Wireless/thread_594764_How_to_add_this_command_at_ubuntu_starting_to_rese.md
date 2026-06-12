---
title: "How to add this command at ubuntu starting to reset wireless?"
date: 2007-10-28
forum: Networking &amp; Wireless
---

### Post by tiroxino on 2007-10-28
There are a pair of commands that I make to reset wireless and set up my home connection, and I would like to add them to the ubuntu starting. I think the place to add them is  **/etc/rc.local**, but I'm not sure. Can anyone help me?

Thanks

The commands are:

[B]ifconfig eth1 down
ifconfig eth1 up[/B]

Where can I add them?

---

### Post by ghantoos on 2007-10-28
Did you try adding your configuration in /etc/network/interfaces?

cheers,

ghantoos

---

### Post by kevdog on 2007-10-28
Here is an example of the syntax in the /etc/network/interfaces file:

auto wlan0
iface wlan0 inet dhcp

    pre-up ifconfig wlan0 up
    pre-up ifconfig wlan0 down 
    pre-up ifconfig wlan0 up
     pre-up ifconfig wlan0 down

---

### Post by tiroxino on 2007-10-28
Here is my interfaces:

```
iface eth1 inet static
address 192.168.X.X
netmask 255.255.255.0
gateway 192.168.X.X
wireless-essid WLAN_XX
wireless-key s:XXXXXXXXXXXX

auto eth1
```

Where I must add them?

Thanks in advance

---

### Post by kevdog on 2007-10-28
Sorry try this:

auto eth1
iface eth1 inet static
pre-up ifconfig eth1 down
pre-up ifconfig eth1 up 
address 192.168.X.X
netmask 255.255.255.0
gateway 192.168.X.X
wireless-essid WLAN_XX
wireless-key s:XXXXXXXXXXXX

---

### Post by tiroxino on 2007-10-28
I tried to fix my problem but I couldn't. The problem is that I can't change to roaming wifi when the wifi configuration is set up with my home wifi parameters. In the other hand, if I start Ubuntu with a roaming wifi configuration, I can change to my home wifi configuration.

The only solution I know is to set the roaming wifi manually before shutdown linux, in order to start with that wifi configuration in the next time.

Could you suggest me something to try?

Thank you very much.

---

### Post by kevdog on 2007-10-28
Ok 

You have run into a limitation with network manager.  If you specificy settings in the /etc/network/interfaces file roaming will be disabled.  If you select roaming, all of those settings are not followed.

What exactly do you want to do -- simply cycle up and down the interface at boot, no matter what the connection type (manual vs roaming)?

---

### Post by tiroxino on 2007-10-28
I need to have 2 wifi setups for diferent places: one for home and the other one for work at the university. 
I use roaming at university, where there are several wifi nodes. So, I have 2 profiles in network manager, one for each place, but the one for university is simply an empty configuration with roaming enabled.

The problem: I need to set the university profile (or enable roaming) before going to the university, because if I start the computer at university running the home-wifi-profile, then when I change it to roaming-profile, wifi doesn't works. In that case, I need to restart linux. On the other hand, if I come back home and start the computer with the roaming-profile and then I change it to my home-wifi-profile, wifi works perfect!   ¿?!!

It's a bit strange, but it's the true story. I have Ubuntu 7.04, and this problem come from Ubuntu 6.06. My laptop is an Acer Aspire with Intel PRO-Wireless 2200BG.

Thank you for your interest and help :)

---

### Post by kevdog on 2007-10-28
Other than using the command line and making some scripts for your various network setups, or switching to wicd, I dont know if I can be of much help

---

### Post by tiroxino on 2007-10-28
Don't mind, I appreciate your help.
Thank you very much

---

