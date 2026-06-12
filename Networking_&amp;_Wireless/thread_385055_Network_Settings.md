---
title: "Network Settings"
date: 2007-03-15
forum: Networking &amp; Wireless
---

### Post by pete stahl on 2007-03-15
I’m new to Ubuntu and loaded Dapper on a separate drive that I have on a dual boot. This was easy to do. Now I want to access the internet and while I can if I boot off the XP drive I still haven’t come close with Dapper yet. I have a WMP54G wireless card which seems to give everyone trouble here on a Pentium 4 PC. I also use Firefox as my web program too. I’d like to know what should be set to what in the Network Settings first then push towards instructions as what is need to set the drivers, wireless card, etc. Here is what I have so far and I can’t cut/paste as I can’t access the internet via Dapper.

Network Settings, Connection Tab: Under the Wireless connection it says = The interface ra0 is active.

Network Settings, General Tab: Under Host Settings – Hostname is ps-desktop, Domain name is My Network Name

Network Settings, DNS Tab: Under DNS Servers it has = 68.87.64.146 and 68.87.75.194, Under Search Domains = hsdl.nj.Comcast.net

Network Settings, Hosts Tab: Too many things to type…

Any of this stuff need to be changed first? Any and all help would be appreciated. Still using XP/2000 PC’s until I get this Linux stuff going smoothly. The up side of this learning curve is very slippery!

---

### Post by glenndavy on 2007-03-15
Hi
Firstly  - im not familiar with that card and its quirks... it seems it just works for some people and not others, apparently uses 3 diff chipsets (as im sure you read)... so before delving into that can I get you to open a terminal and type:

```

iwlist ra0 scanning
ifconfig ra0

```

and paste output?

Another approach if you feel like playing (which could prove much simpler) is to use network-manager... its all magic like... makes it easy..

if you run a command called "nm-applet" you should see a new network applet on your menu task bar thingo.

if you right click on that - can you see your wireless network listed? If so click on it and see if it 'magically' solves your problem (might ask your for wep or wpa or whatever  encryption key). If not, we need to drill deeper.

If nm-applet isnt installed (not sure if it is by default)... install network-manager-gnome ( i assume its on the cd you installed with, but i have to admit i dont know)
```

apt-get install network-manager-gnome

```
should do it.

glenn

---

### Post by pete stahl on 2007-03-15
> **glenndavy said:**
> Hi
Firstly  - im not familiar with that card and its quirks... it seems it just works for some people and not others, apparently uses 3 diff chipsets (as im sure you read)... so before delving into that can I get you to open a terminal and type:

```

iwlist ra0 scanning
ifconfig ra0

```

and paste output?

Another approach if you feel like playing (which could prove much simpler) is to use network-manager... its all magic like... makes it easy..

if you run a command called "nm-applet" you should see a new network applet on your menu task bar thingo.

if you right click on that - can you see your wireless network listed? If so click on it and see if it 'magically' solves your problem (might ask your for wep or wpa or whatever  encryption key). If not, we need to drill deeper.

If nm-applet isnt installed (not sure if it is by default)... install network-manager-gnome ( i assume its on the cd you installed with, but i have to admit i dont know)
```

apt-get install network-manager-gnome

```
should do it.

glenn

Glenn, Thanks for the quick reply. I can't cut/paste, I have NO web access with ubuntu yet. I'm really new to Linux stuff so how do i run a command called nm-applet? I'm guessing I put the apt-get command in the Terminal window????

---

### Post by glenndavy on 2007-03-15
hi pete 

yep my bad - didnt occur to me you couldn't cut and paste...

I'll assume you can get a terminal open? If not I think in gnome (i use kde) you can right click on desktop and open terminal?

with the iwlist command above - im wanting to know if you can see your wireless access point listed in the output

in terms of nm-applet... at the terminal, you can just type 
nm-applet (then hit enter)
you'll prob get heaps of output but dont worry about that for now.

The 'apt-get' command is to install it if it isnt already (assuming its on the media you installed from)

lemme know how you go

---

### Post by chili555 on 2007-03-15
This: ```
Network Settings, DNS Tab: Under DNS Servers it has = 68.87.64.146 and 68.87.75.194, Under Search Domains = hsdl.nj.Comcast.net

``` suggests the card has been, or IS connected. Unless you went to great effort and detective work, the only way for DNS servers to get populated is if your router connected and handed them out. Sorta like lipstick on your collar...

