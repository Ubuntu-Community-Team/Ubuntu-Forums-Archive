---
title: "Some Wireless questions"
date: 2006-11-06
forum: Networking &amp; Wireless
---

### Post by Nirva on 2006-11-06
Hay,


I am working with Ubuntu 6.10 and I have a intel wireless 2200BG card.
I am trying to crack my own network just to see if I could do it ( yeah sure ;-)  ).  I first installed the newest IPW2200 drivers wich support RFMON.
I think everything went fine but I am not sure I copied the firmware to the right location.  
Is there a way how I can check wich version of the drivers I am running right now? 
When I type : ' sudo config eth1 mode monitor '
He actually changes to monitor mode, so I think the driver install went fine.  But when I start airodump, this happens : 


sudo airodump eth1 testje 7

Unsupported hardware link type  803 - expected ARPHRD_IEEE80211
or ARPHRD_IEEE80211_PRISM instead.  Make sure RFMON is enabled:
run 'ifconfig eth1 up; iwconfig eth1 mode Monitor channel <#>'

The same happens when I start aireplay :

sudo aireplay -b 00:13:10:B1:A6:1C -x 512 eth1 -3

Unsupported hardware link type  803 - expected ARPHRD_IEEE80211
or ARPHRD_IEEE80211_PRISM instead.  Make sure RFMON is enabled:
run 'ifconfig eth1 up; iwconfig eth1 mode Monitor channel <#>'


I used to be able to start kismet, but now he gives me this : 
filip@Filip:~$ sudo kismet
Server options:  none
Client options:  none
Starting server...
Will drop privs to filip (1000) gid 1000
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
Source 0 (ipw2200): Enabling monitor mode for ipw2200 source interface eth1 channel 6...
Waiting for server to start before starting UI...
Source 0 (ipw2200): Opening ipw2200 source interface eth1...
Spawned channelc control process 15660
Dropped privs to filip (1000) gid 1000
Allowing clients to fetch WEP keys.
Logging networks to Kismet-Nov-06-2006-6.network
Logging networks in CSV format to Kismet-Nov-06-2006-6.csv
Logging networks in XML format to Kismet-Nov-06-2006-6.xml
Logging cryptographically weak packets to Kismet-Nov-06-2006-6.weak
Logging cisco product information to Kismet-Nov-06-2006-6.cisco
Logging gps coordinates to Kismet-Nov-06-2006-6.gps
Logging data to Kismet-Nov-06-2006-6.dump
Writing data files to disk every 300 seconds.
Mangling encrypted and fuzzy data packets.
Tracking probe responses and associating probe networks.
Reading AP manufacturer data and defaults from /usr/local/etc/ap_manuf
Reading client manufacturer data and defaults from /usr/local/etc/client_manuf
Using network-classifier based data encryption detection
Dump file format: wiretap (local code) dump
Crypt file format: airsnort (weak packet) dump
Kismet 2006.04.R1 (Kismet)
Logging data networks CSV XML weak cisco gps
GPSD cannot connect: Connection refused
Listening on port 2501.
Allowing connections from 127.0.0.1/255.255.255.255
Failed to set up UI server: TcpServer bind() failed: Address already in use
Didn't detect any networks, unlinking network list.
Didn't detect any networks, unlinking CSV network list.
Didn't detect any networks, unlinking XML network list.
Didn't detect any Cisco Discovery Packets, unlinking cisco dump
Didn't capture any packets, unlinking dump file
Didn't see any weak encryption packets, unlinking weak file
Sending termination request to channel control child 15660...
Waiting for channel control child 15660 to exit...
WARNING: Sometimes cards don't always come out of monitor mode
         cleanly.  If your card is not fully working, you may need to
         restart or reconfigure it for normal operation.
Kismet exiting.
[1] + Done                       ${BIN}/kismet_server --silent ${server}


Does anyone has any idea?

PS : A little conclusion :

1) Is there a way how I can check wich version of the drivers I am running right now? 
2) Aireplay + Airodump problem ( wich probably has the same solution )
3) Kismet problem ( wich also might have the same solution, but I don't think so, cause I already could use it sometimes )


Thanks


Edit : The Kismet problem is solved

---

### Post by Gianluca-VLSI-vs-Coss-TDS on 2006-12-07
Unsupported hardware link type  803 - expected ARPHRD_IEEE80211
or ARPHRD_IEEE80211_PRISM instead.  Make sure RFMON is enabled:
run 'ifconfig eth1 up; iwconfig eth1 mode Monitor channel <#>'

Eso me pasa a mi exactamante lo mismo, he intentado usar los controladores del repositorio y ese es el efecto que consigo, ademas de compilarme los de ieee80211 y ipw2100 por mi mano, conseguir compilarlos, y me da el mismo error, la verdad no lo entiendo ](*,)

---

### Post by ahave on 2007-02-09
I too have this same issue.(same error code, same hardware, except Kismet will run fine)  when i try to use airodump i get the same error..even though i can confirm that my wireless card is in monitor mode and set to the correct Hz

did you come across a solution? or are there other IV extraction tools out there other than airodump?

---

### Post by gradedcheese on 2007-02-09
Kismet needs to be configured first -- have you done it?  Take a look at /etc/kismet/kismet.conf and at least fill out the 'source=' section.  You can look online at the kismet manual to see what you need to put there for your driver/card.  Also a quick hint: if you know the network's channel (ex: 6) tell Kismet to scan only that channel.  You can do that by specifying the channel at the command line, or setting the initial channel in the configuration file (also on the source= line).  Then disable the channel hopper by giving kismet a '-X' when you run it.  If you don't do this, Kismet has to multiplex (hop channels), greatly reducing its ability to grab every possible packet.

---

### Post by ahave on 2007-02-09
I do have Kismet configured and working properly. The problem i have is when i try to use airodump.

would it be possible to log the packets with kismet then use the dump files to extract the IV's with airodump/some other program? that way airodump does not have to use any hardware.

---

### Post by gradedcheese on 2007-02-10
Yeah, you can probably do that (kismet's logs are very detailed).  Try opening one in Wireshark (or Ethereal if you have the older version) and see what 802.11 packet info you have.

---

