---
title: "Some Wirelesstrouble (popular item isn't it?)"
date: 2005-04-29
forum: Networking &amp; Wireless
---

### Post by ZC3rr0r on 2005-04-29
Okay,after strolling around the forums for some time, I have no other option than to just ask the question myself.

The situation: 
Ubuntu recognises my wireless card (SMC 2835W) as a Prism GT, which is correct by my knowledge. My router is a SMC 2804WBR, which supports wireless 802.11 b/g connections. 
I used it under windows for some time now, using both wpa and wep based on a passphrase, and I never had any problems. 
Under ubuntu however, I enter my WEP key (i disabled wpa so that it'll work with Ubuntu) and select DHCP to setup my connection. 

The problem:
Although I already disabled WPA, my card recieves no ip address from the DHCP on my router. I have virtually no clue as to what the reason might be, cause everything seems to be fine. I mean, the chipset is recognised, wep key is correct, SSID is correct, even the connection tool shows it can find the network, and it says my conection is between 89% and 100% quality. But despite all this, I still get no ip to use for my wireless connection.

My attempt to fix it:
I decided not to use DHCP anymore, so I entered an ip address withint the range my router was in (192.168.2.x) and entered the router's address as the gateway (192.168.2.1). this fixed nothing,for I was still unable to pint anything, including the gateway itself.

Any ideas / tips / sollutions are welcome. I'm all out of ideas.

---

### Post by dave9191 on 2005-04-29
Are you trying to connect with the GUI tools or through the command line? I connect through the command line, i have a nice script for that. Below are the commands that I use to set my connection up. This assumes that eth1 is your wireless adaptor. And i use 128bit wep. 

```

sudo iwconfig eth1 essid YOUR-NETWORK-ESSID
sudo iwconfig eth1 key YOUR-WEP-KEY
sudo iwconfig eth1 key restricted
sudo iwconfig eth1 ap YOUR-ACCESS-POINT-MAC-ADDRESS

```

Then you can use
```

iwlist eth1 scanning
```

to see if it has connected yet or its still trying. If it says 'unassociated'  it means its still trying. When it connects you can use
```

sudo /sbin/dhclient eth1

```

to get an IP through DHCP. 

I use a scipt for all that mainly because there are several networks i connect to in different places. So when i boot i just run the script that sets up that network depending where i am.

---

### Post by az on 2005-04-29
This is unusual since the prism54 driver is really really good.  Your card should work out of the box.  You can even get wpa working, I beleive by installing some additional packages and poking around.

The networking tool should work fine for you.  

If it were another kind of card that had a so so driver, I would think up something else but....

---

### Post by ZC3rr0r on 2005-04-29
Well, that's exactly the problem, I went through these steps before (with a cisco wlan card on a diff laptop) and it worked, even without entering the ap mac. Now I get this response when i sudo /sbin/dhclient eth1:

Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:04:e2:a5:d0:91
Sending on   LPF/eth1/00:04:e2:a5:d0:91
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

I figure since there is a hardware error something is wrong, but I can't figure out what.

Besides, it'd be nice if I could use the GUI tool in the future though, this way I can save my sister a load of headache's (she a true 100% Windows-no-know ;) ).

---

### Post by dave9191 on 2005-04-29
After entering the the iwconfig stuff, do a iwlist eth1 scanning. If it says unassociated, then dont bother doing a  dhcp scan. And "sit0: unknown hardware address type 776" just means it couldnt do a dhcp scan on your firewire port.

---

### Post by ZC3rr0r on 2005-04-29
I listed mypci devices,perhaps this helps:

0000:02:00.0 Network controller: Intersil Corporation Intersil ISL3890 [Prism GT/Prism Duette] (rev 01)

This is my wireless according to Ubuntu. 

My wireless surroundings look like this:

 Cell 01 - Address: 00:04:E2:BA:02:0E
                    ESSID:"SMC"
                    Mode:Master
                    Encryption key:on
                    Frequency:2.437 GHz (Channel 6)
                    Quality:87/0  Signal level:-83 dBm  Noise level:-170 dBm
          Cell 02 - Address: 00:0C:F6:0C:EF:F3
                    ESSID:"VeBe"
                    Mode:Master
                    Encryption key:on
                    Frequency:2.442 GHz (Channel 7)
                    Quality:86/0  Signal level:-84 dBm  Noise level:-170 dBm

