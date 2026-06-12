---
title: "Can't connect to AccessPoint"
date: 2006-07-24
forum: Networking &amp; Wireless
---

### Post by Koziasty on 2006-07-24
Hi. I have recently installed ubuntu on my desktop. Thanks to wonderful howto, I installed wireless ethernet ([http://ubuntuforums.org/showthread.php?t=197102&highlight=ndiswrapper+howto)](http://ubuntuforums.org/showthread.php?t=197102&highlight=ndiswrapper+howto)).

However, I cannot manage to connect to the access point. 

Funny enough, after typing *iwlist wlan0 scan*, i have no results. Yet, after running Administration -> Networking, and trying *iwlist scan*, the output is somehow positive (i.e. there is my access point listed there, as well as my neighbour's one).

I cannot connect to any of them, neither using DHCP nor by typing IP and the other stuff. 
I guess I should add some logs, but I'm writing this from under Windows (where wireless works perfect) and don't really know what logs should I have copied, so please, if you need them, just tell me ;)

Regards, 
Koziasty

Sorry for my poor and chaotic English ;)


PS One more thing - I tried Kubuntu as well - the wireless worked perfectly (but othyer thins didnt, so I dont really llike the idea of using Kubuntu)

---

### Post by it.henrik on 2006-07-24
hmm ok .. are you using NetworkManager or the tool from SYSTEM -> ADMINISTRATION -> NETWORKING or something else.

if you just run iwconfig in a terminal, what does it say? Are you connected to an access point? 

For me it looks like this when I am connected:

henrik@ubuntu-Latten:~$ iwconfig
lo        no wireless extensions.

sit0      no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"secret"  Nickname:"secret"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:90:4B:31:7E:BC
          Bit Rate:11 Mb/s   Sensitivity:1/3
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=45/92  Signal level=-44 dBm  Noise level=-89 dBm
          Rx invalid nwid:0  Rx invalid crypt:266  Rx invalid frag:28335
          Tx excessive retries:134  Invalid misc:0   Missed beacon:0

henrik@ubuntu-Latten:~$

Notice the "Access Point: 00:90:4B:31:7E:BC" this indicates that I am connected to the access point with my wireless network card eth1. You will have some other output after "Access Point:" when you are connected to your access point. 
If you do not have anything after "Access Point:" it means that you are not connected.  If you are connected to the access point and you are running a DHCP server on your network, you can ask for a ip adress by running

sudo dhclient

Otherwise if you are not running a DHCP server you need to assign the IP your self.. but start with this and let us know what happens :)

If you want a graphical tool for connecting to your wireless network I recomend wifi-radar. You can install it through synaptics.

---

### Post by Koziasty on 2006-07-24
Hi, thanks for your reply.

[QUOTE="IWCONFIG"]
koza@koza-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11g  ESSID: off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
[/QUOTE]

Regarding your post, it means my wlan card is not connected to an access point, right?

> 
-----Before going to System-Administration-Networking------
koza@koza-desktop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wlan0     No scan results

sit0      Interface doesn't support scanning.

and
> 
-----After going to System-Administration-Networking and pressing on Wireless Connection------
koza@koza-desktop:~$ iwlist scan
wlan0     Scan completed :
          Cell 01 - Address: 00:11:F5: D2:82:3E
                    ESSID:"BTVOYAGER2091-3E"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.447 GHz (Channel 8 )
                    Quality:0/100  Signal level:-54 dBm  Noise level:-256 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0



          Cell 02 - Address: 00:14:7C:52:F2:6A
                    ESSID:"3Com"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-78 dBm  Noise level:-256 dBm
                    Encryption key: off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0


I have installed WiFi radar - again, it can see the networks, but it cannot connect to mine. (There is a prompt message that it couldn't obtain an adress, which is strange, since my router does use DHCP)

Regards
Koziasty

---EDIT----
I have kind of succeeded in connecting to the router using the wifi-radar tool. Still, however, I cannot obtain an adress and manual setting does not work.



-------------------------------------------------------
OK, completely succeeded in setting up the card. I had to remove the WEP encryption off my router. Now it is working like a charm, In a nearby future I am going to set it up again. Keep yer fingers crossed please;)

Regards

---

### Post by it.henrik on 2006-07-24
If you did shut off the WEP encryption .. I would seriously recommend that you enable mac-filtering on the router, so only your network card with your mac-adress can connect.

I did once had a problem with a ndiswrapper that didnt support WEP ... could be the same problem as yours.

---

### Post by Koziasty on 2006-07-24
I have already enabled MACfiltering. Thanks for your help  :-) 

Regards, Koziasty

---

