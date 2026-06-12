---
title: "Why does Windows/Ubuntu Tracert differ?"
date: 2006-09-11
forum: Networking &amp; Wireless
---

### Post by ldc_1 on 2006-09-11
Hello

Since building my ubunto systems I have had many network issues with GAIM not connecting for days on end, sometime Firfox does not want to connect or is very slow. Trying to get to the same places using my Windows box is not a problem. I am using all the defualt DHCP setting on the ubunto systems. I even rebuilt one ubunto system, the system worked great after the rebuild using the lattest CD, the problem is that I built the system from the same CD a few weeks back and it ran well for a while. All we did was use GAIM and Firefox on it.

1. At the end of this is some output from GAIM, was hoping someone might see a network error that means something to them.

2. The tracrt from the ubuntu system is attached:

3. Here is the tracert from the windows box to google:

C:\Documents and Settings\Administrator>tracert google.com
 
C:\Documents and Settings\Administrator>tracert google.com
 
Tracing route to google.com [64.233.167.99]
over a maximum of 30 hops:
 
  1     1 ms    <1 ms    <1 ms  192.168.0.1
  2    33 ms    26 ms    26 ms  wltonhbas01-lo0.network.tds.net [69.21.254.1]
  3    41 ms    39 ms    37 ms  nycmnyhed01-a0-0-1310033.network.tds.net [69.128
.250.157]
  4    37 ms    47 ms    36 ms  nycmnycor02-gi2-0.network.tds.net [64.50.237.68]
 
  5    43 ms    39 ms    37 ms  core1-0-0-8.lga.net.google.com [198.32.118.39]
  6    53 ms    45 ms    47 ms  72.14.236.213
  7    70 ms    63 ms    60 ms  216.239.46.14
  8    62 ms    63 ms    63 ms  72.14.232.57
  9    73 ms    71 ms    71 ms  72.14.232.70
 10    62 ms    66 ms    66 ms  64.233.167.99
 
Trace complete.


Some output from GAIM debug:

