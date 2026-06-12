---
title: "No internet with 6.10, but TCP/IP working fine"
date: 2007-02-08
forum: Networking &amp; Wireless
---

### Post by moogatu on 2007-02-08
Here's a weird one: I recently upgraded a stock install of 6.06 to 6.10, installed Synergy (very cool app), and then installed Beryl. I even did a little BitTorrenting with Azureus, so all of those things led me to believe my Internet connection was running smoothly.

Now, all of a sudden, I have no internet access - yet I have network connectivity! Synergy works just fine, and I can slave my Ubuntu box to another machine with no problem.

I can't imagine what I did, and the only thing that sticks in my mind is that at one point, I did a Ctrl-Alt-F12.  I don't know why I did it, I was probably trying to figure some key combo out.  But it blanked my screen, and after hitting ESC, the box rebooted.

I *think* that ever since then, I haven't had Internet connectivity - but, as I say, I have network connectivity.

Any ideas? I have none.

---

### Post by Paul41 on 2007-02-08
Out of curiosity can you access the internet with an IP address instead of a DNS. I have seen some people that have had that problem. You could try [http://64.233.167.99/](http://64.233.167.99/) which should take you to google.

---

### Post by moogatu on 2007-02-08
No, that doesn't seem to work, either. Weird...

---

### Post by bigken on 2007-02-08
could be your dns needs to added manually 

or it could be ipv6 in the address bar type about:config the in the filter bar type ipv6 and double click it to change the value 

dont know if this will help but anything is worth a try

---

### Post by moogatu on 2007-02-09
My default route was all messed up.  I deleted what was there, added a new route to eth0 and a gateway, and now it's all good.

---

### Post by xtrumanx on 2007-02-09
help, moogatu. what exactly did you do? i didn't quite understand what you've said you've done. where did you make changes to your default route? I'm a newbie, and this is the 2nd time i've installed ubuntu hoping to use it but fear I'll give up on using it again cause i can't get my internet connection working on it...

if anyone can help, let me explain the problem I'm experiencing in more detail.

my modem acts kinda like a router and has dhcp on it. my nic is detected by ubuntu and was assigned an ip address automatically. my connection is live and thus i was expecting to be surfing in no time. apparently not.Firefox just takes a loooong time to try to find Google then just gives up. i haven't tried it to find a website via an ip address yet. one weird thing i've found is that one of the times i was reloading the page i saw the part at the bottom of firefox that says "connecting to www.google.com" change from that to my local google address "connecting to www.google.com.my". so i'm pretty sure the internet connection is active but 1 little setting is probably messing everything up :confused: :confused: :confused: 

i really hope i can get this working. not much for me to do with ubuntu without being able to go online and download more apps. thanks in advance.

---

### Post by Paul41 on 2007-02-09
> **xtrumanx said:**
> help, moogatu. what exactly did you do? i didn't quite understand what you've said you've done. where did you make changes to your default route? I'm a newbie, and this is the 2nd time i've installed ubuntu hoping to use it but fear I'll give up on using it again cause i can't get my internet connection working on it...

if anyone can help, let me explain the problem I'm experiencing in more detail.

my modem acts kinda like a router and has dhcp on it. my nic is detected by ubuntu and was assigned an ip address automatically. my connection is live and thus i was expecting to be surfing in no time. apparently not.Firefox just takes a loooong time to try to find Google then just gives up. i haven't tried it to find a website via an ip address yet. one weird thing i've found is that one of the times i was reloading the page i saw the part at the bottom of firefox that says "connecting to www.google.com" change from that to my local google address "connecting to www.google.com.my". so i'm pretty sure the internet connection is active but 1 little setting is probably messing everything up :confused: :confused: :confused: 

i really hope i can get this working. not much for me to do with ubuntu without being able to go online and download more apps. thanks in advance.

Try to disable IPv6 and see if that helps you.  In the Firefox address bar type about:config then filter for IpV6 and disable it.

---

### Post by linuxNewb on 2007-02-09
> **moogatu said:**
> My default route was all messed up.  I deleted what was there, added a new route to eth0 and a gateway, and now it's all good.

I too would appreciate a more detailed explanation of what you did to fix this issue. I'm having the same problem. What is the 'default route' and where is it accessed/fixed? Thanks.

---

### Post by mu2012 on 2007-02-09
Same thing is happening to me.  I'm a Linux newbie.  Just installed 6.10 last night and internet worked perfectly.  Booted up this morning and can't connect with Ubuntu, but Windows is working fine, and I'm actually connected with Windows right now.  Sounds to me like I need to manually configure the 'default route' again; however, I'm not quite sure how to do this.  Any suggestions would be appreciated.  Thank you.

---

### Post by mu2012 on 2007-02-09
Very strange.  My Internet is working again, but I'm not sure why.  I simply logged back into Ubuntu and attempted to disable IPv6 in Firefox; however, it was already disabled.  I then looked around at my network setting, but didn't change anything.  After I tried Firefox again, it's now working !!!  Any suggestions ???

---

### Post by xtrumanx on 2007-02-09
> **Paul41 said:**
> Try to disable IPv6 and see if that helps you.  In the Firefox address bar type about:config then filter for IpV6 and disable it.

dude, would it be wierd if i said i loved you, lol. thanks alot, ur advice worked like a charm, posting from ubuntu currently. but i don't think its a system wide effect as whenever i go to add/remove it doesn't really update the program list. it does a check for installed application then gives a messge saying,"The list of available applications is out of date. To reload the list you need a working internet connection." also, further evidence is the fact the gaim's not working. any idea how to turn off ipv6 for everything (i'm assuming that would be the problem). thanks in advance (to whomever responds).

