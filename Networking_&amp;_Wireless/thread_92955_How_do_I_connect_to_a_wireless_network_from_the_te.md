---
title: "How do I connect to a wireless network from the terminal, sans obtuse GUI'd tool?"
date: 2005-11-20
forum: Networking &amp; Wireless
---

### Post by Plank117 on 2005-11-20
The out of the box tool is a little buggy, the network profiles don't work and I have to reenter a 10 digit key every time I want to connect to my home network. Can I do all of this from the terminal? I'm eventually going to write a shell script to do it, but I'm content with typing in commands at the moment.

---

### Post by Vorian on 2005-11-20
iwconfig eth1 ap (what ever your ap mac address is)
iwconfig eth1 essid (name of your router)
iwconfig eth1 key s:passphrase
dhclient eth1

boom, your in....

i use iwlist eth1 scanning to get the ap address and router name..

---

### Post by mpvano on 2005-11-20
It's too bad UBUNTU relies on the unbelievably broken GNOME applets for this task. They do not seem to work at all for me, and there doesn't seem to be any hope of them being fixed soon. By the way, the network applet seems to be written as thousands of lines of spaghetti code in PERL with badly broken error handling - it's unbelievable that the GNOME foundation ships this. I was really disappointed when they weren't fixed in breezy.

I have the same problems with all my Ubuntu installs, so I manually configure the interfaces using other methods.

For configuring dialup PPP, I use "sudo" to run the standard Debian "pppconfig" command, which I have always found installed in my Ubuntu installs and is klunky but works well. The commands "pon ispname" and "poff" will connect and disconnect (assuming "ispname" is the name you configured for the connection in pppconfig).

For ethernet and wireless, I just directly edit the file "/etc/network/interfaces" using "sudo".

It's ugly, but as a sort of simple profile system, I use "sudo" to copy backup copies of the various configurations over the "/etc/network/interfaces" file.

For more information about what you can do with this file try "man interfaces"

Note that the "interfaces" file doesn't change anything directly, but it controls the next "ifup" operation for the adapter in question. If you configure it properly, for a pcmcia network adapter it will affect the next card insertion or boot. Otherwise you can do "sudo ifdown eth0" (or whatever the adapter's called), change the file, then do "sudo ifup eth0".

To get you started, here's an example from one of my machines (assuming your card comes up as either eth0 or wlan0 (the example configures BOTH, just in case) to work WITHOUT a wireless key and to connect to the first open network they see.

For closed networks, you can change the ESSID line from "any" to the correct ESSID and you can add the following line (with your key replacing the hhhs) to specify your wireless key.

wireless-key hhhhhhhhhhhhhhhhhhhhhhh

Other useful things to do are to substitute the word "static" for "dhcp" and then use "address",  "netmask", and "gateway" lines to configure the interface.

If you use a PCMCIA wired ethernet adapter, you can use the same file for both as long as the configuration would be identical except for the "wireless" lines, since these just fail silently.

The man page also explains how to do things like run arbitrary scripts or commands before and after each interface comes up. I use two "cp" commands to correct static dns entries and to copy the correct host file into /etc to correct for anything a dhcp connection may have done.

WARNING! Do NOT run any other configuration tools if you use this method, they may confuse things by clobbering this file, or may modify other files "ifup" and "ifdown" rely on. It also wouldn't hurt to read the rest of the man pages for these scripts to understand how the whole thing works....

Pardon my bitching about the network applet - I'm not very happy about having to do things this way, but until a better solution is provided by Ubuntu, it gets the job done...

Hope this helps....

Mario


---------------------------------------------------------------------------------------
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
        map wlan0

iface eth0 inet dhcp
wireless-essid any

iface wlan0 inet dhcp
wireless-essid any

---

### Post by 23meg on 2005-11-20
[QUOTE=mpvano]It's too bad UBUNTU relies on the unbelievably broken GNOME applets for this task. They do not seem to work at all for me, and there doesn't seem to be any hope of them being fixed soon. [/QUOTE]
Did anyone here try [GTKWifi]("http://ubuntuforums.org/forumdisplay.php?f=74")? I use it and it automatically switches to my preferred wireless network when it detects it, and switches back to my ethernet one otherwise. I don't touch the Network Settings window at all.

---

### Post by Vorian on 2005-11-21
[QUOTE=23meg]Did anyone here try [GTKWifi]("http://ubuntuforums.org/forumdisplay.php?f=74")? I use it and it automatically switches to my preferred wireless network when it detects it, and switches back to my ethernet one otherwise. I don't touch the Network Settings window at all.[/QUOTE]

I do in breezy, it works great.  Hoary was a bit tricky however.

---

