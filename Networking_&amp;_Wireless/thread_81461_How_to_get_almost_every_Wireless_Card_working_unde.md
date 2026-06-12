---
title: "How to get almost every Wireless Card working under Ubuntu 5.10"
date: 2005-10-24
forum: Networking &amp; Wireless
---

### Post by vcelis on 2005-10-24
- Get ndiswrapper-utils by typing "sudo apt-get install ndiswrapper-utils" in a terminal.
  Give the root password when necessary.
- Get the Microsoft Windows drivers. Copy the .inf and .sys file. Paste these into a folder. 
  (eg. /home/<USERNAME>/Desktop/driver/)
- Open a terminal
- Type the following commands:
    $ cd Desktop/driver/
    $ sudo ndiswrapper -i <name>.inf
    $ sudo modprobe ndiswrapper

Notice that you have to repeat the last step whenever you want to use your device within a session.

If there's any problem, please contact me (vincent.celis@oc-productions.be) or post a reply.

---

### Post by passonno on 2005-10-24
My main problem with this advice, is, of course, the question: How am I to apt-get anything if I don't have any network access to begin with?

---

### Post by Kyral on 2005-10-24
In my case (well, I forgot to compile the driver into my kernel, but thats my fault) I happened to also have a "land-line" (Ethernet) conn available. But you could also download the package from packages.ubuntu.com (With a computer with Internet of course) and burn them to a CD and install them from there

---

### Post by JeffBlouin on 2005-10-24
This work fine with me but is there any way to have the device always install or do i have to modprobe everytime i want to go wireless

Thanks

---

### Post by vcelis on 2005-10-24
[QUOTE=passonno]My main problem with this advice, is, of course, the question: How am I to apt-get anything if I don't have any network access to begin with?[/QUOTE]

The command "sudo apt-get install ndiswrapper-utils" will ask to insert the Ubuntu 5.10 CD. The utility will be installed from the ndiswrapper-utils on the CD.

---

### Post by mjkelly on 2005-10-24
I just booked into this hotel with only wireless ethernet so i went out and bought a wireless NIC for 50 bucks. (is that reasonable or way too much? cuz i know normal NICs are like 5 bucks...??)

Well anyway i cant get it working and i cant get this ndiswrapper file onto my linux partition. I dont have any blank CDs to burn and when i mount the windows partition (/dev/hda1 on /windows) i cant even view it because it says permission denied?? So... that brings me to the problem. Can i transfer a file from my windows partition to my linux partition?

Also when i go into networking, the wireless card is listed. When i go to preferences to configure it, it asks for an IP or if its DHCP and all... this wont work without the driver right? Like i need to get that ndiswrapper working right? I dont have any other linux driver and its an Airlink 101 card but on windows it installed as a texas instrument card.

---

### Post by Manveru913 on 2005-10-24
When i type modprobe ndiswrapper, it fails and says "operation not permitted". im fairly positive i have root privelages. wireless card is a d link dwl g510.

---

### Post by The Mekon on 2005-10-24
[QUOTE=Manveru913]When i type modprobe ndiswrapper, it fails and says "operation not permitted". im fairly positive i have root privelages. wireless card is a d link dwl g510.[/QUOTE]

I believe that the D-Link G510 should just work in Breezy.  I used nidiswrapper on Hoary but I am not using it on Breezy and if you can read this it is certainly working (without WEP).

Brian

---

### Post by Manveru913 on 2005-10-24
It doesnt seem to have been detected when i installed ubuntu. there are no lights flashing on the card, and theres no wireless option in the networking utility.

---

### Post by pau on 2005-10-25
> Get the Microsoft Windows drivers.

I never touched the w$ cds... or whatever... Where are these drivers to be found?

---

### Post by knappen on 2005-10-25
[QUOTE=Manveru913]When i type modprobe ndiswrapper, it fails and says "operation not permitted". im fairly positive i have root privelages. wireless card is a d link dwl g510.[/QUOTE]

Try

sudo modprobe ndiswrapper

---

### Post by TimonVO on 2005-10-25
Nice post vcelis. I think ndiswrapper is a very efficient tool and It's beautiful to see someone posting something like this on the forums.
For people who can't get ndiswrapper working. Try Linuxant Driverloader, search google for it.

---

### Post by bull8042 on 2005-10-25
[QUOTE=TimonVO]Nice post vcelis. I think ndiswrapper is a very efficient tool and It's beautiful to see someone posting something like this on the forums.
For people who can't get ndiswrapper working. Try Linuxant Driverloader, search google for it.[/QUOTE]

The Linuxant worked very well when I tried it, but keep in mind that it is $20 for a permanent license. For me, it was worth the extra effort to get ndiswrapper working.
Then again, I am cheap!

---

### Post by mxyzptlk on 2005-10-25
vcelis i did all you describe here but nothing happens.

I reboot the system and it sent a message like this

files already installed but nothing.
i checked the networ devices and it only detects the internal port but the usb wireless adapter no .

I have the driver and it has one for linux but i dont know how to install it

any suggestion

---

### Post by vcelis on 2005-10-25
[QUOTE=mjkelly]Well anyway i cant get it working and i cant get this ndiswrapper file onto my linux partition. I dont have any blank CDs to burn and when i mount the windows partition (/dev/hda1 on /windows) i cant even view it because it says permission denied?? So... that brings me to the problem. Can i transfer a file from my windows partition to my linux partition?[/QUOTE]

Use "sudo nautilus /windows/" to get the permission to view your windows partition.


[QUOTE=mjkelly]Also when i go into networking, the wireless card is listed. When i go to preferences to configure it, it asks for an IP or if its DHCP and all... this wont work without the driver right? Like i need to get that ndiswrapper working right? I dont have any other linux driver and its an Airlink 101 card but on windows it installed as a texas instrument card.[/QUOTE]

When your wireless card is listed in the network-admin your card is suported by Ubuntu 5.10.

Just fill in the Network ESSID, the Key type and WEP key (when needed), and set the configuration to DHCP when the hotspot is configured for DHCP in the hotel.

---

