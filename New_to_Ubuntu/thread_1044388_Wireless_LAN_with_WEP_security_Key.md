---
title: "Wireless LAN with WEP security Key"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by bart_b on 2009-01-19
Good evening,

Now I've finally succeeded in installing UBUNTU and get it working, I've encountered the next problem:

When I want to connect to our Wireless LAN (Wifi) I have to fill in a WEP security Key (64 bit WEP according to the specifications of my LAN), so I filled in the "passphrase", but I don't get connected, he keeps on asking a security key. Apart from the passphrase, I have also a password for my Wifi network, but also that didn't work out. Is there any solution?

---

### Post by stchman on 2009-01-19
> **bart_b said:**
> Good evening,

Now I've finally succeeded in installing UBUNTU and get it working, I've encountered the next problem:

When I want to connect to our Wireless LAN (Wifi) I have to fill in a WEP security Key (64 bit WEP according to the specifications of my LAN), so I filled in the "passphrase", but I don't get connected, he keeps on asking a security key. Apart from the passphrase, I have also a password for my Wifi network, but also that didn't work out. Is there any solution?

I recommend that if you are going to go to all the trouble to setup wireless security that you go with WPA/WPA2 if your hardware supports it.

WEP is easily broken where WPA/WPA2 is nearly impossible to break if a long complex passphrase is used.

---

### Post by hovzio on 2009-01-19
Is there other hardware (laptop, psp, etc) that can connect with this passphrase? If not you could try to connect to your access point through cable, (if thats an option) from there you could log into your router (whatever it is your using) with a web browser. I would double check the passwords and maybe reset things. Might I suggest using WPA (if its an option) for security sake.

---

### Post by bart_b on 2009-01-19
Hi, thanks for the reply!

I know that WEP isn't the best security solution, but I 'm not able to switch to WPA. Meanwhile I have succeeded to add my wireless network to the list of wireless networks the system finds, and connecting to an unsecured network works, but logging in into my own secured network still doesn't work. One still keeps asking repetative to fill in the passphrase, and I can't connect to the Internet. I do see the signalstrenght of my connection..

There are another 2 PC's connected to the wireless LAN, one of them also wireless, the other serves as central PC, and is connected by wire to the router.

Best,

Bart

---

### Post by Gone fishing on 2009-01-19
You can do this all manually by editing /etc/network/interfaces.

However, you probably need to select  WEP 40/128 WEP bit Key not passphrase

---

### Post by Maheriano on 2009-01-19
You should turn off SSID broadcasting if you can't use WPA, at least then the thief will have to guess your SSID as well.

---

### Post by BDNiner on 2009-01-19
Are you sure that you are entering the correct information relevant to your wireless network settings. One thing that trips me up is ubuntu defaults to an open network when i have a shared key network. And i have to go in sometimes and manually set it

---

### Post by bart_b on 2009-01-19
I have still not yet managed it to get it work. I've been trying to configure the network through the the terminalwindow using some sudo-commands.( I found these commands on another site). However when I want to execute a sudo command, I 'm asked to enter the [sudo] password for 'gebruikersnaam'. When I fill in my own password, the following message is displayed:

[interface]: ERROR while getting interface flags: No such device

What could I do?

---

### Post by mkvnmtr on 2009-01-19
Well I am with you on this. I am sitting here trying to connect two laptops in Ubuntu and don't know the first thing about it. It sounds like we need to know just what this key is and where to find one to use with the password. With two of us looking maybe we can get connected by March.

---

### Post by bart_b on 2009-01-19
Well, that 's a great objective! :cool:

It seems indeed that we have the same problem. What have you already tried to accomplish?

---

### Post by mkvnmtr on 2009-01-19
I have just found thatthey can both see the other one. When I tried setting up with the gui I was asked for a password but I have no idea where to get this key they are talking about. Don't know the mac address of the two or any of the other things I should know. I am searching now for the annswers thats how I found your thread. Looks like you are a little ahead of me.

---

### Post by cmnorton on 2009-01-19
The pass phrase is the ascii string you entered or will enter in your router. Most routers will take an ascii string and translate it to hex. I prefer to enter the hex, but the option is there, as the prompt you are receiving shows, that you can enter a pass phrase.

If you have not done this with your router, I suggest being cabled to it, rather than trying wireless, because you'll loose connectivity when you establish the pass phrase in the router.

---

