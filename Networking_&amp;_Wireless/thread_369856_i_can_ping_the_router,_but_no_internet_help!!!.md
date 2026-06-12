---
title: "i can ping the router, but no internet help!!!"
date: 2007-02-25
forum: Networking &amp; Wireless
---

### Post by liquid134 on 2007-02-25
ok i can ping the router, but no internet. before i reinstalled, it worked fine right off the bat, now i got nothing. when i unplug it, i get no connection can be made or w.e, but once i plug it in, it just sits there "loading", any idea?? im connecting to a router/cable modem. internet is fine on my windows machine, and all other computers in my house. i even tried disableing ipv6. still nothing. help!

---

### Post by liquid134 on 2007-02-25
bump.......any1?? i just reinstalled again, nothing......please i need to figure this out

---

### Post by openix on 2007-02-25
Do you have you DNS settings configure?

No DNS means you can ping but not browse via domain names

---

### Post by liquid134 on 2007-02-25
how do i go about setting the dns settings??? i mean why would it work the first time i installed it without doing anything, and now after i reinstalled (problem with graphics card) it doesnt work?

---

### Post by chewearn on 2007-02-25
Under System -> Administration -> Networking

---

### Post by liquid134 on 2007-02-25
ok its setup to my router 192.168.0.1 and my search domain is chn.comcast.net or w.e for comcast, thats how its been setup.....am i missing something here??? i cant get this to connect for thelife of me, i can ping the router thats bout it

---

### Post by chewearn on 2007-02-25
Can you ping an internet site, e.g. [www.google.com?](www.google.com?)

---

### Post by liquid134 on 2007-02-25
i tried, it sends but i didnt reciever anything.

---

### Post by Koybe on 2007-02-25
Let's try to get what's the point :
- ping 192.168.0.1 works

What for :
- ping 64.233.183.104
- host [www.google.com](www.google.com)
- ping [www.google.com](www.google.com)

---

### Post by liquid134 on 2007-02-25
ok well i ping the ip and google.com, nothing, i do a lookup on [www.google.com](www.google.com), i get 3 ips back and the url, tried pinging one of those ips nothing.

---

### Post by antharr on 2007-02-25
Do you have the default gateway set as the same IP address as your router??

Or do you have DHCP enabled on your router?

---

### Post by liquid134 on 2007-02-25
i have it on auto........but how many connections or w.e are supposed to be under Network Settings > hosts??

---

### Post by chewearn on 2007-02-25
Ok, it is getting to the limit of my networking knowledge now.

Check you gateway ip, is it pointing to your router?

---

### Post by liquid134 on 2007-02-25
im not tooo familiar with linux, but i did to ifconfig, and no gateway IP is shown.....

---

### Post by antharr on 2007-02-25
Is your Default Gateway the same same as your routers IP?

---

### Post by liquid134 on 2007-02-25
on my windows machine, everything dns, dhcp, and gateway are all 192.168.0.1

---

### Post by antharr on 2007-02-25
What about under your GUI network settings?

---

### Post by liquid134 on 2007-02-25
i have it set to automatic....i tried doing it manually, still nothing....

---

### Post by antharr on 2007-02-25
Give us some screen shots.

---

### Post by liquid134 on 2007-02-25
how? i cant get the pc running ubuntu online......im on my other pc, i have to keep switchin the ethernet back and forth lol, i just dont understand why it worked the first time i had it installed.....

---

### Post by RudolfMDLT on 2007-02-25
Hi!

If you still can't get the damn thing to work you can try running a static ip?

in the terminal type the following:

> ifconfig

in the output, scroll up and find eth0 or eth1 and see which one has an ip in the the same range(192.168.0.X) as you router. in all the next commands, replace eth0 with the adapter that you found here. see this example: (See the red 10.0.0? yours should be 192.168.0)

> eth1      Link encap:Ethernet  HWaddr 00:19:D1:17:B5:61  
          inet addr:[COLOR="DarkRed"]10.0.0[/COLOR].4  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d1ff:fe17:b561/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:641800 errors:0 dropped:0 overruns:0 frame:0
          TX packets:354521 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:845956464 (806.7 MiB)  TX bytes:65015279 (62.0 MiB)


> 
sudo cp /etc/network/interfaces /etc/network/interfaces.back

ping 192.168.0.15



if there is no reply from 15 continue. if however you do get a reply from 15 try 14 or 13 until you get a free ip.

then

if you are using Ubuntu:

> sudo gedit /etc/network/interfaces 

or Kubuntu

> kdesu kate /etc/network/interfaces 


then find the heading 

> auto eth0 #or eth1, depending on what ifconfig returned
iface eth0 inet dhcp

and then make it look like this:

> auto eth0
iface eth0 inet static
address 192.168.0.15 #replacing 15 with the ip that was free on your network
subnet 255.255.255.0
gateway 192.168.0.1

press Ctrl+x when finished, press y and enter and you should be finished.

