---
title: "out of ideas. need some help."
date: 2008-12-05
forum: New to Ubuntu
---

### Post by chavy85 on 2008-12-05
Ok so i've been using buntu for some time. i have edubuntu, ubuntu, and kubuntu, all on differnat comps. and one pc i have ubuntu and edubuntu installed for my son and i.

ok.. the list of questions and or problems.
ubuntu, firefox will not store bookmarks. won't save them, nothing. pisses me off. it imported some from my minimal vista install. but i can't save them. i've uninstalled compleatly and reinstalled, still not fixed.

vnc. is there a way for me to vnc into my desktop while my son is using his.? when i do this now i can log in but the screen is black. i'm using my mac with osX to log in remotely. vnc works great when no one is using their log in.  
need details on this. please.
 my appache page is running fine but i get a access log over and over from python to 127.0.0.1. or something like that every 32 seconds in my access log.  i'd get you the exact log but son is using it right now. and again i can't vnc to get the info.

do i need a firewall? i saw fireburner but havent installed it. should i?

hum. that's it for now.
Thanks
H

---

### Post by newbee70 on 2008-12-05
[B]
ok.. the list of questions and or problems.[/B]

ubuntu, firefox will not store bookmarks. won't save them, nothing. pisses me off. it imported some from my minimal vista install. but i can't save them. i've uninstalled compleatly and reinstalled, still not fixed.


What version of firefox are you using? 

if you are using version 3.0x have you went into bookmarks

then down to the organize/ then into import/backup. and did a backup?

---

### Post by chavy85 on 2008-12-05
hum no. when i installed ubuntu it asked if i wasnted to import anything. i toguht it would find my firefox install on vista.. it didn't. havent tryed that yet. will try in the AM.

---

### Post by chavy85 on 2008-12-05
ok i'm on my pc now.
here is the log from Apache.

221.192.199.36 - - [04/Dec/2008:17:51:56 -0700] "GET [http://sevy.eu.org/azenv.php](http://sevy.eu.org/azenv.php) HTTP/1.1" 404 207 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)"
221.192.199.36 - - [04/Dec/2008:21:53:27 -0700] "GET [http://sevy.eu.org/azenv.php](http://sevy.eu.org/azenv.php) HTTP/1.1" 404 207 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)"
127.0.0.1 - - [04/Dec/2008:22:37:07 -0700] "GET / HTTP/1.1" 200 8188 "-" "Python-urllib/2.5"
127.0.0.1 - - [04/Dec/2008:22:37:07 -0700] "GET / HTTP/1.1" 200 8188 "-" "Python-urllib/2.5"

I get those OVER AND OVER AND OVER

---

### Post by Paqman on 2008-12-05
Firefox stores the bookmarks inside /home/username/.mozilla, make sure the permissions are set so that it can write to that (stuff in /home is mostly 755)

---

### Post by chavy85 on 2008-12-05
anyone? any more help?

---

### Post by snova on 2008-12-05
> **chavy85 said:**
> 221.192.199.36 - - [04/Dec/2008:17:51:56 -0700] "GET [http://sevy.eu.org/azenv.php](http://sevy.eu.org/azenv.php) HTTP/1.1" 404 207 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)"
221.192.199.36 - - [04/Dec/2008:21:53:27 -0700] "GET [http://sevy.eu.org/azenv.php](http://sevy.eu.org/azenv.php) HTTP/1.1" 404 207 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)"
127.0.0.1 - - [04/Dec/2008:22:37:07 -0700] "GET / HTTP/1.1" 200 8188 "-" "Python-urllib/2.5"
127.0.0.1 - - [04/Dec/2008:22:37:07 -0700] "GET / HTTP/1.1" 200 8188 "-" "Python-urllib/2.5"

Probably nothing to worry about. I'd guess a script somewhere on your website is using Python's urllib to fetch content from the website, though why, I cannot say.

---

### Post by halitech on 2008-12-05
I'm guessing you aren't in china?

[color="red"]221.192.199.36 - - [04/Dec/2008:17:51:56 -0700] "GET [http://sevy.eu.org/azenv.php](http://sevy.eu.org/azenv.php) HTTP/1.1" 404 207 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)"[/color]

that IP is someone in china and I'm guessing they are using some kind of python script to look for open IPs

