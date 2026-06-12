---
title: "setting up wifi for static ip on ubuntu 12.04"
date: 2013-10-10
forum: Networking &amp; Wireless
---

### Post by jamesbon on 2013-10-10
I want to setup dhcp and static IP I have 2 lan card, Ubuntu 12.04 and it is a laptop the wireless interface I want to give a static IP and lan to have a dynamic ip how should I go about making changes in /etc/network/interfaces file 
the wlan0 is wireless interface and eth0 is lan card that is what ifconfig reports 


till now I tried 

> 
    auto lo
    iface lo inet static
      address 192.168.1.7
      netmask 255.255.255.0
      gateway 192.168.1.1
      network 192.168.1.0
      broadcast 192.168.1.255
      dns-nameservers 127.0.0.1
      dns-search home.lan
      dns-domain home.lan


and

>  
    auto lo
    iface lo inet loopback
    
auto wlan0
    iface wlan0 inet static
       address 192.168.1.7
       netmask 255.255.255.0
       gateway 192.168.1.1
       network 192.168.1.0
       broadcast 192.168.1.255
       dns-nameservers 127.0.0.1
       dns-search home.lan
       dns-domain home.lan
 

these both seem to have broken one or the other service.

---

### Post by chili555 on 2013-10-10
To connect to a wireless network, you must specify the network and the WPA password. I suggest you try:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.7
netmask 255.255.255.0
gateway 192.168.1.1
wpa-ssid your_network
wpa-psk your_key
dns-nameservers 127.0.0.1
dns-search home.lan
dns-domain home.lan
```Make sure the static IP address is outside the range used for DHCP in the router. Get the system to read the changes:```
sudo ifdown wlan0 && sudo ifup -v wlan0
```See if you connected:```
ping -c3 192.168.1.1

```

---

### Post by jamesbon on 2013-10-11
Well after making changes you suggested I do not think it worked
I get following output
```

hp@kalu:/etc/network$ sudo ifdown wlan0 && sudo ifup -v wlan0
ifdown: interface wlan0 not configured
Configuring interface wlan0=wlan0 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant
wpa_supplicant: wpa-driver nl80211,wext (default)
wpa_supplicant: /sbin/wpa_supplicant -s -B -P /var/run/wpa_supplicant.wlan0.pid -i wlan0 -D nl80211,wext -C /var/run/wpa_supplicant
Starting /sbin/wpa_supplicant...
wpa_supplicant: /sbin/wpa_supplicant daemon failed to start
run-parts: /etc/network/if-pre-up.d/wpasupplicant exited with return code 1
ip addr add 192.168.1.7/255.255.255.0 broadcast +       dev wlan0 label wlan0
RTNETLINK answers: File exists
Failed to bring up wlan0.

```
though network manager itself connected to the wireless network.

just posting the /etc/network/interfaces file
```

auto lo
iface lo inet loopback


auto wlan0
iface wlan0 inet static
address 192.168.1.7
netmask 255.255.255.0
gateway 192.168.1.1
wpa-ssid ssid
wpa-psk ssid_pass
dns-nameservers 127.0.0.1
dns-search home.lan
dns-domain home.lan
~                     
```

---

### Post by chili555 on 2013-10-11
> though network manager itself connected to the wireless network.What?? Are you using manual methods or Network Manager?? You will probably not be successful to mix and match.

---

### Post by p.callan on 2013-12-06
I'm trying to do the same thing here, but can't really get it to work. I've only used Ubuntu for two days so I'd rather stay away from the terminal, although I followed these instructions first (couldn't get it to work).
[https://www.youtube.com/watch?v=6Fqrq6_JNaM](https://www.youtube.com/watch?v=6Fqrq6_JNaM)
I think I messed it up after changing to what is said in this thread.

Now, I run 12.04 LTS on a Lenovo S10e as a webserver (LAMP). I need to set both wlan and lan as static IP 192.168.1.9 (I guess mutually exclusive). This is because I am using wlan now, but will switch to wired lan soon enough. I am very new to servers and have just barely managed a WAMP setup before =)
As it is now, the networking interfaces looks like this (nothing else):

[I]auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.9
netmask 255.255.255.0
gateway 192.168.1.1
wpa-ssid My wlan name
wpa-psk My wpa key
dns-nameservers 127.0.0.1
dns-search home.lan
dns-domain home.lan[/I]

After this I need to setup the new www folder in apache, which is the root of drive M: which I can't figure out either.... :/
Ubuntu is a little tricky for me...

Thanks for your kind help.

I THINK I figured it out now. At least I got the IP I wanted (192.168.1.9).
I still can't figure out how to change the www folder to an external hdd I have connected via USB. The name of the hdd is 'M', and I think the path is /media/M
Is this right? And do I just change the www folder to /media/M in the files named 'default' in the apache folders?

Please help, I need to get this working again.

No, wait. It changed back to 192.168.1.16 sigh.......
Can somebody please reply?

---

### Post by chili555 on 2013-12-06
> **p.callan said:**
> No, wait. It changed back to 192.168.1.16 sigh.......
Can somebody please reply?Is Network Manager running here? Either use manual methods or NM; not both.

---

### Post by p.callan on 2013-12-06
Managed to get it back to the right IP, but I still cannot figure out what to set the folder to. 
I THINK it is /media/M  but then again I don't know which file to edit to enter that path. Different guides say different things so I have edited all of them.
When I enter /media/M I get a forbidden mesage when trying to access the website from another machine. When I change it to just M I get a 404 error.
I can't seem to establish contact with the server... Don't know what to do now.

---

### Post by pbrane on 2013-12-06
after you make changes to /etc/network/interfaces to create a static IP for your interface (wlan0) you should do
[FONT=courier new]sudo ifconfig wlan0 <static IP here>[/FONT]
In your case[FONT=courier new]
sudo ifconfig wlan0 down
sudo ifconfig wlan0 192.168.1.9
[/FONT]
This assigns the static IP to the interface.

As for the www subdirectory in the apache directory you should consider using a soft link. It's easier to change. That way you don't have to change the apache config files.

---

### Post by p.callan on 2013-12-06
Thanks, I did the ifconfig.
Don't know what you mean by a soft link. I have a website on which tons of links point to this server, and the external hdd is setup relative to it. Meaning the whole drive is dedicated to serve the website (the site is hosted on weebly by the way, I have no html-files on the drive, only media files etc). So it's important that the root of the server is the root of the drive. I simply want to migrate from my WAMP-setup to a LAMP-setup, with nothing really changed. I don't know ubuntu though, so this makes everything very complicated for me.

Can someone *please *help me out with this? I have now spent two whole days reading guides and tried to get this to work without success. 
I need to get this settled and done so the website can get back up, and so my students can start using it again. And so that I can start exploring ubuntu's fun sides.

My questions are now, which file is to be edited, and how do I put down the correct path? Is it '/media/M/' or '/media/M' or 'M:'  something else entirely??
Also, are there firewall settings to be made? I have 'Firewall configuration' installed on the server computer.

---

### Post by chili555 on 2013-12-06
I think you should start a new thread asking about server settings. Not everyone knows everything about everything in Ubuntu; at least I don't. The title of your thread asks about static IP. I actually think that's fixed, isn't it?

The only server I ever set up, 119 years ago, the data to be served was in /var/www/html. That's all I know.

---

### Post by Iowan on 2013-12-06
> **chili555 said:**
> I think you should start a new thread asking about server settings.Good advice (as usual).  Our Apache gurus may not be looking in threads about wifi static IP's

---

### Post by p.callan on 2013-12-06
Ok, thanks ;)

---

