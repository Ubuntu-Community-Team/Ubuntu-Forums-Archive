---
title: "Setting a static IP in 8.10 - how?"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by mightyoakbob2 on 2009-01-08
Hi,

This should be obvious but I've been trying for 2 days to do this simple task of setting a static IP address on 8.10. I can do it, it works fine for a short time and then for some reason the machine decides it no longer wishes to play ball and goes back to the original settings of DHCP.

I tried creating altering 'Auto Eth0' and tried creating a new profile 'Static Eth0' both work for a few minutes and then the machines switches back.

The instructions for networking don't match with what I'm seeing in 8.10 and anyway shouldn't this be trivially easy.

Before I throw this box through the window will someone tell me how in heavens name you stop the machine reverting to DHCP.


Cheers,

Bob.

---

### Post by tombott on 2009-01-08
I seem to remember this was a bug with NetworkManager when 8.10 was released.
I am able to set a static IP on my 8.10 install, and the static IP sticks even after reboot.
Are you fully up to date with 8.10

Maybe worth running
```

sudo apt-get update
```

From the terminal and installing any updates.

---

### Post by norbsoft on 2009-01-08
Try:

[http://www.ubuntugeek.com/how-to-set-a-static-ip-address-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-set-a-static-ip-address-in-ubuntu-810-intrepid-ibex.html)

---

### Post by tombott on 2009-01-08
> **norbsoft said:**
> Try:

[http://www.ubuntugeek.com/how-to-set-a-static-ip-address-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-set-a-static-ip-address-in-ubuntu-810-intrepid-ibex.html)

I'd only use that as a last resort, as I already said I have Static IP working fine in my Ubuntu 8.10 install.

Check your system is up to date first.

---

### Post by tombott on 2009-01-08
More info on the problem here:

[http://ubuntuforums.org/showthread.php?t=974382](http://ubuntuforums.org/showthread.php?t=974382)

You DO NOT need to remove NetworkManager as per the other link.

---

### Post by hyper_ch on 2009-01-08
I'd use WICD as network manager. I was never happy with the default ones and did manually edit the interfaces file before I discovered WICD.

---

### Post by lazyart on 2009-01-08
I think the key to it was clearing the block that says "System Setting".

I personally go so fed up with this that I just set a reservation on my DHCP server tied to my NIC's MAC address.  Occasionally I get two entries in Network Manager but the ip address is always right.

---

### Post by MrWES on 2009-01-08
If you're behind a router, you can set a static IP from there. I did that for my three household computers via the router.

Bill

---

### Post by mightyoakbob2 on 2009-01-08
Hi,

I've got everything up to date as suggested (128 updates) but is has made no difference I still can't keep a static IP address for more than a few minutes. For such a simple and normal function I can't say I'm too impressed really. Looks like going back to Windows and coming back in another couple of years. Is this all linux distros or just Ubuntu?

Thanks for your help.

Bob.

---

### Post by lazyart on 2009-01-08
This only became an issue with Intrepid for me.  Jaunty will be out in April.  Should be resolved by then.

---

### Post by mikewhatever on 2009-01-08
> **mightyoakbob2 said:**
> Hi,

I've got everything up to date as suggested (128 updates) but is has made no difference I still can't keep a static IP address for more than a few minutes. For such a simple and normal function I can't say I'm too impressed really. Looks like going back to Windows and coming back in another couple of years. Is this all linux distros or just Ubuntu?

Thanks for your help.

Bob.


Static IP with the network manager worked flawlessly for me. Can you post a screenshot of your settings.


> **lazyart said:**
> This only became an issue with Intrepid for me.  Jaunty will be out in April.  Should be resolved by then.

On what grounds can you vouch?

---

### Post by mikewhatever on 2009-01-08
Static IP with NM works flawlessly for me on Intrepid. Can you post a screenshot of your settings.

---

### Post by Iowan on 2009-01-08
[Here]("http://ubuntuforums.org/showthread.php?t=974382") is a workaround for the static address bug in NM.  Yes, removing NM is one of the mentioned "solutions", but there are others as well.

---

### Post by hyper_ch on 2009-01-09
> **mightyoakbob2 said:**
> For such a simple and normal function I can't say I'm too impressed really. Looks like going back to Windows

Wow... with that kind of attitude I wouldn't recommend as there are so many "simple and normal functions" that do not always exactly behave like in windows...

---

### Post by handydan918 on 2009-01-09
> **mightyoakbob2 said:**
>  Looks like going back to Windows and coming back in another couple of years. Is this all linux distros or just Ubuntu?

Bob.
Nah, if Ubu pi55e5 you off, then try another distro. 
Personally, most of my gripes with Ubu are about 
Gnome. I like kde better.
Try a good kde distro. Mint, Mepis, Debian testing...

---

### Post by mightyoakbob2 on 2009-01-09
> **hyper_ch said:**
> Wow... with that kind of attitude I wouldn't recommend as there are so many "simple and normal functions" that do not always exactly behave like in windows...

Its not that I expect it to behave or look like windows at all. What I did expect was:

a) That the documentation for 8.10 to actually match 8.10, it didn't.

b) Basic functions like static IP actually work, it doesn't.

As a complete newbie, meeting issues like this day 1 does not inspire confidence at all.

Thanks again.

Bob.

---

### Post by blazemore on 2009-01-09
You could try disabling the DHCP service entirely.

---

### Post by hyper_ch on 2009-01-09
static IP works... just not the way you tried and there are countless ways to achieve it ;) yet your command about going back to windows just because of that... is... hmmm... you know...

---

