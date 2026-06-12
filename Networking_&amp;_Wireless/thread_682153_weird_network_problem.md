---
title: "weird network problem"
date: 2008-01-29
forum: Networking &amp; Wireless
---

### Post by richardy on 2008-01-29
Hi,
I have been running xubuntu fiesty on a desktop for about six months now with no real issues untill just recently. The network (ethernet had been running fine), then i decide to dual boot windows and Xubuntu gutsy on my laptop. The installation went OK except that i found that the ethernet didnt work. After a lot trials and errors i finally got the ethernet to work and thus a connection to the internet but when i swapped back to my fiesty installation on the desktop the ethernet was ok but i had no internet connection. After a while (including a couple of reboots) the internet connection magicly repeared - the same thing would then happen with the internet connection in Gutsy on teh laptop. Then just recently i powered up the desktop with fiesty and no internet connection was avialable and this continued thru a coulpe of reboots and checking of the ethernet configuration (all OK) so i checked the connection to the ISP by using wimdows on the laptop and there were no problems.  So at this point i'm getting rather confused and somewhat frustrated. At this point i decided to check Ubuntu fiesty which i have dual booted with Xubuntu fiesty on the desktop and everything was fine (so now i'm starting to get really anoyed). I reboot into Xubuntu fiesty and magically the internet conection has reapeared??????? Does this have anything to do with continually changing connections from computer/laptop to modem? It shouldnt do since it is just unplugging from computer to another and this pluging and unplugging doesnt seem to affect windows. 

If anybody has any ideas on what has been going on please please let me know.

Cheers.

---

### Post by Yhetti on 2008-01-30
It can.  Am I assuming correctly that you have either the desktop or the laptop directly plugged in to the modem; as in, you only have one plugged in at a time?

Depending on the model of the modem, it's going to have a MAC address time-out built in.  On well-behaved setups, this shold be 10-30 seconds.  What that means is that it associates an IP address to a MAC address internally, for time X.  Then, mostly likely your cable/dsl modem is set by the provider to only allow one MAC address to access the internet at the time.  If it's configured poorly, say with a 2 minute time-out, lets simulate.

Boot Linux on PC -> Modem now has "PC MAC".  Internet Works.  2 Minute countdown starts now.
You immidiately unplug your PC and plug in the Laptop running Linux.  It gets an IP address from the modem, but it won't access the internet.  You try for about a minute or two and get frustrated.  Reboot to Windows
Laptop boots into Windows.  While it's booting, the 2 minute countdown ends and the modem erases the MAC block.  Windows gets an IP address and your internet works.  Modem relearns the "Internet OK MAC" as the address of the notebook.
You reboot into Linux on the notebook and it works fine.  A few hours later when you're done with the notebook, you shut it down.  2 Minute timer starts from the last packet the modem sees (roughly).

1.5 minutes later LInux on the PC isn't working, so you reboot into Windows...

Does that sound plausible?

---

### Post by richardy on 2008-02-07
Hi, and thanks for replying. Sorry for not geting back to you sooner.
Yes it does sound sort of similar to the problems i am having except that i sometimes leave teh computer on for a while after i boot xubuntu gutsy on laptop for the first time, and realise that  the internet is not conected, however no matter how long a i leave it i still dont seem to get a conection whereas if i boot into windows first i never have any problems. The other thing is that some times it will work correctly (ie boot up and connection is fine) which makes it even more annoying. At the moment, the best method of quarenteeing a working internet connection afer i boot up is to boot into windows first, check internet connection then reboot into Xubuntu. This aproach seems to work but i shouldnt have to do this. Yes i think you are right in that some of the symptoms are explained by your scenario but doesnt fully explain all the problems.

Any further ideas?

Cheers.

---

