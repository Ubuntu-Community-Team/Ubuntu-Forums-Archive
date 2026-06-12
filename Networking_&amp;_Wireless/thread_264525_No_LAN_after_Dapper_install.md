---
title: "No LAN after Dapper install"
date: 2006-09-24
forum: Networking &amp; Wireless
---

### Post by heathw07 on 2006-09-24
Quick rundown of what has happened over the past two months:
- upgraded dekstop from 5.10 to Dapper: no problems
- have run laptop 1 (Windows) on same LAN with no problems
- open Linksys Router webpage and enabled wireless (for laptop 2)
- desktop has never connected to network or Internet since

I've spent the past two months trying everything that I could find on the internet related to the errors and symptoms I have and, in depseration, reloaded Dapper today hoping that would be the final fix; no good. Same symptoms, problem, everything.

Here's what I know:
- my route table is empty. It won't let me add anything and returns the error SIOCADDRT: Network is unreachable.
- card seems to be working correctly.
- after reinstall, ifup eth0 returns "interface eth0 already configured"

I know you'll probably need more info, but tell me what and I will post it ASAP. I know the network is fine (Windows laptop never lost contact with anything) and I can open the Linksys window, etc same as I always able to do.

Whoever solves this one is definitely my hero. I've tried everything I can think of............ please help!!!

---

### Post by NetworkGuy on 2006-09-24
More info please:

Please give us the results of the following:

If your network card is USB:```
lsusb
```
If your network card is PCI or PCMCIA:```
lspci
```
Also
```
iwconfig
``` ```
ifconfig
```

Then we'll try to get this fixed.

---

### Post by heathw07 on 2006-09-24
lspci:

0000:00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (Rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (Rev c2)
0000:00:1f.0 ISA bridge: Intel Corporation 8280EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
0000:01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)

iwconfig:

lo    no wireless extensions
et0   no wireless extensions
sit0  no wireless extensions

ifconfig:

eth0   Link encap:Ethernet HWaddr 00:13:20:18:32:5A
       inet addr:0.144.248.101  Bcast:245.157.248.255 Mask:0.0.0.0
       inet6 addr: fe80::213:20ff:fe18:325a/64 Scope:Link
       UP BROADCAST RUNNING MULTICAST MTU:1500  Metric:1
       RX packets:8 errors:0 dropped:0 overruns:0 frame:0
       TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:1000
       RX bytes:2260 (2.2 KiB)  TX bytes:1152 (1.1 KiB)

lo     Link encap:Local Loopback
       inet addr:127.0.0.1 Mask:255.0.0.0
       inet6 addr: ::1/128 Scope:Host
       UP LOOPBACK RUNNING MTU:16436 Metric:1
       RX packets:5 errors:0 dropped:0 overruns:0 frame:0
       TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:0
       RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

---

### Post by heathw07 on 2006-09-24
By the way, I did edit out the VGA and USB parts in the lspci since I had to type this all by hand. I think I left the significant stuff.

---

### Post by heathw07 on 2006-09-25
Anyone?

---

### Post by mips on 2006-09-25
Do a search here for:  82562EZ

---

### Post by dannyboy79 on 2006-09-25
what does dmesg have in it related to your ethernet port? Also, have you simply gone to Networking and clicked deactivate, wait a sec, then hit activate. I have a problem where ifdown and ifup don't work but when I do the activate thing it does work. Are you using static or dhcp? By the looks of it you're receiving an IP address, it's: 0.144.248.101. What is the address of your XP laptop, if it doesn't start with 0.144.248 than something is really weird. I need to clarify something, are you telling us that you have 2 laptops, 1 has WINXP on it and what does the other have? Than you also have a desktop that you are trying to run Dapper on that you can't seem to get to connect to the internet. Is that correct? If so, please post your /etc/network/interfaces file, also your /etc/hosts file. I am a newbie but I am attempting to help. If you have tried any of this and don't think I could help you than oh well, I am trying.

---

### Post by heathw07 on 2006-09-25
I'll need more specifics on dmesg. I typed it in and a TON of stuff came up. Can you tell me which part would help?

What I think is important is:
```

NET: Registered protocol family 10
lo: Disabled Privacy Extensions
IPv6 over IPv4 tuneling driver
eth0: no IPv6 routers present

```

I tried turning Networking off then on. eth0 appears to come on fine, but still cannot ping anything.

