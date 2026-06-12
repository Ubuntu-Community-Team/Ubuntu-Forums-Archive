---
title: "Wireless Network Issue with Intel 4965 ABGN and Linksys router"
date: 2008-11-02
forum: Networking &amp; Wireless
---

### Post by xstaticdream on 2008-11-02
Hi there guys,

I need your help for a very tricky issue that's driving me crazy.

I'm running Ubuntu 8.10 and everything works fine except for the wireless connection. I have an Intel PRO/Wireless 4965 ABGN card and I'm trying to connect to a Linksys WAG160N Router thru N protocol which works perfectly on Vista.

Ubuntu finds my network but stucks when it comes to retrieve IP address. DHCP is in fact activated on my router and all settings are on automatic on Ubuntu.

I've tried pretty much everything but I just can't get it to work. The only way it does is by giving it a static IP address like 192.168.1.x but it still won't go on the net. And it doesn't work with WiCD either.

Can someone help me with this?

Thank you all in advance!

---

### Post by Poelie on 2008-11-05
Got the same problem here...

Hope that someones has the answer...

---

### Post by stubbz on 2008-11-05
Same problem here..  The only way I can get it to connect is to keep turning wireless off and on until it will finally transmit data.  Network manager shows me as being connected but I can't ping the router.

---

### Post by ecuajosh on 2008-11-05
i have an intel 4965 agn i have ralized tha on a network with key won't connect i just don't know why i tryed updating the driver,manual config.but it just don't work.it shows the network but won't connect unless i take the wep key off.i just don't want people arround to steal my conection.i'm actually using my neightbor's wireless which is not protected.
thanks in advance

---

### Post by Poelie on 2008-11-05
Hi guys,

I tried the connection without a key and it connected right away.
So it has to do with the keysignature...

bye

---

### Post by kshibu on 2008-11-07
I have the same problem on Sony VAIO Laptop.

I'm running Ubuntu 8.10 and everything works fine except for the wireless connection. I have an Intel PRO/Wireless 4965 ABGN card and I'm trying to connect to a Linksys WAG160N Router thru N protocol which works perfectly on Vista.

Ubuntu finds my network but stucks when it comes to retrieve IP address. DHCP is in fact activated on my router and all settings are on automatic on Ubuntu.

[I][COLOR="Lime"]I send email to linksys, the reply they send is

Dear Valued Linksys Customer, 

Thank you for contacting Linksys Support. 

Please try using WPA-TKIP.

Thank you.[/COLOR][/I]

I tried WPA - TKIP. It does not work.

It works only with wireless security disabled.

Thanks

---

### Post by Poelie on 2009-04-16
Hi guys,

downloaded 9.04 to see if the new versions resolves the problem...but no difference...

Is their anyone that knows the problem to this frustrating problem...:(

later

---

### Post by ussndmac on 2009-04-16
Sigh :(

I have had this issue since I got my Dell Laptop last October.

Wifi worked until I loaded a canonical release (thus replacing the Dell installed 8.04)

Since then I've gotten no version of Ubuntu to connect.

My issues are the same as described. It says the linksys is there, but will not talk to the net that the linksys is connected to.

I use static ip's and I have turned off all security, to no avail.

My other machines running WindowsXP connect just fine...

---

### Post by Captain_Glen on 2009-04-16
I had an old wireless router that only worked with WEP.  I had to buy a new router because the signal was so week that you had to be in the same room as the router.  When I got a new one WPA just worked.

---

### Post by ussndmac on 2009-04-16
Indeed I suspect this is and "Old router" issue.

But in my case, I don't think it is a signal strength issue...the PC is 8' from the router. ;)

---

### Post by lilchiko on 2009-04-16
I'm having a similar problem with my wireless connection on my dell inspiron laptop. When running windows xp everything connects fine but when I boot ubuntu I see my network I just can't connect to it. I don't know what the issue is but I can't seem to figure the problem out.

---

### Post by Poelie on 2009-04-18
> **ussndmac said:**
> Indeed I suspect this is and "Old router" issue.

But in my case, I don't think it is a signal strength issue...the PC is 8' from the router. ;)

