---
title: "Particular website opens and then don't after sometime."
date: 2014-10-04
forum: Networking &amp; Wireless
---

### Post by sushant3 on 2014-10-04
Hi!

I'm new to Ubuntu ):P. Just installed 14.04 LTS. Now, I have a particular site which opens sometimes (if lucky) then it won't and after a lot of tries opens again. All other sites are functioning well.

In windows (same PC- earlier and another PC), this site have no problem.

The site is Login.hathway.com. Unfortunately, this is the first site which need to be open to login and connect to net.

In NW tool, I have selected the default - DHCP(automatic) and for IPv6 have tried both none and automatic.

Anyone any clue?:confused::confused::confused::confused::confused:

Thanks in advance.

regards,
Sushant

---

### Post by Bucky Ball on 2014-10-04
Welcome. Won't do anything for me, either. For what reason do you need to access this login and what is it connected to? You are posting on the forums so obviously you are getting online fine. 

You state this in your post"

> Unfortunately, this is the first site which need to be open to login and connect to net.

You seem to be online. :-k

What am I missing?

* Update: I have no issue getting to login from [HERE]("http://www.hathway.com/") though.

Try this address: [http://payonline.hathway.com/mqsubscribe/selfcare/Default.aspx?tabid=103&ctl=Login](http://payonline.hathway.com/mqsubscribe/selfcare/Default.aspx?tabid=103&ctl=Login)

---

### Post by sushant3 on 2014-10-04
Hello,
The link you send works fine - this one is to see the billing status. And so does all other sites.

However, what does not works is 203.212.193.61/bsp/startportal.do?CPURL=http://login.hathway.com/ or login.hathway.com.
This one is required to do login and log-off, in order to utilize the internet facility.
1. out of 50 tries in 30 mins. it works, so I'm logged in.
2. Now that I have internet connection, I may visit any site.
3. Still Login.hathway.com and 203.212.193.61/bsp/startportal.do?CPURL=http://login.hathway.com/ are not accessible/ intermittent (once in 50 tries).
4. on my windows computer after login also, these sites are available.

SO, you see for this particular site/ server only there is a problem, that too in ubuntu not in windows.

Thanks
Sushant

---

### Post by vasa1 on 2014-10-04
Yes, there are quite a few complaints about logging into Hathway (as the internet provider) from linux systems.

See if [http://askubuntu.com/a/386547](http://askubuntu.com/a/386547) helps you.

Also, [http://www.ae.iitm.ac.in/pipermail/ilugc/2006-September/028785.html](http://www.ae.iitm.ac.in/pipermail/ilugc/2006-September/028785.html)

This involves rocket science: [http://gopi-kori.blogspot.in/2013/08/auto-login-to-hathway-broadband-using.html](http://gopi-kori.blogspot.in/2013/08/auto-login-to-hathway-broadband-using.html)

Also, [http://forums.mozillazine.org/viewtopic.php?p=13219199#p13219199](http://forums.mozillazine.org/viewtopic.php?p=13219199#p13219199) (and the other posts there)

---

### Post by jeremy31 on 2014-10-04
> **sushant3 said:**
> Hi!

I'm new to Ubuntu ):P. Just installed 14.04 LTS. Now, I have a particular site which opens sometimes (if lucky) then it won't and after a lot of tries opens again. All other sites are functioning well.

In windows (same PC- earlier and another PC), this site have no problem.

The site is Login.hathway.com. Unfortunately, this is the first site which need to be open to login and connect to net.

In NW tool, I have selected the default - DHCP(automatic) and for IPv6 have tried both none and automatic.

Anyone any clue?:confused::confused::confused::confused::confused:

Thanks in advance.

regards,
Sushant

In the windows file system go to windows[COLOR=#111111][FONT=Lucida Sans Unicode]\system32\drivers\etc\ and open the hosts file and see if there is something about login.hathway.com[/FONT][/COLOR]

---

### Post by Bucky Ball on 2014-10-04
> **vasa1 said:**
> Yes, there are quite a few complaints about logging into Hathway (as the internet provider) from linux systems.

See if [http://askubuntu.com/a/386547](http://askubuntu.com/a/386547) helps you.

Also, [http://www.ae.iitm.ac.in/pipermail/ilugc/2006-September/028785.html](http://www.ae.iitm.ac.in/pipermail/ilugc/2006-September/028785.html)

This involves rocket science: [http://gopi-kori.blogspot.in/2013/08/auto-login-to-hathway-broadband-using.html](http://gopi-kori.blogspot.in/2013/08/auto-login-to-hathway-broadband-using.html)

Also, [http://forums.mozillazine.org/viewtopic.php?p=13219199#p13219199](http://forums.mozillazine.org/viewtopic.php?p=13219199#p13219199) (and the other posts there)

Nicely dug up, vasa. @OP: check these.

---

### Post by vasa1 on 2014-10-04
> **Bucky Ball said:**
> Nicely dug up, vasa. @OP: check these.Thanks! Let's see what OP says. The weird thing is that some Linux-cum-Windows users of Hathway ISP claim that they log on via Windows, quickly do a reboot into Linux and then can access Hathway!

And someone mentioned user agent spoofing as a possibility. No one, AFAICT, reported contacting the ISP with their issue. I wonder how people using Android or Apples access this ISP.

---

### Post by sushant3 on 2014-10-05
Good thread gave insight on what Hathway does for authentication.1. I use to try [http://203.212.193.61/bsp/startportal.do?CPURL=http://login.hathway.com/](http://203.212.193.61/bsp/startportal.do?CPURL=http://login.hathway.com/), doesn't work.2. Installing the Cyberoam client for linux and then configuring it also does not work. Will try once more.Will update on the progress.Thanks.

---

### Post by sushant3 on 2014-10-05
So, I called Hathway. I told I'm not able to access the site on my Ubuntu Laptop.

They told they would resolve and now internet is on 24X7. 

I think they changed some authetication process..

Well, I guess evry1 who have a problem with Hathway should call Customer care - Hathway..
Their default client does not work on Ubuntu..

Best Sushant

---

### Post by Bucky Ball on 2014-10-05
Does this mean everything is fine now? I'm a little unclear. If all is good please mark the thread 'solved' to help others. Thanks. ;)

---

### Post by sushant3 on 2014-10-05
Yes everything is F9. No problems with Ubuntu. ISP support was needed instead.
Thanks for pointing out by means of links.. :p

---

### Post by vasa1 on 2014-10-05
> **sushant3 said:**
> Yes everything is F9. No problems with Ubuntu. ISP support was needed instead.
Thanks for pointing out by means of links.. :p
No problem at all. I'm just happy to help someone from India stay with Linux. It compensates just a tiny bit for my not being able to convince any of my acquaintances to switch to or even to try Linux :)

---

### Post by sushant3 on 2014-10-06
Thanks every1.:p
Vasa Glad there are people like you out there to help :)

---

