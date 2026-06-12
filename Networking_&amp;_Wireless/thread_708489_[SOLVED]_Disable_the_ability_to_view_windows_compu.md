---
title: "[SOLVED] Disable the ability to view windows computers"
date: 2008-02-26
forum: Networking &amp; Wireless
---

### Post by JoeyH on 2008-02-26
I am a student at the local high school, but I also work for the school's network management department. We have a ton of computers (around 400 minimum at the high school, probably over 1200 in the school district).

One of the network administrators decided that one of the smaller computer laps (10 computers) should run Linux. That lab is used by one of the computer classes, and the admin figured it would be better for their class to use Linux other than Windows. After a little debate, we decided on Ubuntu 7.10.

I installed Ubuntu on one of the computers, to make sure that it works properly with all the hardware in the computer. However, when I was checking the network connection, I came across a serious problem.

If I went to the places menu, and clicked network, it showed two of the computers in the lab (versus the seven that were running). I clicked on windows network, than clicked on the district's active directory icon, and it loaded up a list of every computer in the school district. Not just the high school, but every school. That's around 1200 computers in that list.

We really can not have that at all. At the minimum, I fear that it could overload/lag the router (and with the number of people connected to it, we really can't have that). And we're worried that some students might try to cause some damage to the windows computers.

I loaded synaptic, searched for samba, and deleted the two items that were installed. The windows network icon is still there, but clicking it didn't seem to do anything.

I need to know, did deleting those two packages permanently disable the computer's ability to find windows computers on the network? If not, how can I make sure that the users won't be able to access that list?

---

### Post by SpaceTeddy on 2008-02-26
i am going to make myself unpopular here... but WHY is that a problem of ubuntu ? the windows computers are obvisouly broadcasting their shares and everything into the network. Ubuntu just displays what it find. 

So why fix the problem if we can hide it ?

as for she browsing the shares... i think i need to get rid of vfs for gnome or nautlis... not sure.

another way would be to simply block port 137, 139 and 445, which are the windows shares...

> sudo iptables -A OUTPUT -j DROP -m multiport -p tcp --dport 137,139,445

---

### Post by Eiríkr on 2008-02-26
What SpaceTeddy says has truth to it -- the Ubuntu machines aren't going to be bogging down the routers too much more than they are already bogged down by all those Windows machines busily broadcasting.  It sounds like some of the network admins for the school district haven't set things up quite properly; no big surprise, my wife's a teacher, and the Windows-only (as in that's all he knows) network admin at her school couldn't tell a burro from a burrow, so to speak.  :(  I'd suggest trying to inform someone about it, starting with your teachers and your own school administrators, as this kind of network setup is (as you correctly identified) a serious potential security problem, not to mention it's very likely shortening the useful life of at least some of the network equipment.  

But don't be surprised if your attempts at informing someone fall flat -- people can be very touchy when they think they're experts and are suddenly forced to face their own incompetencies.  (The guy at my wife's school is clearly on the gravy train, and isn't about to let his own basic ignorance and unlikability keep him from riding it as far as possible.)  OTOH, the folks on your end could be of a different sort, and your discovery might wind up being a very good thing.  Good luck!  :)

On the more technical side, if your Ubuntu machines have a firewall-equipped router between themselves and the rest of the school district network, dropping packets for those three ports sounds like a dandy idea.  Certainly an easy fix.

Cheers,

Eiríkr

---

### Post by SpaceTeddy on 2008-02-26
i have been a bit rude in my post. Yes, what erikir wrote was what i essentially meant... nonetheless do i also know that fixing something like that is a major task. It is something that will not be accomplished in a few days or even weeks. You must face the fact tho, that anyone who is connected to your network will see those shares, no matter how much you forbid them. The majority of students might be too simple minded to find something like that... but one individual is enough to find and abuse them. I can go on about threat scenarios, as i work for a college myself, and we have the daily trouble of keeping our systems safe from in- and ourside aswell. So i would really suggest you fix that asap - whenever asap is with a network of 1000+ clients

As for fixing the ubuntu issue, i think browsing the smb network is so deep in natilus that you will not be able to forbid it unless you totally cripple your system.i would really suggest that you load the iptables rule i posted up there to automaticially load upon boot on the ubuntu computer (put it into /etc/rc.local - without the sudo) and see if they can still browse. This is neither a safe nor a recommended way, but the easiest you can go at the moment... at least as far as i can see. I hope my horizon is not too close :)

so, happy fixing

---

### Post by JoeyH on 2008-02-26
The problem is that on the windows computers, profiles are pretty much locked down, so you can't just click the "show workgroup computers" button and view all the computers on the network. All the normal ways to browse other computers on a network from windows - command prompt, network neighborhood, etc - have all been blocked. We can't go reporting the problem - our director of network technology wouldn't allow us to build the lab, so we had to build it behind his back. He also is very anti-linux.

With Ubuntu though, such options are not blocked. And some of the people who will be using these computers are real troublemakers. I personally would rather just bar them from using the computers, but I can't do that as they are enrolled in the class (computer networking), and they need access to these computers to complete their work.

I know the majority of them know about the problem, as when I was talking to one of the network administers about it, they were obviously eavesdropping.

Believe me, I would love to have a router for that lab. I know one has been requested in the previous budget. However, we don't have any idea if they approved the request or not. The only way to know if a budget request gets approved is to go into the mail room and see if there are any packages with your name on them.

I like that port blocking idea. I'll have to try that tomorrow. Thanks.

---

### Post by SpaceTeddy on 2008-02-26
then i suggest you try the lines we gave you... comming from another post, i would also suggest blocking udp pakets aswell - so put these four lines in the file /etc/rc.local

> /sbin/iptables -I INPUT -m multiport -p udp --sport 137,138,139,445 -j DROP
/sbin/iptables -I INPUT -m multiport -p tcp --sport 137,138,139,445 -j DROP
/sbin/iptables -I OUTPUT -m multiport -p udp --dport 137,138,139,445 -j DROP
/sbin/iptables -I OUTPUT -m multiport -p tcp --dport 137,138,139,445 -j DROP
The first two block any incomming broadcasts that the computer might pick up, the last two block any program sending out requests to for windows shares... or so they should

you can edit that file with the following command
> gksu gedit /etc/rc.local

that should fix the problem in the worst bits :)

As for the administrator.. being against linux AND not fully in charge of your network is a bad combination... very bad indeed. I feel sorry for you. (i had to fight three years to turn the wheel towards linux - but it is finally done :) )

---

### Post by JoeyH on 2008-02-27
I just tried the port blocking, and it worked perfectly. Thanks to the both of you :)

As for the director of our network not having any control over it - I can agree. He rarely seems to know what's going on. He's even was once standing right next to the little network lab area, and didn't notice anything about it.

---

### Post by Eiríkr on 2008-02-27
Great to hear that it's working.  And many thanks to SpaceTeddy for the specifics!  I'm terrible at iptables -- if it weren't for Shorewall and GRC's Shields Up utility I'm sure my firewall would be much less effective than it is.  :-|

If this fixes your issue, don't forget to mark this thread as SOLVED in the Thread Tools dropdown at the top of the page.  :)

Cheers,

Eiríkr

---