While you may not be able to copy and paste (some guys do it with a USB key; create a text file, copy to USB, reboot to XP, paste to forum), a summary will help. "No scan results", etc.

Please perform the following commands in a terminal and let us hear your summary of the result:```
iwlist ra0 scanning
ifconfig ra0
ping -c3 www.google.com
```Forget about apt-get until we get you connected.

---

### Post by pete stahl on 2007-03-15
When I run iwlist this is what is in the first section, I'm type this in...

Cell 01 - Address: 00:14:BF:83:95:3E
            ESSID:"Techspec56"
            Ecryption key:on
            Channel: 11
            Quality:0/100  Signal level:-26dBm  noise level: -193dBm

Typed nm-applet in the Teminal (Have to go to Application/Accessories/Terminal no right click menu with Terminal on it) reply was: bash: nm-applet: command not found

Typed in the apt-get command and get this: E:  Could not open lock file /var/lib/dpkg/lock - open (Open permission denied)

Sorry you replied yet Glenn?

---

### Post by glenndavy on 2007-03-15
i assume he'd just copied the DNS settings from his windows setup out of sheer frustration thinking that that would hold the magic key

for my own edification chris... is nm-applet installed by default?

---

### Post by glenndavy on 2007-03-15
> Sorry you replied yet Glenn?
nah... all part of the fun

> ESSID:"Techspec56"
ok so it seems that the card is working and can see your access point

lets see if you got an ip address... can you do 
```

ifconfig ra0

``` 
and see if you can see in ip address in output?

the access point has encryption, so Im guessing you prob dont, but lets see anyway

do you know what type of encryption you've got?

you can do 
```

sudo iwconfig ra0 key {put your hex key here}

```

---

### Post by pete stahl on 2007-03-15
Took me a while to get this, had to track down a pen drive first then load open office on my XP machine. Glenn I'll get to you other request shortly. 

ps@ps-desktop:~$ iwlist ra0 scanning
ra0       Scan completed :
          Cell 01 - Address: 00:14:BF:83:95:3E
                    Mode:Managed
                    ESSID:"Techspec56"
                    Encryption key:on
                    Channel:11
                    Quality:0/100  Signal level:-26 dBm  Noise level:-193 dBm
          Cell 02 - Address: 00:12:0E:1A:87:5D
                    Mode:Managed
                    ESSID:"06Z405837480"
                    Encryption key:on
                    Channel:6
                    Quality:0/100  Signal level:-84 dBm  Noise level:-192 dBm

ps@ps-desktop:~$ ifconfig ra0
ra0       Link encap:Ethernet  HWaddr 00:0C:41:6D:A6:10
          inet6 addr: fe80::20c:41ff:fe6d:a610/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3566 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:142640 (139.2 KiB)
          Interrupt:201

ps@ps-desktop:~$ ping -c3 [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)
ps@ps-desktop:~$

---

### Post by chili555 on 2007-03-15
I would suggest: ```
sudo iwconfig ra0 essid Techspec56  <--if that's the one you want to connect
sudo iwconfig key <your_key_here>
sudo dhclient ra0
```and see if you connect.

I am troubled by this: ```
ps@ps-desktop:~$ iwlist ra0 scanning
ra0 Scan completed :
Cell 01 - Address: 00:14:BF:83:95:3E
Mode:**Managed**
ESSID:"Techspec56"
Encryption key: on
Channel:11
Quality:0/100 Signal level:-26 dBm Noise level:-193 dBm
Cell 02 - Address: 00:12:0E:1A:87:5D
Mode:**Managed**
ESSID:"06Z405837480"
Encryption key: on
Channel:6
Quality:0/100 Signal level:-84 dBm Noise level:-192 dBm
```
Every wireless router I've connected to, including the one I am posting from, shows up in scanning as **Master**. You might check in the administration pages for your router to see if any settings are awry, Please disregard if you readily connect with that other operating system...what's it's name? I forget.

---

### Post by pete stahl on 2007-03-15
> **glenndavy said:**
> nah... all part of the fun


ok so it seems that the card is working and can see your access point

lets see if you got an ip address... can you do 
```

ifconfig ra0

``` 
and see if you can see in ip address in output?

the access point has encryption, so Im guessing you prob dont, but lets see anyway

