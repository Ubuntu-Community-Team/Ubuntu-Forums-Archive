---
title: "Sky Broadband"
date: 2007-03-21
forum: Networking &amp; Wireless
---

### Post by koshatnik on 2007-03-21
I'd like to hear your views on sky broadband. 

A friend bought a laptop with vista on it, and is looking to wipe it and replace it with ubuntu. He has just started a 1 year sub with sky for broadband, and sky have told him that the router and broadband modem they supplied will only work with windows. I said "bull****"  - is this the case? Are there any ubuntu users out there using sky broadband?

I suspect Sky are just talking crap. Can anyone shed any light on this?

Thanks

---

### Post by chili555 on 2007-03-21
I have no experience with Sky, but I have experience with two systems in the USA that claim not to support linux; one was cable-based and one is DSL. The DSL provider, in particular is pretty adamant that they do not support linux, to the point of almost hanging up the telephone when you tell them you cannot trouble-shoot through "Start -> Control Panel -> Network" because you don't own a Windows machine.

My experience as a 6-7 year linux user is that if the provider provides a box with a RJ-45 jack on it that a Windows or Mac machine can get an IP address from and surf the web, so can every linux machine I have built or (shudder) bought.

Let's put it another way: > I said "bull****CORRECT!

You might suggest that your friend dual-boot Vista (shudder) with Ubuntu so she/he can always tell Sky, "Yes we run Vista here!"

---

### Post by koshatnik on 2007-03-21
Thanks man.

I did suggest the dual boot route. Trouble is, Vista won't work either with the sky install disk! Once he gets Vista working with the connection, I'll install ubuntu, get that working via ethernet, then wipe vista.

I would really like to hear from anyone that has experienced problems with Sky. Apparently, its not a rare thing :) I thank God I am on cable.

---

### Post by ygarl on 2007-03-22
Basically, the compatabilty with Linux (or any other O/S...) is entirely dependant on the Router/Modem connected. If your O/S recognises it properly, it will work. 

If not, then no O/S in the world - including Vista - will get Broadband working.
Odds are 99% that you're going to be good-to-go however. It is routers' manufacturers interests to keep it strictly generic with their setups for obvious reasons!

---

### Post by mrspoons on 2007-03-22
I've got sky - tried setting up with the wireless connection using a netgear PCI card and the speeds were shocking.
Ended up running a cable from the sky router direct to the pc, works perfectly (15mb connection for £10 a month - bargain :) )

---

### Post by chili555 on 2007-03-22
> 15mb connection for £10 a month - bargain :)Absolutely! The least unsuitable deal I can find here is 1.5Mb/s for $37.95 US or about £20. You Brits get all the good stuff; Guinness, the MG F and now fast cheap broadband.

---

### Post by AlanRogers on 2007-03-22
> **koshatnik said:**
> Sky have told him that the router and broadband modem they supplied will only work with windows.That we're talking about Sky is irrelevent - if the interface to the internet is a router, connected to the computer via TCP/IP, there is no logical reason why it won't work, Linux or otherwise. The best way I've found so far, on a variety of routers, is to NOT install the supplied software - start by browsing to the router's default address.

That Sky, or indeed A N Other ISP, state that it doesn't work with Linux is marketing; what they can't be seen to confessing to is that they haven't tested it with Linux, nor can they afford to train their staff to support it. Windows is the predominant OS in the market, so that's where they concentrate their resource, followed by Mac.

I did ISP Technical Support for five years and we didn't ever officially support Linux. However, a number of the chaps in the call centre used it at home and, provided that call queues allowed, they usually tried to help. Sadly, I doubt that these days the staff have either the time or the motivation - remember; if you pay peanuts, you get monkeys.:-#

---

### Post by netztier on 2007-03-22
> **koshatnik said:**
> and sky have told him that the router and broadband modem they supplied will only work with windows. I said "bull****"  - is this the case?

If their router is a standard ethernet and TCP/IP device that will dole out addresses via DHCP and can be configured via telnet, ssh or Web Browser, it will work with almost any operating system. Period.

As long as the operating system of choice supports it's NIC properly and can correctly pull a DHCP lease without any special driver needed, there's no worries. TCP/IP, DNS, DHCP, HTTP are just what they are. protocols. Most modern operating systems including Linux even support PPPoE, so you can connect your PC directly to the DSL modem without a router in between (although I generally discourage this).

<RANT>
Saying "only Windows" is a sure sign of a service provider with a low budget on service and technical staff (and implies the suspicion that managerhood is at work instead of entrepreneurship). An ISP should always specifiy protocol standards his customers should adhere to, NEVER products. If they can't/won't give the technical details and protocol parameters their infrastructure requires, consider them as "technically challenged". And pick another ISP.
</RANT>

RAAAH... stories like that always get me upset :-/ 


best regards

Marc

---

### Post by karachuonyo on 2007-03-22
I believe the router provided by sky is a netgear 54ghz and seems to work ok with my linux computers. If you are wired you should have no problems but to go wireless will really depend on the chip of your wifi card. I think its easier to tell consumers the router will only work with windows because the techies know how is limited to windows only. My ISP (homechoice) also provided me with pamplets and equipment that they will only technically support if you use windows.

---

### Post by koshatnik on 2007-03-22
Thanks for all your input on this. My first reaction when he told me was "that's a load of crap." I'm sick of big companies just talking complete rubbish at people. Anyway, Vista off this weekend, ubuntu on.

Another license lost. :)

---

### Post by liamwithers on 2007-04-04
I have recently got sky broadband and set it up on my pc today. It really was as simple as plugging it in and clicking firefox. Took about 2 mins and im 12 so it should be pretty simple for anybody out there ;)

---

### Post by takuhii on 2007-08-22
I use Ubuntu Linux and Sky Broadband and have no problem what-so-ever. My guess is, is that if you have any technical support issues, you won't be able to ring them to sort it...

---

### Post by Bernie_the_bolt on 2007-11-02
Hi , I am a Brit now living in France. It is difficult where i live to get a decent broadband connection, so after some research have just ordered a SKY DSL package. It claims fast download speeds via satellite but dial up uploads via your existing dial up ISP.
I dual boot windows XP with edgy eft.
The Sky package had a choice of PCI card or external USB adapter, I have ordered the PCI version.
I will update you on this thread as to how I get on.
Some thoughts,
Disadvantages :
1. Cost of both providers (sky + existing ISP)
2. Slow uploads , presumably preventing successfull SKYPE calls & webcam use ?
3. Still prevents incoming phone calls when surfing, unlike true broadband
Advantages :
1. Much faster speeds achievable (I currently get 45 kbps, and the best adsl I can get here is 512)

---

### Post by Bernie_the_bolt on 2008-06-25
Update : Now been using SkyDSL package for about 6 months. With Pci card and software provided it will only work from my XP install, However I have plans to install it to my wifes xp pc and network the two and access the web from my linux machine.
Thoughts so far : Much faster than dial up.
Tariffs changed just after I signed up, Discovered the tariffs I was on was unusable due to low download max (700mb per month) charged per mb after that. So changed tariff to unlimited downloads but speed dropped to 1mb (actuall acheived 700-800 kytes/sec) A dual tarif can be used where you can choose to double your speed but a charge per mb is made.
Interestingly after about amonth of downloading videos from Usenext.com I noticed a marked drop in download speeds . I suspected "Fair usage policy" but have been unable to get firm answers from SkyDSL.
Think I will change when 12 month contract up.
Capable of very fast speeds if you can afford it.

---