### Post by vcelis on 2005-10-25
[QUOTE=pau]I never touched the w$ cds... or whatever... Where are these drivers to be found?[/QUOTE]

Search for the .inf and .sys file on the device CD.

---

### Post by vcelis on 2005-10-25
[QUOTE=mxyzptlk]vcelis i did all you describe here but nothing happens.

I reboot the system and it sent a message like this

files already installed but nothing.
i checked the networ devices and it only detects the internal port but the usb wireless adapter no .

I have the driver and it has one for linux but i dont know how to install it

any suggestion[/QUOTE]

What's the model number of your wireless card? Is the card listed in the Network tool? (system-->Administration-->Networking or use the "gksudo network-admin" command)

---

### Post by Dajazzz on 2005-10-25
oke the power led of the pcmcia card is burning.
but how can I start some program to connect to my wifi?

its an ASUS 103b chipset is bcm4306.
I also don't see the card in networkadapters.

what next?

---

### Post by vcelis on 2005-10-25
[QUOTE=Dajazzz]oke the power led of the pcmcia card is burning.
but how can I start some program to connect to my wifi?

its an ASUS 103b chipset is bcm4306.
I also don't see the card in networkadapters.

what next?[/QUOTE]

You can use the Network tool to configure your wireless connection and connect with the network or you can follow these steps:

- open a terminal
- sudo iwlist wlan0 scan (look for your access point in the list)
- sudo iwconfig wlan0 channel YOUR_CHANNEL essid YOUR_ESSID mode Managed (YOUR_CHANNEL and YOUR_ESSID should come from the iwlist)
- sudo ifup wlan0

---

### Post by Dajazzz on 2005-10-25
oke I managed to activate the card (wlan0)

but now How do I need to setup my Acces Point?
WPA/WEP 64kb/128kb? hexadecimal or ascii

I have set up some things in the network tool

when I type iwlist wlan 0 scan I get