now restart the network:

> sudo /etc/init.d/networking restart

ignore any error in the order of
> SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device


but please post back if you have errors relating to the actual config file.

What we have done is we have made your machine independent of your router and pointed it directly at it using a fixed ip address.

Please post back with your results - if this does not work please post back with detailed errors if you get them.

cheers,

Rudolf

---

### Post by Koybe on 2007-02-25
This looks strange.

You can type 'route -n' to show your routing table. Copy/paste it here.

Or myba this is a friewall blocking. Could you also copy paste :
iptables -L -v

---

### Post by antharr on 2007-02-25
If you have DHCP enabled on your router, it should do everything for you.

---

### Post by RudolfMDLT on 2007-02-25
I know dhcp does handle this but there have been some  weird issues in the past with routers not grafting with Ubuntu.

Koybe - thanks, those are 2 nice tools I'll remember!

---

### Post by liquid134 on 2007-02-25
still nothing, im seriously still stuck on the fact that it worked the first time i installed this.....now it doesnt, just my luck, i dont kno what else there is to do......

---

### Post by liquid134 on 2007-02-25
ok well i did route -n

comes up             Destination - 192.168.0.0       gateway - 0.0.0.0

why??

i tried running iptable and got errors saying unknown command or sumthing

---

### Post by RudolfMDLT on 2007-02-25
Try the fixed ip thing and force the gateway to 192.168.0.1 and see if that helps...

---

### Post by liquid134 on 2007-02-25
ok i did that but now (ive had it showing eth0 2 times on route -n) but now the top goes like this

192.168.0.0     0.0.0.0              255.255.255.0     and the bottom is
0.0.0.0           192.168.0.1        0.0.0.0

---

### Post by liquid134 on 2007-02-25
**** it didnt space it out like i wanted to, but do u see what i mean?

---

### Post by Koybe on 2007-02-25
The last line seems ok... but you're not showing the whole line. It should ends up with your ethernet card. Heres is mine for example :
```

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```

If you can try to be cleaner in your anwsers, it's hard to understand hwat's happening with your short answers.

You can try to get an ip from your router's dhcp (if it has one) :
```
sudo dhclient eth0
```

---

### Post by liquid134 on 2007-02-25
sry i have to type this all out, it looks like yours does, just with the number i put in the first part, ill try the sudo dhclient eth0 now

---

### Post by liquid134 on 2007-02-25
ok did the sudo dhclient eth0 and this is what i got

Listening on LPF/eth0/00:07:95:51:78:FF
Sending on LPF/eth0/00:07:95:51:78:FF
Sending on Socket/Fallback
DHCPDiscover on eth0 to 255.255.255.255 port 67 interval 7
DHCPOffer 192.168.0.1
DHCPRequest on eth0 to 255.255.255.255 port 67
DHCPPack 192.168.0.1
bound to 192.168.0.13 renewal in 1423 seconds


my ip i had set to 192.168.0.11

---

### Post by Koybe on 2007-02-25
So your dhcp is working worrectly, you get a good IP, DNS is working correctly also (for what i had understand before).

With all this your network must work... I think the only thing that could block you from accessing internet is a firewall. 

Retry with iptables... (it's iptableS with a 's' at the end not iptable)

---

### Post by liquid134 on 2007-02-25
tried it, got errors, and said i had to be root

---

### Post by Koybe on 2007-02-25
```
sudo iptables -L -v
```

It should looks like this if it's 'firewall free' :
```
sudo iptables -L -v
Password:
Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination

```

---

### Post by liquid134 on 2007-02-25
ok i got this

Chain Input  (policy accept 4 packets, 1219 bytes)
pkts bytes target             proto  opt on   opt source destination

Chain Forward  (policy accept 0 packets, 0 bytes)
pkts bytes target             proto  opt on   opt source destination

Chain Input  (policy accept 1 packets, 328 bytes)
pkts bytes target             proto  opt on   opt source destination

---

### Post by liquid134 on 2007-02-25
what you posted is what it looked like the first time so i ran it again and got what i posted

---

### Post by Koybe on 2007-02-25
Hum... It seems ok. I can't get the point with your problem, it's really surprising. Are you able to copy paste here? If yes let's sum it up (sorry to ask again but it should be a misconfig somewhere and I can't get it), paste :
```
sudo cat /etc/network/interfaces
sudo cat /etc/resolv.conf
sudo ifconfig
sudo route -n
ping -c 3 192.168.0.1
dig www.google.com
ping -c 3 64.233.183.103
ping -c 3 www.google.com
sudo iptables -L -v
sudo iptables -t nat -L -v

```

---

### Post by liquid134 on 2007-02-25
i cant copy paste, i cant get the site to load, ive been writing everything on a notebook and typing it out

---

### Post by Koybe on 2007-02-25
Maybe you can ssh your ubuntu box with you notebook so you'll be able to copy paste the results :
ssh user@yourip
Or use putty if you're in windows.

