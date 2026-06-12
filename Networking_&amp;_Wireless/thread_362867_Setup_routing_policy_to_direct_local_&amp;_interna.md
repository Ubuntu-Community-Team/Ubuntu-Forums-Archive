---
title: "Setup routing policy to direct local &amp; international traffic"
date: 2007-02-16
forum: Networking &amp; Wireless
---

### Post by Sidster on 2007-02-16
I have a rather unique problem and I was hoping someone would help me to do this the "Ubuntu" way.

In my country it's popular practice to set-up routing policy to direct local & international traffic through different isp's. This is done because local data transfer is about half the price of international and isp's refuse to implement this service on their side. I've followed a couple of how-to's which you can find [here]("http://tlug.up.ac.za/wiki/index.php/Local/International_Router") and [here]("http://mybroadband.co.za/vb/showthread.php?t=64649") without much success. I get the feeling that this is because the how-to's I've read aren't very concise. Maybe they apply to different distro's. I was wondering if anyone with a bit more expertise than me would help me to update the how-to on the wiki I provided a link to. I would like to add distro specific instructions as well make the whole thing a bit more "beginner" friendly.

What I mainly need is for some helpful person to read over the wiki how-to and post suggestions to make it a bit more "Ubuntu" centric. I plan to either offer to add to the wiki or find a place to post it somewhere accessible to South African users like our local broadband forum for example.

Some advice as to how to get it set-up on my machine would be a step in the right direction. After I've perfected it on my machine I could possibly create a script that does it all for the user.

Any help/advice would be much appreciated. :)

---

### Post by koenn on 2007-02-16
I've read the two links, but I'm not sure what exactly it is they are trying to do - possibly because i'm not familiar with the south african isp context (or by a lack of knowledge in PPPoE - being used to networked solutions)

So, how does this work ?
You have two accounts, each with a different isp ? Is that one in south africa and one abroad ? could you explain how you setup your current internet connection ?
From what i understand, the wiki-approach is that you use 1 computer to act as a router so you'll have 2 computers, 1 as a router, the other as your usal desktop pc. 
I can't really tell if the second link uses that approach as well - it seems to rely on IPcop ) an application I don't know. 
I don't fully understand this : can you have two pppoe connections simultanuously or do you chose to have 1 of the two ?

Beyond that, it gets more clear : routes are added to match 1 of the two connections - the wiki shows an algoritm to wotk out the "local" (south african ?" networks, the otherone just uses a list. 
Then, NAT is used to make to make the connections transparant - similar to a load balancing technique. 

So the routing and NAT poart I'm quite sure are not to hard to get going on an ubuntu machine. The ppoe part is less clear to me. I know Ubunto supports ppoe but i have no experience with it on ubutu so i wouldn't know where to start.

---

### Post by Sidster on 2007-02-19
Thanks for the reply :) You've given me some ideas that I'm gonna research a little more.

Some more info regarding my problem:

South African broadband users want to be able to have two simultaneous PPPoE connections (I know it can be done I just can't find the web page where I read about it now) and then route local traffic through one isp and international through the other. Like you say, the routeing is done either with an algorithm or a simple list of local subnets. That said, there may be an entirely different and simpler way to achieve the above with Ubuntu

I suppose it's such an uncommon request cause it only applies to a handful of South African users. Anyway, some hardcore linux guru's here in South Africa seem to have figured it out on their own. I've asked on the various forums for a more detailed explanation specifically one that's slightly more debian/ubuntu centric but haven't received a reply as yet. :( 

Thanks for the help :)

---

