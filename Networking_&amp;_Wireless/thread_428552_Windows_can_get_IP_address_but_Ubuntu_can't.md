---
title: "Windows can get IP address but Ubuntu can't"
date: 2007-04-30
forum: Networking &amp; Wireless
---

### Post by dangling participle on 2007-04-30
Good morning everyone,

This morning I moved my machine over to a different desk, and now I'm seeing something odd happening with my machine.

-When I load my Ubuntu partition (Feisty Fawn), I am unable to obtain an IP address, and cannot access anything network related as a result.
-When I load my Windows XP partition, everything works fine, I can successfully release and renew an IP address, browse the web, hit network resources etc.

I tried running these 2 commands:
sudo ifdown eth0
sudo ifup eth0

and I am still experiencing the issue.  That is about the extent of my ubuntu troubleshooting, since it's working in windows and was at one point working in ubuntu I don't think it's hardware related, so I'm not really sure where to take this, aside from reinstalling (ugh).

Any thoughts?  I did a quick search on the forums and didn't find anything (though I may be wrong)

Thanks for your help!

---

### Post by jfinkels on 2007-04-30
Have you opened "System > Administration > Network" and enabled the connection, with a dynamic IP address? Just checking, first things first...

check out this page [http://doc.gwos.org/index.php/Main_Page](http://doc.gwos.org/index.php/Main_Page) and look at the Hardware Compatibility Guide to make sure you are supported.

You can also try doing "lspci -v" and see if your card is installed and being recognized, and try "ping -c 5 127.0.0.1" to see if it is able to ping itself!

---

### Post by eyelessfade on 2007-04-30
Sorry if its sounds stupid. But does the network card/switch light up in ubuntu? The reason I ask is it happend to me. A new windows driver shut of the network card as soon as the windows driver was not used anymore. I used quite some time to fix this. "downgrading windows driver, etc"

---

### Post by jpatton on 2007-04-30
> **dangling participle said:**
> Good morning everyone,

This morning I moved my machine over to a different desk, and now I'm seeing something odd happening with my machine.

...

and I am still experiencing the issue.  That is about the extent of my ubuntu troubleshooting, [COLOR="Yellow"]since it's working in windows and was at one point working in ubuntu [/COLOR]I don't think it's hardware related, so I'm not really sure where to take this, aside from reinstalling (ugh).

Any thoughts?  I did a quick search on the forums and didn't find anything (though I may be wrong)

Thanks for your help!

It was working prior to moving the desk in Ubuntu, not sure how all of a sudden it wouldn't work after the move. I wonder if there is a piece of the puzzle we don't have at the moment.

Was there anything else you did prior to the move?

---

### Post by dangling participle on 2007-04-30
thanks for the quick responses.

> 
Have you opened "System > Administration > Network" and enabled the connection, with a dynamic IP address? Just checking, first things first...

yep, by enabled you mean just having the checkbox beside it checked?  yes it is.  Enable roaming mode is unchecked however.

> check out this page [http://doc.gwos.org/index.php/Main_Page](http://doc.gwos.org/index.php/Main_Page) and look at the Hardware Compatibility Guide to make sure you are supported.
this was working before the weekend, before i moved my machine over to a different network drop.  the machine is a dell optiplex 745

> You can also try doing "lspci -v" and see if your card is installed and being recognized, and try "ping -c 5 127.0.0.1" to see if it is able to ping itself!

i can ping 127.0.0.1, and the ethernet controller from the output of lspci -v is the Broadcom Corporation NetXtreme BCM5745 Ethernet PCI Express (rev 02)

> But does the network card/switch light up in ubuntu?
yes it is lit up, and the network activity light is also flashing.

---

### Post by jfinkels on 2007-04-30
> **dangling participle said:**
> 
[...]this was working before the weekend, before i moved my machine over to a different network drop.  the machine is a dell optiplex 745[...]

Really? So you're saying that connected to a different port, both Ubuntu and Windows were able to get an IP address, but now, connected to the current port, only Windows can get an IP address? That sounds fishy to me. Something must have changed between the time you moved the computer and now...try removing and re-inserting the card and unplugging and replugging both ends of the cable, just for kicks. 

Would it be possible for you to plug this computer into a different data port, to see if maybe you've got a bad port or something? I really don't know here.

---

### Post by dangling participle on 2007-04-30
> **jfinkels said:**
> Really? So you're saying that connected to a different port, both Ubuntu and Windows were able to get an IP address, but now, connected to the current port, only Windows can get an IP address? That sounds fishy to me.

yes that is correct.

> **jfinkels said:**
>  Something must have changed between the time you moved the computer and now...try removing and re-inserting the card and unplugging and replugging both ends of the cable, just for kicks. 

the card is built on to the hard drive, and i didn't bring my soldering iron to work ;)

> **jfinkels said:**
> 
Would it be possible for you to plug this computer into a different data port, to see if maybe you've got a bad port or something? I really don't know here.
 

i have tried other network drops with the same result.  the windows partition works, but the ubuntu doesn't.  I've tried different network cables as well.

I also tried running the ubuntu boot CD, and I am unable to get an IP with it either, then i boot back into windows and presto, i can surf the web.
:confused:

---

### Post by jpatton on 2007-04-30
> **dangling participle said:**
> yes that is correct.



the card is built on to the hard drive, and i didn't bring my soldering iron to work ;)



i have tried other network drops with the same result.  the windows partition works, but the ubuntu doesn't.  I've tried different network cables as well.

I also tried running the ubuntu boot CD, and I am unable to get an IP with it either, then i boot back into windows and presto, i can surf the web.
:confused:

I think you mean the card is integrated onto the motherboard, is this a wireless card? Because the earlier poster was asking if you were wired into a different jack, meaning a _wired_ connection.

---

### Post by dangling participle on 2007-04-30
> **jpatton said:**
> I think you mean the card is integrated onto the motherboard, is this a wireless card? Because the earlier poster was asking if you were wired into a different jack, meaning a _wired_ connection.

my bad, case of the mondays and multitasking.  yes, the nic is part of the motherboard.  and it is a wired connection.

and to futher confirm that the nic is working on windows, i have installed synergy on my 2 windows boxes and i am now able to use 1 keyboard/mouse to control both windows boxes over the network.  i'm going to try the ubuntu boot disk on my other windows machine to see if works there.

any other ideas greatly appreciated.

---

### Post by dangling participle on 2007-04-30
here i am on the other windows machine using the ubuntu live CD.

still can't get my original machine to get an IP in ubuntu though.  any thoughts?

---

### Post by dangling participle on 2007-04-30
i am now on the broken box, in the ubuntu liveCD.  which is good news.  i'm going to reboot into my installed ubuntu and see if that works now.

---

### Post by dangling participle on 2007-04-30
no luck, the machine simply refuses to get an IP address when using the ubuntu image..

Any ideas?

doing an ifconfig i noticed "eth0", and "eth0:avah", im not sure what the second one is, but i have vmware workstation installed, could that be doing anything funky?  again all this was working before the weekend, though i'm not sure if that eth0:avah was there or not. lo, vmnet1 and vmnet8 were there before though.


thanks for your help!

---

### Post by dangling participle on 2007-04-30
ok, i clicked on Wired network Connection in my taskbar, and then clicked on "Wired Network", it went through it's cycle to get an ip, and now it's working!!!!

bizarre, wired network was already selected.  i have NO IDEA how this is working now.  I'm going to do a reboot.  if it's back up after the reboot, you probably won't hear from me ( i gotta get some work done now ), if I have any problems i'll check back later.

Thanks for your help!

---

### Post by dangling participle on 2007-04-30
hmmmm,

well when i rebooted my machine i got the same behavior, and the way to fix it was to do the same thing, to click on the "wired network" again.  I don't know why this is happening or how to get around it, it sucks to have to click that every time my machine starts.  Any ideas?

---

### Post by dangling participle on 2007-04-30
i also noticed that the eth0:avah is now missing.  not sure what that is or how it got there.

---

### Post by jpatton on 2007-04-30
The only thing I can think is that somehow your nic is not set to be enabled at boottime?

---

### Post by dangling participle on 2007-04-30
how do i check or change that?

---

### Post by jfinkels on 2007-04-30
> **dangling participle said:**
> how do i check or change that?

I think Ubuntu is supposed to save whatever settings you have enabled in the Networking Manager over sessions and retain them at each startup...I don't know why your computer is doing funky things.

btw, avahi is a local network service discovery system, you can read more about it here [http://avahi.org/](http://avahi.org/)

---

### Post by dangling participle on 2007-05-02
today everything is working fine.  i guess the computer just had a case of the tuesdays.

---

### Post by jfinkels on 2007-05-02
> **dangling participle said:**
> today everything is working fine.  i guess the computer just had a case of the tuesdays.

Sounds like somebody's got a case of the MON-days!

---

### Post by e_james on 2007-05-02
I found this thread because I was looking for help for a very similar problem. i have a laptop running ubuntu 6.06 in dual boot with XP pro. Both ubuntu and XP connect to my router at home with no protests. I did have to play around with some dns settings with both XP and ubuntu to get to this point. When I take the laptop to mates' homes which also have broadband routers, XP connects immediately but I can't seem to persuade ubuntu to connect at all. 

What I am actually looking for is some sort of "howto" which explains all the steps required to connect to a router and the internet and a home lan including any special issues which sometimes crop up. It seems that linux and Windows have slightly different viewpoints on networking. Possibly something to do with security.

I could also use some sort of simple utility which gives me "at a glance" information as to which part of the network is working and which is not. For instance I often get to the point where i can ping my ISP's dns machines but not download web pages or updates.

Any suggestions anyone?

---

### Post by Morpheus666 on 2007-05-02
Switch the NIC cables at the port and see if the problem still exists on the UBUNTU NIC, if it does not and the windows box no longer gets an IP address, switch the cables at the NIC on the systems, if the UBUNTU no longer works, its the cable, if Windows works again, its the port. I think I have that right :)

---

### Post by jodoj80 on 2007-05-02
Hi. I'm trying to get back to Ubuntu. But, this time a got a problem with my ethernet connection. I used this motherboard in my first Ubuntu test and it works fine.

After read this thread I found that I got a weird situation :confused: . Here is a description of my case:
[LIST=1]
[*]On the NETWORK SETTINGS menu the wired connection is ENABLE with DHCP too
[*]When I typed "lspci -v" in the terminal windows my ethernet controller is listed
[*]When I typed "sudo ifconfig" in the terminal windows I got the ethernet controller details.
[*]In the /etc/network/interfaces file it just have:
[INDENT]auto eth0
iface eth0 inet dhcp[/INDENT]
[/LIST]

Regards,
From DR :)

---

### Post by jodoj80 on 2007-05-13
Hello everyone,

I just want to say that I resolve my issue with the ethernet port. I don't know how but it happens after a few hardware upgrades and some cable changes (not the patch cord, because I used around 5 trying to resolve the old issue). 

Thanks, :guitar:

---

