---
title: "Bittorrent Incoming Port Closed"
date: 2008-08-18
forum: Networking &amp; Wireless
---

### Post by Jerrac on 2008-08-18
I have an interesting situation that has me puzzled about what is happening.

I have my router forwarding the ports for bittorrent. But Transmission still reports the incoming port as closed. So I changed the incoming port, and Transmission said it was open. A few minutes later I checked again, and Transmission says that the port is now closed.

I am positive it is not my router, since I have the port forwarding setup correctly, and the port has been open before.

So, could my isp (Comcast) be blocking my port as soon as I start using bittorrent on it?

---

### Post by Italian Prince on 2008-08-25
I am having the same troubles though i changed it 3 times and it has always remained closed. I have set bot udp and tcp for the same port and with the correct ip address to my laptop. Advice will be greatly appreciated.

Thank You,

Italian Prince

---

### Post by Jerrac on 2008-08-25
> **Italian Prince said:**
> I am having the same troubles though i changed it 3 times and it has always remained closed. I have set bot udp and tcp for the same port and with the correct ip address to my laptop. Advice will be greatly appreciated.

Thank You,

Italian Prince

Does it affect your download or upload speeds at all? 

Mine just says there are no incoming connections. Which makes me wonder why it seems to upload just fine...

---

### Post by nhasian on 2008-08-30
even though i'm forwarding the correct port from my router two different bittorrent clients report that the port is still closed.  I even tried a few different port numbers, but no luck.  didnt we have a kernel update earlier this week? I wonder if that has anything to do with it...

---

### Post by caljohnsmith on 2008-08-30
A helpful way to troubleshoot problems like yours is to go to [www.canyouseeme.org](www.canyouseeme.org), type in the TCP port you want to test, and it will tell you if that port on your computer is open or not. Of course you have to be running your bittorent program at the time so there is a program to respond to the incoming request. 

Also, the following command is quite useful:
```
sudo netstat --tcp --listening --programs
```
That tells you what TCP ports are currently open on your computer; therefore you should see your bittorrent program's TCP port listed.

---

### Post by growingneeds on 2008-09-05
After specifically opening and forwarding the required port in my wireless router, Transmission continues to report that the port is closed. However, I am able to download the ubuntu update "ubuntu-8.04.1-desktop-i386.iso" at speeds above 150 kb/s. caljohnsmith's suggestion to [www.canyouseeme.org](www.canyouseeme.org) was helpful. So was using netstat to verify ports that are open and listening on the system. However, I prefer clicking with the GUI to typing in the Terminal: System > Administration > Network Tools > Netstat (tab) > Active Network Servies (bullet) > Netstat (button). It seems that the port has indeed been opened, but for some unknown reason, Transmission did not reflect the change.

--Working hard to embrace Debian/Ubuntu, leaving M$ WinXP in the wake.--

---

### Post by catchfinally on 2009-08-20
This is an old post but I just spent 3 days looking for the solution and I believe I have solved it. 


[LIST=1]
[*]Exit Transmission if it is running.
[*]Go to Places >> Home Folder
[*]Press Ctrl+H to show hidden files.
[*]Open up the folder .Config
[*]Drag the directory "Transmission" and **everything** in it to the desktop.
[*]Launch Transmission and the folder will be recreated and will also see your ports as open.
[/LIST]
I think the file setting.json gets corrupted but I have not narrowed it down further I just let the folder be recreated. Famous fix for Thunderbird a couple years back.

