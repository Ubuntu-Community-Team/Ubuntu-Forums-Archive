---
title: "host file bypassed?"
date: 2008-01-13
forum: Networking &amp; Wireless
---

### Post by vavoem on 2008-01-13
i've setup a webpage on my machine and want to be able to reach it on the same url as i can reach it from the internet
If i type in the url known on the internet i get connected to my nat router, logical because there is an a record in the dns server on the internet that points to my ip address.
To bypass this i have made an entry in my host file to point the external dnsname  to 127.0.0.1
imho this should prevail over dns but somehow it just doesn't
Setting up my own dns is just to much hassle does anyone have an idea?

---

### Post by HermanAB on 2008-01-13
Forward the port in the NAT router to the internal machine.

Cheers,

Herman

---

### Post by vavoem on 2008-01-13
That is allready the case.
The machine can be reached from the internet.

If i type in ping  myserver.somewhere.com on the machine the webpage is running on i get a reply from the external ip address of my router 
If i open the page with firefox the router asks me to logon.

I have put an entry in /etc/hosts like this
127.0.0.1 myserver.somewhere.com
i did 
sudo /etc/init.d/dns-clean restart

and i checked my nsswitch.conf to make sure files is used before dns is.

It is just basicly ignoring anything i put in my hosts file

B.t.w. i am unable to edit dns entries in the router itself

---

### Post by vavoem on 2008-01-13
Ok solved it 
I  did
sudo chmod  644 /etc/nsswitch.conf 
I guess that everybody should be able to read this file. 
Kind of strange since hosts is used by lots of people to bypass adware and popups.
Imho canonical should change this to 644 by default.

---

### Post by commonplace on 2008-04-25
> **vavoem said:**
> Ok solved it 
I  did
sudo chmod  644 /etc/nsswitch.conf 
I guess that everybody should be able to read this file. 
Kind of strange since hosts is used by lots of people to bypass adware and popups.
Imho canonical should change this to 644 by default.

Thanks, that fixed my problem. 644 IS the default. I'm not sure how mine got changed. Very weird, as it was working fine until earlier this week.

/Kevin

---

