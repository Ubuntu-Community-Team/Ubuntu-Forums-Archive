---
title: "netgear ga311 ubuntu 7.04"
date: 2007-08-05
forum: Networking &amp; Wireless
---

### Post by darksidedude on 2007-08-05
hello, I got this new Nic card from best buy and was wondering if it works under linux, I used it on fedora and well it didn't work, i try it on ubuntu and it still acts up:( I use dhcp, because i have a router, i get an IP ok and can connect to the lan, but I can't get to the outside, I don't wana use windows vista again if there is anything you can do please help thanks

ROCK ON:guitar:

---

### Post by moore.bryan on 2007-08-05
*what do you mean by "acts up?"*

---

### Post by darksidedude on 2007-08-06
like I said, I can connect to the lan ( we have 3 computers connected threw samba) but I cant connect to the "internet" like google, yahoo, or even this forum, im useing my parents server 2003 computer to post this:(

---

### Post by moore.bryan on 2007-08-06
*that's REALLY strange... sorry, but i don't have any insights; hopefully someone else will.  good luck.*

---

### Post by darksidedude on 2007-08-06
i had the same problem with fedora 7 but there forums don't even answer my post, its been a week 34 views and no responses sigh... I googled the card and found nothing about it not working

---

### Post by moore.bryan on 2007-08-06
*thinking over a cup of java makes me wonder if it isn't an issue with the router to which you're connecting.  that controls access to the "outside world."  i would double-check your settings on that...*

---

### Post by darksidedude on 2007-08-07
well my private IP is DMZ according to the router
my router came with the qwest internet they got, (here in tucson that was the only choice) 

it is an Actiontec Gt701-WG

---

### Post by moore.bryan on 2007-08-08
*let me look around for some info on that router and get back to you...*

---

### Post by moore.bryan on 2007-08-09
[I]okay, some basic questions:
1) in the router's maintenance section (192.168.0.1), what are the settings in the "wireless settings" section?
2) are you using wpa or wep?
3) what is the make/model/details for the wireless card you have?
[/I]

---

### Post by darksidedude on 2007-08-12
this isnt a wireless card, its gigabit ethernet:( it is easily confused with the wireless model though

---

### Post by moore.bryan on 2007-08-12
[I]wow... so, let me get this straight:
you're "hard-connected" to a router that will let you peruse the networked computers, but not give you internet access?[/I]

---

### Post by darksidedude on 2007-08-12
yea, thats the situation:(

---

### Post by moore.bryan on 2007-08-12
*that really does suck.  i'd still double-check all your router settings, though.  it's obviously working, as it allows you to connect through your network, and your card is obviously working.  it definitely sounds like an issue with the router allowing you outside access.  are all the other comps on the network able to access the net?*

---

### Post by darksidedude on 2007-08-13
yea, there all winblows based ( and wireless) I have to say i think it's DNS because on fedora, debian, freespire, RHEL ( yea bought it last month :( ) they all have my router as my primary DNS server, and my ISP's Dns as secondary, I can't even bother asking them as they don't suport linux in the least bit:popcorn:

---

### Post by moore.bryan on 2007-08-13
*dns shouldn't be the issue... i have opendns and use comcast.  still, you should go into your router's settings and check all the bits and settings.  anything that looks suspicious probably is.*

---

### Post by darksidedude on 2007-08-13
well you might be right,  my computers ip  private address 192.168.0.2
its DMZ. I thank you for the help uve given, maybe I should roll my own Kernel? Heard that works for some peoples issues, sounds hard but I don't want windows in any fashion

Side note tried PCLOS same issue ( didn't expect any difference) based on mandriva and that didn't work either

---

### Post by moore.bryan on 2007-08-13
[I]although daunting at first, compiling your own kernel isn't as difficult as it sounds.  i do think, though, that is extreme for your situation... perhaps there are a few more things we can try.  no worries about the help; that's what the community's for.  ;-)
i have dmz turned-off on my router... why don't you try that?[/I]

---

### Post by darksidedude on 2007-08-13
tried that and can't even get on the lan anymore:(

---

### Post by moore.bryan on 2007-08-13
*hmmm.... that doesn't make sense.  you should probably turn it back on.  ;-)*

---

### Post by darksidedude on 2007-08-14
yea.. as soon as that happened I put DMZ back, this is weird, 

well my 
reslov.conf had this
nameserver 192.168.0.1
nameserver 205.171.3.65

all of the distro's have the same information, so I dont know if its gnome or the router or my Nic card

---

### Post by moore.bryan on 2007-08-14
*i may be stubborn, but i still think it's a setting in your router which isn't letting you on the net...*

---

### Post by darksidedude on 2007-08-15
I don't know what other setting it could be?
well here is a pic of my router stup menu, I cant open all the windows at once, but this is the jist of it I think

---

### Post by moore.bryan on 2007-08-15
[I]could you post the screens of 
services blocking
website blocking
port forwarding
firewall
dynamic routing
static routing
[/I]

---

### Post by darksidedude on 2007-08-15
shure here they are

---

### Post by darksidedude on 2007-08-15
hmm well can only post 5 at a time, here is the 6th one

---

### Post by moore.bryan on 2007-08-15
*well, no clue.  sorry, man... i feel for you.  this doesn't make any sense.  i hope someone stumbles upon this and can actually help you.  if i think-up anything, i'll repost.*

---

### Post by darksidedude on 2007-08-15
I made a test run with RHEL and that worked fine, Fedora dosent but that does, man this aint cool, I dont have a clue about RHEL and there forums never help me EVER, well Im very glad you helped,

---

### Post by noob12 on 2007-08-15
Can you tell us what ```
route -n | grep UG
``` says in the second column?

---

### Post by jaakan on 2007-08-19
> **darksidedude said:**
> well my private IP is DMZ according to the router
my router came with the qwest internet they got, (here in tucson that was the only choice) 

it is an Actiontec Gt701-WG

Why is your computer on the DMZ?
Have you tried a cheap 10/100 NIC?
there is an option to change which IP is on DMZ, have you tried changing that?

When you can't access the internett but you can see the LAN


What happens when you do the following
Can you ping anything outside of your network by name or by IP or niether?
ping [www.google.com](www.google.com)
ping 64.233.169.99
nslookup [www.google.com](www.google.com)

---

