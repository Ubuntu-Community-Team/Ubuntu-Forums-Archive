---
title: "Have to run sudo dhclient everytime, and wireless just won't connect"
date: 2010-07-22
forum: New to Ubuntu
---

### Post by czerdrill on 2010-07-22
I'm not a beginner to ubuntu, but these problems sure make me feel like one haha...I just recently upgraded to 10.04 from 9.04 (which worked perfectly).  Naturally, I ran into networking/wireless issues after the upgrade.  I activated the Broadcom drivers and network manager picks up the networks in the area.  However it won't connect to my home network.  I'll put my password in and itll just stay there for a while and then ask for the password again (the password is definitely correct).  

Also, with wired networking, I have to sudo dhclient everytime I restart my computer.  It won't connect automatically even to wired.  Any idea how to get wireless to work, and/or how to get wired to connect automatically without running the dhclient command? :o

---

### Post by JackNocturne on 2010-07-22
Do you have the **Network Manager Applet** ? Its easy to configure all network-settings from there.

---

### Post by czerdrill on 2010-07-22
Yes the applet is there and running and shows my home network as an available network, but as I mentioned it won't connect to my home network wirelessly, and it wont connect to my wired connection unless I do 

```
sudo dhclient
```

after every restart.  I'm just trying to make it so that the wireless works and/or that wired connects automatically.

---

### Post by d3vi1dog562 on 2010-07-22
I had similar issues... Read a lot of different post and only one worked for my problem. You didn't post very much info on the problem so ill try and remember all the different things i tried.
Try
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install network-manager

then if that doesn't work

sudo NetworkManager
sudo network-manager
sudo etc/init.d/network-manager start
sudo etc/init.d/networking start 



```Sorry thats all I cant think of right now. Let me know if it helps.
Oh and the reason i recommended this is that my nm-applet was messed up on upgrade and couldn't locate my keyring and I had to manually connect my wireless devices.(including dhclient)

---

### Post by czerdrill on 2010-07-22
:( None of those commands did anything.  I'm already on the latest version of network manager, it is running already and it shows the networks in range.  It just won't connect though.  What sort of info do you need from me?  

My wired works fine, provided I run the sudo dhclient after every restart.  My wireless appears to work but doesn't connect to any network...

---

### Post by JackNocturne on 2010-07-22
If all those didn't work,,

Maybe the problem isn't with your computer/laptop?  Maybe the **network** itself?  Try connecting with another computer/laptop and see if the same problem is there.

---

### Post by czerdrill on 2010-07-22
Yeah it works fine on all my computers...in fact on my other laptop running 9.04 I'm able to connect to the network with no issue, as well as on my Windows laptops.  It's definitely some issue with Ubuntu 10.04, but can't figure it out...

---

### Post by d3vi1dog562 on 2010-07-22
Opps i misunderstood there.. that wont help you.. Below is a good idea. Maybe use compat wireless drivers it worked well for me as well.

---

### Post by JackNocturne on 2010-07-22
> **czerdrill said:**
> Yeah it works fine on all my computers...in fact on my other laptop running 9.04 I'm able to connect to the network with no issue, as well as on my Windows laptops.  It's definitely some issue with Ubuntu 10.04, but can't figure it out...


I guess there is a problem upgrading to **ubuntu 10.4** ,the only last thing i recommend is use 
```
lspci
``` in terminal, find your ethernet and wireless driver**(s) **name**(s)**

Find the drivers,download
And re-install them

---

### Post by cwmoser on 2010-07-22
Same thing happened with me.  I have to run ifup eth0 every time I boot up.

This is how I fixed it.

In System -> Preferences -> Startup Applications, press the Add button and enter:
Name:     Network - Start
Command:  ifup  eth0
and then press the SAVE button.

Even though this runs every time my PC boots up, this is not going to work until you set the SETUID bit.  I located the command ifup at /sbin/ifup and then issued the following commands:
sudo chown root /sbin/ifup
sudo chgrp root /sbin/ifup
sudo chmod 4755 /sbin/ifup

The above makes sure the owner and group belong to root, and the third line sets the suid bit so that anytime the command ifup is run, it runs with root privileges.

Carl

---

### Post by czerdrill on 2010-07-22
Ok I guess I will just create a startup script to run sudo dhclient at startup.  Annoying that wireless won't work, but wired is fine.  Thanks for your help guys!

---

### Post by czerdrill on 2010-07-22
> **JackNocturne said:**
> I guess there is a problem upgrading to **ubuntu 10.4** ,the only last thing i recommend is use 
```
lspci
``` in terminal, find your ethernet and wireless driver**(s) **name**(s)**

Find the drivers,download
And re-install them

just tried this and still no go.  Shows my network in the network manager applet, asks me for my password, but won't connect to it...geez this is annoying.   wired works but i guess i'm OCD because i hate not having wireless work when I know it should...

---

### Post by czerdrill on 2010-07-22
Ok well here's a new, weird development lol.  My wireless network is secured, so i tried connecting to an unsecured network that the adapter was picking up in my area and...it worked!  so what the heck is going on...why won't it connect to the secured network but does connect to the unsecured one??

---

### Post by JackNocturne on 2010-07-22
Thats good news. Maybe the to the **secured** one you entered wrong password?

try in terminal if it will work to connect to your wireless network

```
iwconfig eth1 essid [Name of the Access point] channel [Number of channel] key [WEP/WPA pass key]

