---
title: "Cannot connect to closed wireless network"
date: 2008-11-03
forum: Networking &amp; Wireless
---

### Post by Svip on 2008-11-03
After upgrading to 8.10, I am having a strange issue.  I use a Boardcom wireless card, but have been using a working proprietary driver since 8.04.  It works flawlessly.  No problem whatsoever.

Now, after upgrading to 8.10, I am encountering an issue when connecting to the wireless network at home.  The wireless network here is closed with a 128-bit ASCII passphrase.  And it even says I have connected and obtained the exact IP address I have specified for the machine through its MAC address (on the router that is).

However, it is unable to connect to any other device in the home and the Internet.  And no other device is able to see it.  I am simply baffled, cause the wireless manager works perfectly fine on other wireless networks, closed as well.  It is only this network that has proven strange.

Any logs you need, just say so, I can acquire them.

---

### Post by Svip on 2008-11-03
Here is a minor update, every time I try to ping a computer I know exists on the network, I get the following error:

```
ping: sendmsg: Operation not permitted
```

I did several searches on this error, but each time they claimed it to be a problem with firewall or iptables.  But I fail to see how it could be, when it works perfectly on other networks.  Or maybe it is, and my network has some specific issue.

Needless to say, I was unsuccessful with iptables, especially because it is not very straight forward.

Interesting, when I ping the computer *itself*'s IP on the network, not localhost, it works perfectly.  And ifconfig confirms that I have that IP and all that.

---

### Post by The Foz on 2008-11-19
Hi,

Did you resolve this?

I have a similar problem (same ping error message), and would like to fix it.

---

### Post by Svip on 2008-11-19
> **The Foz said:**
> Hi,

Did you resolve this?

I have a similar problem (same ping error message), and would like to fix it.

Yes, but you're not gonna like it.  As usual, upgrading the system did not work flawlessly for me, so after I reinstalled Ubuntu from the bottom up, everything work fine.  I know this seems like a moot solution, but that was mine.

---

### Post by spegru on 2008-11-19
I have a similar problem with a brand new new 8.10 installation on a IBM T41.

The wireless works fine if the network is set up without security

However when setup with WPA-PSK encryption, although the network manager correctly says security is required, there is no way to enter the keys
(the boxes are greyed out)

Anyone else having this problem?

spegru


PS I have already tried resetting the router in case that was the problem

---

### Post by spegru on 2008-11-20
Because I installed ubuntu hardy on another t41 without this wireless problem, I tried a live CD session on hardy instead of Intrepid.
Result was no wireless at all.
So I guess the two machines are different in some way

I did a lspci and this was the result:
 Network controller: AIRONET Wireless Communications Cisco Aironet Wireless 802.11b

It seems possible there is a driver problem with this, when running a secure wireless link.

Ideas appreciated..............

---

### Post by spegru on 2008-11-23
I changed the encryption type to WEP and now it works fine.

However WEP is not really secure and I want to give this laptop to someone who is running WPA, so it's only a temporary solution.

It seems the drivers for this Aironet wirless card do not support WPA encryption  properly.

Help anyone?

spegru

---

### Post by spegru on 2008-11-23
A cursory google indicates that there may be problems with WPA-PSK even in windows - ie it may be a firmware issue. 

I'm still investigating...........

---

### Post by spegru on 2008-11-24
Something called WPA supplicant appears to be relevant to this, but all the information I saw about it iseems to be about a year old so I'm not sure if it is still current to Ubuntu Hardy or Intrepid

As a point of interest I tried the same network with the same laptop but running Mandriva 2009 (quite nice btw). Although this does let me enter the WPA code it still does not connect so I guess it is the same problem

---

### Post by gTinker on 2008-11-24
[QUOTE=spegru]
I did a lspci and this was the result:
 Network controller: AIRONET Wireless Communications Cisco Aironet Wireless 802.11b

Ideas appreciated..............[/QUOTE]

