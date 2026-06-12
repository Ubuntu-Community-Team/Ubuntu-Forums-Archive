---
title: "REALLY want to make Ubuntu work with D-link modem"
date: 2010-01-20
forum: New to Ubuntu
---

### Post by Windoze Refugee on 2010-01-20
Hello people.
Ive suffered many years of Windoze before finally getting to the point where I can take no more!!
During that time I like to think, Ive learned enough about computers to say that I can handle pretty much all but the most complex tasks.
However...
I have a version of Ubuntu installed on a partitioned drive also running XP.
Im depsrate to make the swich but am having a lot of trouble getting online with Ubuntu.
I have a speedtouch modem whcih i use for the XP end of things, but which Ive given up trying to make work with Ubuntu.
So..
Ive now aquired a D-link ethernet modem (as suggested) but cant figure out how to make it work with Ubuntu either.
Argghhhh
Any help would be very gratefully received
Highest
WR

---

### Post by chewearn on 2010-01-20
Are you able to access the modem via it's default IP?  The modem user manual should provide this info.

I'm not familiar with D-link products.  But for Linksys, the default IP is usually 192.168.1.1.  In this case, the PC should be set to the same subnet, i.e. something like 192.168.1.2.  You then access the modem via web browser by entering the IP into the URL bar.  This should show you the modem set-up page.  It would also probably ask for the user name and password, which can be found in the user manual as well.

---

### Post by Temposs on 2010-01-20
Not all of a company's products work equally well on Ubuntu. You can't just assume that just because a D-Link modem product works for someone, you can go out and buy any random D-Link product and expect it to work equally well. The best thing to do is to go to a site like: [http://www.ubuntuhcl.org/](http://www.ubuntuhcl.org/)

This site lists specific pieces of hardware, rates their compaitibility, and people contribute workarounds for any issues there may be. You should check your specific modem model and see if it is compatible.

[http://www.ubuntuhcl.org/browse/search?keywords=D-Link](http://www.ubuntuhcl.org/browse/search?keywords=D-Link)

As you can see, most of the hardware listed there is said to work well, but some of them simply don't work. Is your model on there?

---

### Post by oldsoundguy on 2010-01-20
D-Link makes a lot of stuff!

I use a DI-624 router for both hard wired and wireless.
With the 520x PCI cards for the wireless desktops.
Work flawlessly.

Need to post the MODEL number, but you could also go looking on Google for the quick start guide for your particular router. 
Just follow the yellow brick road.

---

### Post by Temposs on 2010-01-20
Also, what is the model of your D-Link product. No one can really help you well until we know the model of the product you have.

---

### Post by Swab on 2010-01-20
Have you got the D-Link working in Windows?  If so is it assigning your computer an IP address or have you manually put an IP in to Windows?   If the former is true then it should work just fine in Ubuntu, if it's the latter then you should turn on the DHCP server on the D-Link.

---

### Post by Windoze Refugee on 2010-02-28
Hi Everyone & thank you all for your input.
Apologies for the delay in responding - the embarrassing truth was I forgot to click the 'email when I get a reply' thing.
 
OK
Then Modem is  D-link  ADSL ethernet/USB  modem/router
Model DSL-502T
 
I have in fact had some success in that ubuntu recognises the connection (assiging it its own IP address 192.168.1.3 (I think))
I've tried configuring it both manually and using "Automatic (DHCP) addresses only" and entering my DNS servers manually (Im with Onetel and their DNS Servers are  
212.67.96.129 & 212.67.96.130 apparently.
 
But no mater what permutation I use I cant seem to get them to connect or even in fact be able to ping this aaddress or indeed any other. Im guessing it has somehting to do with a gateway (?) and Ive never been prompted for a username or password - is this usual?
 
Im used to having a broadnabd modem whihc 'dials' in using username and password. Is the ethenet connection that radiacally different in the way it negotiates with the server?
 
Still lost, getting a bit nearere (I think) but no less determined
 
Cheers guys

---

### Post by Windoze Refugee on 2010-02-28
Hi Swab, 
how do I turn on the DHCP server on the d-link?
And what is DHCP incidentally?
Cheers
WR

---