### Post by az on 2005-11-21
Network-manager is in universe
[http://packages.ubuntu.com/breezy/net/network-manager](http://packages.ubuntu.com/breezy/net/network-manager)

Apparently it was just too immature for main in Breezy but it should make it in Dapper.  It does what you describe.

Quote the long description:
NetworkManager attempts to keep an active network connection available at all times. It is intended only for the desktop use-case, and is not intended for usage on servers. The point of NetworkManager is to make networking configuration and setup as painless and automatic as possible. If using DHCP, NetworkManager is _intended_ to replace default routes, obtain IP addresses from a DHCP server, and change nameservers whenever it sees fit.

---

### Post by 23meg on 2005-11-21
AFAIK Network Manager does away with the whole Debian system of detecting whether network interfaces are up or down, so perhaps it should be used with caution, making sure any changes it makes are reversible. I'd suggest trying GTKWifi and Wifi Radar (in order of recommendation) and resorting to Network Manager if they don't provide the functionality you're after.

---

### Post by Plank117 on 2005-11-27
Okay, now what do I do with a .deb? Do I just plunk it in /usr/bin?

---

### Post by ethnicman on 2005-11-29
type (as root) dpkg -i filename.dep

---

### Post by robotgeek on 2005-11-29
Another great app to try out is network-manager (sudo apt-get install network-manager, start with 'nm-applet'). very very cool! 

If you want to go cli, [https://wiki.ubuntu.com/WiFiHowto](https://wiki.ubuntu.com/WiFiHowto)

---

### Post by Ventrix on 2007-11-07
try wifi-radar ;)

---

### Post by 21jeremy21 on 2007-12-19
I am having one heck of a time getting my wireless to work. After many sleepless nights and putting more effort into this than into my university studies I have the correct driver installed.

I can even do iwlist scanning and see my wireless networks

but i can not, for the life of me, connect to a network.

I have no luck with any of about 17 wireless network utilities that come with ubuntu ultimate edition so then i resorted to modifying /etc/network/interfaces to put in the info... still no dice

so then i start trying my hand with  iwconfig wlan0 ap, essid, etc... i get all the info in there, then i do dhclient wlan0 and it tries a few times and fails.

i dont know what the "s:passphrase" (s: passphrase)  thing is about here
> iwconfig eth1 key s:passphrase (s: passphrase)  

i get an error if i type it like that so i typed "iwconfig wlan0 key 1a2b3c4d5e" and it took it... is that perhaps where i went wrong??:confused:

i feel like i'm SO CLOSE i can almost taste the wifi, but that makes it all the more frustrating

i am POSITIVE i am entering the key correctly, and ive tried connecting to different encrypted networks. Unfortunately i havent had the chance to try it on an unencrypted AP yet

Please, oh please can somebody help me... i accidently buggered my ntfs partition so im off windows cold turkey... i'll be able to make it if i can just have my wifi

here is what i entered and what i got, can anyone tell me what im doing wrong?
Thank you kindly in advance

```

jeremy@jeremy-ubuntu:~$ sudo -s
[sudo] password for jeremy:
root@jeremy-ubuntu:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:270 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

root@jeremy-ubuntu:~# iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1B:5B:34:A5:C9
                    ESSID:"jpoole16"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:75/100  Signal level:-48 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:16:B6:EE:1A:F0
                    ESSID:"hx"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:20/100  Signal level:-83 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:1B:11:4B:40:B1
                    ESSID:"topsog"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:20/100  Signal level:-83 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 04 - Address: 00:18:3F:BF:D1:B9
                    ESSID:"brenda93"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:15/100  Signal level:-86 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 05 - Address: 00:18:F8:59:95:78
                    ESSID:"Stardog Home"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:15/100  Signal level:-86 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 06 - Address: 00:19:E4:12:24:D1
                    ESSID:"2WIRE648"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:10/100  Signal level:-89 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 07 - Address: 00:18:3F:18:E2:F1
                    ESSID:"wkenward"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:17/100  Signal level:-85 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

root@jeremy-ubuntu:~# iwconfig wlan0 ap 00:1B:5B:34:A5:C9
root@jeremy-ubuntu:~# iwconfig wlan0 essid jpoole16
root@jeremy-ubuntu:~# iwconfig wlan0 key 1a2b3c4d5e
root@jeremy-ubuntu:~# dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 8750
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:16:cf:28:0f:ab
Sending on   LPF/wlan0/00:16:cf:28:0f:ab
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


```

my driver is installed and my wifi light is on

```

bcmwl5 : driver installed
        device (14E4:4328) present

```

again, any help is VERY appreciated... in case you cant tell, im a total linux newb so be gentle

Merry chrismahanukwanzakah!

---

### Post by 21jeremy21 on 2007-12-20
So I've now managed to connect to an unsecure network from terminal using the iwconfig essid, etc commands. This leads me to believe that the part I am having trouble with is, infact, the iwconfig key s: passphrase part.... anyone know why i'm having trouble inputing this? Again and still, any help much appreciated!!!

---

### Post by kevdog on 2007-12-20
Try the link in my signature about connecting from the command line :)

---

### Post by 21jeremy21 on 2007-12-20
Beautiful, i knew there must be a straightforward guide somewhere, just couldnt find it. Unfortunately i followed it precisely and it didnt get me any further.

However, just before i found your reply i did
 ```
iwconfig wlan0 key open
``` 
and that is allowing me to connect and view the web

my only remaining concern is this: is my connection less secure because of this? Secondly, how am i even connected if i didnt give it the WEP code?

thank you kindly for your prompt reply kevdog, i appreciate it a ton, and hopefully you have some more wisdom in there for me

---

### Post by kevdog on 2007-12-20
Isnt key open mean that basically you are using an unencrypted network??? 

Can you tell me what card and driver you are using? (lshw -C network)

Can you just pinpoint the error you are having with your WEP key??  No long explanation please.  Im getting lost in the explanation.

---