And iwconfig for eth1 (wlan) looks like this:

IEEE 802.11b/g  ESSID:"SMC"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:04:E2:BA:02:0E
          Bit Rate:1 Mb/s   Tx-Power=31 dBm   Sensitivity=20/200
          Retry min limit:8   RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:3139-6170-7269-6C31-3938-35   Security mode:restricted          Link Quality=60/0  Signal level=-84 dBm  Noise level=-160 dBm
          Rx invalid nwid:0  Rx invalid crypt:1  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

B.t.w. I had to use apassphrase insteadof akey so I did sudo iwconfig ehti key s:passphrase. Not much differance,but a whole world of differance in connecting to my ap ;)

---

### Post by dave9191 on 2005-04-29
with that output everything should work fine on the wireless...

---

### Post by ZC3rr0r on 2005-04-29
Precicely, but it doesn't, I just get the output I posted above, it can't get dhcp from whatever.

Besides, you are so right, that is my firewire...dumb me....:S Sorry.....

---

### Post by ZC3rr0r on 2005-04-29
And if you'd like to know what dmesg reports back about it:

eth1: resetting device...
eth1: uploading firmware...
eth1: firmware version: 1.0.4.3
eth1: firmware upload complete
eth1: interface reset complete
eth1: no IPv6 routers present

Perhaps the firware version is incorrect? (Just guessing, I seriously have no clues anymore)

---

### Post by dave9191 on 2005-04-29
Im affraid that if that doesnt work, then I cant help you :( Sorry, i cant think of anything either.

---

### Post by ZC3rr0r on 2005-04-29
I was affraid so :(
Azz, you mentioned it should work? Any thoughts on it now? I can provide any output you need, I just wanna get this fixed, becuase I use wireless like 99% of the time for my connections.

---

### Post by dave9191 on 2005-04-29
[QUOTE=ZC3rr0r]
Frequency:2.442 GHz (Channel 7)

Encryption key:3139-6170-7269-6C31-3938-35   Security mode:restricted         

Rx invalid nwid:0  Rx invalid crypt:1  Rx invalid frag:0
[/QUOTE]

Hey, i just had another read through your output. I it is 2.30 am so I could be seeing things. 

But in the scan the freq is 2.442 and in the iwconfig its different. Try setting the freq using the iwconfig command. 

iwconfig does not output the encryption key and security mode once its fully connected and working. 

And Rx invalid crypt... does that mean by any chance that the key has been rejected ?

Just a few questions of a tired man. 

Dave

---

### Post by ZC3rr0r on 2005-04-30
Almost right,but it just might be that I'm tired too. My accesspoint is on 2.437, the SSID is SMC, and by my knowledge the passphrase is ok. I'll give it a go without encryption, and let you know how that went.

---

### Post by ZC3rr0r on 2005-04-30
Okay, without the encryption, i get the following output from sude /sbin/dhclient:

Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:04:e2:a5:d0:91
Sending on   LPF/eth1/00:04:e2:a5:d0:91
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
bound to 192.168.2.155 -- renewal in 237980 seconds.

Which would indicate it works, but it doesn't check my ping to my ap:

PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
From 192.168.2.166 icmp_seq=1 Destination Host Unreachable
From 192.168.2.166 icmp_seq=2 Destination Host Unreachable
From 192.168.2.166 icmp_seq=3 Destination Host Unreachable
From 192.168.2.166 icmp_seq=5 Destination Host Unreachable
From 192.168.2.166 icmp_seq=6 Destination Host Unreachable
From 192.168.2.166 icmp_seq=7 Destination Host Unreachable

And this is what iwconfig tells me:

 IEEE 802.11b/g  ESSID:"SMC"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:04:E2:BA:02:0E
          Bit Rate:1 Mb/s   Tx-Power=31 dBm   Sensitivity=20/200
          Retry min limit:8   RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:off
          Link Quality=94/0  Signal level=-82 dBm  Noise level=-161 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

It still says invalid crypt,even though I get an IP, and i turned wep and wpa off. I set iwconfig to enc: off as well. Any ideas after this? I'm guessing an unencrypted ap should be esay, but apearantly it isn't....

{edit} I just noticed i get replies via 192.168.2.166, so i checked i was using wth1 with ping 192.168.w2.1 -I eth1 but it didn'teven turn up the unreachable messages, just a lot ofloss.

---

### Post by ifrflyer on 2005-04-30
Dave9191 I don't mean to hijack the thread but what you guys are speaking about really helps me. One thing: you said, 

> Are you trying to connect with the GUI tools or through the command line? I connect through the command line, i have a nice script for that. Below are the commands that I use to set my connection up. This assumes that eth1 is your wireless adaptor. And i use 128bit wep. 

That would be wonderful. All my woes seem to come from the GUI connection "manager," which appears to not allow me to override it. Can you please tell me if you know how I can override that from even starting? I'd love to connect using a script or command line. . .  

Thanks in advance

---

### Post by dave9191 on 2005-04-30
Im guessoing that your AP normally responds to pings. An unencrypted and enrypted ones should be just as easy to set up. 

Im guessing that since it aquired the IP address now it was having some trouble with the key.

And the output from that ping thing is kinda weird. 

From 192.168.2.166 icmp_seq=1 Destination Host Unreachable

That should be the IP address that you have been assigned - 192.168.2.155.


And as for the invalid crypt it says 0 next to it, so there are no errors with that.

---

### Post by dave9191 on 2005-04-30
[QUOTE=ifrflyer]Dave9191 I don't mean to hijack the thread but what you guys are speaking about really helps me. One thing: you said, 

 

That would be wonderful. All my woes seem to come from the GUI connection "manager," which appears to not allow me to override it. Can you please tell me if you know how I can override that from even starting? I'd love to connect using a script or command line. . .  

Thanks in advance[/QUOTE]


First of all you need to get rid of any settings you might have in the graphical tools. Then go to the network config file (/etc/network/interface). Edit that as root and comment out (put # infront of it) any code that configures a connection. In my case all i had to comment out was 

#iface eth0 inet dhcp

Then when you start up, confiuguring network interfaces should be lightning fast and when you load up you can run your own network connect script. 

And Im glad that this thread has helped you :) 

Dave

---

### Post by ifrflyer on 2005-04-30
Thanks for that! 

One thing I see in /etc/network/interfaces 

is

```
iface eth0 inet dhcp
wireless-essid fg-wire
wireless-key blahblah
auto eth0
``` 


These are the ones to comment out, right? Thanks again!

---

### Post by dave9191 on 2005-04-30
They look like tho ones. If something goes wrong you can always uncomment them :) But everything should be a ok :)

