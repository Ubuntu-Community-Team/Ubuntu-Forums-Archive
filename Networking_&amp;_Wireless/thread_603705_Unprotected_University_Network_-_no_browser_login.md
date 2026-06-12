---
title: "Unprotected University Network - no browser login"
date: 2007-11-05
forum: Networking &amp; Wireless
---

### Post by speedboy_3 on 2007-11-05
Hi, I've been trying to get my wireless working at school for some time now with no success; time to reach out for some help. I have searched the forum, and wasn't able to resolve my issue.

My university uses a wireless network with multiple access points. The network doesn't have WPA/WEP protection, but once you are connected you have to login to the network through your browser (with windows, this was accomplished by Clean Access Agent that confirmed AV software). With Ubuntu, I can connect to the network (using network manager), but I don't get any browser content or opportunity to login with my university ID.

The university offers a short guide for connecting via Red Hat here: [http://www.usask.ca/its/services/networks/setup_guides/linux.php](http://www.usask.ca/its/services/networks/setup_guides/linux.php)

I have also managed to find a "workaround" for Ubuntu by a cs student at my uni, which I was unable to follow due to lack of experience with Linux - the last time I tried, I ended up with no wireless whatsoever. Here is the content:
> 
-----------------------------------------------------------------------------------------------------------------
# Mount cabinet drive from tcl/tk (/usr/bin/wish) script allowing entry of "NSID" "password" and "mountpoint" 

remember chmod +s /usr/bin/smbmnt and /usr/bin/smbumount first

Hdrive
Rdrive

# Linux wireless config
*Only have it working with Wireless g cards supporting WPA, b cards can theoretically be made to work*

tested with intel wireless card linux native
broadcom (Belkin BMM43xx native linux and ndiswrappered)
install wpasupplicant and wpagui
UBUNTU/XUBUNTU specific

#apt-cache search wpa
wpasupplicant - Client support for WPA and WPA2 (IEE 802.11i)
wpagui  - GUI for wpa_supplicant

apt-get install  wpasupplicant
apt-get install wpagui

use the below /etc/wpasupplicant.conf
wpa_supplicant.conf


put the sh script in users home dir (chmod 755 ./wifi.sh)
wifi.sh
edit the line:
sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf &

Replace wlan0 with (whatever has wifi extensions when you type iwconfig could be ath0 , eth1, wlan...???)
Replace wext with ( wext is a good bet though works with atheros and BCM43xxx)
  hostap = Host AP driver (Intersil Prism2/2.5/3)
  madwifi = MADWIFI 802.11 support (Atheros, etc.)
  atmel = ATMEL AT76C5XXx (USB, PCMCIA)
  wext = Linux wireless extensions (generic)
  ndiswrapper = Linux ndiswrapper
  ipw = Intel ipw2100/2200 driver
  wired = wpa_supplicant wired Ethernet driver
  test = wpa_supplicant test driver

running this script from a launcher on the desktop:
- fires up a console window
- asks for your sudo password (unless you are root <-not a good idea)
-runs wpagui
-runs wpasupplicant
-attaches wpagui to supplicant deamon
-pops up a username and password prompt for your NSID/Password combo
-authenticates you
-then runs dhclient again to get your addreess and gw

finally to get arounde the out of band router  (wifi lan = 172.x.x.x  gw=128.233.x.x)
edit dhclient-script
-------change this-----------------------------------------------------------------
            for router in $new_routers; do

                route add default dev $interface gw $router $metric_arg
            done
-----------------------------------------------------------------------------------

----------to this-------------------------------------------------------------------
            for router in $new_routers; do
#usask
                route add -host $router dev $interface
#usask
                route add default dev $interface gw $router $metric_arg
            done
-----------------------------------------------------------------------------------



(in etc/dhcp3 UBUNTU or in /sbin/ in XUBUNTU)

dhclient-script
---------------------------------------------------------------------------------------------------------

Soo.... does that make enough sense to anyone that they can help a Linux newbie get his study on with some wireless access? Thanks in advance for any time and help!

- I want to add for search purposes that this is for the University of Saskatchewan.

---

### Post by speedboy_3 on 2007-11-05
Alright, after a failed attempt at wicd, I'm back at this script.

Everything seems well until it comes to running the script, wifi.sh; I get a login window, but it closes after about 20 seconds, and I don't know how to run the window without a terminal in the background.

Also, for changing dhclient-script, I don't have such a file in etc/dhcp3

Thanks.

---

### Post by banjo man on 2007-11-06
use the below /etc/wpasupplicant.conf
wpa_supplicant.conf


What is in the script wpa_supplicant.conf?



I also am at a University (IPFW) and we use the wireless 802.1X for the wired resnet...

I've made a script-ish thing to get the wired working, and theoretically, could be used with a wireless connection.. Would just need to change a couple things...

When you attempt to connect to the wireless, do you actually connect (with an IP and everything?)

---

### Post by speedboy_3 on 2007-11-06
wpa_supplicant.conf:
> ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
update_config=0

network={
        ssid="uofs"
        key_mgmt=IEEE8021X
        pairwise=TKIP
        group=TKIP WEP104 WEP40
        eap=PEAP
        phase2="auth=MSCHAPV2"
}


Sorry, I'm new; how do I check my ip in linux?

---

### Post by banjo man on 2007-11-06
Depending on which version of Ubuntu you have, there should be a small icon in the tray in the upper right hand of the screen, next to the time, when you connect, it should changed (like the windows icon does), and/or look like a wireless icon...thing...

Well, right click it and go to connection information...

from the sound of it, your network is a walled garden, until you authenticate it, so,  either this script will help you, or not....

(our university has Linux wifi enabled, and even posts a how to for ubuntu)

that conf file looks very similar to the one I use for my wired...


Ok, I am going to try to simplify that walkthrough...

I have no idea what they are doing here: couldn't even find the binaries they mention...
> -----------------------------------------------------------------------------------------------------------------
# Mount cabinet drive from tcl/tk (/usr/bin/wish) script allowing entry of "NSID" "password" and "mountpoint"

remember chmod +s /usr/bin/smbmnt and /usr/bin/smbumount first

Hdrive
Rdrive

Open a terminal (Applications-->Accessories-->Terminal)

type:

```
apt-get install wpasupplicant
```

 and then run:

```
apt-get install wpagui
```

then, in the terminal, run:

```
sudo gedit wireless.conf
```

put in it:

```
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
update_config=0

network={
ssid="uofs"
key_mgmt=IEEE8021X
pairwise=TKIP
group=TKIP WEP104 WEP40
eap=PEAP
phase2="auth=MSCHAPV2"
}
```

save it and close

in the terminal type:
```

sudo chmod 600 wireless.conf
```

and then

```
sudo chown root:root wireless.conf
```

Now, I would need to see what is in the script they give...

the one they mention here:

> put the sh script in users home dir (chmod 755 ./wifi.sh)
wifi.sh
edit the line:
sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf &

---

### Post by speedboy_3 on 2007-11-14
Hey, thanks a lot for your post!
We actually had a technology week on campus the same week I started these posts, and I have discovered a Linux group here that has a fix online:

> in /etc/dhcp3/dhclient-script UBUNTU or in /sbin/dhclient-script in XUBUNTU and Ubutntu 7.10 change:


for router in $new_routers; do
       route add default dev $interface gw $router $metric_arg
done

to this:

for router in $new_routers; do
       route add -host $router dev $interface
       route add default dev $interface gw $router $metric_arg
done

From: [www.linux4us.usask.ca](www.linux4us.usask.ca)


It works great now; nothing extra was required!
Thanks for your time and help!

---

### Post by banjo man on 2007-11-14
No Problem...

Doesn't seem as like our network as I though...

---

