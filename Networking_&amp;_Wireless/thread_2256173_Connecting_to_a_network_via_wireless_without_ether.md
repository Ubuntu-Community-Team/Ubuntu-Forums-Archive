---
title: "Connecting to a network via wireless without ethernet"
date: 2014-12-10
forum: Networking &amp; Wireless
---

### Post by Banana937 on 2014-12-10
Obviously if you're connecting to a network wireless it is without ethernet, but I mean I don't have ethernet available to download anything. The network is secured with WPA-2 Personal, my server does have a wireless card, I have the driver disk and a CD/DVD drive but have not installed the drivers yet (I'm not quite sure how). Can someone help me out with this?

---

### Post by Hadaka on 2014-12-10
Hi, depending upon the type of wireless card you have will determine
if there is an available driver template for you to use. The one you have on a CD/CvD
is probably an  x.ex windowows driver and useless for your needs. Let's open a terminal
ctrl/alt/t and then copy in and post back these commands.
```
lspci -nnk | grep -iA3 net
rfkil list all
lsmod | egrep 'wl|b43|80211'
uname -r
cat /etc/issue
```
thanks.

---

### Post by Banana937 on 2014-12-10
> **Hadaka said:**
> Hi, depending upon the type of wireless card you have will determine
if there is an available driver template for you to use. The one you have on a CD/CvD
is probably an  x.ex windowows driver and useless for your needs. Let's open a terminal
ctrl/alt/t and then copy in and post back these commands.
```
lspci -nnk | grep -iA3 net
rfkil list all
lsmod | egrep 'wl|b43|80211'
uname -r
cat /etc/issue
```
thanks.
I'm sorry I couldn't do anything better (like a text post), had to take a picture of the screen. However this is what I got when I used those commands. Did you want me to do them with the driver disc in the disc drive? I can re-do it if so.
[IMG]http://i.imgur.com/DWdXfRG.jpg[/IMG]

---

### Post by chili555 on 2014-12-10
Hadaka wants you to edit your /etc/network/interfaces file with the text editor *nano*. Please see: [http://askubuntu.com/questions/464507/ubuntu-14-04-server-wifi-wpa2-personal](http://askubuntu.com/questions/464507/ubuntu-14-04-server-wifi-wpa2-personal) and also: [http://askubuntu.com/questions/54221/how-to-edit-files-in-a-terminal-with-nano](http://askubuntu.com/questions/54221/how-to-edit-files-in-a-terminal-with-nano)

Of course, substitute your details here.

We now return you to your regularly scheduled guru.

---

### Post by Banana937 on 2014-12-11
> **chili555 said:**
> Hadaka wants you to edit your /etc/network/interfaces file with the text editor *nano*. Please see: [http://askubuntu.com/questions/464507/ubuntu-14-04-server-wifi-wpa2-personal](http://askubuntu.com/questions/464507/ubuntu-14-04-server-wifi-wpa2-personal) and also: [http://askubuntu.com/questions/54221/how-to-edit-files-in-a-terminal-with-nano](http://askubuntu.com/questions/54221/how-to-edit-files-in-a-terminal-with-nano)

Of course, substitute your details here.

We now return you to your regularly scheduled guru.
I followed the steps in that first link (here is my interfaces file now):
[IMG]http://i.imgur.com/5ibPa1f.jpg[/IMG]
obviously with the password and SSID blocked out (not like any of you ****ers know where I live anyway--at least I hope not).

And here's the result of that command:
[IMG]http://i.imgur.com/8QlL416.jpg[/IMG]

---

### Post by chili555 on 2014-12-11
Before we get out the plasma cutter and the 15 lb. sledge, please try a reboot and then show us:```
ifconfig
dmesg | grep wlan
nm-tool
```Also, is your second DNS nameserver 192.168.1.1 reachable from 172.16.0.xx?

Finally, I hope you have a reason to start both ethernet and wireless simultaneously.

---

### Post by Banana937 on 2014-12-11
> **chili555 said:**
> Before we get out the plasma cutter and the 15 lb. sledge, please try a reboot and then show us:```
ifconfig
dmesg | grep wlan
nm-tool
```Also, is your second DNS nameserver 192.168.1.1 reachable from 172.16.0.xx?

Finally, I hope you have a reason to start both ethernet and wireless simultaneously.
I don't know how to network... what are the DNS nameservers even used for? Do those need to be set up properly?

And there's the result of those commands (after I turned off ethernet and restarted again):
[IMG]http://i.imgur.com/Oi5dbYh.jpg[/IMG]

---

### Post by chili555 on 2014-12-12
> what are the DNS nameservers even used for? Do those need to be set up properly?DNS nameservers are used by the system to convert names, ubuntu.com for example, into something the internet understands, numbers; in my example, 91.189.89.115. The nameservers are like gigantic phonebooks, that do the same thing; convert names to numbers. 

It only needs to be configured properly if you expect to successfully access the internet!! Generally, we use two nameservers in case the first one goes down; we have a backup. Also, generally, the router has its own list of nameservers available. Therefore, I suggest you amend your file to:```

auto lo
iface lo inet loopback

#auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet static
address 172.16.0.64
netmask 255.2555.25.0
gateway 172.16.0.1
wpa-essid your_network
wpa-psk your_key
dns-nameservers 8.8.8.8 172.16.0.1
```In your latest screenshot, it appears that you connected perfectly.

May I therefore assume you are all set?

---

