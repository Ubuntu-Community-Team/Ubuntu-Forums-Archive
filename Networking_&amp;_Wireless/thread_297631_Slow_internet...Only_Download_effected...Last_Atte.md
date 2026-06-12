---
title: "Slow internet...Only Download effected...Last Attempt..."
date: 2006-11-11
forum: Networking &amp; Wireless
---

### Post by residentninja on 2006-11-11
Ok, this is my last ditch effort to fix my internet before I completely give up and install...oh god...Windows. I love linux and love it as a desktop and think that Ubuntu is a great distro but I can't keep having this problem.

I have searched the internet looking for a solution and am about to give up. Here is my problem and what I have done so far.

When I first boot up my computer the internet works as intended. Fast speeds good response, hurray. But, after a short time the speed will suddenly drop to the point that it is almost unusable. During this time, my computers performance remains the same and Both windows boxes on my network continue to work fine (truely odd). For example.

Everytime I start up my computer and run a speed test (say on speakeasy.net) I get speeds of about: (all numbers are in kbps)
1336 Download and 280 upload

Doing the same test a short time later when I notice sites starting to pull up slowly I get:
50 Download and 280 upload

This varies between 41-59 but is ALWAYS in that range, while upload remains un-effected.

This especially effects me while I'm playing something like World of Warcraft. I will see my speeds and reaction times but fast, then get slower and slower until I finally get disconnected. This seems to vary in length of time for it to happen. Sometimes it will get slower and slower, almost get to the point of disconnection, then will be fine again for awhile. Sometime, but rarely, it will disconnect me then be fine for several hours. Much more common is that it will bog down for long periods of time then cycle back again.

During these times surfing is equally slow so I know it's not just the game. In fact, right now pulling up these pages took forever and I haven't even started up WoW since I booted my computer.

What I have done so far:

1) Changed DNS to my ISPs DNS servers instead of to my router. (Doesn't make since that this would help in this case and it seemed to do nothing. But I read several posts of similar problems and people said it helped them so I tried it.)

2) Disabled IPv6. Before disabling IPv6 the slowness seemed to be more constant and regular. I tried disabling it in several ways that I saw mentioned. IPv6 is disabled though.

3) I found and it was recommended by some networking friends of mine, and read on some forums, that it might be because tcp_window_scaling and tcp_ecn where enabled. I disabled these and on both my wives computer and on mine this seemed to help some but still over all the problem persists.

I really don't want to go to windows for my desktop. I really love running Ubuntu. I'm not a novice at this, I'm the Linux Security Administrator for a large web hosting company, but this problem has me stumped. I've never encountered it before. At my office I run Ubuntu and do not have this problem.

System Specs....
Ubuntu 6.10 Edgy (same problem occured under 6.06 as well)
Processor: AMD 64 X2 4200+ (but I am running 32bit SMP instead of 64 because of install issues with the 64 bit version)
Motherboard: abit Fatality AN9 32x (I have used both the onboard NICs and a PCI NIC and have the same results)
Memory: 1GB
Video Card: eVGA GeForce 7900 GS

Also of interest:

Bizzarly, pings seem to do weird things. So right now I pulled up papajohns.com very slowly, a site I have never been to before. At the same time ping it I get:

ping papajohns.com
PING papajohns.com (63.241.144.120) 56(84) bytes of data.

--- papajohns.com ping statistics ---
33 packets transmitted, 0 received, 100% packet loss, time 32041ms

Afterwards pinging google I get:

ping [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (216.239.37.99) 56(84) bytes of data.
64 bytes from va-in-f99.google.com (216.239.37.99): icmp_seq=1 ttl=246 time=40.6 ms
64 bytes from va-in-f99.google.com (216.239.37.99): icmp_seq=2 ttl=246 time=37.4 ms
64 bytes from va-in-f99.google.com (216.239.37.99): icmp_seq=3 ttl=246 time=39.9 ms
64 bytes from va-in-f99.google.com (216.239.37.99): icmp_seq=4 ttl=246 time=36.4 ms
64 bytes from va-in-f99.google.com (216.239.37.99): icmp_seq=5 ttl=246 time=50.8 ms
64 bytes from va-in-f99.google.com (216.239.37.99): icmp_seq=6 ttl=246 time=45.6 ms
64 bytes from va-in-f99.google.com (216.239.37.99): icmp_seq=7 ttl=246 time=33.1 ms
64 bytes from va-in-f99.google.com (216.239.37.99): icmp_seq=8 ttl=246 time=37.5 ms

--- [www.l.google.com](www.l.google.com) ping statistics ---
8 packets transmitted, 8 received, 0% packet loss, time 6999ms
rtt min/avg/max/mdev = 33.155/40.206/50.845/5.260 ms


This is usually what happens. I can either ping something with descent return times or I can't ping it at all.

Also note: During all of this my 2 Windows XP boxes on my network (1 my laptop and 1 my roommate's computer) work perfectly fine. I simply cannot understand it.

My router:
My "router" is a Debian box that is up-to-date on patches and has a 2.6.8 kernel. I have these exact same result regardless of going through this box or being directly connected to the cable modem. It makes no difference, so I know the problem does not lie here.

Oh I have also re-installed several times and the problem remains. So it's not just a bad installation. When I installed windows just to test it...the windows install worked fine (good speeds constantly) so it doesn't seem to be hardware related.

Any and all help would be appreciated. Please save me from a windows Desktop future. Thanks.

---

### Post by residentninja on 2006-11-11
Immediately after posting this I went and did another speed test. The first one, to the Atlanta,Ga server where I live, came back with:
1208 kbps Download and 277 kbps Upload.

Right after the results came back I tried another one, this time to the New York server listed (this is on speakeasy.net) and got:
38 kbps Download and 278 kbps Upload.

Again right after to the Atlanta server returned 767 down 281 up, again to the Atlanta server with almost same results. Then another to the Washington server with results similar to the New York server only a little slower.

Noting...Doing the same series of tests yelded results in the 1060-1307 kbps everytime Regardless of the server I use.

I have tried other test sites as well all with compareable results.

---

### Post by stream303 on 2006-11-11
One thing you could do for a general speedup is to avoid dns lookups on your favorite sites by placing them in the /etc/hosts file, since that is what is checked first according to /etc/nsswitch.conf  (files before dns line) in Ubuntu.  Some others have this swapped, but most run files then dns)

Something like this in /etc/hosts

123.45.67.89  [www.myfav.com](www.myfav.com)
23.456.78.90  help.rcmodeling.org

hope this helps

---

### Post by residentninja on 2006-11-11
Thanks for the reply.
However, this isn't a dns issue. If it was dns then it would stall while looking up the site then be fast while loading the site. This it just being slow during the whole thing.

Thanks again though.

---

### Post by Michl on 2007-03-01
For what it is worth, I have a very similar problem.  My 56K modem
is fine when surfing or emailing.  It stays on for hours without
disconnecting.  But when i download, say, synaptic packages, I
am disconnected every 5 to 10 minutes.

Michl

---

### Post by HarmonicaGoldfish on 2007-03-01
this may help - I had the same experience of great speed with windows, then slow slow with ubuntu. Tried a bunch of things with dns cache, etc...nothing worked.

Following the instructions here did, though,

[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

---

### Post by Stoffelito on 2007-04-05
Hi there,

i've got exactly the same problem with bad download speeds after some time... "sudo /etc/init.d/networking restart" restores "normal" speeds but after some time speed gets worse again so that is not a brilliant solution...

i also run an athlon x2 (3800+) and an onboard nic (asus board, nforce chipset, forcedeth driver...)

it doesn't seem that there is a solution to that problem yet (i searched this forum and googled a lot...)

regards,

Stoffelito

---

