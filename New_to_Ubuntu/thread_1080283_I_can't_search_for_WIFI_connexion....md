---
title: "I can't search for WIFI connexion..."
date: 2009-02-25
forum: New to Ubuntu
---

### Post by Fabzil on 2009-02-25
Hello dear people ! ):P

Thx for spending time improving Ubuntu community ;)


My problem is simple : 
**TIME 1 :** I install ubuntu with a one-year-old live CD - Everything worked fine
**TIME 2 :** When I found the synaptic program, I said "hey ! that's cool ! Auto-update on Linux ! :p" - I hitted the "check for updates" and the system told me I got to update not just 2 or 3 stuff but my ubuntu enterily. Well, why not ? I just did it
**TIME 3 :** When the install finished, I reboot my laptop and choose the lastest version of Ubuntu on the start. And here comes the pain : _no more Internet !_

WTF?! o_0 I'm quite a g33k but I'm completly a third year computer sciences student, I need da Internet ! 
**-> So** I right-click on the little computer icon on the task bar to be sure that "Activate the network" and "Activate the Wireless NetWork" was checked (dunno the english name as I'm using the french ver. but you got the idea i Think). And what a surprise, but _"Activate the Wireless Network" has disappeared _! **-> Oops... **I made a little search on the net with my Vista, and found that I got to _copy some Intel drivers in one of the system directories_ and it will work. In fact, it did works, I got Internet back. 
**-> BUT** I have to configure it on-hand, the _"Activate the Wireless Network" still isn't here_. So, I got Internet, but I got to write everything every time I changed of network (university, home, family home etc...)


Can you please help me ??? [-o< [-o<
*thxing by in advance...*

P.S. : the driver is : _[Intel® PRO/Wireless 3945ABG]("http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2259&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go!")_

---

### Post by llamabr on 2009-02-25
This is unlikely to be a driver problem.

Why don't you dload the newest version, put it on a cd, and reinstall?  Using an old disk, then doing a massive update, it's difficult to tell what other things are broken.

Did you do an upgrade, or a dist-upgrade?  If the latter, you may have skipped updates, also breaking many things.

Do:

 lsb_release -a

and tell us the output.

---

### Post by superprash2003 on 2009-02-25
set your wifi interface to roaming mode.. you should find it in the network manager..

---

### Post by Fabzil on 2009-02-25
> **llamabr said:**
> This is unlikely to be a driver problem.

Why don't you dload the newest version, put it on a cd, and reinstall?  Using an old disk, then doing a massive update, it's difficult to tell what other things are broken.

Did you do an upgrade, or a dist-upgrade?  If the latter, you may have skipped updates, also breaking many things.

Do:

 lsb_release -a

and tell us the output.

Well, I don't want to get a new car everytime I got a glitch on the glass, but I got what you wanna told me about the disk-upgrades. All upgrades I have made was using the Update-Manager


> set your wifi interface to roaming mode.. you should find it in the network manager..
lol, CAN I be that easy ? I won't trust it... CAN IT BE THAT EASY ???  well, yes :-& :-& :-&

this part is solved, but I got another prob : When i give the manager the right pass, It won't connect me with Ubuntu but with Vista I get the connexion : /    I'll try solved this and i'll tell ya

---

### Post by superprash2003 on 2009-02-26
you have options like - 64bit , 128bit . try all combinations!!

---