---

### Post by ZC3rr0r on 2005-05-01
Hey Dave, I somewhat fixed it. I used my fluke to find 192.168.2.166, and it turned out to be my other interface on my laptop. ifconfig eth0 down fixed that, and now my wireless works like a charm, but without wpa and wep. I'll give that a go now,and I'll let you know what problems I encounter.

---

### Post by ZC3rr0r on 2005-05-01
I found the problem, check this:

key/enc[ryption]
              Used  to  manipulate  encryption or scrambling keys and security
              mode.
              To set the current encryption key, just enter  the  key  in  hex
              digits  as  XXXX-XXXX-XXXX-XXXX or XXXXXXXX.  To set a key other
              than the current key, prepend  or  append  [index]  to  the  key
              itself (this won’t change which is the active key). You can also
              enter the key as  an  ASCII  string  by  using  the  s:  prefix.
              **Passphrase is currently not supported.**
              To  change  which  key  is  the currently active key, just enter
              [index] (without entering any key value).
              off and on disable and reenable encryption.
              The security mode may be open or  restricted,  and  its  meaning
              depends  on  the  card  used.  With  most cards, in open mode no
              authentication is  used  and  the  card  may  also  accept  non-
              encrypted  sessions,  whereas  in restricted mode only encrypted
              sessions are accepted and the card will  use  authentication  if
              available.
              If  you  need  to set multiple keys, or set a key and change the
              active key, you need to use multiple key  directives.  Arguments
              can be put in any order, the last one will take precedence.

It seems as if iwconfig just doesn't support passphrase keys, so I changed mine to hex, and now it works with wep. wpa is still no go though.

---

### Post by dave9191 on 2005-05-01
YEAY :D

As for wpa I have not tired it. My old AP didnt support wpa, and when I installed my new one, i just used the same settings to save editing the config on all my machines. If I ever give that a go, Ill give you a shout how it went.

Dave

---

### Post by ZC3rr0r on 2005-05-01
I just installed the wpa support package, but I can't find it anywhere,my locate just turns up nothing....:S Gonna have another go at this one later today, but first I'm gonna celebrate my victory over iwconfig ;)

