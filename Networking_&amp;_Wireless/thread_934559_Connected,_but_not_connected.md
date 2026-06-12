---
title: "Connected, but not connected"
date: 2008-09-30
forum: Networking &amp; Wireless
---

### Post by RickDJ on 2008-09-30
I have an advent 5401 laptop that i got from PCWorld, wanted vista off ASAP n tried linux kubuntu KDE4 CD iso (at first).. and installed fine.. the problem.. i can't connect to the internet! (can't update the kubuntu package etc)
Konqueror says "Google contacted. Waiting for reply..." until it times out!!
My knetworkmanager says its connected and that its active!!!
I have successfully pinged google!
ifconfig also viewed (have results if need)
also tried -sudo apt-get update- it appeared to start downloading files but in the end says "connection failed".
In the end i used a programme called "Gparted" to completely wip-out anything hidden within my hardrive (just to make sure there was nothing on there to do with microsoft) and did it successfully (so i think). re-installed Kubuntu..
Problem is still there.
I have also tried to instal suse 11, mandriva 2009 beta, mandriva 2008, slackware 8.0 (DVD), ubuntu 8.04.1, kubuntu KDE4, puppy linux. And all succeed, but internet connection still un-available!](*,) (appart from both mandriva' which wont install ?!?!)
Also have 2 other laptops and 4 desktops with mandriva currently running fine on the net.
Im suspecting that vista has left some blood:roll: on my boards on its way out and wont allow anything to operate it.!
I am not an expert on linux at all, and fairly new to it.
I have a friend who can guide me a little while on linux but his knowledge is limited when it comes to problems. :-(
Im starting to think that perhaps microsoft are in team with laptop creators and creating laptops to only run the system it came with. (just a thought)
i hope this isn't the case and that someone here can solve my problem.
ANY info would be much appreciated.

---

### Post by Crafty Kisses on 2008-09-30
Post the results of this command:
```
ping google.com
```

---

### Post by RickDJ on 2008-09-30
PING google.com (64.233.187.99) 56(84) bytes of data.
 64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=1 ttl=240 time=116 ms
 64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=2 ttl=240 time=116 ms
 64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=3 ttl=240 time=117 ms
 64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=4 ttl=240 time=112 ms
 64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=5 ttl=240 time=113 ms
 64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=6 ttl=240 time=115 ms
 64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=7 ttl=240 time=232 ms
 64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=8 ttl=240 time=114 ms
 64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=9 ttl=240 time=115 ms
 64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=10 ttl=240 time=118 ms
 64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=11 ttl=240 time=125 ms
 64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=12 ttl=240 time=221 ms
 64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=13 ttl=240 time=340 ms
 64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=14 ttl=240 time=478 ms
 64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=15 ttl=240 time=117 ms
 64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=16 ttl=240 time=112 ms
 64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=17 ttl=240 time=117 ms
 64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=18 ttl=240 time=129 ms
 64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=19 ttl=240 time=118 ms
 64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=20 ttl=240 time=230 ms
 64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=21 ttl=240 time=112 ms
 64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=22 ttl=240 time=114 ms
 64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=23 ttl=240 time=114 ms
 64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=24 ttl=240 time=211 ms

---

### Post by superprash2003 on 2008-10-01
what happens when you type 64.233.187.99 in your browser

---

