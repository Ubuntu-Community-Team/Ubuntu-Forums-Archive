---
title: "repository probs"
date: 2008-02-11
forum: Networking &amp; Wireless
---

### Post by ankscorek on 2008-02-11
r the ubuntu repositories online

here is my source.list but im unable to connect to them

im in region India

root@skal-laptop:/etc/apt# apt-get update
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.dogfood.launchpad.net](http://archive.dogfood.launchpad.net) feisty-backports Release.gpg
  Could not connect to archive.dogfood.launchpad.net:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out

source.list

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security restricted main multiverse universe #Added by software-properties
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy restricted universe multiverse main
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy restricted main multiverse universe #Added by software-properties
#Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security main restricted
 #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security restricted main multiverse universe
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security restricted main multiverse universe
 #Added by software-properties
#deb [http://archive.ubuntu.com/ubuntu/gutsy/main](http://archive.ubuntu.com/ubuntu/gutsy/main)

:guitar:

---

### Post by jan quark on 2008-02-11
yes there are online :) just tested it
> 
Could not connect to archive.ubuntu.com:80 [COLOR="Red"](1.0.0.0)[/COLOR], connection timed out

but this Ip address seems strange
do not know what to do with that now

---

### Post by NIT006.5 on 2008-02-11
Are you able to access other sites normally?

Is it possible that the DNS settings for your connection are not configured correctly? Coz, that IP it's showing is very strange. Never seen that before. 

1. Perhaps try:

```
nslookup archive.ubuntu.com
```

And see if you get a response and what it shows. It should look something like:

```
Non-authoritative answer:
Name:   archive.ubuntu.com
Address: 91.189.88.31
Name:   archive.ubuntu.com
Address: 91.189.88.45
Name:   archive.ubuntu.com
Address: 91.189.88.46

```

At least then you can see if your DNS is functioning correctly and go from there.

2. Also try:

```
ping 91.189.88.31
```

If you get a reply, then your connection is working, and depending on what happened with the nslookup, it might give some clues.

Hope that helps.

---

### Post by ankscorek on 2008-02-11
im able to ping all sites

now the problem to start off is 

when i try using lynx [www.google.com](www.google.com)

it says sending request to the site but im unable to see the site contents on the text browser and it continues to send request

moreover in my network tool im only able to see "roaming mode enabled"

what is all this

i was having the same problem with kubuntu but i did

#apt-cdrom add

then the repositories worked fine

however ubuntu is behaving very strange

i tried the same stunt as on ubuntu ie making new sources.list file but of no help

any guidance please

---

### Post by NIT006.5 on 2008-02-11
Hi,

You never mentioned what the result of the nslookups were?

By adding the cd-rom to the sources, it just means you're getting packages from the disc and not from the net - so it doesn't actually solve your net problem. 

You could try changing the mode to use DHCP instead of roaming, but not sure if that will help and it will depend on your network config. 

As a further test to establish if it's a dns issue, you can also try and access google on one of it's IP's (thereby "bypassing" any possible dns issues). So try:

[http://66.102.9.99](http://66.102.9.99)

and see if you can open it. If you can, then it's definitely a dns-related issue. If you can't, then it has to be something else.

---

### Post by NIT006.5 on 2008-02-11
Also, if you pinged the sites using the actual IP, try pinging using the dns name:

ping archive.ubuntu.com

and see if your ping is still successful.

---

### Post by ankscorek on 2008-02-11
i built the fresh index from the cd

however i checked the restricted modules the multiverse modules and restricted modules 

i am able to download the packages from kubuntu

i unchecked roaming mode and physically configured the eth card for dhcp but same results

can i have the files i can use

can i go ahead with working slackware files for networking on ubuntu?

ankush@skal-laptop:~$ nslookup archive.ubuntu.com
Server:         192.168.1.1
Address:        192.168.1.1#53

Non-authoritative answer:
Name:   archive.ubuntu.com
Address: 91.189.88.46
Name:   archive.ubuntu.com
Address: 91.189.88.31
Name:   archive.ubuntu.com
Address: 91.189.88.45

ankush@skal-laptop:~$



ankush@skal-laptop:~$ ping archive.ubuntu.com
PING archive.ubuntu.com (91.189.88.31) 56(84) bytes of data.
64 bytes from leningradskaya.canonical.com (91.189.88.31): icmp_seq=1 ttl=53 time=209 ms
64 bytes from leningradskaya.canonical.com (91.189.88.31): icmp_seq=2 ttl=53 time=209 ms
64 bytes from leningradskaya.canonical.com (91.189.88.31): icmp_seq=3 ttl=53 time=209 ms
64 bytes from leningradskaya.canonical.com (91.189.88.31): icmp_seq=4 ttl=53 time=207 ms

---

### Post by NIT006.5 on 2008-02-12
Thanks for the feedback. Ok, I have to admit, I'm completely stumped and have no idea what the problem could be.

Unfortunately I also don't have much time right now as I'm about to move house, but I wish you the best of luck!

---

### Post by ankscorek on 2008-02-13
i fixed repository probs with ubuntu but however im unable to get the view of browser page on it

any group policy etc?


OK GUYS HERE IS IT HOW I GOT IT FIXED

I INSTALLED BIND9 AND APACHE2 AND EDITED MY RESOLV.CONF

ADDED THE LINE

NAMESERVER 127.0.0.1

I MADE MY MACHINE INTO A DNS SERVER

I AM TYPING FROM UBUNTU

ANY OTHER SOLUTIONS ARE MOST WELCOME

THIS I FIGURED OUT WHEN I WAS USING SLACKWARE I WAS HAVING THE SAME PROBLEM

---