Yes, the other IP addresses are 0.144.248.xxx and I see where I am getting assigned an IP address (yes, it's DHCP) thus why I'm so lost and frustrated!!

You're correct that both laptops have Windows on them. The desktop has Dapper and is the only one not connecting to the network or internet.

cat /etc/network/interfaces yields:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```

What is eth1, 2, ath0, and wlan0?? Didn't know I had these!

cat /etc/hosts:
```

::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

Newbie or not, I appreciate all the help I can get!!!!!!!!!!!!

Thank you!

---

### Post by heathw07 on 2006-09-26
Any last minute suggestions would be appreciated. Otherwise, after work, I'm going to try installing Knoppix and see if it doesn't pick up the network any better.

Thank you.

---

### Post by mips on 2006-09-26
Did you do that search as I suggested as other people had isues with that card.

I can't look right now as we have lightning and I have to unplug the pc and adsl before it gets fried.

---

### Post by heathw07 on 2006-09-26
Yeah, I tried what I could find there. Thing is, this card worked perfectly fine up to two months ago when I enabled wireless on the router. Then it wouldn't connect again. We'll see what happens with Knoppix and I'll let you know what happens. Thank you.

---

### Post by heathw07 on 2006-09-26
OK, just can't get myself to deep-six Ubuntu; everything seems to be working and I know this will turn out to be something rediculously small. One other thing to note that I didn't put inmy previous posts: when I start up the computer it says:

Client MAC address: xx:xx:xx:xx:xx:xx  GUID: xxxxxx xx xxxxx
DHCP ... X

X is some type of spinning clock. My guess is that it's getting the IP address from the router??

I also notice that the MAC address is different from the router which, I believe, it's supposed to be. HOWEVER when I do an ipconfig /all on my windows system, it shows the same MAC address as the router (physical address).

Does this help at all.

---

### Post by heathw07 on 2006-09-26
Another question: does everyone think I will have these same problems if I buy a new ethernet card? Any suggestions for what works best with Linux??

---

### Post by mips on 2006-09-27
Lets try this from a different angle.

Configure your IP address, Default Gateway, Netmask, Broadcast, DNS all statically and see if it works.

If it does not work, disable IPv6 and see if that makes a difference.

---

### Post by heathw07 on 2006-09-27
Gotta head to work right now but will get on this when I get home and post the results. Thank you.

---

### Post by dannyboy79 on 2006-09-27
i noticed that your missing your loopback from your interfaces file!! I think that matters! when I get home I'll post the results of my interfaces file but I know for sure it has 127.0.0.0 localhost in it or something along those lines. I also put all my ip address of each of my boxes in this file. I also put the ip of it's own machine in here. I'll post it when I get home tonight. I am a newbie and I really want to help you with this. DON'T GO TO KNOPPIX YET, please. Talk to you later! You said u can't ping anyone, can you ping the router by ip address or any other mahcine by ip? I can;t believe you don't have internet access if you have an ip address??? We'll figure it out don't worry!

---

### Post by dannyboy79 on 2006-09-27
This is what my hosts file has in it:

127.0.0.1 localhost XUBUNTU
192.168.0.5 XUBUNTU

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
192.168.0.3 UBUNTU
192.168.0.4 WINXP

---

### Post by dannyboy79 on 2006-09-27
I just read what you were saying about seeing the dhcp thingy spinning and you seeing another mac address. I noticed that when I had set my boot sequence to boot a onboard lan item before the hard drive that the os  is installed on. That probably doesn't have anything to do with it but check out your bios and see what your boot sequence states.

---

### Post by heathw07 on 2006-09-27
I appreciate the help!!

Here's what I got to answer your questions:

On the DHCP thing spinning: BIOS says it boots CD/DVD drive then the Ubuntu drive. No other hardware or anything else to boot.

I can't ping anything at all. This is one thing that's KILLING ME!!! How the heck am I getting assigned an IP address from the router but "Network is unreachable". It's driving me crazy; I actually dreamt about this stupid stuff last night!!!!!!

I think I have the loopback in the interfaces file, no? I thought it was the part that reads:
```
auto lo
iface lo inet loopback
```
If this is wrong, please tell me what more I need to add in there.

OK, so, about entering the IP addresses of your boxes in the hosts file, does it matter where they go? I notice you had a couple of addresses up top of your post, then the remaininng file toward the bottom. Was that on purpose? I might be burning out so please be patient if I misunderstood things.

Mips, on changng things to Static IP addresses (and this is really stupid, I know), I went into my router last night and could easily see where to turn DHCP off but couldn't see where I manually enter IP addresses for my computers. Somehow I know I'm missing something easy but I went through page by page for about 45 minutes and couldn't come up with it. Do I just turn DHCP off and keep the addresses that are already assigned to the computers?

Thanks alot all, I truly appreciate the efforts you're putting into this. It seems so close to working and I've tried everything I know. I verified last night that swapping the cables with my XP laptop made no difference to either system, Rebooted everything under the sun, etc etc so I know this isn't hardware.

---

### Post by heathw07 on 2006-09-27
By the way, I'm still open to the idea that, for some stupid reason, I need a new network card. Does this sound like a reasonable answer or am I just grasping at straws? If this seems reasonable, please recommend a card that I can try.  ](*,)

---

### Post by dannyboy79 on 2006-09-28
back to my other q, tell me what dmesg states anything relating to your interface you're trying to use to get internet, i think it's eth0, then unplug the wire, and tell me what it says again, then again after your replug it in.

Next part, 
NO, don't give up yet. If and when 
you do give up, I am sure that any gigabit card will work fine. Good point about having my ip addresses on the top and the bottom of the ipv6 stuff, however I don't think it matters since everything works for me I am going to change it so that they are all at the top so it'll look like this.
127.0.0.1 localhost XUBUNTU
192.168.0.5 XUBUNTU
192.168.0.3 UBUNTU
192.168.0.4 WINXP

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

the order might matter, so put your local machine first like mine, then if you're going the static route, put the ip of your local machine, then put the ip address of all the rest. You don't put the ip address for each computer within your router, you define that in each machine. also, don't turn off your routers dhcp server, in case you want another machine to be able to get an ip and you don't want static for that particular box. the way I have my router setup is that it's a dhcp server that serves addresses from 192.168.0.20 thru 192.168.0.999, that way I can set up statis ip's which are from 192.168.0.2 thru 192.168.0.19. the way to setup static ip on ubuntu is go to, system, then administration, then networking, and then click on properties of the interface you want to modify (i only have one interface because my machine only has an ethernet port and doesn't have a modem from the old days), i think yours is eth0, then enter the ip you want it to have, then enter the default gateway which is the ip of your router, which is whatever ip you use to modify within a web browser (my home network is all 192.168.0.XXX, the .1 is my router and then all the rest go up from that), you need to enter 2 ip addresses for the dns servers which you should be able to find in your router config pages. if not you can call you isp to find out. I noticed something huge I think, your subnets of your loopback and your eth0 don't match eth0 Mask:0.0.0.0
lo Link encap:Local Loopback Mask:255.0.0. 

I have never ever seen a subnet like this, mine always populates itself on it's own with 255.255.255.0. also if you can't ping anything, NOT EVEN THE ROUTER??? than you have a major issue!! that means the basic tcp/ip protocol isn't even working. do you know for a fact that the port you are using to connect your computer to on the router works??? try the port that your other machine uses that actually works! we need to straighten out the pinging first before we talk about viewing machines thru nautilus and whatnot. canb you even ping your own ip address. why don't we talk thru xchat or whatever irc method so I can help ya. I like helping others! even though I am a linux newbie, I think I have caughten on pretty quickly. hope to hear back from you soon! my email is [email]darfsten@hotmail.com[/email], i should be ready to help tonight around 8:30 central standard time.

---

### Post by heathw07 on 2006-09-28
First, thanks for hanging in there. This is quite a challenge!!

OK, dmesg:
```

IPv6 over IPv4 tunneling driver
ADDRCONF(NETDEV_UP): eth0: link is not ready
e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
ADDRCONF(NETDEV_UP): eth0: link is not ready
e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

lp0: using parport0 (interrupt driven)
lp0: console ready
eth0: no IPv6 routers present
```

Pulled the cable:
```
same as above
```

Plugged 'er back in:
```
same as above
```

I swapped the cables with the Windows system, no change to either system. Changed the cables at the router, no change to either system. Put them back to original, no change to either system. Light on the ethernet card turns green every time I plug a cable in so it knows when there is/isn't a cable in it.

Updated the /etc/hosts file with the IP addresses and nothing changed. Rebooted, nothing changed.

Noticed "Failed to bring up eth0" during boot sequence.

Sorry I missed you on chat/email tonight. Saturday or Sunday night would be ideal if you're available. My email is 
[email]hwilkinson07@yahoo.com[/email]

I'm down to praying for devine intervention.....  [-o<

---

### Post by heathw07 on 2006-09-28
I just realized that I failed to mention in all these posts that I have done a full HDD wipe and reloaded Dapper -- twice! That was about three weeks ago.

---

### Post by dannyboy79 on 2006-09-29
sunday night it'll be then. I really really want to help you get this working as I do enjoy trouble shooting things and getting the satisfaction of making it work. also since it's linux which is all new to me. We'll get it don't worry.

---

### Post by dannyboy79 on 2006-09-29
oh yeah, i'll email you around 8 or 9. my screen name within xchat is new2linx. i normally go into the ubuntu channel on freenode. i'll email you first though, so if you don't get an email from me saying I'll meet ya there than something arose and we'll do it another time but most likely i'll email ya. talk to you then.

---

### Post by heathw07 on 2006-09-30
More details to add:

mips: I did try to assign everything statically and had no change.

In fishing through things this morning, I notice that the router sees the linux box (it's in the tables, etc) so the router knows I'm there. I can see the assigned IP address on my box so it's accepting that from the router. But messages still remain "Network is unreachable".

Could this be some type of firewall thing on the linux side keeping things from working? I can't ping the linux computer from the Windows one either (request time out).

---

### Post by dannyboy79 on 2006-09-30
heath, did you read my post about the subnet question? i am thinking that might be the issue. Also, have you tried sudo ifdown eth0 and then sudo ifup eth0. plus u didn't answer me about whether or nor you can ping the router.

---

### Post by dannyboy79 on 2006-09-30
i just noticed another thing, when you posted your info from ifconfig it says: inet addr:0.144.248.101 Bcast:245.157.248.255 Mask:0.0.0.0.
notice the bcast is 245.157.248.255 and your mask is 0.0.0.0. well the bcast should have the couple begining numbers that match the ip of your computer i know this because look at my ifconfig.

inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0


also, notice the mask, yours should match the subnet of what;s in your router!!! Check all this out.

---

### Post by heathw07 on 2006-09-30
OK, sorry for missing that one but no, I cannot ping anything out of the linux box (the windows laptop or the router).

I follow what you're saying about the addresses, so hopefully my last question is how do I change those?

Thanks!!!!!!!!!!!!!!

---

### Post by heathw07 on 2006-09-30
On the subnet issue, as of this minute, my ifconfig says:

```

eth0 
inet addr: 0.144.248.101  Bcast 0.144.248.255  Mask 255.255.255.0

lo
inet addr: 127.0.0.1   Mask: 255.0.0.0

```

---

### Post by dannyboy79 on 2006-10-01
alright, well, you should be able to be getting on the internet then! this is so weird. if you are doing dhcp and you are getting   ip from the router than you obviously are connecting to the router so I can't understand why you can't ping it!!! this is so f__ked!!! i am running out of ideas myself. why don't you try a different driver for your ethernet card. other than that I am not sure what to tell you. why don't you try to set your linux box with a static ip. when you look at your router you did say that you can see your linux box correct? why don't you gogle "can't ping router?" and see what you get.

---

### Post by heathw07 on 2006-10-01
I'm following the google idea. I did just yield one thing: the first and only thing that I can successfully ping: 127.0.0.1

I can't ping myself though; it says invalid argument. I assume that is normal.

---

### Post by mips on 2006-10-01
> **heathw07 said:**
> 
I can't ping myself though; it says invalid argument. I assume that is normal.

No, it's because 0.144.248.0 is an invalid network !

Are you dual-booting on this pc ? If you are open a command prompt/dos window  and post the COMPLETE output of **ipconfig /all** here. If you are NOT dual-booting then maybe suppky the output from the laptop but the pc would be better.

Something is horribly wrong here.

---

### Post by heathw07 on 2006-10-01
No dual boot, mips, so here's off the laptop:
```

Host name: Jennifer
Primary Dns Suffix: (nothing here)
Node Type: Hybrid
IP Routing Enabled: No
WINS Proxy Enabled: No
DNS Sffix Search List: comcast.net

Connection-specific DNS Suffix: comcast.net
Description: National Semi Corp blah blah blah PCI Adapter
Physical Address: oo-0B-dc-54-d4-24
Dhcp Enabled: Yes
Autoconfig Enabled: Yes
IP Address: 0.144.248.100
Subnet: 255.255.255.0
Default Gateway: 0.144.248.1
DHCP Server: 0.144.248.1
DNS Server: 68.78.86.146
            68.78.56.98
Lease Obtained: Sunday, Oct 1  7am
Lease Expires: Monday, Oct 2 7am


```

---

### Post by heathw07 on 2006-10-01
BTW, mips, I just found out last night that I can FINALLY do a route add.

What do I need to add to that file? I'm googling away to find out but figured I should ask.

---

### Post by mips on 2006-10-01
What file ?

---

### Post by dannyboy79 on 2006-10-02
one thnig that has been bothering me this whole time is your internal lan ip's? i have never in my life heard of anyones lan having an ip like this?????? normally they are either 10.x.x.x or 192.0.0.0, why don't you log into your router and change it's ip address and also change the ip address range of the addresses that get handed out. for example, my router ip is 192.168.0.1 and it hands out ip addresses of 192.168.0.20 thru 192.168.0.999 i believe (i am not sure how high but that's not relevant) i have the dhcp server of the router hand out addresses between .20 and .999 so that I can assign static ip's to things that need it, like my xbox, my server etc etc. so lets do this first then trouble shoot. I know you say that your winxcp laptop is working with having this weird 0.144.blah blah but I just thnk we should try this and see what happens. oh, 1 more thing, you did state that you have 2 laptops, 1 dapper desktop, a cable modem, and a wireless router, is this correct? i bring this up because some isp's only allow a customer to have 1 ip address and even hooking up a router doesn't help so maybe that's where we are stuck, but if you already have 2 winxp laptops on your lan and they both have internet access and can ping each and can ping the router than that probably isn't it. also, please post your ipconfig/ifconfig/iwconfig from ALL your computers AFTER you change your routers ip as well as the ip addresses that your routers dhcp server is handing out. thanks, and hopefully soon we'll get you going. oh, you could always find out if it's ubuntu's problem by downloading knoppix or damn small linux and boot the live cd, configure the ethernet connection and see if you have internet and if you do you can stop wasting your time cause it's Ubuntu then and I am out of options on what to tell ya.

---

### Post by heathw07 on 2006-10-04
OK, so, this is the most bizarre friggin' thing in the world, but I had to put it in here in case others have this problem.

Long story short: when I tried to turn on the Wireless options on my linksys router, it changed it's IP address to 0.144.248.1. My windows system picked this up with no problem; my Ubuntu system ran for a month with these settings for a month then Dapper for a week and then didn't connect to the network again (for the past two months). Well after two months of trying everything under the friggin' sun, tonight I changed my routers IP address to something more conventional and I am writing this right now on my Linux unit (temporarily with Knoppix but as soon as I'm done, I am loading Dapper.....). This was, beyond a shadow of a doubt, bizarre but maybe someone else will have a similar problem in the future.

Yikes.........................

Special thanks for dannyboy and mips for hanging in there and helping me through this.  :p :p :p :p :p :p :p :p

---

### Post by dannyboy79 on 2006-10-05
> **heathw07 said:**
> OK, so, this is the most bizarre friggin' thing in the world, but I had to put it in here in case others have this problem.

Long story short: when I tried to turn on the Wireless options on my linksys router, it changed it's IP address to 0.144.248.1. My windows system picked this up with no problem; my Ubuntu system ran for a month with these settings for a month then Dapper for a week and then didn't connect to the network again (for the past two months). Well after two months of trying everything under the friggin' sun, tonight I changed my routers IP address to something more conventional and I am writing this right now on my Linux unit (temporarily with Knoppix but as soon as I'm done, I am loading Dapper.....). This was, beyond a shadow of a doubt, bizarre but maybe someone else will have a similar problem in the future.

