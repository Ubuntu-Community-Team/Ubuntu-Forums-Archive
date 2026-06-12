---
title: "Periodic Loss of Internet Connectivity"
date: 2008-07-07
forum: Networking &amp; Wireless
---

### Post by kikazaru on 2008-07-07
Can anyone suggest how to debug this problem? I'm pretty sure it's a software problem, because it just started happening right after I upgraded a whole bunch of packages (in xubuntu 8.04).

I have an ADSL modem, with a Buffalo Air Station wireless router attached, and I use a laptop on wifi (no problem) and a desktop with a wired connection through the wireless router.

Sometimes I can get a connection, but sometimes not, and when I do, it's never long before I lose it. When I try:

sudo /etc/init.d/networking restart

It tries to get a DHCP about 4 or 5 times and gives up with something like this:

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

I can't ping the router or the modem.

---

### Post by hodad on 2008-07-07
I'm having the same problem w different hardware.  I'm also convinced it's something in the software.  I attended a monthly webinar last week.    Network dropped out ten times during webinar; very BAD!.  Never had a problem until upgrading to 8.04.  My solution was to power down/up the wireless router, which takes about 30 seconds a pop.  (Your network restart is a better idea!).

I did network upgrades thru upgrade manager after webinar last week in hopes of fixing the problem; no joy.

I also went thru my Inet provider.  They checked out their equipment all of the way thru to my router; all was OK on their end.

My setup:
System 76 Pangolin laptop
DLink DIR 615 wireless router (bought because I though my previous router was the problem)
Intel Pro/Wireless 3945ABG card

Thanks in advance for any help/suggestions!

---

### Post by kikazaru on 2008-07-07
Yeah, the fact that my laptop connects through the same router no problem reveals that it is not an external problem. It *could* be something to do with the modem or router I suppose... but I don't think so, because it was running fine for several months until I did some upgrades. To tell the truth, I had this problem a long time ago too, I don't know what I did, but it went away. Maybe some package that I installed fixed it...

---

### Post by MJBoa on 2008-07-07
I'm having the exact same problem. Through iwconfig it says I'm connected to my router, has the access point MAC address and the essid but I can't ping the router or anything else. This has to be a linux problem because I dual boot with windows on the same computer and I have no problems. This actually started happening randomly. I can't remember changing any settings. But now, it happens even on the live CD. What the hell?

---

### Post by kikazaru on 2008-07-07
Well, it's comforting at least to know that I am not the only one experiencing this problem. It's pretty tricky debugging these network problems sometimes... I went through a couple of online guides but they didn't help. 

I hope someone has an answer!

---

### Post by kikazaru on 2008-07-20
Come on guys... 

Some help would really be appreciated..!

---

### Post by kikazaru on 2008-07-27
Please please please!

Isn't there some a walkthrough guide for debugging a faulty connection?

I'm aware of the wiki one, but it doesn't really help.

---

### Post by My Name on 2008-07-29
Bumpety bump
I have the same problem.
somebody must have an idea??

---

### Post by My Name on 2008-07-29
well I've found a work around if anyone is interested.
I think the dropping of the wireless connection has something to do with the encryption method.
My solution is to change the router settings so that there is no encryption but will only accept specific mac address.
I don't know if all routers work the same way but with mine I opened the wireless with no encryption. then i connected all my wireless machines.  this then shows all machines connected and their mac address. add these mac address to the allowed connection list and activate the list so that only machines with these mac address are allowed to connect.
I'm not sure how secure this method is but I suspect it is no less secure than WEP encryption which i understand to be pretty poor.
I have yet to loos my connection, which was dropping every couple of minutes

---

### Post by My Name on 2008-07-29
scratch that. i've just dropped my connection...
back to the drawing board.

---

### Post by WebSiteGuru on 2008-07-29
I am using [UBUNTU] with GNOME. I, also, have the same problem. I use WEP encription and it is dropping my connection like fly... :confused: :( :( I can't get any work done at all when I don't have connection.

My hardware configuration is also different than everyone else that is having problem here. I also have a Window OS that connect at full speed with no problem. So, I don't think that it is the hardware problem.

---

### Post by waka324 on 2008-08-12
I have been having the same issue, only I loose my connection under high bandwidth use. I wish to gather some info so that we might be able to figure out this issue. List things that apply (ie ubuntu build, drivers, wether you use lan or wlan, and hardware)

Hardy 8.04
ndiswrapper around broadcom 43XX drivers
occurs on BOTH eth0 and wlan0
broadcom 4328 rev3 adapter
tx2000 tablet PC
dir 625 router
motorola cybersurfer cable modem

Again, lets list any common traits about this to see if we can get it solved!

---

### Post by Onay on 2008-09-13
I see the trend here...

I have the same problem: using ndiswrapper to connect to a usb wireless device. Previous windows installations worked flawlessly so the problem does not lie within the router.

Connection drops whenever I use deluge or even when loading bigger web pages due to high bandwidth usage.

This is a common problem without a common solution. SOMEONE HELP US

---

### Post by gali98 on 2008-09-14
Guys this is kinda hard to pin...

The most likely reason is because of the drivers, Not the software.
If you have to use ndiswrapper, that is a good clue.
If so, try using restricted drivers
System->administration->hardware drivers.

Some wireless cards are just not going to work right. You can't really blame that on the ubuntu software, but on the wireless driver.

I can only say that each of these cases are going to be specific.
You each need to search your chipset and see if it works with linux. Google works great.
Again that is about all the help I can give you all at once.
Just search for help by your chipset.
Kory

---

### Post by lambda-belka on 2008-12-04
Hello from ArchLinux territory! ):P

Having the same problem here.. In fact, it was one of reasons why i left ubuntu. But as I see now, it doesn't make any different on Arch.
The only way i'm getting connected is via script that deletes dhcpcd and wpa_supplicant sessions, and starts new ones. Connection drops gradually - speed drops until zero, and rarely recovers. Reboot helps getting better quality, but only for some small amount of time. 
In kubuntu, when booting with wireless switched on - wired connection also gets nasty. Besides when wireless is switched on, ubuntu won't start without nolapic/nolapictimer option.

My intuition tells me that problem's somehow connected with low level hardware managment, and with, perhaps, buffer somewhere owerflow.

Sys. conf.:
* 2 OSes: winXP, arch
* 2.6.27-ARCH
* Toshiba Sattelitte A200 1G2
* Intel Pro/Wireless 3945ABG card
* Realtek RTL8101E/RTL8102E PCI Ethernet 

If more infomation is needed, please, ask. I wish [-o< i knew a better way than putting network kill/reborn script on cron that runs each 2 minutes. Also is anybody aware of any apropriate hardware testing software? I suspect a defect.. ](*,)

WinXP has no problems with networking.

---

### Post by jflaker on 2008-12-04
I've found I needed to set the wifi channel to the upper or lower channels  to get around my cordless phones and cell phone.  No drop outs since then....it has been rock steady.

---

