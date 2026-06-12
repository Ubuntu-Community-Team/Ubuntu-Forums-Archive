---
title: "Old Pc. New Linux"
date: 2007-03-01
forum: Networking &amp; Wireless
---

### Post by TheWilliz on 2007-03-01
I just ressurected a old PC of mine. I installed Ubuntu server version on it. I plug it into my Vista machine and Vista isn't detecting it. Help me please?

PS. I AM A NOOB TO LINUX!

---

### Post by wireddad on 2007-03-01
What do you mean plugged into XP?

---

### Post by Maelgwyn on 2007-03-01
have you installed Samba? ;)

---

### Post by TheWilliz on 2007-03-02
XP? wtf where'd you get that from....Samba?

---

### Post by rjfioravanti on 2007-03-02
do some research on something called samba, there are lots of resources, samba is what allows windows systems to access linux machines over a network

---

### Post by TheWilliz on 2007-03-02
Yeah well I'm a total noob so more in depth help is needed.

---

### Post by rjfioravanti on 2007-03-02
go to [www.google.com](www.google.com)

search for samba

read some of the search results

---

### Post by TheWilliz on 2007-03-02
I did it. It doesn't really help me....

---

### Post by punx45 on 2007-03-02
some more detail as to what "connected to" means would help too.

how are they connected? 
what physical ports?  what type of wire? or is it wireless?   is it a network with a router or switch? are the directly connected? etc..

i dont intend to be mean, but vague questions beget vague answers.   we want to help but we need to know what we are helping with! :)

---

### Post by rjfioravanti on 2007-03-02
ok, looks like this is a good spot to start setting it up... there are instructions to install and add network users

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Samba_Server_for_files.2Ffolders_sharing_service](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Samba_Server_for_files.2Ffolders_sharing_service)


let me know if you get stuck

---

### Post by TheWilliz on 2007-03-02
kk connected by enet ofc. I installed samba now what?

---

### Post by TheWilliz on 2007-03-02
Vista is picking it up as unidentified network with limted/ no connection yet it is being sent packets.

---

### Post by TheWilliz on 2007-03-02
Bump.

---

### Post by punx45 on 2007-03-02
still not really sure what you are attempting to do..

are either of the PCs connected to the internet? are they on the same network?

are you trying to share directory on the ubuntu with windows?

if so:   have you read any of the SAMBA documentation yet?   I know they have a number of example configurations on the site.

here is another thread discussing SAMBA also:

[http://ubuntuforums.org/showthread.php?t=372726](http://ubuntuforums.org/showthread.php?t=372726)

---

### Post by TheWilliz on 2007-03-02
....I am trying to connect the linux computer to my Vista computer to use the Linux as a file dumo. The Vista computer is connected to another XP computer via router. The XP computer is on the web and so is the Vista one via the router.

---

### Post by rjfioravanti on 2007-03-03
is your linux machine also connected to the router.. or is it only connected to the vista machine

---

### Post by TheWilliz on 2007-03-03
Linux is connected to vista. Vista is connected to router.Router is connected to XP.Xp is connected to Modem...I've sussed it I think. [http://ubuntuforums.org/showthread.php?t=372726](http://ubuntuforums.org/showthread.php?t=372726) 5 posts down. I'll do it later as I cant be bothered to at the moment.

---

### Post by punx45 on 2007-03-04
plug everything directly to the router.

---

### Post by TheWilliz on 2007-03-04
Maybe I should have posted what router I use....[http://www.homeplugs.co.uk/acatalog/diagrams.html](http://www.homeplugs.co.uk/acatalog/diagrams.html)

Homeplug downstairs plugged into plug socket...Enet cable from that to comp..Homeplug upstairs enet cable from that to my vista comp then becuase I have 2 network slots on the vista's mobo spare slot has a enet going into the Linux comp.

---

### Post by punx45 on 2007-03-04
ok.. so looks like your problem lies in the Vista PC.   you are going to have to get help on the visa end on how to bridge the two network ports on the Vista machine.   that would explain the "unidentified network" message you are getting in Vista.

another option would be to add a switch between the wall unit and the two computers.

---

### Post by TheWilliz on 2007-03-04
Well Linux is picking up windows network in its network window. I switched to desktop as I thought it would be easier.

---

### Post by TheWilliz on 2007-03-04
Nope bridging did jack.

---

