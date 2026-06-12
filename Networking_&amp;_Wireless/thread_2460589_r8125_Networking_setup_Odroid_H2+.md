---
title: "r8125 Networking setup Odroid H2+"
date: 2021-04-14
forum: Networking &amp; Wireless
---

### Post by mrs-selp on 2021-04-14
Hi people, 

i am already on quite a odissey and describe for short what happened: 

I bought a Odroid H2+ to setup a homeserver running nextcloud, i installed Ubuntu Server 20.04 but it needs the Drivers for Realtek r8125. I did install it and unistalled reistalled but it wasnt working as it should. I set it up it was recognized but still couldnt connect to the internet even after this: 

ifconfig enp3s0 up 

It was displayed as UP but couldnt connect to the internet.
 
 I was fiddling around like two days and in the middle of the night i remember doing some more stuff like searching searching searching, and found myself in some config or program and the adapter was up BUT there was something like DISABLED but maybe not exactly maybe also not running or similar. I thought that is strange i ENABLED it, and boom it worked flawlessly. 

I was so proud of myself i am absolutely no administrator or anything. I instantly made a backup and thought it worked but it didnt -.- 

Around a week later my SSD burnt and was just dead not found anymore. I replaced it and learned the backup wasnt there...I should have done it through liveboot as i know it. 

I am stuck here again at the place i was before and cant remember because i didnt take any notes at all..big mistake.

Adapters installed with apt repo, and found with ehttool link is showing up, it is blinking on the deviceport but no connection.

So i am searching for some config or program where i can enable the adapter again. Right now the only way I can access with SSH threw usb internet connection from my phone, that is kind of nasty for configuration. I know it is something super simple I am searching for, it is not /etc/networking or /etc/netplan. Maybe someone has some ideas where to find this configuration i am eager to get the Nextcloud server up even tough there are sure more challenges waiting for me. 

If you think i am not in the appropriate place  to ask this, i am sorry maybe you have some recommendations. I red the Odroid H2+ plus forum but apparently people dont have the same problem as me and it isnt too active too.

Wish you all a nice day and thanks for reading

Mrs-selp

---

### Post by philhughes on 2021-04-15
The drivers for the r8125 are not in the kernel. You need to download the drivers from here:

[https://www.realtek.com/en/component/zoo/category/network-interface-controllers-10-100-1000m-gigabit-ethernet-pci-express-software](https://www.realtek.com/en/component/zoo/category/network-interface-controllers-10-100-1000m-gigabit-ethernet-pci-express-software)

Download the drivers "2.5G Ethernet LINUX driver r8125 for kernel up to 5.6".

This will download a file "r8125-9.005.01.tar.bz2". Extract this file:

```
tar xvjf r8125-9.005.01.tar.bz2
```

This will produce a directory "r8125-9.005.01".

Now install the drivers:

```
cd r8125-9.005.01
sudo ./autorun.sh
```

Note that you must have the package "build-essential" installed, which is not installed by default.

```
sudo apt install build-essential
```

---

### Post by mrs-selp on 2021-04-15
Thanks, sure i know I installed with  all three different methods before already.  And it didnt work even after trying all the different ones and running: 

ifconfig enp3s0 up 

but i remember i edited somewhere from DISABLED to ENABLED or something similar and boom it worked. 

But the SSD burnt. It is so frustrating hanging at a problem I already solved before.

---

### Post by chili555 on 2021-04-15
What is the response to:

```
sudo dhclient enp3s0 
```May we also see;

```
cat /etc/netplan/*.yaml
```

---

### Post by mrs-selp on 2021-04-17
Hi, 

I replied so late cause i couldnt establish the SSH from my phone. I works now(the ssh) but I dont know why. :/

I ran

```
[COLOR=#000000][FONT=&quot]sudo dhclient enp3s0[/FONT][/COLOR][COLOR=#000000]

[/COLOR]
[COLOR=#000000][/COLOR]
```

And it didnt have any output but I realized it assignde a ipv4 adress when running 

```
ip a
```

The 

```
cat /etc/netplan/*.yaml
```

And the output was: 

> 
network:
    ethernets:
        usb0:
            dhcp4: true
    version: 2

Seems for me like the ethernet isnt listed, thats a problem I guess

---

### Post by chili555 on 2021-04-17
> Seems for me like the ethernet isnt listed, thats a problem I guessWell, yes.

Please do:

```
sudo nano /etc/netplan/*.yaml

```
Amend the file to:

```
network:
  version: 2
  ethernets:
    enp3s0:
      dhcp4: yes
```Netplan is very particular about spacing, indentation, etc., so proofread carefully twice. Save (Ctrl+o) and exit (Ctrl+x) the text editor. Follow with:

```
sudo netplan generate
sudo netplan apply

```
Note and post any errors.

Servers are a bit easier to reach with a static IP address. A sample template is here:

```
cat /usr/share/doc/netplan/examples/static.yaml

```

---

### Post by mrs-selp on 2021-04-18
Hi thank you Magicwoman or Man. 

It worked 

I am not sure maybe it would have worked already after the because it already assigned a Ipv4 adress.

[COLOR=#000000]sudo dhclient enp3s0

[/COLOR]

but I had a problem with my wifirepeater that I resolved after doing all the steps.

Anyway I also made this: 

```

network:
    version: 2
    ethernets:
        enp3s0:
            dhcp4: yes
```

and this:

```

sudo netplan generate
sudo netplan apply
```


Worked as a charm! Thanks a lot!!!

I screwed up afterwards when setting up a hidden service for remote connection but I can resolve this myself if I have a screen available.

I am so grateful! 

All the best to all of you I mark this SOLVED.

---

### Post by chili555 on 2021-04-18
> I am not sure maybe it would have worked already after the because it already assigned a Ipv4 adress.

sudo dhclient enp3s0Indeed. However, the dhclient command won't survive a reboot. I assume that what is most convenient for most of us is for the server to get an IP address automagically on boot. That's what netplan is designed to do. 

I'm glad it's working as expected. Have fun!

---