wlan0   scan completed
Cell 01 Address (mac-address
ESSID: "DAJAZZZ"
protocol:IEEE 802.11b
mode: Managed
frequency 2.412GHz (channel 1)
Quality 0/100 signal level: -38dBm Noise level: -256dBm
encryption key: on
bit rate1 ......
bit rate2 ......
.....
[SIZE="1"]
I think he doesnt find my AP because when I switch it off it shows the same results
in the config tool I inserted the name for SSID so thats how he knows I think[/SIZE]

Ow I did it again and then it shows no scan results. Sorry 

Already thanks for all help!

---

### Post by vcelis on 2005-10-25
[QUOTE=Dajazzz]oke I managed to activate the card (wlan0)

but now How do I need to setup my Acces Point?
WPA/WEP 64kb/128kb? hexadecimal or ascii

I have set up some things in the network tool

when I type iwlist wlan 0 scan I get

wlan0   scan completed
Cell 01 Address (mac-address
ESSID: "DAJAZZZ"
protocol:IEEE 802.11b
mode: Managed
frequency 2.412GHz (channel 1)
Quality 0/100 signal level: -38dBm Noise level: -256dBm
encryption key: on
bit rate1 ......
bit rate2 ......
.....

I think he doesnt find my AP because when I switch it off it shows the same results

in the config tool I inserted the name for SSID so thats how he knows I think

Already thanks for all help![/QUOTE]


Try to fill in all the necessary information about you're connection in the Network tool. You can click activate or use "sudo ifup wlan0"

Ignore the "Quality 0/100 signal level"

---

### Post by Dajazzz on 2005-10-25
Oke so i am connected
result of ifup is:
interface wlan0 already configured.

but I cannot acces internet or ping to my router.
when I try to ping with PING 10.0.0.2 (thats my router)
I get NETWORK IS UNREACHABLE

what can I do?

---

### Post by vcelis on 2005-10-25
[QUOTE=Dajazzz]Oke so i am connected
result of ifup is:
interface wlan0 already configured.

but I cannot acces internet or ping to my router.

what can I do?[/QUOTE]

Follow these steps:

- open a terminal
- sudo ifdown wlan0
- open the network tool and fill in the necessary information
- use the activate button in the network tool or use "sudo ifup wlan0"

---

### Post by Dajazzz on 2005-10-25
[QUOTE=vcelis]Follow these steps:

- open a terminal
- sudo ifdown wlan0
- open the network tool and fill in the necessary information
- use the activate button in the network tool or use "sudo ifup wlan0"[/QUOTE]

ifdown shows:
killed old client process, removed PID file
internet systems consortium DHCP client V3.0.2
copyright 2004 internet systems consortium
all rights reserved
for info ........

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
listning on LPF/wlan0/00.0e.a6......
sending on LPF/wlan0/oo.oe.a6.......
sending on socket/fallback

After this I have only the looback interface, vmnet1 and vmnet 8 (from vmware)
so my ethernet AND wlan is not shown in this list anymore.....

after this I just typed sudo ifup wlan0 and get this

error for wireless rezuest "set encode (8B2A)
   set failed on device wlan0 ; ivalid argument.
there is already a pid file /var/run/dhclient.wlan0.pid with pid 0
internet systems consortium DHCP client v3.0.2
copyright.........

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
listning on LPF/wlan0/00.00.xx.....
sending on LPF/wlan0/.......
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
No DHCP OFFERS received.
no working leasis in persistent database - sleeping.

---

### Post by vcelis on 2005-10-25
[QUOTE=Dajazzz]ifdown shows:
killed old client process, removed PID file
internet systems consortium DHCP client V3.0.2
copyright 2004 internet systems consortium
all rights reserved
for info ........

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
listning on LPF/wlan0/00.0e.a6......
sending on LPF/wlan0/oo.oe.a6.......
sending on socket/fallback

After this I have only the looback interface, vmnet1 and vmnet 8 (from vmware)
so my ethernet AND wlan is not shown in this list anymore.....[/QUOTE]


Try to modprobe it again with "sudo modprobe ndiswrapper".

Open the network tool and if your card is listed, select the card, click on properties, fill in the information, click on OK and click on activate.

Let me know the result of this.

---

### Post by Dajazzz on 2005-10-25
[QUOTE=vcelis]Try to modprobe it again with "sudo modprobe ndiswrapper".

Open the network tool and if your card is listed, select the card, click on properties, fill in the information, click on OK and click on activate.

Let me know the result of this.[/QUOTE]

First I tried to switch off DHCP. to set a static IP (10.0.0.3)
then I wrote sudo ifdown wlan0 and sudo ifup wlan0
result:
SET failed on device wlan0 ; invalid argument

sudo modprobe ndiswrapper
result:
same as first time but now signal level = -45dBm

now i can sellect wlan0 again in the network icon in the upper right screen

I try to ping to my router (10.0.0.2)
result:
PING 10.0.0.2 (10.0.0.2) 56(84) bytes of date
from 10.0.0.3 icmp_sec=2 Destination host unreachable
......3
......4
......5
100% packet loss

so now I dont get the network unreachable error anymore. 

I try to ping to my ASUS WL330 G Accespoint (192.168.1.1)
result:

100% packet loss

---

### Post by Dajazzz on 2005-10-25
I have used as settings for my AP
SSID DAJAZZZ
response to SSID request
channel 1
operation mode mixed
transmit rate atuo
preamble auto
authentication mode shared key
Encryption  WEP 128Bits
Passphrase abcdef

and in the interface properties of ubuntu
device wlan0
activate
ESSID DAJAZZZ
keytype HEX
WEP key abcdef
conf static IP
IP 10.0.0.3
sub 255.255.255.0
gate 10.0.0.2

---

### Post by vcelis on 2005-10-25
[QUOTE=Dajazzz]I have used as settings for my AP
SSID DAJAZZZ
response to SSID request
channel 1
operation mode mixed
transmit rate atuo
preamble auto
authentication mode shared key
Encryption  WEP 128Bits
Passphrase abcdef

and in the interface properties of ubuntu
device wlan0
activate
ESSID DAJAZZZ
keytype HEX
WEP key abcdef
conf static IP
IP 10.0.0.3
sub 255.255.255.0
gate 10.0.0.2[/QUOTE]

10.0.0.3??

Try to activate DHCP in your AP and try to connect with DHCP.

---

### Post by Dajazzz on 2005-10-25
[QUOTE=vcelis]10.0.0.3??

Try to activate DHCP in your AP and try to connect with DHCP.[/QUOTE]

my AP is in bridge mode my ADSL modem/router is setup as DHCP

Now i set ip to DHCP in properties of wlan0
takes a lot of time..... 

in that time I setup my other laptop (windows xp)
to use the same AP and same WEP and I connect and I get an IP from my router. 10.0.0.82 So the AP and router are working fine. (always good to check)

in network tools I see that I only have a IPv6 and not an IPv4 (when I enterd a static one there was dislpayed ipv4 10.0.0.3.

after down and up wlan 0 I get NO DHCP found

---

### Post by Dajazzz on 2005-10-25
and from the ping answer is Network is unreachable

so I will put my ip back on static.

But I have to go to work tomorrow.... 
Hope to chat with you again soon. You've been already a great help.
please post any tips that you know (or someone else ofcourse also)

---

### Post by vcelis on 2005-10-25
[QUOTE=Dajazzz]my AP is in bridge mode my ADSL modem/router is setup as DHCP

Now i set ip to DHCP in properties of wlan0
takes a lot of time..... 

in that time I setup my other laptop (windows xp)
to use the same AP and same WEP and I connect and I get an IP from my router. 10.0.0.82 So the AP and router are working fine. (always good to check)

in network tools I see that I only have a IPv6 and not an IPv4 (when I enterd a static one there was dislpayed ipv4 10.0.0.3.

after down and up wlan 0 I get NO DHCP found[/QUOTE]

Hmm, You can try this:

Disable the WEP key in your AP.
Configure your card for DHCP without the WEP Key.
Ensure the "Enable this connection" is checked.

NOTE: DO NOT ADD ANYTHING IN THE HOSTS TAB!

Try to connect to your AP with the activate button or with Sudo ifup wlan0.


I'm very tired and tomorrow is a school day (yes I go to school, I'm 15 ;))

If there's any progress, mail it to [email]vincent.celis@oc-productions.be[/email].

Greetz from Belgium

---

### Post by Manveru913 on 2005-10-25
> Try

sudo modprobe ndiswrapper

tried that, still get the same error, "Operation not permitted".
my original post was back on the first page, just so you all know im not hijacking this thread.

---

### Post by vcelis on 2005-10-25
[QUOTE=Manveru913]tried that, still get the same error, "Operation not permitted".
my original post was back on the first page, just so you all know im not hijacking this thread.[/QUOTE]

Try this:

- open a terminal
- type the command "su"
- Give the root password when necessary
- type the command "modprobe ndiswrapper"

I really go to bed now, bye

---

### Post by Manveru913 on 2005-10-25
yea ive already tried all that before: 
modeprobe ndiswrapper,
sudo modprobe ndiswrapper,
neither work.
ive had root privelages, still doesnt work.

edit: ok, does ndiswrapper come preinstalled on ubuntu? cause ive read that the problem may be because two versions of ndiswrapper are installed. if this is in fact the case, how would i go about uninstalling one/both of them?

---

### Post by mxyzptlk on 2005-10-25
root@ubuntu:~ # ndiswrapper -l
Installed ndis drivers:
ainu58  driver present, hardware present
ainu58.sys      invalid driver!
ainu58x.sys     invalid driver!
atmelwlandriver-ss-20030522.tar.gz      invalid driver!
aynu58  invalid driver!


so none of the windows drivers work at all
it seems that in the beggining it worked with the first ainu58 it says hardware present but now not

---

### Post by carlosqueso on 2005-10-25
I set up ndiswrapper as described in this thread, and my card shows up, but it won't connect to the internet, and makes my keyboard all weird, anyone have any ideas

The relevant lspci entry is:
0000:02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)

ndiswrapper -l yeilds:
Installed ndis drivers:
netr33x driver present, hardware present

---

### Post by carlosqueso on 2005-10-26
*bump*

---

### Post by Copter on 2005-10-26
hi!

ive got some problems with configuring my wlan card. i used ndiswrapper as you said with the same drivers that win xp uses. when i type iwconfig i see wlan0 card present but all its parameters are set to default / not present. when i run kde gui network tool i see that wlan0 is disabled. when i click enable it pops up the box with 'configuring ...' text. after a second or two wlan0 flashes for a moment (enable) and it goes to disable mode again.

what can i do? maybe some handy console settings? or maybe i have to write all network settings to _some_ file (please post which one)? i had similar problems with cable (eth0) lan card. i had to add 'eth0 inet dhcp' to /etc/interfaces (or something like that (using xp atm)) and reboot the system with lan cable sticked to my computer. if i run the system without the cable i could not (or dont know how to) change anything.

any ideas?

(sorry for such newby post here... im despered... been forced to use xp again ;( )

btw. my configuration

LG GS50 laptop, Proxim 842x (Orinoco) [HermesII chip] **USB** 802.11b wifi card

copter :]

---

### Post by Dajazzz on 2005-10-26
> **vcelis]Hmm, You can try this:

Disable the WEP key in your AP.
Configure your card for DHCP without the WEP Key.
Ensure the "Enable this connection" is checked.

NOTE: DO NOT ADD ANYTHING IN THE HOSTS TAB!

Try to connect to your AP with the activate button or with Sudo ifup wlan0.


I'm very tired and tomorrow is a school day (yes I go to school, I'm 15  said:**
> vincent.celis@oc-productions.be[/email].

Greetz from Belgium

Hi vincent! (ik spreek Nederlands,, heb je msn?)

Oke a new day new changes,,,,
I found out that if I dont put a static IP address I can NOT ping.
When I ping with DHCP to my router (10.0.0.2 
-$ ping 10.0.0.2
connect: Network is untreachable

When I ping with a static IP (10.0.0.40) I get this
-$ ping 10.0.0.2
PING 10.0.0.2 (10.0.0.2) 56(84) bytes of data
From 10.0.0.40 icmp_sec=2 Destination Host Unreachable.
100% packet loss

(Encryption key:off)

---

### Post by OneSeventeen on 2005-10-26
I have set up ndiswrappers as described here, and the strange thing is, when I go to set up the wireless network (clicked the network icon, clicked configure, selected wireless adapter, clicked properties.... sounds like a mac/windows process, huh? [SIZE="1"]click click click[/SIZE]) and when I click the drop-down menu for network ID, it shows my wireless network and a few others in the neighbourhood!!  This proves the wireless card is doing *something*

Now, my problem is when I connect, it still doesn't do anything!
I can't browse the web, and I can't see any network drives or anything...

I'm using a HP zv6000 laptop, and have the same drivers I used with 5.04 (which worked).


also, this should make it so you don't have to modprobe everytime, shouldn't it?:
```

sudo echo "ndiswrapper" >> /etc/modules

```
(**heavy** emphasis on the ">>" **not** ">", must use two or it will clear out your modules file)

---

### Post by OneSeventeen on 2005-10-26
**UPDATE**
In order to get my wireless adapter to work, I hit caps-lock, to be sure my WEP key was all caps (since my WEP key at home is all caps... not sure if it is case sensitive) but the most important thing is that I switched from ASCII to HEXIDECIMAL in the wireless configuration window.

The only thing I can't do yet is connect to an unsecured network.  Is there something special I have to do?

---

### Post by carlosqueso on 2005-10-26
I have the same thing on a ze4200....does yours make your keyboard wierd too (IRQ issues maybe?)

---

### Post by Dajazzz on 2005-10-27
[QUOTE=carlosqueso]I have the same thing on a ze4200....does yours make your keyboard wierd too (IRQ issues maybe?)[/QUOTE]

is the key the same as the passprase?
like when I can set up my AP I enter abcdef as key and below there are 4 lines which show. A8D3DCD............
so do I need to but the passprase or the A8D3............

gr jas

---

### Post by carlosqueso on 2005-10-27
That's the A8D3DCD...but make sure the drop-down says "Hexidecmal" instead or "ASCII", but mine's unsecured...so I guess we have different issues.

---

### Post by Dajazzz on 2005-10-28
I gave up.....
I just can not get it working.
I can see my SSID, but can not use internet.
with or without a key....

I will just use a cable. Its pissing me 2 much.....

---

### Post by indymcse on 2005-10-28
okay I have the driver installed and I've configured a SSID and everything.  When I do iwconfig, I see for wlan0 that:

 ESSID:off/any

I don't understand why I see that when I set my ESSID in Networking.  Can anyone help with this?

---

### Post by iammrhand on 2005-10-29
Once you modprobe it, it should work without any future modifications.

---

### Post by sharingan on 2005-10-29
hi

i'm in the same situation as some of you after setting up ndiswrapper.

[FONT="Courier New"]sudo iwlist wlan0 scan[/FONT] works fine and i can see my AP listed there:

```
Cell 01 - Address: 00:C0:49:5D:50:5D
                    ESSID:"USRHOME"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-35 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:48 Mb/s
                    Bit Rate:54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=1
```

i've also updated [FONT="Courier New"]/etc/network/interfaces[/FONT] like this:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
iface eth0 inet dhcp

auto eth0

#auto wlan0
iface wlan0 inet dhcp
#iface wlan0 inet static
#       address 192.168.1.3
#       netmask 255.255.255.0
#       network 192.168.1.0
#       broadcast 192.168.1.255
#       gateway 192.168.1.1
       wireless_essid USRHOME
       wireless_mode Managed
       wireless_channel 11
       wireless_rate auto
#       name Wireless CardName
#       wireless_keymode restricted
#       wireless_key1
#      wireless_defaultkey 1
```

and run through

```

sudo ifconfig etho0 down
sudo ifconfig wlan0 up
sudo dhclient wlan0
```

with this nasty result:

```

There is already a pid file /var/run/dhclient.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:0f:cb:ad:79:69
Sending on   LPF/wlan0/00:0f:cb:ad:79:69
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

my wireless lan was working fine with ubuntu 5.04, but with 5.10 it's driving me crazy :confused:

---

### Post by jumpingin on 2005-10-30
Hello Vincent, 

Many thanks to you, and to everyone who has posted here.

I've done what you described, and everything ALMOST works. I can ping a numeric IP address, but not a URL. I have no such DNS problem when I'm connected through the wired ethernet. Any suggestions?

By the way, I found that switching to hexadecimal was necessary to get any connection.

Thanks!

Loren

---

### Post by TMR on 2005-11-16
Ubuntu 5.10 did such a good job of detecting my hardware when I installed it, I thought I'd do the easy thing: put a PCI WIFI card in my desktop and reinstall Ubuntu.

God this is hard.  Why is it so hard? Getting a bloody PhD was easier.

So I realised I'd need to use ndiswrapper.  So I did.  I mistyped the original .inf and when I tried the modprobe it said I couldn't.  But I realised the mistake, and 
used ndiswrapper -e to get rid of it all, then did it properly.  Then the modprobe worked.

Then I used the network admin tool.  This is a joke.  If I set a static address, it doesn't work: ping returns "Destination host unreachable" for my router (192.168.1.1).  And if I set it to DHCP and run dhclient, I get the same problem as a previous poster --- I broadcast DHCPDISCOVER but I get no offers.

I am totally f***ked off with it, so I'm hoping the 15 yo vcellis, or some other boy (or girl) genius can help me before I get have to get the Windoze XP disks out.

If you can help me get it to work, I'll update the wiki with the procedure.

...TMR  (The (notso) Mighty Rechecki)

---

### Post by Pent on 2005-11-19
I've had the same problem with my d-link router (cable connection sharing) and ubuntu, it auto found my wifi internal card, but when i go to obtain DHCP ip I get nothing, I've been up all night over it.

---

### Post by thenoobest1 on 2005-11-19
this shot is after everything was installed... im a total noob to ubuntu, or any kind of linux to be honest. but i do know it installed right because i tried to install it again and it said that it was already there.

i dont see a wireless adapter in my networking window and as you can see when i "sudo modprobe ndiswrapper" nothing happens. any ideas would be a huge help!

*EDIT*
i did "sudo ndiswrapper -l" and got hardware and driver present but an invalid driver. 
im using the D-link dwl-122 and i downloaded the v. 1.02 driver for XP/2000

---

### Post by el duderino on 2005-11-19
Hello all,

I'm glad I'm not the only one having Wifi problems.

My problem. Fresh install of Ubuntu 5.10 on a generic mobo with a celeron processor and 256ram. Every thing but the onboard video card installed fine.
It saw my pci Wifi card but didn't install anything I could see. 

I need to get back on it and get the text message the terminal gave. I ran a iwconfig or shucks can't remember... Anyway it said something to the effect of I needed version 18 instead of 17. 

Ok that tells you guys alot.;)  Back in five with what it said...