### Post by bart_b on 2009-01-19
I've found some valuable information on the following link:
[http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html]("http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html")
But do you just want to connect two computers to each other (in an adhoc network) or do you want to establish the connection to an acces point (router)?
If you just want to connect two computers, you could maybe choose not to use WEP..

My problem is that I can't execute to sudo commands because I'm asked after a password, but I haven't got the foggiest about which password that could be, and I seem to fill in the wrong one. So I still cannot connect to my wireless network.

---

### Post by gsocker on 2009-01-19
> **Maheriano said:**
> You should turn off SSID broadcasting if you can't use WPA, at least then the thief will have to guess your SSID as well.
Turning off SSID broadcasting is pointless. Tools like Kismet can still find the SSID by passively sniffing the packets received, and it can make it 
much harder for some devices to connect. Of course, the average person who is only looking for "free" internet access is unlikely to have such software or know how to use it. BTW, "shared" is actually less secure than "open", despite the name, since the same information is send as  plain text and encrypted, allowing the key to be deduced.

---

### Post by mkvnmtr on 2009-01-19
Well I have found that you can get the key. Do a google search for wep 40 1288 bit key and you will find a page that will generate a key. All the talk of routers does not help me I just want to connect the two together. I will see how mnuch farther I get with a password and key.I will figure out later how to use a more secure connection. To learn how to connect the two I would settle for a straight connection.

---

### Post by gsocker on 2009-01-19
Following assumes both are running Linux. If one is running Windows you will have to refer to the appropriate documentation and read about ad-hoc networks.
Try this: open a terminal.
Run on PC #1:
```

sudo iwconfig interface_name  essid "my-ssid"
sudo ifconfig interface_name 192.168.12.10

```
PC #2:
```

sudo iwconfig interface_name essid "my-essid"
sudo ifconfig interface_name ip 192.168.12.20

```
If you don't know what interface name to use, try running 
```
 sudo iwlist scan 
``` and see which one returns something other than "no wireless extentions"
You should then be able to ping one from the other. For WEP,  sudo iwconfig interface_name key xx-xx-xx-xx-xx(repace with hex key) should work if run on both ends. WPA is more complicated.

Note: the iwconfig/ifcommands complain only. If all you see after running then is another command prompt, everything went fine. If you see a message, something went wrong. This is true of many CLI programs in Linux/Unix.

---

### Post by bart_b on 2009-01-20
Maybe a very silly question, but where do I found the 'interface_name' to fill in in for example the instruction: "sudo ifconfig [interface] down ?

Thanks a lot!

---

### Post by bart_b on 2009-01-20
Meanwhile I discovered how to find the interfacename. 
I also discovered that the ilw3945 driver is standard included in Ubuntu, so I haven't to worry about that...

So, I googled and I found the following commands to configure a wireless WEP connection:

WEP Connection

You must have either your 64bit or 128 bit HEX Key or the ASCII Equivalent of your HEX Key.

sudo ifconfig [interface] down
sudo dhclient -r [interface]
sudo ifconfig [interface] up
sudo iwconfig [interface] essid “ESSID_IN_QUOTES”
sudo iwconfig [interface] key HEX_KEY <<<-------- If using ASCII Equivalent, this is s:ASCII_KEY (please make note of the prefix s:)
****Additional Comand that may be needed -- sudo iwconfig [interface] key open <<<----See note below
sudo iwconfig [interface] mode Managed
sudo dhclient [interface]

***The security mode may be open or restricted, and its meaning depends on the card used. With most cards, in open mode no authentication is used and the card may also accept non-encrypted sessions, whereas in restricted mode only encrypted sessions are accepted and the card will use authentication if available.

The first two commands work, but when I want to execute the third one, the message "NOT SUPPORTED" becomes displayed. Also the assignment of the essid and the key end up in a "NOT SUPPORTED" message. How can that be fixed?

Best regards

---

### Post by gsocker on 2009-01-20
Sure you have the right interface? If using an Intel card on a laptop with 1 ethernet port, the wireless card should be eth1.
Also, please post the exact error messages. Even if you can't figure out what they mean, someone else probably can.

---

### Post by bart_b on 2009-01-21
So this is what I did:

WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 02
       serial: 00:13:02:56:88:9b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.2.145 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 10
       serial: 00:18:f3:2b:97:d6
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes

Thus, the interfacename is "wmaster0"