---

### Post by dave9191 on 2005-05-01
do a  

sudo updatedb  

to update the locate database to include newly installed files. It will take a couple min to run and ubunutu does it by itself every now and then.

---

### Post by ZC3rr0r on 2005-05-01
I know, I'm just to lazy to do it now. I've been trying to speed up my boot by removing some lines from /etc/interfaces but when I remove the auto tag things go wrong,and when I keep it there, but I don't plugin a cable, things go wrong too. :S

As for wpa, it's a package called wpasupplicant, you can get it off Ubuntu universe if I'm not mistaken.

---

### Post by dave9191 on 2005-05-01
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
#iface eth0 inet dhcp

``` 

Thats how my interface file looks. The configuring network interfaces is pretty much instant on boot. And I might mess about with wpa in a few weeks after my exams :)

---

### Post by Vincent_Lin on 2005-05-03
Dear all,

I have been following this thread with great interests and have been learning a lot of wireless networking under ubuntu.  Obvious reason is that my Intel Pro/Wireless LAN 2100 3B (rev 04) on IBm x31 is not working/connecting to Verizon DSL through a NetGear wireless router.

My situation is very strange.

Basic - I had (before ubuntu) set ESSID and WEP key before on the router, and the channel/frequcncy is set to channel 11. 

sudo iwlist eth0 scanning - returns a number of cells, two of them being my NetGear router (MAC address shows that).  One with my pre-set ESSID, the other being <hidden>.  Someone mentioned this before in the forum.  Channel shows 11 on both cell.

sudo iwconfig eth0 ap xx.xx.xx.xx.xx (MAC address of NetGear) has never really register this MAC address onto my eth0.  Following iwconfig eth0 returns ap as 00.00.00.00.00.

And then sudo iwconfig eth0 chennel 11 - returns SET failed on device eth0: Operation not supported.  The same results happens when I sudo iwconfig etho freq 2.462G.

SO, I could not set channel/frequency on my Intel 2100 3B card, and I can't register ap MAC onto the said card.  Wireless networking never works on this machine/card under ubuntu.

I had to state that during installation, ubuntu recognized this card and downloaded updates, etc... via this wireless card.

Have you guys experienced this?

Thanks for all the help.

Vincent

---

### Post by ifrflyer on 2005-05-03
Lovely to see that we may very well be getting to the crux of this, and I am delighted that your router is netgear and not Linksys - because some had posted elsewhere that Linksys routers may have been the problem. 

However, I think that this thread may very well have uncovered a feature: if we suppose, and we just have, that Intel Pro wifi cards seem to detect the hidden ESSID sent by routers attempting to hide the ESSID, then holy crap, this is something else!

 :-P 

Okay, okay, let me get hold of myself. I actually don't think that this is the case.  I suspect a caching issue somewhere; the card connects once and stores the information about the ESSID and somehow doesn't refresh. 

I guess the only way to test  is to 

1. Connect with an ESSID which is broadcast in the clear. 
2. Reconfigure the router with a new ESSID
3. Reconfigure the router to HIDE the new ESSID
4. do some version of iwlist [interface] scanning  either commandline or GUI

If we see both ESSIDs (the hidden and the old, or just <hidden> and <old-essid>)  I guess that means we have a cacheing issue. If we see <hidden> and the *new* ESSID, then I guess we have a genuine x-ray vision wifi card , and a whle new set of problems!

Does anyone agree with this/have a better way to proceed?

---

### Post by dave9191 on 2005-05-03
Vincent_Lin, your problem is strange to me. If you set the ap mac address give it some time to associate the connection. With my b standard access point this could take up to 2 min, but on my g standard its done in a few sec. If its still saying 00.00.etc then see if any of the error counters at the bottom are incrementing. If you arent sure then post the result of "iwconfig" here (blank out any sensitive data if you want". 

As for operation not supported this is probably a limitation of the driver as it stands right now. But the channel or freq should be set when the card associates with the AP. If not then there is a problem with your settings somewhere if this worked during the install. Maybe the installer was using a different wireless driver for your card. 



And ifrflyer, thats prolly the best way to go about things. Other then a getting a computer that never saw the network in the first place and seeing if that sees the hidden essid. I sometimes pick up a network with a hidden essid, and that only has one entry on the scan as hidden and no other entry with the essid disclosed. 

Im guessing that hidden essids should never come up as the AP should not be transmitting them. So its prolly a chacheing issue. Id look into that, but I dont have one of them wireless cards :)

---

### Post by Vincent_Lin on 2005-05-04
Thanks.

Here is the output of sudo iwconfig --version

vincent@x31:~/Docs$ sudo iwconfig --version
iwconfig  Wireless-Tools version 27
          Compatible with Wireless Extension v11 to v17.

Kernel    Currently compiled with Wireless Extension v17.

eth0      Recommend Wireless Extension v16 or later,
          Currently compiled with Wireless Extension v17.

After poking around a bit, I noticed that I could actually set key by pasphrase by using  s: prefix to a string double quoted, ie sudo iwconfig eth0 key s:"this is me" and iwconfig did not complain, but register a different result/key than the WEP key  I see generated by my NetGear using the same passphrase.  Maybe I should forget about using passphrase, since I am not able to use it after initial setup, why bother.

Other back ground.  

I checked Verizon web-site and found the DNS entried for my area (Boston, MA) and now wired networking via this NetGear router works.

I also checked to run static ip instead of dhcp and both worked for wired connection via my NetGear ap.  Actually, this ap has been running all time during my test since my wife could go on the net all time from her xp laptop, a better version of Intel 2200BG with 54 Mbps full speed.

What else?  

Thanks.


Vincent

---

### Post by dave9191 on 2005-05-04
[QUOTE=ZC3rr0r]
              **Passphrase is currently not supported.**
[/QUOTE]

Its in the iwconfig manual. You need to use a hex key instead. 

And what about us seeing the iwconfig output after you input the mac address ?

---

### Post by Vincent_Lin on 2005-05-06
I found the cause my wifi problem.

I removed wireless utilities (iwconfig, iwlist, etc..., version 27, as indicated in my last post) using synaptic package manager, and then installed wireless utilities, again.  This time, it is still at version 27 (sudo iwconfig --verion shows exactly the same as previous installation has), but this package has 27-1ubuntu1 as the version number.

Now, my Intel 2100 3B is working to access an open ap now.

I have to go home and test with my NetGear ap with set WEP.

Will let you all know soon.

Vincent

ps. I was even playing sudo route stuff, as it was often mentioned in other threads as well.  sudo route add default gw xxx.xxx.xxx.xxx failed with SIOCADDRT error.  Anyway, many funny stuff - default gateway sticks for wired connection eth1, but it never worked for wireless eth0.    A very exciting learning process, indeed.

---

### Post by Vincent_Lin on 2005-05-11
OK.  Here is what happened:

1. As my last post stated, after having reverted back to wireless-utils signed by ubuntu, I have wireless access via my ipw2100, as eth0.

2. I removed ESSID and WEP KEY entries from eth0 section in /etc/network/interfaces file but kept auto eth0 there so that wireless interface will be brought up right after boot.

3. So, I boot up the machine (IBM x31) and this eth0 picked up whatever wireless AP I can access.  Two examples: when I am at work, this machine picks up the signal from an public AP set up by the company downstairs. When at home, (after a fresh boot, or just let gnome-menu-system-management-network select any available AP out there, and this machine picks up an AP, I think, from an unknown neighbor(whoes ESSID is, you might've guessed it - linksys).  In both cases with AP without keys, the MAC of both APs were unknown to me (even I could have used iwlist scanning to get them, but I did not) and ESSID were given to me in gnome setup screen.  It also happens after booting freshly.

4. However, I still could not use my own AP which has WEP key setup.  I haven't tried another AP with WEP key setup since I don't know anyone else has such setup. yet.

5. In these learning process, I kindof think that I figure out how the handshaking of wireless networking works.  As long the driver/firmware/wireless-utils are installed properly, all information you need to give to iwconfig stuff is ESSID, provided that the AP you are trying to access is open without key, and ESSID and KEY if the AP has WEP setup.  All other parameters/options such as channel/frequency stuff are taken care of by the handshaking process.  I SHOULD NOT have to worry about those options.

6. /sbin/dhclient should then help you to setup domain, DNS, and default gw stuff, provided that the communication in above point is done.

7. So why my NetGear AP with WEP could not work with my ipw2100, is beyond me.  I am sure my AP is working because I could dual/boot this x31 into YouKnowWho and access internet via proper shared WEP key setup.  So does my wife's T42 with 802.11g card (translated into ipw2200 if I could convince her to install ubuntu).  

Any comments?  Thanks.

Vincent
PS. I am typing this while I am accessing the forum en route my neighbor's, who-knows-who-he/she-is, linksys AP with ESSID "linksys".

PPS. I will find sometime during weekend to disable my NetGear AP to see what will happen.

---

### Post by dave9191 on 2005-05-11
Yeh, that pretty much spot on. Once you establish the connection, dhclient will setup all the other parts of it for you like IP, gateway, name servers and so on. 

But since you dont seem to want to post the output of iwconfig, i cant really see whats going on with it and try to help you.

Dave

---

### Post by ifrflyer on 2005-05-11
I believe I have the answer to MY problem, and I have written a how to to share it. I can only hope someone makes a sticky 

Problem:
Users of Ubuntu 5.04 with computers which use the Intel® Pro/Wireless 2200 802.11B/G WLAN experience troubles including:

    * Intermittent connectivity
    * Inability to switch between networks or regain a lost network connection without rebooting
    * Inability to configure wireless connection using Network Connection GUI 

Cause:
Ubuntu 5.04 Hoary Hedgehog ships with version 0.19 of the driver for this card. The current version is 1.0.3. The stable version is 1.0.0, and this is the version it is recommended to use with Ubuntu. Of course, you can try any version you like!

Solution:
Remove completely version 0.19 and upgrade to version 1.0.*


HOW TO:
[http://nickselby.com/articles/technology/index.htm?a=1807](http://nickselby.com/articles/technology/index.htm?a=1807)

---

### Post by Vincent_Lin on 2005-05-12
Dear all,

Mt problem is solved - thank to all of the response I received.

In particular, from this thread [http://ubuntuforums.org/showthread.php?t=32002](http://ubuntuforums.org/showthread.php?t=32002) someone mentioned the open mode/instead of shared mode should be set on the AP.  Mine was set to shared.  Changed that to open, and I am surfing via my own AP!  No more stealing other people's bandwidth!!!

This forum is great!   People are great!  
 
Thanks to all again.

Now I have to figure out ACPI for battery and CPU scaling stuff, plus sleep/wakeup issues.  One at a time, right?

Happy Vincent

---

### Post by dave9191 on 2005-05-12
Glad you got it sorted :) 

Although mine works fine with shared mode on. And I find that CPU scaling works out of the box for me. And you'll get there, one thing at a time  :grin:

---

### Post by adamvert on 2005-05-21
Count me in as just one more with IPW2200 problems... except that I've tried versions 1.0, 1.0.3 and 1.0.4 of the driver, and whichever one I try, I still can't change ESSID without doing

```
sudo ifdown eth0; sudo rmmod ipw2200; sudo modprobe ipw2200; sudo ifup eth0
```

Which wouldn't be a problem, except that I keep getting moved to a different ESSID while I'm working, and I'm getting sick of having to enter the commands manually, and retype my #!@ing password for the nth time.

And what I really don't understand is how come this worked fine in Warty?  I used to be able to move between ESSID's to my heart's content.

So if anyone has any ideas about what more I could do in terms of installing drivers or setting settings (I've been following the relevant instruction for compiling and installing ipw2200 drivers), I would be *very* happy!

I've got a Toshiba M30 Centrino laptop...

thanks,
Adam

---

### Post by adamvert on 2005-05-21
Ha!  Thankyou Vincent Lin!

After sending that last post, I was reading through the parts of this thread that I hadn't got to yet (I know, I know, read *then* post), and I read Vincent's report about reinstalling wireless-tools.  Tried it out and lo and behold, it works!

Sorry for taking up space here, but maybe this is a hint for others, if all else fails - just try reinstalling wireless-tools via synaptic.

Adam

---

### Post by pnhughes on 2005-09-12
[QUOTE=adamvert]<snip>
And what I really don't understand is how come this worked fine in Warty?
<snip>
[/QUOTE]

THANK you!  Wireless support (Shared, WEP) on my Thinkpad T42 worked perfectly in Warty, but has been borked every since upgrading to Hoary and beyond.  Now trying Kubuntu 5.10 preview, and I see that the problem has still not been resolved.  

I'm not trolling - I'm off to try the many good suggestions here - but I'm left wondering why support for what seems to be a very common wireless config has been changed/omitted in newer distributions...

---