---

### Post by el duderino on 2005-11-19
oh yeh, I'm using a D-Link DWL-520, I saw it in the device manager, prism 2.5 chipset I think.

here's the terminal text:

ELduderino@ubuntu:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:294 errors:0 dropped:0 overruns:0 frame:0
          TX packets:294 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:24792 (24.2 KiB)  TX bytes:24792 (24.2 KiB)

ELduderino@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

Warning: Driver for device wifi0 recommend version 18 of Wireless Extension,
but has been compiled with version 17, therefore some driver features
may not be available...

wifi0     IEEE 802.11-DS  ESSID:"test"
          Mode:Master

wlan0     IEEE 802.11-DS  ESSID:"test"
          Mode:Master
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

ELduderino@ubuntu:~$

would the ndiswrapper solution solve my problem? or am I just that much of a noob?

---

### Post by shade87 on 2005-11-22
Hello
I also want to configure wlan with WEP encryption.
When I try to connect to the ap I always get the following error:
authentication failed, reason: specified protocols are not supported

I have read something about a module called hostap_crypt_wep.
What's that? I don't have installed this module and also don't know where to get it and how to install it.
I think that's my problem.

Can anyone help me?
The kernel version is: 2.6.10-5-386
I installed everything from the Ubuntu install CD and I am using ndiswrapper + ndisgtk to do the configuration.

---

### Post by nurd186 on 2005-12-14
my card seemed to become connected from the very first post in this thread only problem is i can't access the internet, the card shows it's linked, the laptop says it's connected, i get IPs and everything i just can't seem to get a webpage up it's almost as if i have a firewall somewhere i just don't know how to check any of that if anyone could help it'd be much appreciated thnx in advance

---

### Post by penno on 2006-02-12
'nutha n00b question! hehe. Can't make this thing work, here's what I [COLOR="DarkRed"]do[/COLOR] / get...

[FONT="Courier New"]root@DT:~# [COLOR="DarkRed"]ndiswrapper -i NetRt61G.INF[/COLOR]
Installing netrt61g
root@DT:~# [COLOR="DarkRed"]ndiswrapper -l[/COLOR]
Installed ndis drivers:
netrt61g        driver present, hardware present
root@DT:~# [COLOR="DarkRed"]modprobe ndiswrapper[/COLOR][/FONT]

And that is it. Hangs right there, doesn't give me my prompt back, and no matter how long I wait, doesn't play the game. The rest of the system is still responsive, but that terminal is a goner. Any ideas??? Switch OS's is about the only thing I can think of.... :cry: 

Oh running breezy, and trying to install a dlink DWL-G510 ver c1.

---

### Post by Lambert on 2006-02-12
before trying to modprobe ndiswrapper, check to see if the rt2500 module is loaded as you may have a driver conflict.

```

lsmod | grep rt2

```

If you don't get any output, just a new prompt then it's not loaded and this isn't the problem.

If you do get something like this.

```

rt2500                173540  0


```

Then you need to unload the rt2500 module first and then try ndiswrapper

```

sudo modprobe -r rt2500

```

If this is your problem and it solved by removing module, to prevent the rt2500 to load at boot then add a line like this

```
blacklist rt2500

```
to /etc/hotplug/blacklist file.

---

### Post by ananchai on 2006-02-12
Quote:  How to get almost every Wireless Card working under Ubuntu 5.10 

--------------------------------------------------------------------------------