When I want to initialize my wireless connection I get the following:

$ sudo ifconfig wmaster0 down
[sudo] password for "username": ******

$ sudo dhclient -r wmaster0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Sending on   Socket/fallback

$ sudo ifconfig wmaster0 up
SIOCSIFFLAGS: Operation not supported

$ sudo iwconfig wmaster0 essid "*********"
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wmaster0 ; **Operation not supported.**

$ sudo iwconfig wmaster0 key ********** // I filled the Hex form in (10 characters)
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wmaster0 ; [B]Operation not supported.
[/B]
$ sudo iwconfig wmaster0 mode Managed
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wmaster0 ; **Operation not supported.**

$ sudo dhclient wmaster0
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
SIOCSIFFLAGS: **Operation not supported**
SIOCSIFFLAGS: **Operation not supported**
wmaster0: unknown hardware address type 801
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Sending on   Socket/fallback
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 6
send_packet: Network is down
receive_packet failed on wmaster0: Network is down
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 11
send_packet: Network is down
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 13
send_packet: Network is down
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 1
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Does anyone see the problem?

---

### Post by bart_b on 2009-01-21
I have to mention that at the moment I was executing these commands, I had a connection to another unsecured wireless network.. But I don't know whether it affects the results.

---

### Post by gsocker on 2009-01-21
Problem is, wmaster0 is a "master" interface, which then creates one or more sub-interfaces. It's not intended to be used itself.
Run:
```
sudo iwlist scan
``` and see which one returns something other than "Interface doesn't support scanning".

Example output:
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

**eth1      Scan completed :**
          Cell 01 - Address: 00:22:B0:05:FC:87
                    ESSID:"SSID1"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:4/5  Signal level:-65 dBm  Noise level:-18 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                       Preauthentication Supported
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s

```The one that says "scan completed" is the interface name to use - here eth1.

---

### Post by bart_b on 2009-01-25
Thanks gsocker, I found out that the interface to use is wlan0.

Now, I repeated the configuration of my wireless network, and after completing

sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "xxxxxxxxx"
sudo iwconfig wlan0 key xxxxxxxxxx //in HEX-code
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0

I get the following output:

....
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11

NO DHCPOFFERS received
No working leases in persistent database - sleeping

And I still got no connection.
What now?

---

### Post by bart_b on 2009-01-26
No one who has any idea? I'm turning totally nuts. :-)

---

### Post by stchman on 2009-01-26
> **Maheriano said:**
> You should turn off SSID broadcasting if you can't use WPA, at least then the thief will have to guess your SSID as well.

That is a COMPLETELY worthless form of security.  I put that up there with MAC filtering.

A person can get your SSID from other sources.

---

### Post by gsocker on 2009-01-29
Forget DHCP for the moment. Do you have (rather useless) MAC filtering turned on? If so have you added your wireless card's MAC address to the router? Note that the MAC address is **not** the same as the one for the Ethernet card.
Also, WEP can have 4 keys. Are you entering the same one you have selected in the router? Eg, if you have selected key index 4 on the router, you will need to enter the key associated with it, not the "primary" key at index 1.
After you have run those commands, what is the output of ```
sudo iwconfig
``` Please post.

Try manually assigning an address ```
sudo ifconfig wlan0 ip  ip_address_here
``` in the range you have setup. 
Then try pinging the router ```
ping router_ip
```. If this succeeds , then you have connected and the next step is to try and figure out why DHCP won't work.

BTW, there is no need to bring the interface up manually with DHCP, the client does this for you. Assigning an address will also bring up the interface.

---

### Post by izizzle on 2009-02-08
I am having the same problem! I have a 64-Bit key that I use to connect to my network, and I cant get an option to put it in! I only see stuff like 40 bit and 128 bit. How should I go about solving this? I made a thread, but no replies so far:

[http://ubuntuforums.org/showthread.php?t=1063371](http://ubuntuforums.org/showthread.php?t=1063371)

---

### Post by squire_uk on 2009-02-08
Hey guys, I've just managed to get my wireless network to working tonight as well.....

not sure if you're having the same issues as I was, but, wouldn;'t hurt to read thru my problem, and see if it ties in, the solution worked as soon as I typed everything in correctly!!

[http://ubuntuforums.org/showthread.php?t=1064118](http://ubuntuforums.org/showthread.php?t=1064118)

good luck!.

---

