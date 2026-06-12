---
title: "help! DoS ?"
date: 2005-06-27
forum: Networking &amp; Wireless
---

### Post by soonindallas on 2005-06-27
hello all.  I have a dual-boot laptop.  I am connected right now with XP because I can't get ubuntu to work with the www.  I believe it's because of my isp's insecure network, and I need your help to figure this out.

firstly, I have neen happly running Ubuntu on this laptop for as long as I have owned it -- about 2 months.  This weekend I wanted to check some email and the connection to my ISP failed.  No biggie, it happens rarely and I had a bunch of other things to get done so I let it go on Saturday... HOWEVER... today Monday, after 2 calls to my ISP and having to boot back into WinXP for the benefit of their helpdesk, I am at a loss... I need to figure this out because www functionality with XP is impaired, and with Ubuntu it is nil !!

what gives ?!?

teh Ubuntu: Hoary 686, almost stock, and in any case with no modification since all was well friday.  I have tried going back to Hoary 386, which I was using until about 2 weeks ago but I have the same problems. 

teh connection: ethernet cable directly into my cable modem, a motorola fwiw.

teh symptoms:
when I connect to my ISP's network (DHCP) to browse the web, get email, ping stuff,  I suffer from sluggishness and periodic disconnection (not me personally, my connection)

I notice that my gnome panel applet shows that packets are being constantly received.  This, I think is unusual.

Q1: how can acquire these packets to see what they are ?  I think I might need them to show to anyone here who might be interested in helping, and in any case it might help my ISP.

When I saw all these packets received I thought maybe I inherited the IP address that was the victim of a DoS attack.  Since, the lease has been renewed, I have a different IP address -- I know how to do this in WinXP but not in Ubuntu, can anyone point me to a howto here ? -- but the problems remain.

Q2: how can I fix this ???

thanks for your attention.

Peter

---

### Post by dialate on 2005-06-27
A1: You can use Ethereal ($ sudo apt-get install ethereal) to get a closer look at what is coming in. When you are done capturing, you can look at each packet recieved, get an exhaustive analysis in a dropdown list, and then look at it bit by bit. To use it in promiscuous mode (see packets received that weren't intended for your machine) you should:
$ gksudo ethereal

To renew the dhcp, try
```

$ sudo dhclient -r eth0
$ sudo dhclient eth0

``` 

A2: You could use Firestarter, a good software firewall. [http://www.ubuntuguide.org/#firestarter](http://www.ubuntuguide.org/#firestarter)

---

### Post by Arthemys on 2005-06-27
[QUOTE=soonindallas]hello all.  I have a dual-boot laptop.  I am connected right now with XP because I can't get ubuntu to work with the www.  I believe it's because of my isp's insecure network, and I need your help to figure this out.

firstly, I have neen happly running Ubuntu on this laptop for as long as I have owned it -- about 2 months.  This weekend I wanted to check some email and the connection to my ISP failed.  No biggie, it happens rarely and I had a bunch of other things to get done so I let it go on Saturday... HOWEVER... today Monday, after 2 calls to my ISP and having to boot back into WinXP for the benefit of their helpdesk, I am at a loss... I need to figure this out because www functionality with XP is impaired, and with Ubuntu it is nil !!

what gives ?!?

teh Ubuntu: Hoary 686, almost stock, and in any case with no modification since all was well friday.  I have tried going back to Hoary 386, which I was using until about 2 weeks ago but I have the same problems. 

teh connection: ethernet cable directly into my cable modem, a motorola fwiw.

teh symptoms:
when I connect to my ISP's network (DHCP) to browse the web, get email, ping stuff,  I suffer from sluggishness and periodic disconnection (not me personally, my connection)

I notice that my gnome panel applet shows that packets are being constantly received.  This, I think is unusual.

Q1: how can acquire these packets to see what they are ?  I think I might need them to show to anyone here who might be interested in helping, and in any case it might help my ISP.

When I saw all these packets received I thought maybe I inherited the IP address that was the victim of a DoS attack.  Since, the lease has been renewed, I have a different IP address -- I know how to do this in WinXP but not in Ubuntu, can anyone point me to a howto here ? -- but the problems remain.

Q2: how can I fix this ???

thanks for your attention.

Peter[/QUOTE]
 A quick thing to try:

Open up a shell in GNOME and type in...

sudo ifdown eth0
sudo ifup eth0

And see if that helps you any, what that will do is release your IP address and attempt to acquire a new one from the DHCP server.

---

### Post by soonindallas on 2005-06-27
Thanks for the suggestions... all seems to have come back online tonight... though what it might be down to is anyones guess... my cable operator is in constant denial of any QoS issues, though the forums are full of complaints about outages and other problems that cannot be coincidental.

[QUOTE=dialate]A1: You can use Ethereal ($ sudo apt-get install ethereal) to get a closer look at what is coming in.... [/QUOTE]

Thanks. that looks interesting, though I don't know where to start to interpret the stuff that app produces....  The output I looked at earlier did not look 'clean', even to my untrained eye: lots of 'out of order' (?) and 'lost' and resent in the comments.


[QUOTE=dialate]
To renew the dhcp, try
```

$ sudo dhclient -r eth0
$ sudo dhclient eth0

``` 
[/QUOTE]

I tried this and for some reason kept getting the same IP back from my ISP.  Another mystery.

Thanks again.

/PC

---

### Post by dialate on 2005-06-27
> I tried this and for some reason kept getting the same IP back from my ISP. Another mystery. 

Ah, I've run into this too...you have to wait awhile after you've released your IP address for someone else to take it, or a lower number IP opens up, so you can get another one.

For my ISP, this takes about 5 mins. It might be longer or shorter for you depending on the size of your ISP (more people = more chance someone changes something)

---

### Post by kvidell on 2005-06-27
I doubt it's an attack. If you've gotten several new ip addresses and still suffer the problem I think something else is to blame...
An attack wouldn't cause a disconnect...
Not to mention DoS's are not OS specific... If it was happening to you in linux, it'd happen to you as hard if not harder in windows.

Do you by any chance have IPv6 enabled? What are your DNS servers when you're in linux? (cat /etc/resolv.conf)

- Kev

---

### Post by soonindallas on 2005-06-27
[QUOTE=kvidell]

Do you by any chance have IPv6 enabled?
[/QUOTE]


[I]peter@ubuntu:~$ dmesg | grep IPv6
IPv6 over IPv4 tunneling driver
eth1: no IPv6 routers present
eth0: no IPv6 routers present
eth0: no IPv6 routers present
eth0: no IPv6 routers present
eth0: no IPv6 routers present
eth1: no IPv6 routers present[/I]

>  What are your DNS servers when you're in linux? (cat /etc/resolv.conf)

'cat /etc/resolv.conf' returns the search domain and the private IP of my wlan gateway.

My router gets my ISP's DN server info.  When I look at the 'router status' page is contains the correct DNS info.
/PC

---

### Post by kvidell on 2005-06-27
[QUOTE=soonindallas]'cat /etc/resolv.conf' returns the search domain and the private IP of my wlan gateway.

My router gets my ISP's DN server info.  When I look at the 'router status' page is contains the correct DNS info.[/QUOTE]manually edit the file (with root access, obviously (sudo!)) and remove the search domain, save the file, exit.. then try going to your favourite website again.
- Kev

---

### Post by soonindallas on 2005-06-27
[QUOTE=kvidell]manually edit the file (with root access, obviously (sudo!)) and remove the search domain, save the file, exit.. then try going to your favourite website again.
- Kev[/QUOTE]

I did this.  It didn't seem to break anything...
May I ask why you suggest this ?

thx

---

