---
title: "Can't get Evo/Thunderbird mail from Compuserve"
date: 2006-07-25
forum: Networking &amp; Wireless
---

### Post by dgermann on 2006-07-25
Hi--

The problem: neither Evolution nor Thunderbird can connect to my Compuserve POP3 account to collect my e-mail. ](*,) 

The symptoms: 

1. Yahoo mail and mail2web connect to this account and collect e-mail properly. And dialup, too.

2. Telnet stalls out connecting to pop.compuserve.com 110 without offering a "server ready" prompt, except once every 20 tries.

3. tracepath sometimes connects, sometimes times out.

4. Neither Thunderbird nor Evo ask for a password when connecting to CompuServe; but when connecting to ComCast they do. For Compuserve, they just time out.

My system: 4 Ubuntu 6.06 boxes, a WinXP Pro, and two Win95 boxes connected through a LinkSys router WRT54G. ComCast is my ISP.

What I've tried: About every combination of settings for the accounts under Evo and Thunderbird, including creating new accounts via their wizards.

Asking at Compuserve--so far they seem stumped.

Turning off the firestarter firewall--made no difference.

Trying Evo from a different computer--made no difference.

Trying telnet from a Win95 box--made no difference.

Checking the router settings to see if there is something blocking any sites, including compuserve--nothing that I can see.

Pulling my hair out for about 6 hours--made no difference. ;) 

It seems to me that I am not connecting reliably to their server from inside my network. But where the problem is, I cannot figure out.

Any ideas?

Thanks!

---

### Post by dgermann on 2006-07-30
Hi--

Is there some way I can bypass my router as a test?

Originally, when the router was set up, I set it up using a WinXP machine. Do I have to use that machine to do the test? Because when I try to connect a Ubuntu machine directly to the modem, bypassing the router, I get nothing. No Web. No ping.

Thanks!

---

### Post by Roger Steiner on 2006-08-28
I am also trying without success to access my Compuserve mail with Evolution. My system is Breezy
My isp is Roadrunner
I access Compuserve on line

The server address I have been using is csmail.compuserve.com

I receive no error messages except that the sent mail did not go and is being held in my outbox.

Is anyone currently using Evolution and Compuserve successfully?

Roger in Hawaii

---

### Post by dgermann on 2006-08-29
Roger--

Think I replied to you on another board, too.

I did get it working sort of when I got a new router. I think there was a problem with that router, for sure.

But the bigger problem is CIS. The folks on the PC Hardware forum on CIS finally told me that CIS has had problems since it started offering POP mail--they apparently don't dedicate enough bandwidth or something to meet the demand.

As a result I have to attempt to logon to CIS several times, and eventually I can. Today I got on in 3 tries one time, and 11 another time.

What is strange is that mail2web and yahoo mail can both connect pretty reliably to my CIS POP mail account--but then I don't know if they are set to keep retrying if they don't get an immediate response.

Hope that helps. The people on the PC Hardware and Classic e-mail forums were quite helpful, so you might ask over there, too.

---