```and then 
```
dhclient eth1
```

---

### Post by czerdrill on 2010-07-22
Ok tried the first command you suggested and got:

```
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth1 ; Operation not permitted.

```Ideas?

Nevermind...didn't sudo it before running that command...my network has a space in it....is that why?

---

### Post by JackNocturne on 2010-07-22
So what did it say after you ran **sudo** with it?

---

### Post by czerdrill on 2010-07-22
> **JackNocturne said:**
> So what did it say after you ran **sudo** with it?

Error for wireless request "Set Encode" (8B2A) :
    invalid argument MY KEY HERE

but the KEY is absolutely correct, checked it several times and am able to connect with the same key on other laptops

I use WPA if that matters and not WEP

---

### Post by JackNocturne on 2010-07-22
WPA/WEP doesnt matter, i have to say that now i think its beyond my scope:(,im sure **someone will **provide** solution **soon. 

My last suggestions before i give up, try installing the **old driver** that worked for you in Ubuntu 9.04 or try getting the newest driver version for your WLAN

---

### Post by czerdrill on 2010-07-22
> **JackNocturne said:**
> WPA/WEP doesnt matter, i have to say that now i think its beyond my scope:(,im sure **someone will **provide** solution **soon. 

My last suggestions before i give up, try installing the **old driver** that worked for you in Ubuntu 9.04 or try getting the newest driver version for your WLAN

Ok I appreciate your help and patience!  The startup script i made works as far as connecting wired on boot so I don't have to run the command everytime I restart. I'll look around and see if I can figure out the wireless thing somewhere else.  Thanks again!

---

### Post by cavalier911 on 2010-07-22
Make a new user account to see if the problem is local or global.

Thread #4 had your problem,but his solution is too vague.
gnome-keyring has known bugs on upgrade,NetworkManager is locked out of gnome-keyring so it can't get your password. 
The log for NetworkManager is /var/log/daemon.log may be some helpful info there.

---

### Post by czerdrill on 2010-07-22
> **cavalier911 said:**
> Make a new user account to see if the problem is local or global.

Thread #4 had your problem,but his solution is too vague.
gnome-keyring has known bugs on upgrade,NetworkManager is locked out of gnome-keyring so it can't get your password. 
The log for NetworkManager is /var/log/daemon.log may be some helpful info there.

New user account same deal, sees my network doesn't connect after supplying key, but unsecured networks connect fine...

How do I manually enter my key information into network manager?

---

### Post by d3vi1dog562 on 2010-07-27
Questio:
Did you by any chance check the config file to see if dhclient=false ? 
At work right now and not sure where it is but if i find out maybe you can check that, but a start-up script is an easy fix. Maybe use a differnt wireless wrapper? Say compat? It made my non working 3945 work again ;P Let us know progress ;0

---

### Post by abdusamed on 2011-02-27
I also am facing this problem on both eth0 and wlan0. If I don't run sudo dhclient wlan0 periodically, my transfer speed drops like a stone -from 600kb/sc to 30kb/sec!

plz need help

---

### Post by wizard10000 on 2011-02-27
I've found network-manager to be fairly buggy, at least on KDE installations.  I routinely pitch it and install wicd instead.

Be careful, though - some wicd installations have failed to remove all network-manager components, leaving you with broken networking.  If that happens just remove the rest of the network-manager components and networking will come back up  ;)

For wired connections you might consider adding (as root) the following to /etc/network/interfaces - as network-manager isn't required for a wired connection either.

```
auto eth0
iface eth0 inet dhcp
```

---

