---
title: "[SOLVED] ssh &amp;quot;no route to host&amp;quot;, can't open webpages either"
date: 2008-01-17
forum: Networking &amp; Wireless
---

### Post by clarezoe on 2008-01-17
First, the webpage of my university is [HTML]www.gu.se [/HTML], I can't open all the webpages with the domain "gu.se", but if I use proxy, it works.

Second, I can't login to my school personal account by "ssh"
```
$ ssh thesis4@evo.lundberg.gu.se
ssh: connect to host evo.lundberg.gu.se port 22: No route to host
```
Strangely, I use "ssh" can login to another personal account in another university, then use "ssh" again, I can login successfully
```
$ ssh feifei@remote1.tekno.chalmers.se
feifei@remote1.tekno.chalmers.se's password: 
Last login: Thu Jan 17 23:42:02 2008 from jehoven-laptop.csbnet.se
-bash-3.00$ ssh thesis4@evo.lundberg.gu.se
Password: 
Last login: Thu Jan 17 23:05:52 2008 from remote1.student.chalmers.se
Directory: /home/thesis4
Directory: /home/thesis4
Fri Jan 18 00:24:58 CET 2008
evo /home/thesis4>
```

Can anyone help me? I have no idea what's the problem, and why!

---

### Post by dbentson on 2008-04-09
I have just been fighting with this and found a solution. It appears that the issue was related to my wired connection. My wireless was configured for home and my wired connection was configured for my work. When I tried to connect to any computer at my workplace (either SSH or HTTP), the attempted connection failed. 

I was very very frustrated for weeks with it. Finally it occurred to me that the only problem was with my work servers and that it was acting as if I were on the wrong subnet or something. Even though my wireless was configured just fine, I surmised that the system might be trying to use my wired connection. 

When I disabled the wired connection with this:
[FONT=Courier][INDENT]**[COLOR="Navy"]sudo ifconfig eth0 down[/COLOR]**[/INDENT][/FONT]
I was then able to connect just fine.

There must be a way to have the system know when I am at home and that it shouldn't bother using the wired connection, but I haven't stumbled upon that yet.

i hope this helps.

dbr4good in Vancouver

---

### Post by Eiríkr on 2008-04-09
@clarezoe --

Similar to what dbentson notes, your description of ssh-ing into a different machine and then ssh-ing from there to your gu.se account suggests that the network setup on your personal machine might be goofy.  I'm unfortunately no networking guru, so someone else will probably have to pitch in, but for starters, I'd suggest that you start by running these commands and posting the results here.  Also run the following for the intermediary server you ssh into (tekno.chalmers.se above).  Post both, and be sure to label which is which.
```
ifconfig
cat /etc/network/interfaces
cat /etc/resolv.conf
```

Also, from your personal machine, can you ping evo.lundberg.gu.se?

Cheers,

Eiríkr

---

### Post by clarezoe on 2008-04-09
I didn't get a reply promptly, but now I've update to hardy, this problem is gone, thank you very much.

---

### Post by Eiríkr on 2008-04-09
Glad to hear things are working.  :D  Since your issue is resolved, please mark this thread as SOLVED in the Thread Tools dropdown towards the top of the page.  This will help others who are looking for a solution.  :)

Thanks,

Eiríkr

---

### Post by clarezoe on 2008-04-09
But It's not solved by applying any suggestions, it just went away itself, should I still mark it?

---

### Post by Eiríkr on 2008-04-09
Suggestions or no, your original problem was solved.  If someone else is looking for threads with similar subjects, but only wants to find the SOLVED threads, your solution (i.e. "install Hardy") will not appear.  So ultimately, marking the thread as SOLVED helps people looking for solutions.  There's no real points system here that I know of, aside from the "Thanks" button, so there's no worry that we're somehow getting a freebie if you mark the thread.  ;)

Cheers,

Eiríkr

---

### Post by clarezoe on 2008-04-09
Sure, and Thanks!:lolflag:

---

### Post by Jopie64 on 2008-04-27
Your problem might have been solved when Hardy was installed, mine started with it. I cannot connect out of my home network, it is not able to find a route outside of my home network. I'm using DHCP and other pc's in my network are doing fine. 

Its a wired connection and my pc does not have a wireless network card installed.

Any ideas left?

In gutsy I installed virtualbox with a network bridge (br0). Its still configured that way...

---

### Post by Jopie64 on 2008-04-27
WEIRD!!!

I did:
sudo ifdown br0
All went ok. Outside network was working again.

Then I did:
sudo ifup br0
All still ok.

Well... if it works, don't fix it :)

---

### Post by dbr4good on 2008-06-30
Jopie,

What is br0? Sorry if that's a dumb question but I haven't seen that before.

---

