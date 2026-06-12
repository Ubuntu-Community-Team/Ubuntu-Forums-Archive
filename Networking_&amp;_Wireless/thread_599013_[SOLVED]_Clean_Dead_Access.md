---
title: "[SOLVED] Clean Dead Access"
date: 2007-10-31
forum: Networking &amp; Wireless
---

### Post by airbornemist6 on 2007-10-31
My university hates its students, and has implemented Cisco Clean Access Agent. Personally, I hate it, and I hate it even more now. When you connect to the network and try to go to a page it is SUPPOSED to redirect you to a login page. Well, there's a problem, I get the redirect page, but it seems firefox (and operah, and iceape) cannot resolve the DNS server. I originally thought the server was down, but it wasn't. I spent most of the day talking to IT (which was an insult to me, the people at the help desk didn't know half what I know) help desk. They said this was the first linux computer they had EVER seen. I was getting worried at that point. If linux is that rare on our campus (which is extremely strange, since our university has one the top comp sci departments in the state) I'm starting to worry that our network has never been tested for it. I mean hell not even the network techs who are both cisco and novell certified knew anything about, I know because I applied there and got denied. Anyway sorry about the rant, I'm just pissed off. Oh btw, the DNS servers don't respond to my pings. That worries me further.

System:
Ubuntu Gutsy Gibbon
AMD Turion 64 X2
Geforce Go 7150M
2GB ram
Broadcom a/b/g/draft-n (don't know the model, but it is working perfectly everywhere else)

I saw one topic similar to this, but he had problems with java not being installed, that is not so in my case. I have java installed and everything.

I just want to know if anyone else has had a similar problem, or if there is a known bug that keeps clean access from working on ubuntu/gutsy

---

### Post by mpokrywka on 2007-11-01
I have no experience with that "agent" but maybe they (mis)configured access so that DNS works only after authorization? :) Try adding ip of that authorization host to your /etc/hosts.

---

### Post by airbornemist6 on 2007-11-01
Ah that's a good idea. Right now I'm in windows, which actually will log in with no problem. I'll try that idea when I get home and fix grub

---

### Post by airbornemist6 on 2007-11-01
Ok, I didn't get around to testing your idea, however, I did find a workaround. I found out that if I use the clean access agent in windows and then boot into Ubuntu, I will have internet access until the timer ends. I remembered an exploit one of my friends was telling me about not having to have clean access when in windows. The exploit was taking advantage of not needing the clean access agent in mac and linux. Clean access only looks at people based on mac address, therefore, as long as you still have the same mac, it thinks you are using the same OS.

Of course, once the timer expires I can't log back in. But, I can boot back into windows and login. So I'd say this is solved... more or less.

---

### Post by n0m0rth4nu on 2007-11-05
I have a solution to your problem. On wireless at your university, the domain suffix is angelo.local. There is a problem with debian/ubuntu in resolving .local names. To fix this problem you need to change /etc/nsswitch.conf

By default, a particular line should look like this:
```
hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4
```

You need to change it to this to allow the resolution of .local as a unicast domain:

```
hosts: files dns mdns4
```

This will fix your problem. I know because I have done it. You may need to restart your browser though. If you want more information about what is really going on with .local unicast domains on ubuntu, refer to

[http://avahi.org/wiki/AvahiAndUnicastDotLocal](http://avahi.org/wiki/AvahiAndUnicastDotLocal)
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=393711](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=393711)

---

### Post by airbornemist6 on 2007-11-12
Ok, I'm about to try that.

On another note, how did you know what university I went to? xD

EDIT:
Wow! It worked! Thanks! :D
Now I don't have to touch windows again on this laptop! Hooray!

---

### Post by n0m0rth4nu on 2007-11-12
> **airbornemist6 said:**
> 
On another note, how did you know what university I went to? xD!

I work there.

---

### Post by airbornemist6 on 2007-11-13
Ah, think you might be able to convince them to put these instructions on the website to make our lives earier?

---

### Post by jfluhmann on 2007-11-13
Also, to add my thoughts into this thread, make sure that if anything like this occurs again, have the help desk put in a ticket.  Problems like this aren't something our help desk is equipped to handle (to my knowledge), but there are several people on campus and in IT using various flavors of GNU/Linux and *BSD.  Having them put in a ticket will get the problem resolved much quicker.

I'm not sure how Clean Access help information or FAQs are setup for our campus, but I would imagine the "fix" will get included in there.

On another note, if your location is San Angelo, TX, there's only one university here ;-) (and Howard College wouldn't have a need to implement Clean Access)

---

### Post by airbornemist6 on 2007-11-13
Well, I actually got a ticket and they did actually call someone from networking. However, it seems they called the wrong person. I'm actually kind of surprised to find anyone from ASU on these forums after that experience. I had a feeling there had to be at least a few Linux users, but yeah. Anyways, thanks a lot guys!

---

### Post by Tux.Ice on 2007-11-13
whatever:guitar:

---

### Post by n0m0rth4nu on 2007-11-13
> **airbornemist6 said:**
> Well, I actually got a ticket and they did actually call someone from networking. However, it seems they called the wrong person. I'm actually kind of surprised to find anyone from ASU on these forums after that experience. I had a feeling there had to be at least a few Linux users, but yeah. Anyways, thanks a lot guys!

I actually am the wrong person that they called from networking. Good day!

---

### Post by airbornemist6 on 2007-11-16
...Er sorry....

---