As far as I know there weren't any B cards that were capable of WPA. WEP was what was used in that era. Of course, I don't know everything about all hardware but unless you flashed a firmware upgrade or something I think  wireless B with WEP is going to be the best you can do with that card.

You can do a threat-risk assessment to decide if you need to upgrade for the higher security.

---

### Post by spegru on 2008-11-25
gTinker you may be right but I some people seem to have got this working.
However I cannot be sure about that. 

Can anyone confirm?



I may even change the wlan card for a more modern one if necessary

---

### Post by spegru on 2008-12-06
I was going to change the wlan card but the spare one i had is a mini pci and the one in the T41 is larger possibly full pci and so my spare one won't fit

So I'm back to trying to get ths cisco aironet thing to work with WPA encryption. Yes WEP does work, but it's known to be insecure and I want to give this to someone.

I've new tried 3 different distros and althouhg all of them detect the card and the network ok, none of them will connect in WPA mode

Maybe this has something to do with the WPA supplicant? What is that and how could I use it?

Any other ideas?

help please?

---

### Post by spegru on 2008-12-17
After fiddling further with the Cisco Aironet card without success, I bought a replacement intel miniPCI card off ebay.
Only £1.99 (+£5 p&p)

Since this was for an IBM Thinkpad T41, at first it would not boot due to an 'unauthorised' device error at bootup (before the OS started)
However this was fixed easily using a bios tool called no-1802 that you can download as a bootable CD iso image: [http://www.vincentkong.com/wp-content/uploads/2008/06/no-1802-cd.zip](http://www.vincentkong.com/wp-content/uploads/2008/06/no-1802-cd.zip)
Honestly it only took about half an hour between finding that surprising problem and fixing it!


Anyway, having done that, WPA wireless encryption works fine, and that £6.99 has to be one of the best ones I ever spent - should have done it weeks ago!
Intel is probably one of the best options for Linux wireless - no need for ndiswrapper etc - it just works!

---

### Post by chris.olive on 2008-12-17
Useing a Compaq V4335EA laptop, Broadcom 2200b/g card I can light the wifi lamp on the machine [for the first time] window drivers are installed, ndswrapper works, all appears OK but still cannot connect any ideas out there.

---

### Post by spegru on 2008-12-17
Did you enter the security code for your network?
How are you sure the card is working?
It might be worth trying on a network with security temporarily switched off

---

### Post by chris.olive on 2008-12-18
Spegru
Yes as far as I can tell the security code is entered,
Windows drivers detects the card, the card worked fine under windows [now gone].
Hardware test [Ubuntu] says the card is fine, other programs wifi radar etc will not detect the router, terminal query finds card and appears to show that drivers etc are working.
Tryed security off with no effect.
Later today I intend to swop routers from the [supplied] club-internet one to a Linksy I have will report later.
Thanks
chris

---

### Post by spegru on 2008-12-18
Try the different router.

Also 

1. Have you tried running from a live DVD?
2. There appear to be Intel Linux drivers for this card avaiable at 

[http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=944&OSFullName=Linux%2A&lang=eng&strOSs=39&submit=Go%21](http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=944&OSFullName=Linux%2A&lang=eng&strOSs=39&submit=Go%21)

---

### Post by chris.olive on 2008-12-18
Tryed Linksys and when set up it froze the machine needing a restart [lots of times] also it would not connect to the wired network allthough it said it was there will order a live DVD and try that.
have the linux 2200 b/g drivers installed
will try new drivers thanks for your help.
chris

---

### Post by chris.olive on 2008-12-21
Problem solved I have no idea how.
I spent most of two days delving into the Linksys router and laptop, on the second after connecting:) up my supplied router it suddenly connected via wifi even if a bit slow to do so, but it works.
Guess somehow something must have been wrong and my delving sorted it.
Anyway many thanks to all those who offered advice, now if I can only solve the freezing up problem!
Chris

---