---

### Post by moogatu on 2007-02-09
> **xtrumanx said:**
> help, moogatu. what exactly did you do? i didn't quite understand what you've said you've done. where did you make changes to your default route? I'm a newbie, and this is the 2nd time i've installed ubuntu hoping to use it but fear I'll give up on using it again cause i can't get my internet connection working on it...

I followed this page: [http://linux-ip.net/html/basic-changing.html](http://linux-ip.net/html/basic-changing.html) and just kind of went from there.  Basically, I took the ethernet connection down (sudo ifconfig eth0 down), gave it a new IP address and brought it back up (sudo ifconfig eth0 192.168.1.16 netmask 255.255.255.0 up), and then added the gateway IP address of my router (sudo route add default gw 192.168.1.254).

After that, it worked like a charm, even after a couple of reboots.

---

### Post by xtrumanx on 2007-02-09
> **moogatu said:**
> I followed this page: [http://linux-ip.net/html/basic-changing.html](http://linux-ip.net/html/basic-changing.html) and just kind of went from there.  Basically, I took the ethernet connection down (sudo ifconfig eth0 down), gave it a new IP address and brought it back up (sudo ifconfig eth0 192.168.1.16 netmask 255.255.255.0 up), and then added the gateway IP address of my router (sudo route add default gw 192.168.1.254).

After that, it worked like a charm, even after a couple of reboots.

thanks for the explanation and link. does gaim and add/remove work for you (meaning can they connect online)? i got firefox working now (needed to disable ipv6) but the system as a whole still cant connect online for me.

---

### Post by Paul41 on 2007-02-09
> **xtrumanx said:**
> dude, would it be wierd if i said i loved you, lol. thanks alot, ur advice worked like a charm, posting from ubuntu currently. but i don't think its a system wide effect as whenever i go to add/remove it doesn't really update the program list. it does a check for installed application then gives a messge saying,"The list of available applications is out of date. To reload the list you need a working internet connection." also, further evidence is the fact the gaim's not working. any idea how to turn off ipv6 for everything (i'm assuming that would be the problem). thanks in advance (to whomever responds).

Glad I could help.  Try this for disabling it system wide. [http://doc.gwos.org/index.php/DisableIPV6](http://doc.gwos.org/index.php/DisableIPV6)

---

### Post by moogatu on 2007-02-09
> **xtrumanx said:**
> thanks for the explanation and link. does gaim and add/remove work for you (meaning can they connect online)? i got firefox working now (needed to disable ipv6) but the system as a whole still cant connect online for me.

You know, I don't know.  My weather applet updated correctly, my FireFox was working (and the Google Browser Sync plugin worked, too)... I just kind of called it a triumph and left it at that, haha.  It was late and I needed to get to bed, but I'll check these other things when I get home tonight.

---

### Post by xtrumanx on 2007-02-09
> **Paul41 said:**
> Glad I could help.  Try this for disabling it system wide. [http://doc.gwos.org/index.php/DisableIPV6](http://doc.gwos.org/index.php/DisableIPV6)

Tried it... still not working (rebooted as well btw). Perhaps not a ipv6 problem? Any other reason you can think of firefox is the only application that can go online after ipv6 is disabled?

---

### Post by epsilonaurigae on 2007-02-09
on the terminal try doing:

sudo dhclient (the network you want to connect)
example: sudo dhclient eth0

also try commenting out the other interfaces in /etc/network/interfaces except the one you want to connect with.

try disabling ipv6 on firefox
[http://en.opensuse.org/Disable_IPv6_for_Firefox](http://en.opensuse.org/Disable_IPv6_for_Firefox)

also try turning off ipv6 systemwide [http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html](http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html)
this may get reset if you install new updates, you may need to change it again.

if the other interfaces are still coming up they may be interfering with the interface you want to use, turn that off using
sudo ifconfig interface down
example: sudo ifconfig eth1 down

also, after these changes when you boot your comp make sure that the network cable is not connected, connect it only after the comp starts up completely.

at some later point even if the dhclient doesnt work, restart ur modem and router and it shud work. 

this worked for me.

EA

---

### Post by xtrumanx on 2007-02-09
I've tried everything up till now, and still the system can't connect online (besides firefox that is). here's a list of everything i've done so far:

1. Disable ipv6 on firefox's about:config
2. Disabled ipv6 from etc/modprobe.d/aliases 
    this is what it looks like now:
         # alias net-pf-10 ipv6  (original)
         alias net-pf-10 ipv6 off (i've added)
         alias net-pf-10 off (i've added)
         alias ipv6 off (i've added)
3. Commented out unused interfaces in /etc/network/interfaces

I've rebooted while cable was unplugged and still nothing. 

Side-note to epsilon: what were all the other interfaces in /etc/network/interface for? did you want me to comment all of them out? here's what it looks like now:
#auto lo
#iface lo inet loopback
auto eth0
iface eth0 inet dhcp
#auto eth1
#iface eth1 inet dhcp
#auto eth2
#iface eth2 inet dhcp
#auto ath0
#iface ath0 inet dhcp
#auto wlan0
#iface wlan0 inet dhcp
#iface dsl-provider inet ppp
#provider dsl-provider

(removed spaces in between lines for the sake of the post)

---

### Post by epsilonaurigae on 2007-02-09
that looks correct, thats what i did.

those are the network interfaces available on ur system and eth0 is the wired connection

anyway, the sudo dhclient eth0, didnt work for you?

can you paste the output here.

i am not an expert but i know how frustrating it gets and just wanted to help. and net is working great after i did what i did.

also make sure you document all the changes so you can backout anytime if there are any issues.

EA

---

### Post by xtrumanx on 2007-02-09
eth0 is my wired connection. here's the output for sudo dhclient eth0 :

"Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/ (mac address)
Sending on   LPF/eth0/ (mac address)
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.2 -- renewal in 1506 seconds."

dhcp is working fine since i'm currently online on ubuntu. what exactly does sudo dhclient eth0 do anyways?

thanks for all your help (everybody).

---

### Post by epsilonaurigae on 2007-02-09
great. nice to know its working for u as well.

you can do a man dhclient to find more or just see here [http://linuxreviews.org/man/dhclient/](http://linuxreviews.org/man/dhclient/)

EA

---

### Post by xtrumanx on 2007-02-09
> **epsilonaurigae said:**
> great. nice to know its working for u as well.

you can do a man dhclient to find more or just see here [http://linuxreviews.org/man/dhclient/](http://linuxreviews.org/man/dhclient/)

EA

oh no, i guess i didn't explain it right. dhcp is working fine, i'm online (as in surfing the web on firefox) on ubuntu but the system as a whole is still not online. i can't update the program list nor can i sign-in on gaim. Hope ur still checking this thread.

oh, i just read the title of the thread and thought i'd mention this just in case it made a difference. i'm using Ubuntu 6.06 LTS - the Dapper Drake not 6.10. I received from the mail a few days back. Ordered it off the Ship-it service on ubuntu.com

---

### Post by Paul41 on 2007-02-09
I don't know if this will work but it is worth a try.

Create a file named bad_list in /etc/modprobe.d containing just this one line:

alias net-pf-10 off

---

### Post by epsilonaurigae on 2007-02-09
ok, got you. so you are not able to download and install any updates or login to gaim.

are you doing the update using the gui or terminal?
if using the terminal, can you paste the output here that will give me some idea.
sudo aptitude update

i am not sure abt gaim, let me try login with gaim and check if i have the same issues.

EA

---

### Post by xtrumanx on 2007-02-09
ok, man, i haven't felt like this much of an idiot in a looong time. Apparently, I was crying about not having a system wide internet connection and as proof of such i presented:

Exhibit A: GAIM's was not working 
Exhibit B: Add/Remove was not reloading

Well then i wondered what would happen if I were to try to press one of those check marks and try to download one of those programs anyways............. and it worked. Gaim still isn't working but that's probably I'm not using it properly (first time using it anyways). One thing though, i did deactivate and reactivate my interface before trying this and I have a feeling that *may* have had something to do with it but can't be sure now anyways.

May appreciation to Moogatu, Paul41, epsilonaurigae and everybody else on this thread. I really now am understanding what the whole community deal is all about in Ubuntu.

---

### Post by moogatu on 2007-02-09
So, how's this for dumb? My problems were caused by... ME!

Here's the skinny: my home network goes cable modem -> wireless router (network printer, all wireless connections, file server off of this) -> router used as a hub/switch (feeds a WinXP box and my problem-prone Ubuntu box).

I forgot to turn DHCP off on the non-wireless router, so it was trying to hand out IP addresses at the same time as the wireless router.  DUUUUUUUUUUH.  I logged into the non-wireless router, turned off DHCP, and ALL my issues went away.

Just thought I'd share that with you all.  So, even though I did add a gateway to my route, thus defeating DHCP services for a while, I didn't *need* to do that.

/smacks head

---

### Post by bradford72 on 2007-02-11
> **xtrumanx said:**
> help, moogatu. what exactly did you do? i didn't quite understand what you've said you've done. where did you make changes to your default route? I'm a newbie, and this is the 2nd time i've installed ubuntu hoping to use it but fear I'll give up on using it again cause i can't get my internet connection working on it...

if anyone can help, let me explain the problem I'm experiencing in more detail.

my modem acts kinda like a router and has dhcp on it. my nic is detected by ubuntu and was assigned an ip address automatically. my connection is live and thus i was expecting to be surfing in no time. apparently not.Firefox just takes a loooong time to try to find Google then just gives up. i haven't tried it to find a website via an ip address yet. one weird thing i've found is that one of the times i was reloading the page i saw the part at the bottom of firefox that says "connecting to www.google.com" change from that to my local google address "connecting to www.google.com.my". so i'm pretty sure the internet connection is active but 1 little setting is probably messing everything up :confused: :confused: :confused: 

i really hope i can get this working. not much for me to do with ubuntu without being able to go online and download more apps. thanks in advance.

here's something to try...I did a couple of different things, but then was steered right by this little instruction.  First open a terminal and put in ```
                                                      sudo gedit /etc/modprobe.d/aliases 
```then go down a few lines until you find a line that says >  alias net-pf-10 ipv6 change that line to read >  alias net-pf-10 off remember to save the file, then re-boot your machine...see if that works...I got another one (the about:config method...but technically that's not the way to do things)  the method I described should work for you though

---

