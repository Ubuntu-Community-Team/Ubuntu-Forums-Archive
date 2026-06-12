---
title: "Dell xps 1330 wireless not connecting"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by NoobixCubeOne on 2009-09-14
Hey all,

Thought I would finally dual boot my laptop and make the shift to Open source software. I have a Dell XPS M1330. 

It worked perfectly out of the box except for the wireless. I have an Intel wifi link 4965AGN wireless card. It is able to recognise my wireless connection I would like to connect to, but when I complete the detail to log onto the network.
I am using a WEP 40/128 bit key where the authentification is Open. All the details are the same as when I log onto my Windows 7 OS (which connects no problem). But as I push connect, it attempts to do so and then the window returns. I assume that indicates that it could not connect.

I have tried resetting the router, and the wired connection works perfectly.

It seems that a few people have had this problem with older versions of Ubuntu. 

Any help would be really really appreciated as I would really love to stick with Ubuntu!

Cheers

---

### Post by I WILL DO IT on 2009-09-14
sounds like a firewall, does the wireless connection have a wep or wpa???

---

### Post by NoobixCubeOne on 2009-09-14
I do have to enter a WEP Key which is ten characters long, but the authentification is Open.

---

### Post by I WILL DO IT on 2009-09-14
mmm idk what it could be then, make sher your connecting to the network.

---

### Post by mc4man on 2009-09-14
I'm on a 1330 now with same card
 > description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation


I'm on hardy but have used live cd's of 8.10 thru 9.10, and had 9.04 installed for a bit.

Overall it has worked perfectly with just entering the key.

There has been no problems connecting with any using the wep except for a couple of reasons.

Obviously if the key is entered wrong it won't connect, though there were times when entering it properly when re prompted didn't work. (may of only been on live cd's
Then I'd just delete the connection,  reacquire and enter if right.

I think initially it wouldn't accept any of the keys. ( my router gives 4, though only the first one listed works on ubuntu.

The fix there was to access the router,use a new pass-phrase and get a new key. Has worked perfectly since, the only exception is a live hardy cd, then it won't work.

Edit:
The thought I forgot to mention was that on any live cd from 8.10 to 9.10 alpha 5 you should be able to connect right away, only entering the key and clicking connect. You may want to try that, the live cd should be a known  factor in regards to the m1330 and card. ( in other words, probably about the same hardware  and same install.

If not try resetting or considering the router.

---

### Post by NoobixCubeOne on 2009-09-15
Hey all thanks for the help!

Basically, I deleted the original wireless account, and set it all back up again.

It has worked like a charm! I this stable wireless connection is long-lived


:popcorn:

---

