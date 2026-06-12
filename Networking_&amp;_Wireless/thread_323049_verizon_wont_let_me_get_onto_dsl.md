---
title: "verizon wont let me get onto dsl"
date: 2006-12-21
forum: Networking &amp; Wireless
---

### Post by heathersnogles on 2006-12-21
one day i woke up and my interenet wouldnt work and all i get is a message from verizon saying it doesnt support linux and in order to get it to work i need to either install windows or get on a computer that suppports windows...is this a new thing?  can anyone help me?  lamens terms becase im a newbie
thanks

---

### Post by Carbonbasedmistake on 2006-12-21
I get quite a few drops from Verizon. I usually just open a terminal and type in "poff dsl-provider" then "pon dsl-provider" (without quotes) and the connection is re-established. I also run "plog" and it shows me the connection status. If I have an IP and DNS info all is good to go.

In some cases I must deactivate the ethernet connection - then cycle power on the modem. Next I wait untill the modem lights come on - then activate the ethernet connection ( through the graphical networking utility ) and then issue pon dsl-provider and I reconnect.

Something goofy is going on to cause the drops - just haven't had time to try to figure it out

luck

bob

---

### Post by punx45 on 2006-12-21
I know that buying more stuff usually isnt the optimal solution, but if you were to get a cable/dsl router (wired or wireless doesnt matter) and configure it to make the connection then you shouldn't have the "unsupported" problem.

routers can be had pretty cheap these days.

---

### Post by heathersnogles on 2006-12-26
im gonna go home and try this today, i thin alreaqy tried this, but ill try again
any other ideas?
thanks

---

### Post by heathersnogles on 2006-12-26
did nt work
it said when typed poff dsl-provider
tsaid no pppd is running
when i did pon dsl-provider
weird symbols started scrolling
when i typed plog
ppp0 interface
timeout sending config-requests
connection terminated
teflush failed: bad file descriptions
tcsettr:invalid argument line 1101
exit


please help

---

### Post by Carbonbasedmistake on 2006-12-27
Try Typing "sudo pppoe.conf" and answering the questions - you'll need a user name and password that is registered with Verizon. You can go directly to online Verizon dsl registration to do so if you haven't already. 

Then use pon dsl-provider to turn it on ---- poff dsl-provider to turn it off.


hope it helps


bob

---

