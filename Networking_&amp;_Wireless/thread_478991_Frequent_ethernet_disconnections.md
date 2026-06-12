---
title: "Frequent ethernet disconnections"
date: 2007-06-19
forum: Networking &amp; Wireless
---

### Post by sunshine12 on 2007-06-19
Hi all,
I am facing problem with the ethernet connection.

My wired ethernet connection got disconnected while downloading big files, like torrents or any other transfer from any site. It got disconnected after 40-50MB downloading, connection comes to 0 and have to restart the pc to start working again. Terminal showing message.. "disabling irq 11"

Using Ubuntu feisty,
ethenet card is Hangzhou silan microelectronics ltd, sc92031 chipset.. 
actually NIC  not detected by ubuntu, so installed the driver manually

Thanks

---

### Post by sunshine12 on 2007-06-19
works fine when browsing sites, no disconnections whatsoever while browsing, but during file transfer/downloading it freezes...

---

### Post by crazyjx23 on 2007-06-19
Maybe your card has compatibility issues. Check your router and see that it's in order and if you have another computer, fool with it's connections. This might help narrow down the problems.

---

### Post by sunshine12 on 2007-06-20
> **crazyjx23 said:**
> Maybe your card has compatibility issues. Check your router and see that it's in order and if you have another computer, fool with it's connections. This might help narrow down the problems.

Ya it might be having compatibility issue.
don't understand the other comments "Check your router and see that it's in order and if you have another computer, fool with it's connections"

lspci shows

01:09.0 Ethernet controller: Hangzhou Silan Microelectronics Co., Ltd. Unknown device 2031 (rev 01)

thanks

---

### Post by sunshine12 on 2007-06-20
there I found the patch for the silan drivers for kernel 2.6.x version...

How to apply the patch... if somebody can guide!!

---

### Post by sunshine12 on 2007-06-20
I don't know what is this patch, but there is file with .patch extention and how to apply this patch?? if it is possible? please guide

---

### Post by sunshine12 on 2007-06-28
Problem solved...

no need for patch anymore.. Ndiswrapper solved my problem, installed windows xp driver using ndiswrapper and internet is working like it should.

Now no disconnections, can download big files...

Thanks to everyone for helping me..

---

### Post by vishalmanohar on 2007-07-03
Hi,

Can someone tell me how to set the driver manually for the Hangzhou Silan Lan Card? 

Thanks.
Vishal

---

### Post by sunshine12 on 2007-07-04
> **vishalmanohar said:**
> Hi,

Can someone tell me how to set the driver manually for the Hangzhou Silan Lan Card? 

Thanks.
Vishal

Dear Vishal, 
Why do you want to set the driver manually?  it will give you problems like disconnections (I have experienced it).. Try using ndiswrapper and windows xp drivers provided with the mini cd. It will  work perfectly without any problem.

Try it and post if any problems..

Good luck..

---

### Post by lost_poet on 2007-08-05
ummm...I have a simmilar problem.

I have the Stupid counterfeit Intex Card which says it uses realtek but has Silan (u must all know it by now). So I used *ndiswrapper* and got it running. used *pppoeconf* to make myself an PPPoE connection. Fine till then.

Then the net is running full on, no problems.

Then I update. And from 2.15, I goto 2.16 (I am  newbie so I do not know what it is, but it says Linux image...something). I restart. Then my nightmare begins.


My PPPoE gets frquently d/c and I have to constantly watch for it and use *pon* to redial it.

So I thought I shud remove my xp driver which I installed using *ndiswrapper* and then reboot and reinstall it and go through the entire configuration again.

So I do it.
 
ndiswrapper installs my driver.

Then I type out the following (got it from a forum) :-

> sudo depmod -a (goes okay)

Sudo modprobe ndiswrapper (goes okay)

Sudo ifconfig wlan0 192.168.1.2

here, my system tells me something about device not being there.



What do i do?:confused::confused: Can someone plz hlp me or direct me towards a solution? Plz plz?


edit: okay, seems like I have fixed it by reconfiguring my PPPoE connection through *pppoeconf*. I said no at two places the *noauth  and something* and at the *mss clamp option*. That has stopped my connection from being terminated all the time! hope this lasts!
For the record : I am on BSNL DataOne ADSL Broadband at 256kbps, on Ul 900+ (okay, I am basically putting this up so that ppl from my location are able to search this and contact me in future if need be).  I am using the infamous Silan SC92031 chipset on the Intex Ethernet / lan card.

---

### Post by lost_poet on 2007-08-05
All that Ado, and It didn't even last!

Well, that *apparently* was there for a reason. The solution did last me an hour but then it gave again!

And i have no clue what is going on!

IF anyone wants it I can provide a copy of my *plog* entries...

someone plz help! I am clueless out here!

---

### Post by sunshine12 on 2007-08-07
what is your system stats...
It is working fine with the updates, no disconnections....

---

### Post by lost_poet on 2007-08-07
Well, I am running - 

P3 @ 1113mhz

256 SD Ram

SmartAX MT841 Huwaei Sterlite ADSL Modem

That FAKE lan-card (Hangzhou Silan SC92031)

Intel MoBo (4got the model)

what else do you want to know?

---

### Post by sunshine12 on 2007-08-08
May be you should try installing with the ndiswrapper again and use network manager to configure it instead of pppoeconfig..

Can't figure out what is the actual problem, because it is working perfectly for me with ndiswrapper.

When I first installed it manually with some driver, the same problem occured and also after update with kernel, the connection failed to recognize. But with ndiswrapper even after kernel update there isn't any problem.

May be there is something wrong during installation.

Your problem will be solved with the newer kernel 2.6.21, that includs the driver for this chipset, and it will be recognized out of the box. Till then try something or other to fix it.

---

### Post by sunshine12 on 2007-08-08
it was working properly before kernel update??
I mean up and running for a long time.....?
post last 10 lines of dmesg and ifconfig

---

### Post by rave23 on 2007-09-20
hai .....

i have upgraded to 2.6.22 ...
it has sc92031 loaded ..
cheked using lsmod ......

also ping works for 127.0.0.1 and 192.168.1.1 

BUT IN INTERNET CONNECTION SAYS ............NO DEVICE CONNECTED 

lspci show d silcan as manufacturer ........

MY problem was ... i didnt have driver sc92031.ko ....
no My problem is ...... got driver loaded but hardware not detected .... (eve though PING works successfuly ) .


also in 2.6.20 ... i tried  to compile driver ...
but got error as NO CONFIG.H file .....
wht do i do ???  i have d headers ...

---

### Post by simontay78 on 2007-09-22
I have similar frequent Ethernet disconnection when ever I download big files via torrent and also download too many files at the same time. It's very annoying.

"lspci" in terminal I get this...
```
3Com Corporation 3c900B-TPO Etherlink XL 
```

do advice...

Newbie in Ubuntu for 1 month!!

System AMD 64
ATI 
10MB Broadband (but torrent shows my download is like 0.01kbps!!)

Please help!! :confused:

---

