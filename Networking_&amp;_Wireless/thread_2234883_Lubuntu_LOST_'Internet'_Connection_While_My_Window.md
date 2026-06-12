---
title: "Lubuntu LOST 'Internet' Connection While My Windows STILL WORKS"
date: 2014-07-17
forum: Networking &amp; Wireless
---

### Post by Andrew_Jay on 2014-07-17
Today I LOST my Lubuntu 'internet connection' while my windows PC still works perfect.

Internet had been working perfectly fine for a month prior to this [I](hence I suspect it's not a driver issue).

[/I]I put the term 'internet' in scare quotes because in actual fact I AM connected... It's just the browsers and download managers are being blocked from accessing the internet.

Here's some basic data:

Wifi Connection: active (68%)

**PING test:** Pinged 66.220.144.0 (this is an IP associated with facebook.

**Results were: **PING 66.220.144.0 56(84) bytes of data. 5 Packets transmitted, 0 received, 100% packet loss.

So as you can see I am getting some serious mixed signals from Lubuntu here. Apparently it's connected to the internet but it's like there's something '**** blocking' it from sending any data. Is it possible this is a firewall issue?

BTW I've had this issue before, and it just went away with time... But this is a work related computer so I'd appreciate a solution that I can actively implement.

Any help would be hugely appreciated!

---

### Post by Bashing-om on 2014-07-17
Andrew_Jay; Hello,

Too soon to make a call, but for starters ->.
> 
But this is a work related computer

1) Are you behind a proxy ?
2) Can you ping your router there at work ?
3) Can you connect when at home ?
4) What results from checking the local loop ?
```

ping -c3 127.0.0.1

```

[INDENT][INDENT]traffic management
[/INDENT][/INDENT]

---

### Post by Andrew_Jay on 2014-07-17
I actually fixed it by turning off the computer and turning it on again.

Problem solved.

---

### Post by Bashing-om on 2014-07-17
Andrew_Jay; Yes !

That all powerful 'power button' ! Most times for bad, this time for good.
As this crisis is now at an end:
Please mark this thread solved; 
aides others seeking the solution,
 helps keep the forum clean and 
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]happy trails to you
[/INDENT][/INDENT]

---

