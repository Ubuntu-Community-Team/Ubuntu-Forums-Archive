---
title: "XP Box can ping Ubuntu, but not the other way"
date: 2007-07-28
forum: Networking &amp; Wireless
---

### Post by ZootNerper on 2007-07-28
I have Ubuntu Fiesty on one box and XP on another connected via a wired LAN which includes a switch and a router.

I've been battling to get them to talk. This morning I got Ubuntu to see and read files on the XP, but not the other way round.

I had initially had set the Domain name on Ubuntu to MSHome and later changed it to WORKGROUP as on the XP box. I installed some additions that allowed me to see Windows files and everything was OK from the Ubuntu end.

But XP did not see Ubuntu under WORKGROUP but MSHome. I re-booted both machines and the router. Same.

I noticed in on Ubuntu in hosts I still had something like "127.0.0.1 MSHome"  (I don't know why 127... as my network uses 192.168.1.x). I deleted it and then everything went downhill. I rebooted, no better. There were some other hosts in there with strange unix-like names. I got rid of them too. (Sorry, not clever).

I took the LAN card out, booted up. Put the LAN card back and booted but no unix-like host names re-appeared (I hoped they were "defaults"). I can't find anything that tells me what these unix like names may be.

Anyway, now, my Ubuntu box cannot ping XP unless I get XP to ping Ubuntu first, which XP does successfully. After the first ping from the XP, Ubuntu can start pinging the XP. If I stop the Ubuntu pinging within a minute or two maybe less I cannot again ping XP.

Ubuntu can still ping the router and access the Internet.

I guess my problem lies in not having the host "defaults" and then getting rid of any last vistage of "MSHome"

Any ideas. I'm totally new to Linux and Ubuntu and have been mostly running it as an experiment to see how it goes. The Ubuntu machine has been on 24/7 running World Community Grid software, but little else as I evaluate it's reliability. Impressed so far.

Thanks in advance.

Zoot

---

### Post by jakev383 on 2007-07-28
127.0.0.1 is a local loop back.  It points back to your machine, and always will (even on Windows machines).
Here's what my /etc/hosts file looks like:
127.0.0.1       localhost
127.0.1.1       jake-lapbox

jake-lapbox is the name of my laptop.  You at least need the first line there, or a LOT of things won't work.

---

### Post by ZootNerper on 2007-07-28
Thanks,

I set up the numbers the same as your two rows and now I can ping from my Ubuntu box to the XP box no problems. The 127.0.1.1 I set to the name of my Ubuntu box "********3" (sorry) I guess 127.x.x.x is a loopback address. I rebooted Ubuntu, XP
 and the router and now the Ubuntu reports 127.0.1.1 as "********3.WORKGROUP".

But I cannot still see the files on XP.

On XP I have re-defined the folders I want to share. I did this on Ubuntu too, going System-Administration->Shared Folders. In the "General Properties" I found a reference to MSHome in the Domain/Workgroup entry. I changed this to WORKGROUP. The properties for both shared folders show "share through" to be "Windows Networks (SMB)"

I rebooted Ubuntu.

If I open Places->Network I get one line "Windows Network". If I open it I get a blank page.

Any further ideas?

---

### Post by pongfmm on 2007-09-04
same problem here....  please help, i'm a newbie linux ( ubuntu ) user ...  my linux box ip configuration is 192.168.0.3 and my xp box is 192.168.0.2,  from my xp box i can ping my linux box but not the other way around... i am using a crossover cable...

---

### Post by daveisadork on 2007-09-04
IIRC, the XP firewall will refuse pings by default. You might try disabling it for a while to see if that's your problem.

---

### Post by pongfmm on 2007-09-04
> **daveisadork said:**
> IIRC, the XP firewall will refuse pings by default. You might try disabling it for a while to see if that's your problem.

sir daveisadork, my xp box firewall is already disabled, i will try a second look at it... thnx sir...  i'll keep you posted...

---

### Post by pongfmm on 2007-09-11
problem solved, its the firewall of my xp box that refuses the ping...thanks...

---

### Post by TNakos on 2007-09-11
Maybe your XP box has firewalls? I noticed that windows doesn't like being seen by even other windows box's. Vista sucks. Same with XP. Thats why Im all ubuntu

---