I have a linksys WAG160N so i don't think it has to do with old routers...

Just like everyone else around...windows it's working fine..Ubuntu it doesn't.

:(

---

### Post by kit.regan on 2009-04-18
I was hoping this would be resolved in 9.04 but sadly no. The solution is to stick with 8.04 or err.. Windows.

---

### Post by Poelie on 2009-04-18
maybe on the final release of 9.04:P

is their already made a bug issue?

---

### Post by Ericyzfr1 on 2009-04-18
I was thinking of buying a wirelessN router.....I will hold on that until that issue is resolved.

---

### Post by Poelie on 2009-04-25
mmm...with the new stable release of ubuntu 9.04 , the bug doesn't disappear..

---

### Post by Ken_Lewis81 on 2009-05-27
I've the same problem with my WAG160N.  Using NetworkManager after 0.70 (I'm testing Kubuntu Karmic and had been using Debian Sid) has problems with any form of encryption with my WAG160N.  I even went as far as e-bay to buy a second network card to try it with, so I know that RT2x00 (for a rt2500pci card) and IPW2x00 (ipw2915 card) don't mesh with NetworkManager and my router.  Both cards work fine with Windows and I've even got the 2915 to associate using WPA when I stopped the NetworkManager service[1] and started wpa_supplicant.

Can anyone confirm which versions of the WAG160N they're using?  I have a v.1, Annex A running the original 1.00.06 and newer 1.00.12 firmwares.

[1] I ran: "sudo /etc/init.d/NetworkManager stop" and restarted it with "sudo /etc/init.d/NetworkManager restart".


Cheers all,
Take care.
K3ninho.

---

### Post by Poelie on 2009-05-27
hi all,

Currently I have a Linksys wrt54 connected to my linksys wag160n. Connecting to the wrt54 is going without any problems. of course, Connecting to my linksys wag160n has problems.

lately I installed the new 1.00.12 which doesn't solve the problem...

Poelie

---

### Post by Andropopolips on 2009-07-24
GAH! This is so frustrating! I'm on the wireless now, but the only way I can get a connection is by disabling encryption altogether. It won't even let me WEP in. It looks like it's athenticating properly by then sits on "Obtaining ip address" for a minute or so and dies out.

Has anyone been able to either fix this or get some more word from Linksys?

---

### Post by warfacegod on 2009-07-25
I've been trying to fix this problem for quite some time as well. I've wandered the forums a good bit and I see allot of people with the same issue regardless of what router or wireless card is in use. It looks like network manager isn't properly remembering the encryption passkey. If you tell it to show you the passkey after it spins it's wheels, it comes up as a garbled mess. That is about as far as I've gotten with this issue, the workarounds I've found are well outside of my competence level or where simply too tedious i.e. using long terminal commands every single time you want to use secured wireless.

---

### Post by johngrimes on 2009-10-26
I am having this same problem - I have submitted a new bug to Launchpad at the following address: [https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/461557](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/461557).

Please submit any extra information to this bug page so that we can help to get this problem resolved.

---

### Post by Poelie on 2009-10-29
Guys,

the bug is fixed in 9.10.
So this item can be changed to solved.

Greets

---

### Post by OSConvert on 2009-12-08
I am still having problems with 9.10.  In fact my WPA wireless has not worked since 7.10 - which I have been running until this week.  I've tried every release since 7.10 with no success.

I put on 9.10 last weekend as a new install (not upgrade), dual booting with vista, but still no wireless.  I installed the linux-backport-modules-karmic according to intellinuxwireless website, but wireless WPA still won't work.

I hope someone can help.

---

### Post by Reinaldo1981 on 2009-12-09
Hi, i'm also having the same problem after a fresh install... any help would be great...
Thanks,
Reinaldo

---

