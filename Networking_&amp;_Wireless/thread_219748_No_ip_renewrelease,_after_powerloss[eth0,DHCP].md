---
title: "No ip renew/release, after powerloss[eth0,DHCP]"
date: 2006-07-20
forum: Networking &amp; Wireless
---

### Post by stanz on 2006-07-20
Hi All..
After having a power loss, last week...I had a hard time figuring out how to get a new ip addy assigned.
The DSL modem naturally assigned a _new ip address_, after the power came on, but,
I've found no **'reset',** **'release',** or **'renew'** option- in 'Networking' or 'Networking Tools'. I was 'Disconnected'. :mad:
When I lost power again, the search went on, but found no solution.
Restarting pc- atime or three, don't do it...or removing the jack- from nic card...restarting again...nadda.
I remove my isp's DNS #, from networking. And pull power again.
After all that- it comes back- but...that ain't the fix.
So...I'm here, asking...cause I found no help @ the wiki either.  ](*,)
As Always..Thanks...

---

### Post by murph2481 on 2006-07-20
Go to the terminal and run:

sudo dhclient

That should do it

---

### Post by stanz on 2006-07-20
Hey murph...Thanks for your advise...
sorry ~ I forgot to mention I found that, and it didn't work.
This is copied, but simular to what i got when not connected...
```
 DHCPDISCOVER on eth0 to 255.bla.bla.bla port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
Internet Systems Consortium DHCP Client V3.0.3
``` I went searching for something, that might 'teach', a trouble shooting fix- but
the topics head off in different directions.
Tho this don't appear to be a common problem among users,
I just might cut power to the modem again...to simulate & attempt affix?
Get something in the wiki...?:-k

---

### Post by murph2481 on 2006-07-20
That message would mean that your router or service is not releasing an IP address to you.  It could also mean that ubuntu doesn't like your ethernet connection on your computer.  Can you plug into a router or something and see if you can get an IP address?

---

### Post by stanz on 2006-07-20
No router here...
Right now, I got an ip addy from 'network tools', None @ that time.
Geez...When I first got service here[or elsewhere], All workes like a snap!
No problems grabbing the new addy...but, then- pc gets unplugged. ;)
It's at a '*change ~ or newly assigned ip addy*'...& power loss, 
cause I turn nothing off here.
[I] ---Still searching for info, I'm checking out, 'Network Manager'.---  :???:
Well thats not fun!...[/I]
I guess its the same as network tools, and nothing new towards...
"Renew/Release".  ](*,)

---

### Post by stanz on 2006-07-27
So...this must be a rare problem? I've searched Launchpad, the wiki... I donno.
Is it like ~ a matter of 'dislike'? or am I missing a commandline fix, or :confused:.
==========================
I've been checking out the- # [FONT=Courier New]dhclient-script, [FONT=Verdana]and see there's accounts of:[/FONT]
    [/FONT]> BOUND|RENEW|REBIND|REBOOT)
    EXPIRE|FAIL|RELEASE|STOP)[FONT=Courier New]
[FONT=Verdana]also:[/FONT]
[/FONT]> # IP address changed. Bringing down the interface will delete all routes,
            # and clear the ARP cache. I know I don't have a clue, to all this- but it sounds like it's set to do the renew/release thing..?
:-&
==========================
* * * * * * * * * * *
Update: I've looked into bugs: [https://launchpad.net/distros/ubuntu/+source/gnome-network/+bug/33447](https://launchpad.net/distros/ubuntu/+source/gnome-network/+bug/33447)
And Filed This: [http://bugzilla.gnome.org/show_bug.cgi?id=349331](http://bugzilla.gnome.org/show_bug.cgi?id=349331)

Also...I've managed to fiddle & create a 'window' [?] with the options I
believe will solve this problem!
Let me know what `cha think!

---

### Post by stanz on 2006-08-12
No joy...
I did a freash install this week, and just get back from another power loss!
Again..nothing got me connected to the net - untill I powered down & pulled power plug, for afew minutes...then it good.
Try it folks! Power off your working dsl modem & pc.
dsl modem is back on with power - pc is set, 'not to power up when power returns'.
Turn pc on- 'give it a minute'.
Can you surf? Get a stream? Chat?  I think not!
Anyway...nuff rambling to myself....

---

### Post by stanz on 2006-09-30
and another month...another powerloss...same ol`--same ol`..

---

### Post by tnthomas17 on 2007-01-26
You're not the only one getting this issue, everytime I wander from one wireless area to another, I run into the same problem, unable to release my IP and get a new one... any help anyone has found, please, I'm on a latitude 120L Laptop with all stock hardware.

God Bless

#-o

---

### Post by tech_cheetah on 2008-07-18
I am also facing the same problem in Hardy Heron.
Why have they not fixed this problem. Also there is no help from ubuntu forums :(

---

### Post by tuga on 2008-07-18
Hi,

I think that I have a similar issue. After power up the PC, the internet is not available.
The internet is available after:
sudo ifup eth0
ipmasq

How can I have internet after power up?

Thanks

---

### Post by stanz on 2008-07-21
Hi all...
Wow ~ this is still happening?!
I noticed some small change with the network gui, "enable roaming mode"
or something to that effect.
Maybe a new thread in the 'networking' section, is needed.
A link to this thread may jump start things?

Well, check with 'bugs', maybe add your own.
Anything in the wiki yet?

---

