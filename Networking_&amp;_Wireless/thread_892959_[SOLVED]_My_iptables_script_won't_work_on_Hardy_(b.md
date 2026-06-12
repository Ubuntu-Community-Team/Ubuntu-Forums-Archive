---
title: "[SOLVED] My iptables script won't work on Hardy (but did in Gutsy)"
date: 2008-08-17
forum: Networking &amp; Wireless
---

### Post by Dan_Dranath999 on 2008-08-17
I used script to open the ports for aMule, Azureus and aMSN, on Gutsy. It worked just fine.

I upgrade to Hardy last week (fresh install, but kept my home folder in a separate partition)...

And now, using the exact same script, I can't make all those apps to "see" the open ports!  

--when i do
```
sudo iptables -L
```

My port configuration seems like it should be, so the script IS LOADING, but the rest of my programs don't.

---

### Post by caljohnsmith on 2008-08-17
Just wondering, but why do you need to open ports for those programs with iptables? When I run amule for example, it automatically opens up the TCP port it needs, and I can confirm that with:
```
sudo netstat -tupan | grep "LISTEN"
```
The only thing I have to do is of course port forwarding with my router, and amule works perfectly. So just wondering why you need to use iptables?

---

### Post by Dan_Dranath999 on 2008-08-18
well, just followed Azureus site instructions: Needed to open a port for Azureus, so i copied their script, and added to the startup sequence (following their instructions, dunno what the hell those commands do)

Then, i needed to do the same for aMule.
aMSN wanted some ports too..
And i needed to block certain address.. so y just added some rules in a script i had already running at startup...

(anyway, i don't know how to delete that script from startup -i assume that if someday i need to delete those iptables rules, i just go to the script and add #comment to every line-)

BUT ANYWAY, I FOUND THE SOLUTION:  Turns out, that by [COLOR="Red"][SIZE="3"]installing Hardy, my connection settings were re-set as DYNAMIC IP[/SIZE][/COLOR] (my IP was other than the one the ports in my router settings were looking for), so i turned them to static, and gave it the same ip it was on the router, and there you go! Everything is working fine now!

---