oscar: CrosbyDad02 0: 0x45
oscar: CrosbyDad02 0: 0x 5
oscar: CrosbyDad02 0: 0xf7
oscar: CrosbyDad02 0: 0x5f
oscar: CrosbyDad02 0:
dns[21430]: nobody needs me... =(
oscar: no more icons to request
oscar: CrosbyDad02 0: userinfo: **warning: unexpected TLV:
oscar: CrosbyDad02 0: userinfo:   sn    =cutex52
oscar: CrosbyDad02 0: userinfo:   type  =0x0026
oscar: CrosbyDad02 0: userinfo:   length=0x0004
oscar: CrosbyDad02 0: userinfo:   value:
oscar: CrosbyDad02 0:
userinfo:
oscar: CrosbyDad02 0: 0x44
oscar: CrosbyDad02 0: 0xf0
oscar: CrosbyDad02 0: 0x98
oscar: CrosbyDad02 0: 0xd8
oscar: CrosbyDad02 0:
oscar: no more icons to request
idle: Setting CrosbyDad02 unidle
oscar: CrosbyDad02 0: userinfo: **warning: unexpected TLV:
oscar: CrosbyDad02 0: userinfo:   sn    =CrosbyDad02
oscar: CrosbyDad02 0: userinfo:   type  =0x0022
oscar: CrosbyDad02 0: userinfo:   length=0x0002
oscar: CrosbyDad02 0: userinfo:   value:
oscar: CrosbyDad02 0:
userinfo:
oscar: CrosbyDad02 0: 0xae
oscar: CrosbyDad02 0: 0xba
oscar: CrosbyDad02 0:
oscar: CrosbyDad02 0: userinfo: **warning: unexpected TLV:
oscar: CrosbyDad02 0: userinfo:   sn    =CrosbyDad02
oscar: CrosbyDad02 0: userinfo:   type  =0x0027
oscar: CrosbyDad02 0: userinfo:   length=0x0004
oscar: CrosbyDad02 0: userinfo:   value:
oscar: CrosbyDad02 0:
userinfo:
oscar: CrosbyDad02 0: 0x45
oscar: CrosbyDad02 0: 0x 5
oscar: CrosbyDad02 0: 0xf7
oscar: CrosbyDad02 0: 0x5f
oscar: CrosbyDad02 0:
oscar: CrosbyDad02 0: userinfo: **warning: unexpected TLV:
oscar: CrosbyDad02 0: userinfo:   sn    =CrosbyDad02
oscar: CrosbyDad02 0: userinfo:   type  =0x0022
oscar: CrosbyDad02 0: userinfo:   length=0x0002
oscar: CrosbyDad02 0: userinfo:   value:
oscar: CrosbyDad02 0:
userinfo:
oscar: CrosbyDad02 0: 0xae
oscar: CrosbyDad02 0: 0xba
oscar: CrosbyDad02 0:
oscar: CrosbyDad02 0: userinfo: **warning: unexpected TLV:
oscar: CrosbyDad02 0: userinfo:   sn    =CrosbyDad02
oscar: CrosbyDad02 0: userinfo:   type  =0x0027
oscar: CrosbyDad02 0: userinfo:   length=0x0004
oscar: CrosbyDad02 0: userinfo:   value:
oscar: CrosbyDad02 0:
userinfo:
oscar: CrosbyDad02 0: 0x45
oscar: CrosbyDad02 0: 0x 5
oscar: CrosbyDad02 0: 0xf7
oscar: CrosbyDad02 0: 0x5f
oscar: CrosbyDad02 0:
oscar: CrosbyDad02 0: userinfo: **warning: unexpected TLV:
oscar: CrosbyDad02 0: userinfo:   sn    =CrosbyDad02
oscar: CrosbyDad02 0: userinfo:   type  =0x0022
oscar: CrosbyDad02 0: userinfo:   length=0x0002
oscar: CrosbyDad02 0: userinfo:   value:
oscar: CrosbyDad02 0:
userinfo:
oscar: CrosbyDad02 0: 0xae
oscar: CrosbyDad02 0: 0xba
oscar: CrosbyDad02 0:
oscar: CrosbyDad02 0: userinfo: **warning: unexpected TLV:
oscar: CrosbyDad02 0: userinfo:   sn    =CrosbyDad02
oscar: CrosbyDad02 0: userinfo:   type  =0x0014
oscar: CrosbyDad02 0: userinfo:   length=0x0001
oscar: CrosbyDad02 0: userinfo:   value:
oscar: CrosbyDad02 0:
userinfo:
oscar: CrosbyDad02 0: 0x 3
oscar: CrosbyDad02 0:
oscar: CrosbyDad02 0: userinfo: **warning: unexpected TLV:
oscar: CrosbyDad02 0: userinfo:   sn    =CrosbyDad02
oscar: CrosbyDad02 0: userinfo:   type  =0x0022
oscar: CrosbyDad02 0: userinfo:   length=0x0002
oscar: CrosbyDad02 0: userinfo:   value:
oscar: CrosbyDad02 0:
userinfo:
oscar: CrosbyDad02 0: 0xae
oscar: CrosbyDad02 0: 0xba
oscar: CrosbyDad02 0:
oscar: CrosbyDad02 0: userinfo: **warning: unexpected TLV:
oscar: CrosbyDad02 0: userinfo:   sn    =CrosbyDad02
oscar: CrosbyDad02 0: userinfo:   type  =0x0014
oscar: CrosbyDad02 0: userinfo:   length=0x0001
oscar: CrosbyDad02 0: userinfo:   value:
oscar: CrosbyDad02 0:
userinfo:
oscar: CrosbyDad02 0: 0x 3
oscar: CrosbyDad02 0:
idle: Making CrosbyDad02 away automatically
oscar: CrosbyDad02 0: userinfo: **warning: unexpected TLV:
oscar: CrosbyDad02 0: userinfo:   sn    =CrosbyDad02
oscar: CrosbyDad02 0: userinfo:   type  =0x0022
oscar: CrosbyDad02 0: userinfo:   length=0x0002
oscar: CrosbyDad02 0: userinfo:   value:
oscar: CrosbyDad02 0:
userinfo:
oscar: CrosbyDad02 0: 0xae
oscar: CrosbyDad02 0: 0xba
oscar: CrosbyDad02 0:
oscar: CrosbyDad02 0: userinfo: **warning: unexpected TLV:
oscar: CrosbyDad02 0: userinfo:   sn    =CrosbyDad02
oscar: CrosbyDad02 0: userinfo:   type  =0x0022
oscar: CrosbyDad02 0: userinfo:   length=0x0002
oscar: CrosbyDad02 0: userinfo:   value:
oscar: CrosbyDad02 0:
userinfo:
oscar: CrosbyDad02 0: 0xae
oscar: CrosbyDad02 0: 0xba
oscar: CrosbyDad02 0:
oscar: CrosbyDad02 0: userinfo: **warning: unexpected TLV:
oscar: CrosbyDad02 0: userinfo:   sn    =CrosbyDad02
oscar: CrosbyDad02 0: userinfo:   type  =0x0022
oscar: CrosbyDad02 0: userinfo:   length=0x0002
oscar: CrosbyDad02 0: userinfo:   value:
oscar: CrosbyDad02 0:
userinfo:
oscar: CrosbyDad02 0: 0xae
oscar: CrosbyDad02 0: 0xba
oscar: CrosbyDad02 0:
oscar: CrosbyDad02 0: userinfo: **warning: unexpected TLV:
oscar: CrosbyDad02 0: userinfo:   sn    =CrosbyDad02
oscar: CrosbyDad02 0: userinfo:   type  =0x0014
oscar: CrosbyDad02 0: userinfo:   length=0x0001
oscar: CrosbyDad02 0: userinfo:   value:
oscar: CrosbyDad02 0:
userinfo:
oscar: CrosbyDad02 0: 0x 3
oscar: CrosbyDad02 0:
oscar: CrosbyDad02 0: userinfo: **warning: unexpected TLV:
oscar: CrosbyDad02 0: userinfo:   sn    =CrosbyDad02
oscar: CrosbyDad02 0: userinfo:   type  =0x0027
oscar: CrosbyDad02 0: userinfo:   length=0x0004
oscar: CrosbyDad02 0: userinfo:   value:
oscar: CrosbyDad02 0:
userinfo:
oscar: CrosbyDad02 0: 0x45
oscar: CrosbyDad02 0: 0x 5
oscar: CrosbyDad02 0: 0xfd
oscar: CrosbyDad02 0: 0xc7
oscar: CrosbyDad02 0:
oscar: CrosbyDad02 0: userinfo: **warning: unexpected TLV:
oscar: CrosbyDad02 0: userinfo:   sn    =CrosbyDad02
oscar: CrosbyDad02 0: userinfo:   type  =0x0027
oscar: CrosbyDad02 0: userinfo:   length=0x0004
oscar: CrosbyDad02 0: userinfo:   value:
oscar: CrosbyDad02 0:
userinfo:
oscar: CrosbyDad02 0: 0x45
oscar: CrosbyDad02 0: 0x 5
oscar: CrosbyDad02 0: 0xfd
oscar: CrosbyDad02 0: 0xc7
oscar: CrosbyDad02 0:
oscar: removing icon input watcher
oscar: removing chatnav input watcher
idle: Setting CrosbyDad02 idle 604 seconds
oscar: CrosbyDad02 0: userinfo: **warning: unexpected TLV:
oscar: CrosbyDad02 0: userinfo:   sn    =CrosbyDad02
oscar: CrosbyDad02 0: userinfo:   type  =0x0022
oscar: CrosbyDad02 0: userinfo:   length=0x0002
oscar: CrosbyDad02 0: userinfo:   value:
oscar: CrosbyDad02 0:
userinfo:
oscar: CrosbyDad02 0: 0xae
oscar: CrosbyDad02 0: 0xba
oscar: CrosbyDad02 0:
oscar: CrosbyDad02 0: userinfo: **warning: unexpected TLV:
oscar: CrosbyDad02 0: userinfo:   sn    =CrosbyDad02
oscar: CrosbyDad02 0: userinfo:   type  =0x0014
oscar: CrosbyDad02 0: userinfo:   length=0x0001
oscar: CrosbyDad02 0: userinfo:   value:
oscar: CrosbyDad02 0:
userinfo:
oscar: CrosbyDad02 0: 0x 3
oscar: CrosbyDad02 0:
oscar: CrosbyDad02 0: userinfo: **warning: unexpected TLV:
oscar: CrosbyDad02 0: userinfo:   sn    =CrosbyDad02
oscar: CrosbyDad02 0: userinfo:   type  =0x0027
oscar: CrosbyDad02 0: userinfo:   length=0x0004
oscar: CrosbyDad02 0: userinfo:   value:
oscar: CrosbyDad02 0:
userinfo:
oscar: CrosbyDad02 0: 0x45
oscar: CrosbyDad02 0: 0x 5
oscar: CrosbyDad02 0: 0xfd
oscar: CrosbyDad02 0: 0xc7
oscar: CrosbyDad02 0:
oscar: CrosbyDad02 0: userinfo: **warning: unexpected TLV:
oscar: CrosbyDad02 0: userinfo:   sn    =CrosbyDad02
oscar: CrosbyDad02 0: userinfo:   type  =0x0027
oscar: CrosbyDad02 0: userinfo:   length=0x0004
oscar: CrosbyDad02 0: userinfo:   value:
oscar: CrosbyDad02 0:
userinfo:
oscar: CrosbyDad02 0: 0x45
oscar: CrosbyDad02 0: 0x 5
oscar: CrosbyDad02 0: 0xfd
oscar: CrosbyDad02 0: 0xc7

---

### Post by tbonius on 2006-09-12
Not sure what treaceroute differing has to do with your issue.. but read the sticky posts on Network Issues.  Disable IPv6.  Describe your setup a little more.  Are you directly connected via a Cable/DSL modem or through a router?

T

---

### Post by spd106 on 2006-09-12
Ubuntu's default traceroute (tracepath) app uses udp packets, windows uses ICMP echo request. If you want to use ICMP as well then the easiest way is to install traceroute and use the -I switch.

Not sure about your other issue. As tbonius says could you please provide more information.

---

### Post by ldc_1 on 2006-09-13
Hello

My network is setup like this.
- Actiontec DSL gate way router, wireles box.
- 3 feet CAT5E to a 24 port Procurve 2724 switch which feeds the house.
- Cat5E running around the house.
- In my office (about 30 feet from switch above) is a Procurve 408 8 port switch with 2 Windows and one unbunto system off it.
- The other ubunto is in my dughters room, about 80 feet of cat5E straight of the 24 port switch, she also has a Windows system in the room off a secound wire.
- We also have a Dlink hub in our living room with one Windows box and a wirless AP unit hung off it.

All of the above network gear has been in place for a year or more. We have two wirless PC that are used around the house by kids/wife. All windows boxes continue to work fine, wirles or cable, only the to ununtu boxes are having issues. Which is really to bad because the kids were getting interested in using them.

My daughters unbunto system has had only evoltion mail and gaim setup on it, the only other updates were from the system update tool.

My unbunto system has had Skype, Evolution mail and Gaim setup, along with the system updates.

NOTE, we can no longer do the system updates, nodes keep timing out.

I rebuilt one of the two systems using the ubuntu disk and that system works great, interestingly the one change we had to make was in Firefox, had to turn on IPV6 to make it work all the time.

Thank for the help,

-ldc-

---