- Get ndiswrapper-utils by typing "sudo apt-get install ndiswrapper-utils" in a terminal.
Give the root password when necessary.
- Get the Microsoft Windows drivers. Copy the .inf and .sys file. Paste these into a folder. 
(eg. /home/<USERNAME>/Desktop/driver/)
- Open a terminal
- Type the following commands:
$ cd Desktop/driver/
$ sudo ndiswrapper -i <name>.inf
$ sudo modprobe ndiswrapper

Notice that you have to repeat the last step whenever you want to use your device within a session.

If there's any problem, please contact me (vincent.celis@oc-productions.be) or post a reply.

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>

I have Linksys Wireless-B USB Network Adapter WUSB11 ver 4.0, and I can't get it to work. The followings are what I found on cd driver.

- E:\Drivers\LSPMUSB.inf
- E:\Drivers\NETUSB.inf
- E:\Drivers\WUSB11v4.inf
- E:\Drivers\LSPMUSB.sys
- E:\Drivers\M4301A.sys
- E:\Drivers\NETUSB.SYS
- E:\Drivers\NETUSBXP.SYS
- E:\Drivers\PRISM9x.SYS
- E:\Drivers\PRISMXP.SYS
- E:\Drivers\vnet58l.sys
- E:\Drivers\vnet58lx.sys
- E:\Drivers\vnetu9xl.sys
- E:\Drivers\VNETUSBA.SYS
- E:\Drivers\vnetusbl.sys
- E:\Drivers\vnetusbxp.sys

Please help me what xxx.inf and xxx.sys you would like me to copy them to 
"(eg. /home/<USERNAME>/Desktop/driver/)".

Thanks.

---

### Post by penno on 2006-02-12
[QUOTE=Lambert]before trying to modprobe ndiswrapper, check to see if the rt2500 module is loaded as you may have a driver conflict.

```

lsmod | grep rt2

```

If you don't get any output, just a new prompt then it's not loaded and this isn't the problem.
[/QUOTE]