Yikes.........................

Special thanks for dannyboy and mips for hanging in there and helping me through this.  :p :p :p :p :p :p :p :p

That is so awesome, that's so funny cause my last post suggested to change te ip to either 192.x.x.x or 10.x.x.x which are your more comman lan ip's!!! I am happy for ya! So what ip did you end up going with?

---

### Post by mips on 2006-10-05
That would help. I find it really weird if not downright stupid for your linksys to use an IP address starting with 0. Windows of course does not care and bends rules all the time. The fact that it worked in breezy is strange. You cannot have an address below 1.0.0.1, period.

> **heathw07 said:**
> OK, so, this is the most bizarre friggin' thing in the world, but I had to put it in here in case others have this problem.

Long story short: when I tried to turn on the Wireless options on my linksys router, it changed it's IP address to 0.144.248.1. My windows system picked this up with no problem; my Ubuntu system ran for a month with these settings for a month then Dapper for a week and then didn't connect to the network again (for the past two months). Well after two months of trying everything under the friggin' sun, tonight I changed my routers IP address to something more conventional and I am writing this right now on my Linux unit (temporarily with Knoppix but as soon as I'm done, I am loading Dapper.....). This was, beyond a shadow of a doubt, bizarre but maybe someone else will have a similar problem in the future.

Yikes.........................

Special thanks for dannyboy and mips for hanging in there and helping me through this.  :p :p :p :p :p :p :p :p

---

