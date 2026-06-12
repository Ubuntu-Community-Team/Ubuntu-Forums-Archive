---
title: "[SOLVED] Remote access over school network"
date: 2008-09-11
forum: Networking &amp; Wireless
---

### Post by shortylonglegs on 2008-09-11
It is very possible that this is a stupid question, in which case you'll have to forgive me.  I have 2 laptops, the one I usually use, running Ubuntu, and the other running XP, which I need for school.  At home, I had set up ssh hosts on both machines, using cygwin on the windows computer, so I never had to worry about needing a file that was left on the other computer or something like that.  My question is, is this possible to do this on a college network?  And more important, is it safe?  At home I had changed the default ports and had a firewall running, but I hesitate to do anything here even with that security.  It is not a specific fear, just general caution that I think is probably prudent on the typical college campus.  If I don't have access to the network to setup port forwarding and all that, is there a way I can access my machines from the internet?

     Very long question.  Any help at all would be great.

---

### Post by Whiffle on 2008-09-11
I don't see any reason not to, I don't think the college network is any more dangerous than the internet itself.  I use ssh on a school campus fairly often to work on school computers from wherever I happen to be sitting, no issues.  

Chances are if one machine is in your dorm, you'll be able to get to it from anywhere you're connected to the school network.  I doubt you'll be able to get to it from the internet at large though.

---

### Post by shortylonglegs on 2008-09-11
Ok, thanks

By the way, I like that avatar; great movie.

---

### Post by TreeFinger on 2008-09-11
I didn't really read your post, since it seems like you got your answer but I want to rant about something.

I had set up my firewall to forward some obscure port to port 22 of one of my computers behind the firewall so I could log-in from school.

Well guess what, my school for some reason blocks pretty much every OUTGOING port.. where is the sense in that?? If someone has some could you please explain to me?

Outgoing port 22 is of course open... so I had to have 22 open on my firewall which led to a lot of attacks.

---

### Post by shortylonglegs on 2008-09-11
My high school's IT was rather incompetent for most of my time there, both positives and negatives from that.  I could ssh through a random port to my computers at home.  That was extremely helpful the day I left my paper sitting on the printer at home.  Just scp the file and print it at school.  But that also left the computers open to the other people at my school, who had nothing better to do then try to wreck them.  There were quite a few computers around with so much spyware and adware on them I'm surprised the whole network didn't come down.
     Then we got Macs which don't let you install that stuff...so they just stole them.  I like college much better.

---

