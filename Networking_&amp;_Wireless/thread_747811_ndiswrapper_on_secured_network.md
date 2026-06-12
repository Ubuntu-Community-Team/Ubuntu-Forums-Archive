---
title: "ndiswrapper on secured network"
date: 2008-04-06
forum: Networking &amp; Wireless
---

### Post by sdwinder on 2008-04-06
Hello all, i have recently noticed an issue with ubuntu and NDIS wrapper, im not sure if im doing something wrong or if its just the network im using it for.

Anyway, NDIS wrapper works rather flawlessly when it comes to my own home wireless network (128 bit encryption key).

My issue is at school, well, you know how when the connection requires some kind of login name and password (in my schools case its your user name and pw for all your other stuff) anyway, its an LEAP authentication which NDIS wrapper has.

The issue is, the first time i install ubuntu, and the NDIS wrapper, and i try to connect to my schools connection, it works fine. the screen turns on and asks me for pw, i type it in and off we go, hooray fast internet.

The issue arises when i shut down my pc and i try to connect again anytime after the first time. When i turn on the pc, i see it try to connect, but it never does, and when i try to reset it so i can re enter the PW and user name, the prompt never shows up. Ive tried to do manual config, but that doesnt seem to work either. 

Its almost as if it doesnt store the PW, even though it thinks it does, because it never pops up again...ever.

in ubuntu i notice its 2 green lights that try to connect, the first one connect, the seconds one turns on when your good to go, Well when the pw is wrong, the first green light lights up, and then it resets because the pw or username is wrong. Well after the connection works the first time. The second time it shows that it is trying to connect to the network, but none of the lights ever turn on, or blink (like its not trying at all, or the network doesnt exist, even though the network clearly shows up under wireless network list).

Anyone ever heard of this?

---

### Post by sdwinder on 2008-04-07
never mind i fixed it, apparently for this particualy network i have to manually give it access to keyring through the network manager

---

