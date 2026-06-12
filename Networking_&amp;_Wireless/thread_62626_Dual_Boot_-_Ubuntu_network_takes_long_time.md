---
title: "Dual Boot - Ubuntu network takes long time"
date: 2005-09-05
forum: Networking &amp; Wireless
---

### Post by floppy on 2005-09-05
I'm dual booting Ubuntu and Windows XP. Each time XP closes it's doing "something" to the network interface that causes Ubuntu to take a long time (about 30 seconds) during the bootup network configuration. That attempt appears to fail because I get an error message about a Temporary Failure in the networking. After the boot I have to deactivate eth0 and then reactivate it for networking to function.

Any clues about how to proceed on this one?

---

### Post by tehwa on 2005-09-05
Stop using XP :razz:

---

### Post by floppy on 2005-09-05
I know you meant that in a carefree, humorous manner, but now fewer people will bother to read this thread, thinking it's being answered.

As far as why I need XP, see:
[http://www.ubuntuforums.org/showpost.php?p=334534&postcount=35](http://www.ubuntuforums.org/showpost.php?p=334534&postcount=35)

Any real help would be deeply appreciated.

---

### Post by sanneman on 2005-09-07
Hi Floppy

[QUOTE=floppy]I'm dual booting Ubuntu and Windows XP. Each time XP closes it's doing "something" to the network interface that causes Ubuntu to take a long time (about 30 seconds) during the bootup network configuration. That attempt appears to fail because I get an error message about a Temporary Failure in the networking. After the boot I have to deactivate eth0 and then reactivate it for networking to function.

Any clues about how to proceed on this one?[/QUOTE]

I actually have the same situation. Dual boot, XP is working, but can't connect to the network since I have removed a router. I get the error message 'temporary failure, can't resolve name'. I suspect he can't find the right DNS or something, but I'm not sure. Any help is appreciated. If I find the solution, I'll post it here, hope you do the same.

greetz,
Sanne

---

### Post by floppy on 2005-09-07
Hi Sanne,

If I find one, I will. I'm still looking at various clues. It's interesting to see that your router is disconnected. Mine is not, by the way.
A friend has theorized that the problem could be a module failing to load in time for the network requests to be seen. I only mention it in passing as one more avenue being explored.

I wish us both luck!

---

### Post by GreyFox503 on 2005-09-07
Are you sure it has something to do with XP?  If you are using Ubuntu (and your networking is correct) and you reboot, does it do the same thing anyway?

---

### Post by mlomker on 2005-09-07
Is your lengthy delay with the ethernet plugged in or unplugged?  There is along delay during boot while the system tries to set the time to an NTP server on the Internet...which won't be there if there's no network connection.  I get that problem on my laptop a fair bit because the wireless card isn't started that early in the boot process.

You could try looking at /etc/network/interfaces.  If you want the network card to simply be down and then you'll manually turn it on...remove any references to 'auto eth0' or 'map eth0' (under hotplug).

---

### Post by Heavenly Evil on 2005-09-08
[QUOTE=sanneman]Hi Floppy



I actually have the same situation. Dual boot, XP is working, but can't connect to the network since I have removed a router. I get the error message 'temporary failure, can't resolve name'. I suspect he can't find the right DNS or something, but I'm not sure. Any help is appreciated. If I find the solution, I'll post it here, hope you do the same.

greetz,
Sanne[/QUOTE]
 My networking in Ubuntu works perfectly fine, but when I try to connect in XP it takes quite a while to acquire a network address. I can still access the internet while it's searching, but have problems with the network (ie. transferring files between computers). It's strange that I can reach the internet through the router but not the other computers. Once the network address has been found (after 15 mins or so), everything works fine.

---

### Post by eraclito on 2005-09-08
[QUOTE=Heavenly Evil]My networking in Ubuntu works perfectly fine, but when I try to connect in XP it takes quite a while to acquire a network address. I can still access the internet while it's searching, but have problems with the network (ie. transferring files between computers). It's strange that I can reach the internet through the router but not the other computers. Once the network address has been found (after 15 mins or so), everything works fine.[/QUOTE]


in my laptop  (ubuntu  and no xp  \\:D/ )  "starting network interface" takes a long time (30 seconds too)  when I'm not at home and I cannot find my wi-fi router.

at home (whit router on) it is fast.

i think that ununtu tryes to connect to the router for a default time.

I'd like to chanmge that time, but i do not know how

any idea?


eraclito

---

### Post by floppy on 2005-09-08
[QUOTE=GreyFox503]Are you sure it has something to do with XP?  If you are using Ubuntu (and your networking is correct) and you reboot, does it do the same thing anyway?[/QUOTE]

Yes, I'm sure. Rebooting from Ubuntu to Ubuntu again works ok. I'm assuming, probably wrongly :), that XP is doing something to the interface as it shuts down.

---

### Post by floppy on 2005-09-08
[QUOTE=mlomker]Is your lengthy delay with the ethernet plugged in or unplugged?  ...  If you want the network card to simply be down and then you'll manually turn it on...remove any references to 'auto eth0' or 'map eth0' (under hotplug).[/QUOTE]

It's plugged in to my router (hardwired). I really, really do NOT want to have to manually fiddle with it whenever I reboot. My wife uses that machine sometimes.

---

### Post by GreyFox503 on 2005-09-08
The fact that the problem only happens after you shut down from XP is really weird...

The only other thing I can think of is finding out if there is a difference between *rebooting* from XP and doing a cold shutdown and powerup.  That would be a sure way to clear the memory.

Or you could just push the big power button in XP instead of going to Start > Shut Down :)

---

### Post by floppy on 2005-09-11
I'm going to drop this issue. I'm tied up with other stuff at the moment. When Breezy's released I'll try reinstalling. Maybe the network issues will have cleared up.

Thanks for the help, folks.

---

### Post by boosted_sled on 2006-05-08
Anyone figure this out yet? I'm having nearly the same problem, but in my case boot time isn't slowed but it looks like the network driver doesn't load.  If I shut down my machine and pull the power cable for 5 sec I can get linux to see the network again, but I haven't found any other fix yet.

---

