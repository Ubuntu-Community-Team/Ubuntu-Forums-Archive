---
title: "wireless, rt2570"
date: 2007-10-06
forum: Networking &amp; Wireless
---

### Post by eeerik on 2007-10-06
feisty fawn 7.04
hey!
ok, so going through numerous threads and trying common solution problems havent yielded anything. the trouble isnt with the driver (rt2570 is set up and running), out of the box.

been using network manager, and it finds networks automatically. the gui will tell me 0% on them,  most of the time, but iwlist scan will show actual percentages so i know its finding them. connecting with network-manager will ask for wep key but wont actually connect. sometimes i will get bars showing percentage in the gui, but it still wont actually connect after giving wep.

after toying aroudn with cmdline enough i finally decided to uninstall network-manager (as suggestion by some threads) and went with only Administration - Network.

Set up correctly, and thus far ive gotten far enough that the router supplies nameservers and an ip.

ifconfig gives:
rausb1
link encap: Ethernet HwAddr: 00:14:BF:75:CE:D6
inet addr: 192.168.1.155 Bcast 192.168.1.255 Mask: 255.255.255.0
inet6 addr: fe80::214:bfff:fe75:ced6/64 Scope: Link
UP BROADCAST RUNNING MULTICAST MTU: Link Metric: 1
Rx Packets 0 errors 0 dropped 0 overruns 0 frame 0 
Tx Packets 64 errors 0 dropped 0 overruns 0 frame 0
Rx bytes 456kb Txbytes 10.5kb

iwconfig gives:
rausb1 rt2500usb wlan essid "kbhome" nickname ""
mode: managed freq: 2.437ghz acc point: 00:0f:66:24:13:5b
bit rate: 11mb/s
RTS thr: off Fragment: off
Link quality 80/100 Signal level -55dbm Nose lvl -195dbm
Rx and TX show 0 for everything

(i copied this onto paper and then into here so thaats why there are some abbreviations etc)

ping to router yields nothing, which is weird.
any ideas as to why this isnt working?

thanks!

---

### Post by killkoy on 2007-10-06
What encryption are you using?

---

### Post by eeerik on 2007-10-06
hm, im not sure.
you mean whaat do i select as an option when entering WEP?
never actually set up wireless in network.
ive tried all three options. 128/64bit hex, ascii and 128bit passphrase, if thats what you mean.

---

### Post by eeerik on 2007-10-06
so, i tried to enable roaming mode just to see what happens, since i havent tried it since uninstalling network-manager.

say id like to (from commandline) select the wireless network "erik" with wep "12345", which perimeters would i issue iwconfig for it to do that (just to give it a try), and if it isnt enough with just essid and key, please specify so.

(iwlist scan presents it as being there, but it chose one of the neighbours instead)

---

### Post by MrFSL on 2007-10-06
Perhaps this might help:
[http://cbbk.free.fr/bonrom/](http://cbbk.free.fr/bonrom/)

I haven't tested it myself but I have heard good things.

---

### Post by eeerik on 2007-10-07
trouble is i have no removable media, and needless to say no internet on said machine.

im sort of wondering if one of the previous posts wasnt on to something when asking what encryption i was using? seeing as how the router has issued search and nameservers and an ipadress im getting /somewhere/.

---

### Post by MrFSL on 2007-10-07
> **eeerik said:**
> trouble is i have no removable media, and needless to say no internet on said machine.

...Reminds me of those early days of linux trying to get a dial-up modem working! "If only I could get it to work it would unlock the glorious gates of the internet which, in turn, would allow me to finish patching and upgrading and researching and configuring my new slackware box!" :D

---

### Post by eeerik on 2007-10-07
haha, yeah, i was there too.
trying to get a single channel isdn (with unsupported modem) to work on slack 3.1 (darkstar)

ive been away for a long time.

---

### Post by eeerik on 2007-10-08
seriously, no one has a clue?

---

### Post by Lambert on 2007-10-08
run the command [COLOR="Red"]route[/COLOR] and see if it lists your router as a gateway.

---

### Post by MrFSL on 2007-10-08
Well the first thing to do is to minimize variables. If you are using Open WEP (as apposed to Shared) then your computer can associate with the Access Point regardless of encryption keys (but your connection rate will stay at 0%)

The first thing to do is remove encryption and test your connection. 
1) Ping AP IP
2) Ping DNS IP(s)
3) Ping URL ([www.google.com](www.google.com) - etc.)

If everything works then it is an encryption problem. If things do not work, leave encryption turned off until we can get it working. IMHO - Always add encryption last!

This sounds like an encryption problem to me.

---

