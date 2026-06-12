---
title: "dsl connection"
date: 2005-09-09
forum: Networking &amp; Wireless
---

### Post by daniel49 on 2005-09-09
Ok finally got dsl into my neighborhood. 

I have a duel speed hub that I have hooked the dsl modem up to and uplinked to my 2 network cards on each respective machine.

This is a combo modem/router provided by qwest
[http://www.qwest.com/dslhelp/modems/gt701/index.html](http://www.qwest.com/dslhelp/modems/gt701/index.html)

win xp sees everything fine and its working great
Now I duel boot on both of these machines.
this one is ubuntu and the other fedora core3

I have changed it to auto on the dchp
In fedora at first It would only go to one specific site in firefox, so I loaded conquerer browser it would go everywhere i sent it by typing in the url.
then I closed it and firefox now will also go everywhere...wierd but ok it works now.

Now for ubuntu which is on the primary machine. I got rid of the serial dialup modem, enabled dchp and firefox again will only go to the same one site.  a comp forum I visit daily. plus synaptec will download, also some of the preconfigured bookmarks for firefox will work.

But you type in any other url it just sits there forever trying to connect and never does.
So I downloaded epifiny browser from synaptic to try that behaved exactly the same. upgraded firefox no change.

what the hecks going on almost seems like it cannot resolve the sites address or something, but I am not sure

---

### Post by s_p_a_r_k_y on 2005-09-09
what does the command line tell ya?

try typing in

host domain.com

where you replace domain with whatever you are trying to go to, to see if it resolves. THen try pinging it.

---

### Post by manicka on 2005-09-09
You could also try manually entering your dns server. I have to do this as my router doesn't provide this info properly via dhcp

---

### Post by daniel49 on 2005-09-09
[QUOTE=s_p_a_r_k_y]what does the command line tell ya?

try typing in

host domain.com

where you replace domain with whatever you are trying to go to, to see if it resolves. THen try pinging it.[/QUOTE]


no that didn't accomplish anything and I checked the dns numbers they are the same as they are for xp

---

### Post by daniel49 on 2005-09-11
ok found a fix here.

[http://www.linuxquestions.org/questions/printthread.php?s=&threadid=244026](http://www.linuxquestions.org/questions/printthread.php?s=&threadid=244026)

thx for the imput
dan

---

