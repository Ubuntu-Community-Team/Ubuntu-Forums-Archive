---
title: "How Ubuntu connects to a WPA2 PSK network"
date: 2017-10-14
forum: Networking &amp; Wireless
---

### Post by akr07 on 2017-10-14
Hello folks,
I'm a newbie to this community and this is my first post. If this is a wrong place to post this, kindly direct me.
Ok, so here is my doubt. I would like to know how ubuntu 12(this is the version I'm using as my host machine) or in general a ubuntu machine connects to a WPA2 PSK network when the user selects the network to connect from the Desktop GUI. So far my assumption was any device which connects to a WPA2 Wifi should use wpa_supplicant.

The background of why I would like to get this understanding is, I have Realtek 8192EU chipset based Wifi USB Dongle. Ubuntu 12 doesn't have this driver inbuilt. Hence I downloaded the driver and compiled it, then insmod the driver. After insmod, i connected to dongle and the pop up "Wifi connections available" on the desktop appeared through which i selected the PSK network, i wanted to connect. The connection was established seamlessly as expected. 

Now i disconnected the connection (not the dongle, it is still plugged into the PC) and tried to do this manually via the terminal.
When i do this manually via terminal by using the wpa_supplicant, the connection doesn't seem to get thru. I only observe repeated IOCTL errors being printed on the console.
I was a bit confused on seeming these conflicting behaviors and hence wanted to get a clear picture for experts here. am i missing to do anything at the terminal?

Command at the terminal :

wpa_supplicant -B -i wlan0 -D wext -c /etc/wpa_supplicant.conf

My config file : 
ctrl_interface[COLOR=#666600]=[/COLOR]DIR[COLOR=#666600]=[/COLOR][COLOR=#008800]/var/[/COLOR]run[COLOR=#666600]/[/COLOR]wpa_supplicant GROUP[COLOR=#666600]=[/COLOR]netdev
update_config[COLOR=#666600]=[/COLOR][COLOR=#006666]1[/COLOR]

network[COLOR=#666600]={[/COLOR]
ssid[COLOR=#666600]=[/COLOR][COLOR=#008800]"ASUS"[/COLOR]
psk[COLOR=#666600]=[/COLOR][COLOR=#008800]"password123"[/COLOR]
proto[COLOR=#666600]=[/COLOR]RSN
key_mgmt[COLOR=#666600]=[/COLOR]WPA[COLOR=#666600]-[/COLOR]PSK
pairwise[COLOR=#666600]=[/COLOR]CCMP
[COLOR=#000088]group[/COLOR][COLOR=#666600]=[/COLOR]CCMP
auth_alg[COLOR=#666600]=[/COLOR]OPEN
[COLOR=#666600]}


[/COLOR]

---

### Post by coffeecat on 2017-10-14
Hello, and welcome to the forum.

The programming talk section is about programming languages, so it wasn’t the correct place. I’ve moved this thread to the ***Networking and Wireless*** section for the time being because, although you don’t ask for support so much as ask the question “how does Ubuntu connect?” you are really posing a support question.

The first thing to say is that “Ubuntu 12” is past end of life, although you don’t say whether you mean 12.04 or 12.10. The LTS 12.04 became obsolete in April this year, and the short term support 12.10 in April 2014. It would be irresponsible for anyone to help you get an obsolete version of an operating system, hence vulnerable, connected to the internet, so you need to install a currently supported version of Ubuntu, which would have later versions of drivers. I would suggest the currently-supported LTS versions, either 14.04 or 16.04. 16.04 would be a better idea.

That being said, I believe that your Realtek 8192EU chipset might be problematic in any version of Ubuntu, but that is no reason not to be using a supported version.

Please also read this sticky: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

It might be useful to run the wireless info script, even though you are running an out-of-date version of Ubuntu. At least that will confirm the wireless chipset.

In the meantime, others with experience of Realtek chipsets may have constructive things to add.

---

### Post by akr07 on 2017-10-14
Hello coffeecat

Thanks for your reply. I understand Ubuntu 12.04 LTS has become obsolete in this year April. But as i was saying this is the recommended host environment for our dev board. Hence we are sticking to this. However, we have a 16.04 LTS machine and I'm yet to test this behavior in this machine. I will the update after testing the same.

I'm just curious about to understand the theory behind how ubuntu connects when selected from the GUI desktop and doesn't when tried to connect from the terminal. Whats the difference maker here? Is it like when selected from GUI desktop, wpa_supplicant isn't used at the background to connect to PSK2 Network? Why isn't the same IOCTL issue being faced there?

Also as per the instructions, I will run the wireless script too and post an update here.

---