[http://whois.domaintools.com/221.192.199.36](http://whois.domaintools.com/221.192.199.36)

---

### Post by handydan918 on 2008-12-05
I'd worry about unsolicited contacts. 

whois output:

```
inetnum:      221.192.0.0 - 221.195.255.255
netname:      CNCGROUP-HE
descr:        CNCGROUP Hebei Province Network
descr:        China Network Communications Group Corporation
descr:        No.156,Fu-Xing-Men-Nei Street,
descr:        Beijing 100031
country:      CN
admin-c:      CH455-AP
tech-c:       KL984-AP
remarks:      service provider
mnt-by:       APNIC-HM
mnt-lower:    MAINT-CNCGROUP-HE
mnt-routes:   MAINT-CNCGROUP-RR
status:       ALLOCATED PORTABLE
remarks:      -+-+-+-+-+-+-+-+-+-+-+-++-+-+-+-+-+-+-+-+-+-+-+-+-+-+
remarks:      This object can only be updated by APNIC hostmasters.
remarks:      To update this object, please contact APNIC
remarks:      hostmasters and include your organisation's account
remarks:      name in the subject line.
remarks:      -+-+-+-+-+-+-+-+-+-+-+-++-+-+-+-+-+-+-+-+-+-+-+-+-+-+
changed:      hm-changed@apnic.net 20040329
changed:      hm-changed@apnic.net 20060124
changed:      hm-changed@apnic.net 20060125
changed:      hm-changed@apnic.net 20080314
source:       APNIC

route:        221.192.0.0/14
descr:        CNC Group CHINA169 Hebei Province Network
country:      CN
origin:       AS4837
mnt-by:       MAINT-CNCGROUP-RR
changed:      abuse@cnc-noc.net 20060118
source:       APNIC

role:         CNCGroup Hostmaster
e-mail:       abuse@cnc-noc.net
address:      No.156,Fu-Xing-Men-Nei Street,
address:      Beijing,100031,P.R.China
nic-hdl:      CH455-AP
phone:        +86-10-82993155
fax-no:       +86-10-82993102
country:      CN
admin-c:      CH444-AP
tech-c:       CH444-AP
changed:      abuse@cnc-noc.net 20041119
mnt-by:       MAINT-CNCGROUP
source:       APNIC

person:       Kong Lingfei
nic-hdl:      KL984-AP
e-mail:       konglf5@cnc.cn
address:      Shi Jiazhuang City, HeBei Province,050011,CN
phone:        +86-311-85128637
fax-no:       +86-311-86685210
country:      cn
changed:      konglf5@cnc.cn 20071226
mnt-by:       MAINT-CNCGROUP-HE
source:       APNIC


```

Want an egg roll with that?

):P

---

### Post by aimpau on 2008-12-05
Hackers.

---

### Post by handydan918 on 2008-12-05
> **aimpau said:**
> Hackers.

WE are hackers. THEY are crackers.

It's like the difference between a locksmith and a burglar.

Intent.

---

### Post by halitech on 2008-12-07
> **aimpau said:**
> Hackers.

> **handydan918 said:**
> WE are hackers. THEY are crackers.

It's like the difference between a locksmith and a burglar.

Intent.

if you want a little better detailed explanation of the difference, this is a good read

[http://searchenterprisedesktop.techtarget.com/tip/0,289483,sid192_gci998037,00.html](http://searchenterprisedesktop.techtarget.com/tip/0,289483,sid192_gci998037,00.html)

---

### Post by chavy85 on 2008-12-11
aswesome guys thank you for the help. i jsut get them OVER AND OVER AND OVER. getts annoying scroling past all of them to see who else and gettin on my site. not much yet. although google bot has started hittin alot latly. so it' just a matter of time. :-)

Thanks again..
now for the remote desktop.?

when using my Mac i can vnc://(my-ip) and it'll connect but only if my user name is on the main PC I'm vncing into.. not if say my wife or son is on. if they are on then it's a black screen.
HELP. 
heck even with XP and vista there were hack to were i could do this with mstsc. so i need to fix this.. thanks guys.

H

---

### Post by chavy85 on 2008-12-11
anymore help
^BUMP^^^

---

### Post by mkvnmtr on 2008-12-11
I am sure there is a better way but when i first installed I moved my bookmarks by doing copying all of them to my desktop in my Mac OS then moved them to Ubuntu on a stick and put the file on my desktop. When I double click on the file it opens in firefox. Then I justn went to each site and bookmarked it. Found a lot I didn't use anymore. I bet there is a way to import them from the file into firefox but I was not that experienced.

---

### Post by Duck2006 on 2008-12-11
Export them from win to a 3.5FDD or a usb stick, start up ubuntu and import them to firefox in ubuntu. That is the easy way of doing it.

---