do you know what type of encryption you've got?

you can do 
```

sudo iwconfig ra0 key {put your hex key here}

```

Glenn, The type of encryption I have is WPA Personal. Don't know the hex key, how can I find this. Also here's what I got from running ifconfig ra0. Thanks again for your help.

ps@ps-desktop:~$ ifconfig ra0
ra0       Link encap:Ethernet  HWaddr 00:0C:41:6D:A6:10
          inet6 addr: fe80::20c:41ff:fe6d:a610/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19673 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:786920 (768.4 KiB)
          Interrupt:193 Base address:0xc000

---

### Post by pete stahl on 2007-03-15
> **chili555 said:**
> I would suggest: ```
sudo iwconfig ra0 essid Techspec56  <--if that's the one you want to connect
sudo iwconfig key <your_key_here>
sudo dhclient ra0
```and see if you connect.

I am troubled by this: ```
ps@ps-desktop:~$ iwlist ra0 scanning
ra0 Scan completed :
Cell 01 - Address: 00:14:BF:83:95:3E
Mode:**Managed**
ESSID:"Techspec56"
Encryption key: on
Channel:11
Quality:0/100 Signal level:-26 dBm Noise level:-193 dBm
Cell 02 - Address: 00:12:0E:1A:87:5D
Mode:**Managed**
ESSID:"06Z405837480"
Encryption key: on
Channel:6
Quality:0/100 Signal level:-84 dBm Noise level:-192 dBm
```
Every wireless router I've connected to, including the one I am posting from, shows up in scanning as **Master**. You might check in the administration pages for your router to see if any settings are awry, Please disregard if you readily connect with that other operating system...what's it's name? I forget.

sudo iwconfig ra0 essid Techspec56  <--if that's the one you want to connect
Typed this and hit return and just got the prompt back
sudo iwconfig key <your_key_here>
What key do I put in there???
sudo dhclient ra0

Here's what I got from the terminal. I don't know what Router settings to look for. I haven't had any trouble connecting to it except for via ubuntu.

ps@ps-desktop:~$ sudo iwconfig ra0 essid Techspec56
ps@ps-desktop:~$ sudo dhclient ra0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/ra0/00:0c:41:6d:a6:10
Sending on   LPF/ra0/00:0c:41:6d:a6:10
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
ps@ps-desktop:~$

---

### Post by chili555 on 2007-03-15
> The type of encryption I have is WPA Personal You can find the keys, etc. in the administration pages of the router. Then search the forum for WPA. The gurus here have a few posts that will help you.

---

### Post by pete stahl on 2007-03-15
> **chili555 said:**
> You can find the keys, etc. in the administration pages of the router. Then search the forum for WPA. The gurus here have a few posts that will help you.

Can you give me links to posts you talk about? I can get to my router pages but don't know what key you are referring to. Can you give me a hint, how many numbers would it be?

---

### Post by chili555 on 2007-03-15
[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

Wish I could be more help, but WPA is not my specialty. I am a plumber and you need an electrician.

---

### Post by pete stahl on 2007-03-15
Any idea how to install Network Manager. I get a error message when I tried 

Sudo apt-get install network-manager-gnome

error message is: E: Couldn't find package network-manager-gnome

---

### Post by pete stahl on 2007-03-15
Can I even use Network Manager with Dapper?

---

### Post by chili555 on 2007-03-15
Yes, it's probably on your install CD. Plop your install CD in the drive and do: ```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install network-manager-gnome
```Let us know.

---

### Post by glenndavy on 2007-03-15
question 1...
there are 2 routers in your vacinity...
"Techspec56 " and  "06Z405837480"

Which of these do you physically have control over? and which one do you 'connect' with when in windows?

question 2...
To connect to this in windows, you had to enter a 'key'... probably a string of letters and characters... doesnt matter if your using 'nm-applet' your pda, windows, or a mac... this had to be entered. Where did you get that key from? If you dont know or cant remember, or cant ask someone, have a poke around in the windows settings - Im not sure what you'll find? If the answer to question 1 is 'yes i own the router', then you'll be able to use windows to look at the routers admin pages and take a look at the keys? These keys are generated from a pass phrase, so if you cant find the key, but know the phrase - then we might be able to get somewhere with that.

question 3
whats the output of 

```

dpkg -l |grep network-man
dpkg -l| grep wpa

```

---