Bugger. I don't get any output, before, during or after. Had my hopes up! hehe The only thing I got that even starts with "rt" is "rtc", whatever that may be... Meanwhile I got another modprobe, sittin' there, doin' whatever it's (not!) doin'. C'mon modprobe! You can do it! Go you good thing!! (c:

---

### Post by bscbrit on 2006-02-12
Ananchai

I would say that the inf file is quite easy to identify : E:\Drivers\WUSB11v4.inf.

I don't know if copying all the .sys files will do any harm, after all, you only specify the *.inf file to ndiswrapper and it seems to know which .sys file to pickup.  At least it did with mine, which had one 'inf' file but two 'sys' files.

---

### Post by penno on 2006-02-15
Got it working - enventually. :-D To save repeating myself, [here's]("http://www.ubuntuforums.org/showthread.php?p=734076#post734076") what I did. Which is really just a pointer to [here]("http://61.222.76.235/phpbb2/viewtopic.php?t=1400&postdays=0&postorder=asc&highlight=rt2600&start=15") hehe.

---

### Post by rbaraz on 2006-02-15
has anyone tried this on D-Link's DWL-G630?

I wanted to dld the Linux driver from their web site but they don't have. This is the only driver i am missing before i can migrate to Linux.

thnx guys for ur support

---

### Post by Belyel on 2006-02-16
Hey, Ubuntu n00b here (Linux n00b, to be honest).  I've been running ubuntu 5.10 i386 on my laptop for about a week, and have yet to be able to get my wireless chipset to work!  I followed the directions listed in the first post in this thread.  Here's what i'm getting as output:

The card (chip) is Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02) <<as detected by Ubuntu

I installed the driver using ndiswrapper, shown:

ndiswrapper -l
Installed ndis drivers:
bcmwl5  driver present, hardware present


Then do a # modprobe ndiswrapper

However, I get no indication that the modprobe did anything, and when I look for my wireless card using iwconfig or the network administration tool, there is no wlan0 showing.  Help?

---

### Post by Belyel on 2006-02-17
I got my card to work, despite a lack of immediate response to my last post :P.  What had happened is my windoze drive had been 'hibernating' when I removed it, and for some reason my WIC was disabled when it hibernated.  I put the windoze drive back in my laptop, enabled the WIC after booting from scratch, shut down windoze normally.  When I restarted my machine the WIC was already turned 'on' and after doing modprobe ndiswrapper, I configured my wireless card and it's working great now.


BTW, how would I turn on/off my wireless card inside linux?  I have a compaq presario 2104US laptop.

---

### Post by hiikeeba on 2006-03-25
[QUOTE=mxyzptlk]vcelis i did all you describe here but nothing happens.

I reboot the system and it sent a message like this

files already installed but nothing.
i checked the networ devices and it only detects the internal port but the usb wireless adapter no .

I have the driver and it has one for linux but i dont know how to install it

any suggestion[/QUOTE]

Ndiswrapper installed like a charm.  However, I still don't have wlan0 in the networking window.  According to the Device Manager, Ubuntu sees the card bus, sees the PCMCIA card, and can tell it's from LinkSYS with a Broadcom chipset.  It also calls it an unknown device.  I have a PCMCIA ethernet card, but when I plug it into my router, Ubuntu doesn't see the network.  It's almost enough to get me to reinstall Windows.

Jeff

---

### Post by Guaver on 2006-03-25
I'm getting the same message as another person. When i type modprobe ndiswrapper, it fails and says "operation not permitted". wireless card is smc2862w-g ez

I tried the suggested fixes but got the same thing. I did some reading elsewhere and it recommended the newest driver. I downloaded it and put it on a cd to get it to my new ubuntu puter. But no luck same error. When I did the apt-get to install ndiswrapper I got no errors but since that machine isn't on the net I was wondering if it actually installed. Thanks for your help.

---

### Post by mr best buy on 2006-04-01
I am new.  I have an hp laptop with a broadcom wireless card built in.  I  am trying to follow you post step my step.  I have a linksys router wrt54g v2.2  I went ti the link sys web site and they do not have any drivers for this unit on their web site.
So where do I go to get "the Windows drivers"?

---

### Post by SilentSam on 2006-04-06
Hey all,

Am I the only one who has gotten this error when trying to install ndiswrapper?:

[FONT="Courier New"]
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  ndiswrapper-source
The following NEW packages will be installed:
  ndiswrapper-utils
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/25.7kB of archives.
After unpacking 131kB of additional disk space will be used.
Media change: please insert the disc labeled
 'Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)'
in the drive '/cdrom/' and press enter[/FONT]

Whats up with that, any ideas?
 I did start out using KDE but than migrated to GNOME some time ago. Did i bork something up?

Any help is appreciated. Thanks,
sam

---

### Post by txruss2 on 2006-04-06
[QUOTE=mr best buy]I am new.  I have an hp laptop with a broadcom wireless card built in.  I  am trying to follow you post step my step.  I have a linksys router wrt54g v2.2  I went ti the link sys web site and they do not have any drivers for this unit on their web site.
So where do I go to get "the Windows drivers"?[/QUOTE]

You can get the drivers here:  [http://www.mikeycal.com/zv5360us.html](http://www.mikeycal.com/zv5360us.html)

I still can't get my HP zv5000 wireless to work though.  I have a Broadcom card, and am running Breezy.

when I run [COLOR="Indigo"]~$ sudo ifup wlan0[/COLOR], here's what comes up...

[COLOR="Indigo"]sit0: unknown hardware address type 776
SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
sit0: unknown hardware address type 776
Bind socket to interface: No such device
Failed to bring up wlan0.[/COLOR]

---

### Post by txruss2 on 2006-04-06
[QUOTE=txruss2]You can get the drivers here:  [http://www.mikeycal.com/zv5360us.html](http://www.mikeycal.com/zv5360us.html)

I still can't get my HP zv5000 wireless to work though.  I have a Broadcom card, and am running Breezy.

One more thing, I'm getting this when I use modprobe:

[COLOR="Navy"]~/Desktop/driver$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-10-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted[/COLOR]

---

### Post by SilentSam on 2006-04-06
[QUOTE=SilentSam]
Hey all,

Am I the only one who has gotten this error when trying to install ndiswrapper?:


Reading package lists... Done
Building dependency tree... Done
Suggested packages:
ndiswrapper-source
The following NEW packages will be installed:
ndiswrapper-utils
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/25.7kB of archives.
After unpacking 131kB of additional disk space will be used.
Media change: please insert the disc labeled
'Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)'
in the drive '/cdrom/' and press enter

Whats up with that, any ideas?
I did start out using KDE but than migrated to GNOME some time ago. Did i bork something up?

Any help is appreciated. Thanks,
sam
[/QUOTE]
[QUOTE=vcelis]The command "sudo apt-get install ndiswrapper-utils" will ask to insert the Ubuntu 5.10 CD. The utility will be installed from the ndiswrapper-utils on the CD.[/QUOTE]

Missed that bit. Sorry.
When i inserted the cd all was well. I followed the parent posts instructions and am now able to access my D-Link 624's IP address to configure it. 

Strange, Ubuntu picked up my ethernet modem (SpeedStream) w/ out any probs, I'm just not sure how to get through my wireless router to my ethernet modem and online. 

I'll start a new thread when I get a chance, I just wanted to say thanks to vcelis for posting such concise instructions on how to set up ndiswrapper.

Thanks,
sam

---

### Post by ReTheOff on 2006-04-09
I cant get Wlan0 to show up.  I can run ndiswrapper -l and it shows my device and hardware present.  Modprobe runs and installs the module without error.  The device is present in lsusb.

I also ran ndiswrapper -d 0457:0162 sis162u, which worked fine.

I ran ndiswrapper -m.
Then depmod -a
and modprobe ndiswrapper
No problems.

Basically, everything seems to work, but if I run iwconfig wlan0, I get:
wlan0    no such device

I tried the Trendnet usb drivers, and also the drivers from SIS.  The Trendnet driver installs with an error, and modprobe gave me a segmentation fault error.  But the SIS driver works and installs without errors.  But, no wlan0.

I also tried removing the module (which shows with lsmod, and has "used by" = 1) running modprobe -r ndiswrapper, then re-adding it after I removed the usb device and reinserting it.

Still, no wlan0.  What am I missing?  Thanks for any help.

---

### Post by ReTheOff on 2006-04-09
OKAY....

Running dmesg reveals the problem with the TEW-229UB:

ndiswrapper ... Windows driver couldn't initialize the device (c000009a)
ndiswrapper: probe of 1-2:1.0 failed with error -22

I tried the SIS drivers, the Trendnet Win2k and Winxp drivers. (for USB 2.0, which is the adapter I have)

Anyway, just a hunch, is this a problem because ndiswrapper on Breezy is only version 1.1.  And on other searches I have found that ndiswrapper is at version 1.8, right?   Or, maybe it's the Win driver anyway.  

I think I'll just get a different card, this is too much messing around.

---

### Post by monomaniacpat on 2006-04-10
Hi, I have tried to install the D-Link DWL-G122 USB dongle, but as with other cards, my hardware is not detected. What can I do?

---

### Post by Vspecimport on 2006-04-13
Having an issue with the Airlink101 AWLC3025. I am getting no power on the card. I used ndiswrapper and everything seems to be loaded correctly for some reason I just can't get power. I also have a USB wired adapter could that be causing any issues?

-lspci displays this 
0000:01:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface

it also shows up in device manager.

-iwconfig
wlan0     IEEE 802.11b+/g+  ESSID:"MS-HOME"  Nickname:"acx100 v0.2.0pre8"
          Mode:Auto  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

-sudo ifup wlan0  says that everything is already installed.
I have also tried dhclient with no success 
I am new to linux and would really like to get this working.
Thanx for the help.

---

### Post by whereareyoutakingme on 2006-04-18
in reply to the very first post of this thread...this is what i typed in:

"$ sudo apt-get install ndiswrapper-utils" --> into a terminal

copied the .sys and .inf Windows drivers to <username>/Drivers/LinkSys Wusb11

"$ cd <username>/Drivers/LinkSys Wusb11"

"$ sudo ndiswrapper -i <name>.inf" <----problem line

and then i was going to type...

"$ sudo modprobe ndiswrapper" into a terminal, but when I hit enter on the before indicated problem line, i got an error message that said

"ndiswrapper: command not found"

What do I do to get my internet working?

---

### Post by whereareyoutakingme on 2006-04-18
okay i figured it out.....let's just say i'm a nerd and forgot to put the ubuntu cd in the tray before i tried all that code in the terminal. :???:

---

### Post by gondilon on 2006-04-19
[QUOTE=mjkelly]I just booked into this hotel with only wireless ethernet so i went out and bought a wireless NIC for 50 bucks. (is that reasonable or way too much? cuz i know normal NICs are like 5 bucks...??)

Well anyway i cant get it working and i cant get this ndiswrapper file onto my linux partition. I dont have any blank CDs to burn and when i mount the windows partition (/dev/hda1 on /windows) i cant even view it because it says permission denied?? So... that brings me to the problem. Can i transfer a file from my windows partition to my linux partition?

Also when i go into networking, the wireless card is listed. When i go to preferences to configure it, it asks for an IP or if its DHCP and all... this wont work without the driver right? Like i need to get that ndiswrapper working right? I dont have any other linux driver and its an Airlink 101 card but on windows it installed as a texas instrument card.[/QUOTE]
[http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm)
at the url listed above, you can get a program that will allow you to read and write your linux partition from windows.

---

### Post by gondilon on 2006-04-19
when I run sudo modprobe ndiswrapper it says "modprobe command not found. Please help!

---

### Post by Blacktalon on 2006-04-19
What if you don't have the cd that contained the wireless drivers, is there somewhere I can download it.  I am using a Broadcom Bluetooth incase that helps with helping me find a solution to my problem.


Thanks
  Blacktalon

---

### Post by TrojanSkin on 2006-04-19
I don't think this will work with Bluetooth as this is for a wireless internet connection, however I may be wrong. If you need drivers try DriverGuide.com  (The login is drivers, and the password is all). Good luck.

---

### Post by Blacktalon on 2006-04-20
Actually I just found some drivers for Broadcom Bluetooth, and downloaded it.  Do you know how I could possibly install it, and how to create the module for it?  But thanks anyways for the suggestion to the DriversGuide site....but would you have any clue on how I could install and get my linux drivers I found installed.


Thanks
  Blacktalon

---

### Post by SuicideInvoice on 2006-04-28
[QUOTE=Vspecimport]Having an issue with the Airlink101 AWLC3025. I am getting no power on the card. I used ndiswrapper and everything seems to be loaded correctly for some reason I just can't get power. I also have a USB wired adapter could that be causing any issues?

-lspci displays this 
0000:01:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface

it also shows up in device manager.

-iwconfig
wlan0     IEEE 802.11b+/g+  ESSID:"MS-HOME"  Nickname:"acx100 v0.2.0pre8"
          Mode:Auto  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

-sudo ifup wlan0  says that everything is already installed.
I have also tried dhclient with no success 
I am new to linux and would really like to get this working.
Thanx for the help.[/QUOTE]

I have the same card as VSPec and i'm also unable to get this card working.  I have the exact same issues.  Device shows up in the 'device manager' and can be set to active.  It shows in ndiswrapper -l as 'driver present, hardware present'.  

Trying a iwlist wlan0 scan will give me a 'wlan0   Interface doesn't support scanning : Resource temporarily unavailable'.

a ifdown wlan0 will give me a "interface wlan0 not configured"

Anyone have any ideas?

---

### Post by n3tfury on 2006-05-01
suicide and vspec - exactly which driver are you using?

---

### Post by teamofemus on 2006-05-05
Hello - I am using the Linksys Wireless-B PCMIA Card on Ubuntu Standard. I have tried the steps above and see my network and It says that the connection is active in the network preferences menu, but it won't work in Firefox. Any Ideas?

---

### Post by _linux_ on 2006-05-06
[QUOTE=The Mekon]I believe that the D-Link G510 should just work in Breezy.  I used nidiswrapper on Hoary but I am not using it on Breezy and if you can read this it is certainly working (without WEP).

Brian[/QUOTE]
The DWL-G510 does work in Breezy. I have it, and it works great! I followed the ndiswrapper instructions in the Ubuntu Wiki guide ([https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto]("https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto"))

---

### Post by SuicideInvoice on 2006-05-07
[QUOTE=n3tfury]suicide and vspec - exactly which driver are you using?[/QUOTE]

I was using the W2K drivers off the Airlink CD.  I have since given up on ndiswrapper and that airlink.  I receintly purchased the Belkin 54G card that i'm told has the RT2500 chipset.  I'm currently fighting with this.  In fact, i'll be posting soon with my problems.  Thanks for the help.

---

### Post by quadz0 on 2006-05-07
I tried this method with a DWL 520 Rev D
It won't work. the driver was installed and it came up in teh networking place, but when i activate it, it doesn't work. In the ip box, am i supposed to type the ip i get from whatismyip.com or the ip of the router?

---

### Post by Motoxrdude on 2006-05-08
[QUOTE=vcelis]- Get ndiswrapper-utils by typing "sudo apt-get install ndiswrapper-utils" in a terminal.
  Give the root password when necessary.
- Get the Microsoft Windows drivers. Copy the .inf and .sys file. Paste these into a folder. 
  (eg. /home/<USERNAME>/Desktop/driver/)
- Open a terminal
- Type the following commands:
    $ cd Desktop/driver/
    $ sudo ndiswrapper -i <name>.inf
    $ sudo modprobe ndiswrapper

Notice that you have to repeat the last step whenever you want to use your device within a session.

If there's any problem, please contact me (vincent.celis@oc-productions.be) or post a reply.[/QUOTE]
Ok, i did all of that until the last step. I typed "sudo modprobe ndiswrapper" and it says somehing like FATAL: error inserting ndiswrapper....Operation not permitted" 
Any clue what to do?

---

### Post by shooterae5 on 2006-07-05
where can I download the drivers fo the atheros 802.11 a/b/g nic card in my toshibe laptop?

Everything (wifi wise) worked under hoary.

DA

---

