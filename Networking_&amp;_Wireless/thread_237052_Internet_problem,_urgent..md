---
title: "Internet problem, urgent."
date: 2006-08-15
forum: Networking &amp; Wireless
---

### Post by dannyb37 on 2006-08-15
I'm having a big problem with ubuntu 6.06.
I just installed it and I coulden't get internet when connected to the network.

From reading one of the other threads I did this

> 
in the firefox address bar type about:config

and in the filter bar type ipv6

and change from false to true= just double click it

shutdown firefox

restart firefox.

It worked for firefox.
Now I still can't connect in anything els! ](*,) 

I need help. Badly,

~ Danny

---

### Post by dannyb37 on 2006-08-15
[http://www.ubuntuforums.org/showthread.php?t=202838](http://www.ubuntuforums.org/showthread.php?t=202838) I tried that.

It didn't work!
Please, anyone?

---

### Post by dannyb37 on 2006-08-15
Sorry for triple posting.
But this is giving me a headach.

I used the EXACT same live cd of ubuntu that I used a while ago and the internet worked, I tried it now and it won't work!!!!!!

I'm useing the live cd now and I had to disable the ipv6 in firefox to post this, I have never had to do that before.

If I can't get this problem solved, I'll have to format ubuntu and just use windows! :( I really don't want to do that.

---

### Post by sdebo on 2006-08-15
Had same problem.  Installation could not configure networking.  But then I realised there was a loose connection with the router.  

I know it is naive, but maybe you overlooked it like I did.  Be sure to confirm that your hardware is ok.

Maybe you are experimenting with Firesarter?  I haven't used that yet.

---

### Post by drtvasudevan on 2006-08-16
> **dannyb37 said:**
> 
I used the EXACT same live cd of ubuntu that I used a while ago and the internet worked, I tried it now and it won't work!!!!!!


I'm useing the live cd now and I had to disable the ipv6 in firefox to post this, I have never had to do that before.

live cd loads in the RAM and the changes made are lost with rebooting.
unless you install it will not remain in memory.
you will have to do the changes again.
for otheres to work you need a systemwise change and that is done by the methods in the thread you mentioned.
hope you read upto the last post esp the last post that sums up everything.

if you have installed ubuntu and cant connecct we can further look into the issue.

---

### Post by dannyb37 on 2006-08-17
I installed it and coulden't connect!
I now am useing winXP, I had to keep my computer useable so I had to.
If we can get to the bottom of this problem, then I will install ubuntu linux permently.
I'll install it on a small partition later if that would help! ;)

---

### Post by jensenhearing on 2006-08-17
With these many threads on connecting and reading the HOWTO's am still getting on this forums via WinXP. Is there a dialer like function in Ubuntu to just dail into the internet?

Have tried pppconfig and pppoeconf. Both do not connect me to the net. Am running LiveCD Ubuntu 5.10.

---

### Post by dannyb37 on 2006-08-17
I think my problem might be in the router...

I swicked ipv6 off in firefox, solved the problem, but only in firefox...

How can I switch ipv6 off for the rest of linux?
Thanks :)

---

### Post by coffeecat on 2006-08-17
You need to disable IPv6 system-wide by editing a couple of system files. Look at [this thread]("http://www.ubuntuforums.org/showthread.php?t=87798"). Go right through to the end because the first post is a howto for Breezy and according to later posters this won't work in Dapper. What you have to do in Dapper appears later in the thread.

Alternatively, see if there is a later version of the firmware for your router and if there is, update it. This problem is usually down to old or inadequate router firmware. Disabling IPv6 is a quick fix but a bad idea in the long term. IPV6 is there for a purpose.

---

### Post by dannyb37 on 2006-08-17
In the router? Or the wifi card of my laptop?
If the router, I'll talk to my dad, see if he can do something about it...
Thanks! ;)

---

### Post by dannyb37 on 2006-08-17
I have a problem.

Disableing ipv6 only is working for FireFox and retreving CD info.
It isn't working for updates and software packages! :(

There isn't any firmware updates avalable for the router! :(

We still have the old router, but my dad refuses to use that one.
He keeps saying if it works on the rest of the computers (all windows) it will work on linux.

Is there any other to solve the problem?

---

### Post by dannyb37 on 2006-08-17
Another Question.

The router is a wireless adsl, that goes directly into the phone socket and then into the computer, If I plugged in the old router aswell as that would It work over the old router (with the one that won't work) as another hub? or not?

And with this new router, how can I use the internet without changeing it (as there is no firmware avalable for it)

---

### Post by coffeecat on 2006-08-17
If there is no updated firmware for your router then you must disable IPv6 system-wide. I've already given you a link for that.

---

### Post by dannyb37 on 2006-08-17
I have done, just it still won't let me update ubuntu and install from the package manager! :(

---

### Post by francolq on 2006-08-17
> **coffeecat said:**
> You need to disable IPv6 system-wide by editing a couple of system files. Look at [this thread]("http://www.ubuntuforums.org/showthread.php?t=87798"). Go right through to the end because the first post is a howto for Breezy and according to later posters this won't work in Dapper. What you have to do in Dapper appears later in the thread.

Hello (my first post!). I had a similar original problem: installed Dapper and internet was very very slow (when worked). Then I disabled IPv6 (and checked with lsmod that the module ipv6 doesn't get loaded) and things got a little better.

Now the are new problems: the speed is right but very frequently the connections are lost (e.g. Konqueror, Konversation, Adept, Kopete). And getting an IP from the router with DHCP only works at boot time. When I do 'dhclient eth0' or 'ifdown eth0; ifup eth0' I get  'No DHCPOFFERS received.'.

I still have Breezy installed in another partition and internet works very well with ipv6 enabled and loaded. Any idea? I can give you all the information you ask for. Thanks in advance and sorry for my english.

---

### Post by francolq on 2006-08-17
Some additional information: I am using the 64-bit Kubuntu 6.06.1 LTS on an AMD64. 'lspci | grep Eth' says:
0000:00:08.0 Ethernet controller: VIA Technologies, Inc. VT6105 [Rhine-III] (rev 86)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78 )

I guess the 1st is eth0 (PCI card) and the 2nd is eth1 (onboard, the manual says VT6013L)...

---

### Post by drtvasudevan on 2006-08-18
> **dannyb37 said:**
> I have done, just it still won't let me update ubuntu and install from the package manager! :(
updates are always a problem to many.](*,) 
proxy issues, busy servers.... so many reasons cited and no soultion in sight!:-k 
if you are able to browse well be happy!

:)

---

### Post by dannyb37 on 2006-08-18
> **drtvasudevan said:**
> updates are always a problem to many.](*,) 
proxy issues, busy servers.... so many reasons cited and no soultion in sight!:-k 
if you are able to browse well be happy!

:)

I had to bo back to windows. :mad: 
I need updates and beeing the linux newbi I am, I need the easy-to-use package manager lol.

Thanks for all of your help btw!

~ Danny

---