Or if not possible answer question by question and tell what clearly happend on each step.

---

### Post by liquid134 on 2007-02-25
i have to keep switching out the cat5 cable when i switch to the linux machine, i dont have a switch that works, but it was working fine earlyier then i reinstalled and now this.....but i ran what you had typed out (i had to hand write it in a notebook and type it allback out) and then everything seemed to run pretty quick except when i got to the pinging of 64.233.183.108 and [www.google.com](www.google.com)

---

### Post by Koybe on 2007-02-25
Sorry but I don't get it.
What if you :
```
traceroute www.google.com
```

---

### Post by liquid134 on 2007-02-25
when i traceroute it brings back 3 ips for google.com

---

### Post by Koybe on 2007-02-25
And it shows the full route? You can get to it? Uh I really do not understand.

---

### Post by liquid134 on 2007-02-25
ok sry, when i do lookup on [www.google.com](www.google.com) it comes up with 3 other ips for google......traceroute just keeps saying 'tracing route to google.com'

but i checked ifconfig again and it says

inet addr: 192.168.0.13 Bcast: 192.168.0.255 

is that right??

(i have my ip manually set to 192.168.0.11)

---

### Post by Koybe on 2007-02-25
Yes this is because with used dhclient before.
You can restart your network configuration :
sudo /etc/init.d/networking restart

Anyway i have no more ideas to really help you. It seems to be ip/routing problem, but everything is ok regarding to your configuration. The only thing that can stop you is a higher level product... which means firewal and/or proxy which you don't seems to have.

It's all I can do, sorry. If someone as another idea....

---

### Post by koenn on 2007-02-25
I'll have a look.

> when i do lookup on [www.google.com](www.google.com) it comes up with 3 other ips for google
I don't understand what you mean. How do you 'lookup on www.google.com' ? what are those 3 ip addresses ?

Also : dou you have a USB stick or even a floppy drive or so ? Then you could copy the output of commands to a text file, transfer it to the other machine, and post them from there. People here will need to check that information to be able to find out what's going wrong.

---

### Post by liquid134 on 2007-02-25
actually ya i have a flash drive (small usb thing) will i have to do anything to get it to work on linux?

---

### Post by koenn on 2007-02-25
just plug it in and see it appear as a drive on your desktop or in your file browser

---

### Post by liquid134 on 2007-02-25
i did that, it locked up pretty much, rebooted, and then got an error when it was booting, errr reinstalling right now lol.........damn

---

### Post by koenn on 2007-02-25
hmm, sounds to me that that computer has more serious problems than just not being able to get a working internet connection

---

### Post by RudolfMDLT on 2007-02-25
Hi, this might be off the topic - but earlier you said something about graphics not working wither on the second install? what else doesn't work on your computer? Do you have Internet when working on the live CD? Koybe is right - He/She's tried everything and it still doesn't graft. The fact that your usb doesn't work is a symptom of a bigger problem... 

Goodluck,

Rudolf

---

### Post by liquid134 on 2007-02-25
its not that the graphics didnt work, i was working on getting dual monitor setup. and i got that to work too, but couldnt figure out how to change resolution for either of the monitors, and thats when i started tryin diff. how to's and it got screwed up

---

### Post by liquid134 on 2007-02-25
and when i used to have windows on that machine, i never had a problem with graphics or the usb drive

---

### Post by RudolfMDLT on 2007-02-25
> **liquid134 said:**
> and when i used to have windows on that machine, i never had a problem with graphics or the usb drive

I can't fault you for saying that... 


Though Ubuntu works beautifully for me - it took a lot of sweat and blood to get it to work. I don't use windows now.

Anyway - you must be beyond frustration now.

If you wish I can try and help you sort all this junk out! It's 22:30 this side of the world and in a couple of hours I'll be off to bed. But in the meen time, post your machine specs and I would recommend a clean install(format the entire drive). From there we tackle one problem at a time.

Having no networking is a big pain in the neck, I agree. If you do try the reinstall, please tell me whether you get the symptoms on the live cd as well. Anyway, I'll be checking back to see if I can't help you.

Best of luck!

Rudolf

---

### Post by liquid134 on 2007-02-25
ya well seeing as i was up till about 7am over here trying to get this to work lol, right now im going through doing another reinstall, but ive been getting errors while it was creating the ext3. so im going to try it again, and if same errors, then i dunno what to do.

---

### Post by liquid134 on 2007-02-25
well i dont know what that was all about, as im posting from my linux machine now!!!!!! i ended up reformating the drive completly on my windows machine using partition magic, and then when i installed it, i did it manually, and now it works!!! so lets hope i dont have to worry about the internet messing up on me.....now time to get dual monitor working!!!

---

### Post by koenn on 2007-02-25
great. 

have fun !

---

### Post by RudolfMDLT on 2007-02-26
I'm glad mate! All the best! :)

---

