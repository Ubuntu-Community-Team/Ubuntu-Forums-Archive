---
title: "Samba -bandwidth limiting?"
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by darkdays on 2007-04-26
I've just setup two samba shares, I'm using them to share stuff with a couple of friends. I've set guest ok and set their IP's in hosts allow and denied everyone else. Everything works fine although I'm pretty new with these things, just switched to Ubuntu as my main OS after a horrible Vista experience. 

Is there a way to limit the total bandwidth these shares use so my friends can't eat the whole 10Mbit?
Say to prob 6Mbit or so..

---

### Post by thingy on 2007-04-26
I looked around and I think this program is probably a good solution for you.

iprelay

Read up on it here: 

[http://www.penguin-soft.com/penguin/man/1/iprelay.html](http://www.penguin-soft.com/penguin/man/1/iprelay.html)

---

### Post by darkdays on 2007-04-26
Thank you, it does indeed look like a really good solution, but for some reason I can't get samba to use other ports than 139 & 445..
I put "smb ports = 7139 7445" in my smb.conf but when I portscan my IP they don't show up as open, when using standard ports the standard ports do. 
How do I make samba use non-standard ports, so I can iprelay the standard ports to the non-standard ports?

---

### Post by thingy on 2007-04-26
oh! my mistake! Maybe this might not be possible then.

hmm wait

according to this url: [http://www.linuxjournal.com/article/6604](http://www.linuxjournal.com/article/6604)

to get samba to use a different port, you need to run it using inetd. hmm looks like it would work...not sure though....

the best solution is to just use iproute/iptables to do traffic shaping:

[http://www.knowplace.org/pages/howtos/traffic_shaping_with_linux.php](http://www.knowplace.org/pages/howtos/traffic_shaping_with_linux.php)
[http://howtos.linux.com/howtos/Traffic-Control-HOWTO/intro.shtml](http://howtos.linux.com/howtos/Traffic-Control-HOWTO/intro.shtml)
[http://linux-ip.net/articles/Traffic-Control-HOWTO/](http://linux-ip.net/articles/Traffic-Control-HOWTO/)


but setting up a traffic shaping firewall is not easy :-(

If you get further, please do document it here so that others can benefit from it

good luck


btw, you did restart samba after adding the smb port = blah blah line right? did you see any messages in /var/log from samba? try port numbers < 1024 as well if samba didn't like something, im sure it will complain so check the logs

---

### Post by darkdays on 2007-04-27
Been looking into the subject a bit deeper now and you were most definitely right when you said:

> but setting up a traffic shaping firewall is not easy 


I'm going to look into the first solution again when I get some free time from my studies, went through the many samba logs but couldn't find anything that looked like a port related error. 

It's a bit frustrating, this kind of limiting could be handled beautifully under XP with BWmeter. 
Have some other bandwidth limiting I need to do as well. ( We're allowed a max of 15 gb total traffic outside of our subnets, more and they shut you down for 24h. So I need to figure how to avoid that happening too. :-I )

Thanks for your help, I'll post when/if I get something working.

---