Bill Kearns
[http://www.gnidesign.com]("http://www.gnidesign.com/")
:guitar:

---

### Post by misterfixit on 2009-08-26
> **catchfinally said:**
> This is an old post but I just spent 3 days looking for the solution and I believe I have solved it. 


[LIST=1]
[*]Exit Transmission if it is running.
[*]Go to Places >> Home Folder
[*]Press Ctrl+H to show hidden files.
[*]Open up the folder .Config
[*]Drag the directory "Transmission" and **everything** in it to the desktop.
[*]Launch Transmission and the folder will be recreated and will also see your ports as open.
[/LIST]
I think the file setting.json gets corrupted but I have not narrowed it down further I just let the folder be recreated. Famous fix for Thunderbird a couple years back.

Bill Kearns
[http://www.gnidesign.com]("http://www.gnidesign.com/")
:guitar:



What about if you have Comcast and their stealth software is watching and then killing your ports?  Or do they just see a particular amount of up and down from a specific cable modem and then tighten the flow on it down to a trickle?

---

### Post by nhasian on 2009-08-26
you'll be happy to know the US Government is on your side:

[http://tech.slashdot.org/story/09/08/25/2044233/FCC-Declares-Intention-To-Enforce-Net-Neutrality](http://tech.slashdot.org/story/09/08/25/2044233/FCC-Declares-Intention-To-Enforce-Net-Neutrality)

> **misterfixit said:**
> What about if you have Comcast and their stealth software is watching and then killing your ports?  Or do they just see a particular amount of up and down from a specific cable modem and then tighten the flow on it down to a trickle?

---

### Post by misterfixit on 2009-08-27
> **nhasian said:**
> you'll be happy to know the US Government is on your side:

[http://tech.slashdot.org/story/09/08/25/2044233/FCC-Declares-Intention-To-Enforce-Net-Neutrality](http://tech.slashdot.org/story/09/08/25/2044233/FCC-Declares-Intention-To-Enforce-Net-Neutrality)

What's that saying about "I'm from the government and I am here to help you" ?

---

### Post by misterfixit on 2009-09-02
OK, I've done an experiement over the past week.  I have BitTorrent (BT) open on one of my desktops, it is downloading several movies and seeding 7 or 8 movies, plus Ubuntu 32 and 64 and a couple of Ubuntu variations.

I have the BT configure set to restrict in bound and out bound traffic to 25KB and to use an open port which I selected and tested.  The times which BT is allowed to operate (also set with the configuration parameters) is between 9pm and 6am local time.

Now for the interesting observation:  Each day at 6am when I check the system, the Cable Router (or modem or adaptor) hooked to Comcast is stalled.  The light which shows "Cable" is steadyly blinking, indicating a bad connection.  The Cable Router is a Linksys BEFCMU10.  It sits on a desk top with no obstructions and does not appear to be any warmer than "warm".  Then I have to power off the Router and power it back on to reconnect to the cable.  I also discovered that the Linsys has to be told where to save it's logs and unless preset the logs go away when the Router is power cycled.

I've just started out with a completely new log and have checked to make sure that EVERYthing is included, even "informational messages"  This seems to be the only way for me to determine for sure that something is happening to the Router during the night periods when BT is running.

Does any have any ideas or suggestions?  No need to tell me what a POS Comcast has been and still is and about their "Traffic Shaping" software (Vinewire, or Dickweed or something).  In my community it is the only wideband carrier available unless I went to Sprint 3G which is just as bad or worse.

What I will do is keep the logs and each morning after I look at them (after BT has run and the Comcast connection has been lost) to post it here for you to look at.

Wonderwhere/if BT keeps a detailed log?  Haven't found it yet even in the logs or in the BT folder.


Regards,

Dave

---

### Post by misterfixit on 2009-09-02
> **misterfixit said:**
> OK, I've done an experiement over the past week.  I have BitTorrent (BT) open on one of my desktops, it is downloading several movies and seeding 7 or 8 movies, plus Ubuntu 32 and 64 and a couple of Ubuntu variations.

I have the BT configure set to restrict in bound and out bound traffic to 25KB and to use an open port which I selected and tested.  The times which BT is allowed to operate (also set with the configuration parameters) is between 9pm and 6am local time.

Now for the interesting observation:  Each day at 6am when I check the system, the Cable Router (or modem or adaptor) hooked to Comcast is stalled.  The light which shows "Cable" is steadyly blinking, indicating a bad connection.  The Cable Router is a Linksys BEFCMU10.  It sits on a desk top with no obstructions and does not appear to be any warmer than "warm".  Then I have to power off the Router and power it back on to reconnect to the cable.  I also discovered that the Linsys has to be told where to save it's logs and unless preset the logs go away when the Router is power cycled.

I've just started out with a completely new log and have checked to make sure that EVERYthing is included, even "informational messages"  This seems to be the only way for me to determine for sure that something is happening to the Router during the night periods when BT is running.

Does any have any ideas or suggestions?  No need to tell me what a POS Comcast has been and still is and about their "Traffic Shaping" software (Vinewire, or Dickweed or something).  In my community it is the only wideband carrier available unless I went to Sprint 3G which is just as bad or worse.

What I will do is keep the logs and each morning after I look at them (after BT has run and the Comcast connection has been lost) to post it here for you to look at.

Wonderwhere/if BT keeps a detailed log?  Haven't found it yet even in the logs or in the BT folder.


Regards,

Dave


Aha!  I'm making some progress:  Here is an entry from the Router Log .. immediately after I started BT and it began to seed adn download .. via open port 6882:

Dropped packet from 192.168.0.101 to 69.231.119.130 (IP protocol 6) as unable to create new session

dave@dave-desktop:~$ whois 69.231.119.130
AT&T Internet Services SBCIS-SIS80 (NET-69-224-0-0-1) 
                                  69.224.0.0 - 69.239.255.255
rback23a.irvnca SBC06923111200020050113135528 (NET-69-231-112-0-1) 
                                  69.231.112.0 - 69.231.127.255

It doesn't want to start a connection .. but why with AT&T instead of Comcast?

Still investigating .. stand by for more infos:

Here is another message ... I think this might be a BitTorrent seeder or feed, being blocked by Comcast?

dave@dave-desktop:~$ whois 93.182.172.59
% This is the RIPE Database query service.
% The objects are in RPSL format.
%
% The RIPE Database is subject to Terms and Conditions.
% See [http://www.ripe.net/db/support/db-terms-conditions.pdf](http://www.ripe.net/db/support/db-terms-conditions.pdf)

% Note: This output has been filtered.
%       To receive output for a database update, use the "-B" flag.

% Information related to '93.182.128.0 - 93.182.191.255'

inetnum:        93.182.128.0 - 93.182.191.255
netname:        SE-VIAEUROPA-20080506
descr:          ViaEuropa i Lund AB
country:        SE
org:            ORG-ViLA1-RIPE
admin-c:        MJ1080-RIPE
tech-c:         MJ1080-RIPE
status:         ALLOCATED PA
mnt-by:         RIPE-NCC-HM-MNT
mnt-lower:      MNT-VIAE
mnt-domains:    MNT-VIAE
mnt-routes:     MNT-VIAE
source:         RIPE # Filtered

organisation:   ORG-ViLA1-RIPE
org-name:       ViaEuropa i Lund AB
org-type:       LIR
address:        ViaEuropa i Lund AB
                Winstrupsg. 1
                22222 Lund
                Sweden
phone:          +46705102360
fax-no:         +46465400150
admin-c:        MJ1080-RIPE
mnt-ref:        RIPE-NCC-HM-MNT
mnt-ref:        MNT-VIAE
mnt-by:         RIPE-NCC-HM-MNT
source:         RIPE # Filtered

person:         Max Jonborn
address:        ViaEuropa i Lund AB
address:        Winstrupsgatan 1
address:        SE-222 22 Lund
address:        Sweden
abuse-mailbox:  [email]abuse@viaeuropa.net[/email]
phone:          +46 (0)46 - 540 01 00
nic-hdl:        MJ1080-RIPE
mnt-by:         MNT-VIAE
source:         RIPE # Filtered

% Information related to '93.182.128.0/18AS47155'

route:          93.182.128.0/18
descr:          ViaEuropa Network
descr:          *************************************************
descr:          Abuse issues should be sent to:
descr:          [email]abuse@viaeuropa.net[/email]
descr:          *************************************************
origin:         AS47155
mnt-by:         MNT-VIAE
source:         RIPE # Filtered


dave@dave-desktop:~$ whois 71.199.195.41
Comcast Cable Communications, Inc. ATT-COMCAST (NET-71-192-0-0-1) 
                                  71.192.0.0 - 71.207.255.255
Comcast Cable Communications, Inc. KNOXVILLE-15 (NET-71-199-192-0-1) 
                                  71.199.192.0 - 71.199.207.255

Dave

---

### Post by mrintegrity on 2011-01-02
> **misterfixit said:**
> 
Here is another message ... I think this might be a BitTorrent seeder or feed, being blocked by Comcast?

dave@dave-desktop:~$ whois 93.182.172.59
% This is the RIPE Database query service.
% The objects are in RPSL format.
%
% The RIPE Database is subject to Terms and Conditions.
% See [http://www.ripe.net/db/support/db-terms-conditions.pdf](http://www.ripe.net/db/support/db-terms-conditions.pdf)

% Note: This output has been filtered.
%       To receive output for a database update, use the "-B" flag.

% Information related to '93.182.128.0 - 93.182.191.255'

inetnum:        93.182.128.0 - 93.182.191.255
netname:        SE-VIAEUROPA-20080506
descr:          ViaEuropa i Lund AB
country:        SE
org:            ORG-ViLA1-RIPE
admin-c:        MJ1080-RIPE
tech-c:         MJ1080-RIPE
status:         ALLOCATED PA
mnt-by:         RIPE-NCC-HM-MNT
mnt-lower:      MNT-VIAE
mnt-domains:    MNT-VIAE
mnt-routes:     MNT-VIAE
source:         RIPE # Filtered

organisation:   ORG-ViLA1-RIPE
org-name:       ViaEuropa i Lund AB
org-type:       LIR
address:        ViaEuropa i Lund AB
                Winstrupsg. 1
                22222 Lund
                Sweden
phone:          +46705102360
fax-no:         +46465400150
admin-c:        MJ1080-RIPE
mnt-ref:        RIPE-NCC-HM-MNT
mnt-ref:        MNT-VIAE
mnt-by:         RIPE-NCC-HM-MNT
source:         RIPE # Filtered

person:         Max Jonborn
address:        ViaEuropa i Lund AB
address:        Winstrupsgatan 1
address:        SE-222 22 Lund
address:        Sweden
abuse-mailbox:  [email]abuse@viaeuropa.net[/email]
phone:          +46 (0)46 - 540 01 00
nic-hdl:        MJ1080-RIPE
mnt-by:         MNT-VIAE
source:         RIPE # Filtered

% Information related to '93.182.128.0/18AS47155'

route:          93.182.128.0/18
descr:          ViaEuropa Network
descr:          *************************************************
descr:          Abuse issues should be sent to:
descr:          [email]abuse@viaeuropa.net[/email]
descr:          *************************************************
origin:         AS47155
mnt-by:         MNT-VIAE
source:         RIPE # Filtered


dave@dave-desktop:~$ whois 71.199.195.41
Comcast Cable Communications, Inc. ATT-COMCAST (NET-71-192-0-0-1) 
                                  71.192.0.0 - 71.207.255.255
Comcast Cable Communications, Inc. KNOXVILLE-15 (NET-71-199-192-0-1) 
                                  71.199.192.0 - 71.199.207.255

Dave

Digging up a random old thread here but this is the ip address of an ipredator user (Swedish pirate bay anonymizing vpn service). Something I just happened to get working :D

:)

---

