---
title: "Virus Warning from ISP"
date: 2007-03-02
forum: Networking &amp; Wireless
---

### Post by punx45 on 2007-03-02
Yesterday I got an email from my ISP saying that my computer was involved in "attempted virus propagation."

My entire LAN consists of *nix computers, and there are no lusers that use any of them.   So I'm thinking that there aren't any actual active viruses on any of my computers.   But still, something triggered their warning.

Is this a typical event for someone running public services?   I have HTTP and SSH open to one machine on the LAN.   Is it possible that some rogue robots were mucking about with the HTTP server?   Anyone else ever have similar issues?

---
Or maybe i just got burned for being lazy and leaving my wireless open 	](*,)

---

### Post by milton1 on 2007-03-02
more than likely somebody spoofed your email address as the source of their attack. Someone who has you in their address book probably got a virus.

Edit: They could have spoofed your ip as well, depending on the type of attack.

---

### Post by chili555 on 2007-03-02
> maybe i just got burned for being lazy and leaving my wireless open

Entirely possible, IMO, for someone to see your open network at 3:15am from their laptop and connect and launch a virus or download kiddie porn or, worst of all, bit torrent! HELP! The RIAA is coming to *your* door with their lawyers to seize *your* computer because of what Hairy Hacker did while you were blissfully asleep.

WEP and MAC filtering are easy to set up. WPA, a little less so. Please post back when you can confirm you are no longer open. :)

---

### Post by punx45 on 2007-03-02
yeah, the open router in question also died within the last couple days ( hmm.. :-k ) so while replacing it, I took the time to re-enable WEP/WPA :)   

I was thinking the more likely than a 3AM driveby would be that my neighbor may have connected to it accidentally instead of his own (i can hop onto their wireless from where my stuff is)  definately some hardcore noobage and viri potential over there. 

also, third option could be that the ISP is wrong, since my IP is dynamic, could be finger pointing similar to the John Doe subpoenas that the RIAA pulls. i.e. "we dont know who it is so lets just accuse an IP range and flush out the badguy.."

---

### Post by tturrisi on 2007-03-02
More than likely the result of spammers who spoofed your email address.  I received a spam yesterday with a spoofed sender address but valid sender ip.  I did an nmap scan of the ip and found some strange open ports.  The ip belongs to a customer at SBCInternet in Calif. and the open ports are ones used by known RAS email trojans.  I deduced that the owner has no clue he/she has infections.  An isp with decent tech personnel can see this, but it's possible your isp auto sends those messages after a certain quantity of incoming & outbound messages have been logged using your From address.

---

### Post by punx45 on 2007-04-04
well, its been a month since i started this thread, and I finally discovered (by accident no less) what probably caused that warning from my ISP, and I am suprised I haven't been shut down yet!

I noticed this morning that my hard drive was ticking, almost like a clock.   So, out of mere casual interest, (and concern that the hard drive might have been communicating its need for replacement) i checked the syslog, and found much to my surprise that a user account that I set up for my friend (and stupidly gave a *!WEAK!* [-X ](*,)  password)  was running a cron job every second.   this friend has no clue what a cron is im sure, so i know he didnt do it.   so i dove into the /home/user and found a public_html file that i dont remember placing, (but who can remember i screw around on that host a bunch...) so i checked out its contents (and if it was available publicly, which is was ) and it was some sort of ebay scam.   knowing it was active and live, i didnt spend too much more time poking around, I just tarred the whole user directory to another drive and then shut down.   I will inspect more when i get home and can take the machine offline.

so shame on me, and let this be a lesson to you all, when you set up accounts for friends, dont give them weak passwords, and maybe even bother to disable remote access if they dont need that!

---