### Post by wizard10000 on 2009-01-09
> **mightyoakbob2 said:**
> As a complete newbie, meeting issues like this day 1 does not inspire confidence at all.

Agreed, Bob - but it's a coincidence.  I use a static IP on Intrepid and when I couldn't get any joy out of network manager I just manually configured /etc/network/interfaces like this -

auto eth0
iface eth0 inet static
address 192.168.1.101
network 192.168.1.0
netmask 255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.1

Don't mess with the loopback section in there - no need.

I've been doing this for awhile and manage desktop support for a 3,000 user federal agency - and in my shop all static IP addresses have to be reserved on the DHCP server, not set on the workstation.  The reason for this is that hardcoding an IP address on a workstation creates a nonstandard configuration and I try not to have any more of those than I absolutely have to.

Unfoirtunately my cheapo wireless access point doesn't support MAC reservations so I have to do it on the workstations at home  :(

But - you did trip across something that didn't work right.  It happens.

---

### Post by mikewhatever on 2009-01-09
> **hyper_ch said:**
> static IP works... just not the way you tried and there are countless ways to achieve it ;) yet your command about going back to windows just because of that... is... hmmm... you know...

+1. Threatening to go back to Windows does not inspire help support here.

---

### Post by mightyoakbob2 on 2009-01-09
> **wizard10000 said:**
> Agreed, Bob - but it's a coincidence.  I use a static IP on Intrepid and when I couldn't get any joy out of network manager I just manually configured /etc/network/interfaces like this -

auto eth0
iface eth0 inet static
address 192.168.1.101
network 192.168.1.0
netmask 255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.1



I've just looked in that file and cureently it has just the following:
auto lo
iface lo inet loopback

Are you saying I should replace the first line with the above lines (obviously with my settings)?

Cheers,

Bob.

---

### Post by mightyoakbob2 on 2009-01-09
> **mikewhatever said:**
> +1. Threatening to go back to Windows does not inspire help support here.

No, I'm sure it doesn't. I wasn't really a threat, more a statement of intent at that time. I think it most unlikely that I will be able to set this machine up to do the couple of jobs I want it to do. I just can't see me getting there.

I keep trying to go linux, I like the idea of it and I'm no Microsoft fan but, and its a big BUT Linux is hard, very hard. At least I find it very hard. Most things that I find takes seconds on a PC take hours or days on Linux and inevitably you always end up on the command line like computers 20 years ago. Add to that bugs and documents that don't match the software and its getting past a joke.

I would like to provide a password protected samba share next. Heaven help me.

---

### Post by hyper_ch on 2009-01-09
> **mightyoakbob2 said:**
>  more a statement of intent at that time.

Which is a threat...

---

### Post by mightyoakbob2 on 2009-01-09
> **wizard10000 said:**
> I just manually configured /etc/network/interfaces like this -

auto eth0
iface eth0 inet static
address 192.168.1.101
network 192.168.1.0
netmask 255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.1

Don't mess with the loopback section in there - no need.


I have eventually managed that and at the moment it is looking good, I think this may have fixed it. Thanks and well done.

Cheers,

Bob.

---

### Post by wizard10000 on 2009-01-09
> **mightyoakbob2 said:**
> I've just looked in that file and cureently it has just the following:
auto lo
iface lo inet loopback

Are you saying I should replace the first line with the above lines (obviously with my settings)?

You figured it out but for the rest of our studio audience those two lines are for the loopback adapter I suggested we not mess with - sorry for not being more clear.

The Ethernet configuration should go under those two lines.

Glad you got it working  :)

---

### Post by blazemore on 2009-01-09
Now this issue is settled, I'd like to point something out that I have noticed.
A lot of users who have migrated from Windows get quite agitated when things don't work exactly how they want.
They come on here and rant and rave, and "threaten" to go back to Windows (suits me fine, why would I care?).
The issue is that they think they are entitled to support.
This is true when you are dealing with a company: You have payed the company an arbitrarily set sum of money, and the company owes you support.
Not so with Free software (unless you purchase commercial support).
Nobody is "entitled" to community support, and the best thing to do is to work *with* the people who are, simply out of the kindness of their hearts, trying their best to help you with your problem.

---

### Post by lazyart on 2009-01-09
At least with Linux you are entitled to a refund.

Yes, all support here is volunteered.

---

### Post by mightyoakbob2 on 2009-01-09
> **blazemore said:**
> Now this issue is settled, I'd like to point something out that I have noticed.
A lot of users who have migrated from Windows get quite agitated when things don't work exactly how they want.

Or at all.

> **blazemore said:**
> They come on here and rant and rave,

A rant and rave? I thought I was pretty succinct and to the point.

> **blazemore said:**
>  and "threaten" to go back to Windows 


Threaten in the sense of 'I'm going up the pub tonight' yes. Threaten in the sense of coercion, I don't think so. 

> **blazemore said:**
> (suits me fine, why would I care?).

Exactly, not much of a coercion threat then is it.

> **blazemore said:**
> 
The issue is that they think they are entitled to support.


No I don't actually. I presume you mean me.
> **blazemore said:**
> 

simply out of the kindness of their hearts, trying their best to help you with your problem.

I would mark the thread as solved but I can't work out how and yes I have looked.

Thanks to everyone who gave their time to help me.

Bob.

---

### Post by handydan918 on 2009-01-09
> **mightyoakbob2 said:**
> 
I would mark the thread as solved but I can't work out how and yes I have looked.

Thanks to everyone who gave their time to help me.

Bob.

Go back to your OP and click "edit", then "go advanced". That should display a pulldown menu toward the top that will do the job.

---

### Post by AgTeq01 on 2009-01-09
mightyoakbob - did you get this sorted?

---

