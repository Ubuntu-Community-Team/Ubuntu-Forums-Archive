---
title: "ufw as a firewall"
date: 2010-06-09
forum: New to Ubuntu
---

### Post by tinydancer88 on 2010-06-09
I have a customer coming into the shop soon who has switched her computers to Ubuntu because of a problem with hackers.  She heard that Linux based operating systems might be easier to protect, but doesn`t know anything about Ubuntu at all.  I`m just wondering a few things, as I am sort of a beginner myself:

1. how good would ufw be as far as blocking hackers from her computer, and should I try to block anything specific that tends to be a problem?  
[https://help.ubuntu.com/9.10/serverguide/C/firewall.html](https://help.ubuntu.com/9.10/serverguide/C/firewall.html) is where I`m getting my info on ufw

2. what else should I tell her about Ubuntu as a non-linux user, and someone who doesn`t know terribly much about computers to begin with?  They mostly just use the internet for email and banking and things, so I think that`s mostly self-explanatory, but is there anything else they could need to know for basic maintenance?

Thanks so much for any help that you can give.

---

### Post by sb5551 on 2010-06-09
I am relativly new to linux too. I would reccomend installing gufw which is just the graphical front end of ufw. If she isn't going to be torrenting or talking to other computers on her network (if she has one) just deny all incoming connections. 
 
She will have to get some familarity with the command line just in case, but the latest Ubuntu 10.04 does a pretty amazing job of not requiring the terminal to be used. 
 
The last thing I can reccomend is become a member here and search the internet there are thousands of reliable resources online and almost every problem she will encounter someone else has had before. It doesn't sound like she will be using her computer to venture into any unchartered territory. 
 
Oh yea, a really strong password and dont use any of the ones she used on her windows computers.

---

### Post by sydbat on 2010-06-09
> **tinydancer88 said:**
> I have a customer coming into the shop soon who has switched her computers to Ubuntu because of a problem with hackers.  She heard that Linux based operating systems might be easier to protect, but doesn`t know anything about Ubuntu at all.  I`m just wondering a few things, as I am sort of a beginner myself:

1. how good would ufw be as far as blocking hackers from her computer, and should I try to block anything specific that tends to be a problem?  
[https://help.ubuntu.com/9.10/serverguide/C/firewall.html](https://help.ubuntu.com/9.10/serverguide/C/firewall.html) is where I`m getting my info on ufw

2. what else should I tell her about Ubuntu as a non-linux user, and someone who doesn`t know terribly much about computers to begin with?  They mostly just use the internet for email and banking and things, so I think that`s mostly self-explanatory, but is there anything else they could need to know for basic maintenance?

Thanks so much for any help that you can give.Let's see... for #1 - no ports are open by default in a fresh Ubuntu install, so you shouldn't need to change anything in the firewall. gfuw is the graphical interface to change settings in ufw.

For #2 - make sure that Firefox is set to remove all personal information when it closes (except saved passwords...those can be a pain to type if you have to sign into places alot). There are many add-ons for FF that can help make surfing a bit safer too (WOT, Secure Login, No Script, Adblock Plus, etc).

---

### Post by oldos2er on 2010-06-09
Good info on Ubuntu Security here: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by admiralspark on 2010-06-09
You said they do online banking, so I'm going to recommend against getting a no-script addon for firefox. AdBlocker is great, and I've never heard of the other two distro's. 

As for a recommendation? Puppy Linux (of any variety, but newer=better, preferable 4.3.1 or 5.0) will scream on nearly any computer with 128mb RAM or more. It loads completely into the RAM, so everything opens near-instantly. It's also very easy-to-use and very secure. 

Another recommendation is to try Linux Mint (8 or 9). Mint is a spinoff of Ubuntu, except it has a much more logical layout (especially for ex-Windows users), a cleaner and easier menu, and it fixes most of the post-release problems that Canonical doesn't care enough to do (read: it's more refined). I'd try it first, everyone I know who's used it (including me, obviously) loves it. 

Either way, when you go to burn a bootable cd, you MUST burn it at the lowest speeds possible. Recommended is 4x for CD and 1x for DVD. I've been through enough useless CD's because I was impatient.

Here are the site links:
[Linux Mint](http://www.linuxmint.com/)
[Puppy Linux](http://puppylinux.org/main/index.php?file=Overview%20and%20Getting%20Started.htm)

---

### Post by sydbat on 2010-06-09
> **admiralspark said:**
> You said they do online banking, so I'm going to recommend against getting a no-script addon for firefox. AdBlocker is great, and I've never heard of the other two distro's.No Script will not effect bank sites. You just allow them. I've been using No Script for quite awhile and have had no trouble doing online banking.

> As for a recommendation? Puppy Linux (of any variety, but newer=better, preferable 4.3.1 or 5.0) will scream on nearly any computer with 128mb RAM or more. It loads completely into the RAM, so everything opens near-instantly. It's also very easy-to-use and very secure. 

Another recommendation is to try Linux Mint (8 or 9). Mint is a spinoff of Ubuntu, except it has a much more logical layout (especially for ex-Windows users), a cleaner and easier menu, and it fixes most of the post-release problems that Canonical doesn't care enough to do (read: it's more refined). I'd try it first, everyone I know who's used it (including me, obviously) loves it. 

Either way, when you go to burn a bootable cd, you MUST burn it at the lowest speeds possible. Recommended is 4x for CD and 1x for DVD. I've been through enough useless CD's because I was impatient.

Here are the site links:
[Linux Mint](http://www.linuxmint.com/)
[Puppy Linux](http://puppylinux.org/main/index.php?file=Overview%20and%20Getting%20Started.htm)What the hell are you talking about? Did you even read the OP?

---

### Post by bodhi.zazen on 2010-06-09
I think the crux of the issue, why does your client feel she is being attacked by hackers ? How are they accessing her system ? 

If you can answer this question we can probably do some good. It makes a big difference if she is running VNC or SSH or Apache or wireless cracking or a problem with physical access. You get the idea, the list goes on an on.

UFW does nothing to protect against internet privacy of Phishing issues for example.

Also in my experience, new users often assume any and every problem they are having is due to "viruses" or "hackers". Most often this is not the case and in general Linux is very secure.

So , I advise you do a little more foot work and try to understand the problem first. UFW, or any security tool really, does little good if you do not understand what problem you are trying to fix.

---

### Post by tinydancer88 on 2010-06-09
[[COLOR=#980101]**bodhi.zazen**[/COLOR]]("http://ubuntuforums.org/member.php?u=89054"): thanks for that advice.  I`ve been waiting for them to call back so that I could ask them more questions- specifically, what were the symptoms of the hacker attacks when they were running windows.  Unfortunately I just started this job and don`t have enough knowledge to ask the questions that I need to ask in a case like this, but I`m the only one here with linux knowledge, so they dumped this case on me.  Can you think of any specific questions that I should be looking for the answers to, and how I can help them find the answers?  I would be hugely indebted to you.

---

### Post by Paddy Landau on 2010-06-09
Linux comes with a strong built-in firewall.

ufw isn't a firewall; it's just a way to access Linux's firewall.

Unless you're running a server, you don't need to do anything with the firewall. It's already strong.

If you want to check, [GRC's Shield's Up!]("https://www.grc.com/x/ne.dll?bh0bkyd2") is a great place to check your firewall. When I checked last, Linux without any changes to the firewall scored 100%, better than Windows did with a reputable paid-for firewall with antivirus.

---

### Post by bodhi.zazen on 2010-06-09
> **tinydancer88 said:**
> [[COLOR=#980101]**bodhi.zazen**[/COLOR]]("http://ubuntuforums.org/member.php?u=89054"): thanks for that advice.  I`ve been waiting for them to call back so that I could ask them more questions- specifically, what were the symptoms of the hacker attacks when they were running windows.  Unfortunately I just started this job and don`t have enough knowledge to ask the questions that I need to ask in a case like this, but I`m the only one here with linux knowledge, so they dumped this case on me.  Can you think of any specific questions that I should be looking for the answers to, and how I can help them find the answers?  I would be hugely indebted to you.

No, just ask them for a more detailed description of the problem.

---

### Post by Paddy Landau on 2010-06-09
> **tinydancer88 said:**
> what else should I tell her about Ubuntu...
Here are three things that I can think of:

[LIST=1]
[*]Set her computer to install security updates automatically. System > Administration > Update Manager > Settings > Updates > Check for updates "Daily" > Install security updates without confirmation. You may want to ask her to run Update Manager manually anyway every week or so to install non-urgent updates.
[*]In Firefox, find the [WOT (Web Of Trust) add-on]("https://addons.mozilla.org/en-US/firefox/addon/3456/") and install it.
[*]Explain to her how to install and uninstall programs, i.e. do not download programs from the Internet but instead install and uninstall through Ubuntu Software Centre.
[/LIST]

---

### Post by The Cog on 2010-06-09
As others have said, you don't really need a firewall unless you install extra services (which I don't think you're planning to do). But if you want a firewall anyway, just install gufw and leave it at default settings.

Firefox add-on noscript is worth having. You'll have to show her how to use it of course. If you don't know yourself, it's worth finding out because it makes such a big difference to your browsing safety. Same probably goes for flashblock.

Teach her what phishing is - not to trust links that might send her to something that **looks** like her bank but isn't, and asks for her login details.

---

### Post by sydbat on 2010-06-09
> **The Cog said:**
> As others have said, you don't really need a firewall unless you install extra services (which I don't think you're planning to do). But if you want a firewall anyway, just install gufw and leave it at default settings.

Firefox add-on noscript is worth having. You'll have to show her how to use it of course. If you don't know yourself, it's worth finding out because it makes such a big difference to your browsing safety. Same probably goes for flashblock.

Teach her what phishing is - not to trust links that might send her to something that **looks** like her bank but isn't, and asks for her login details.This is what makes No Script so invaluable. Once you set it to Allow for the legitimate bank site, if someone tries to phish via email or spoof the actual bank site, no scripts will run.

---

### Post by sille777 on 2010-06-09
> **Paddy Landau said:**
> ....
If you want to check, [GRC's  Shield's Up!]("https://www.grc.com/x/ne.dll?bh0bkyd2") is a great place to check your firewall. When I checked last, Linux without any changes to the firewall scored 100%, better than Windows did with a reputable paid-for firewall with antivirus.

=D>

I love that site! [ GRC's Site]("http://www.grc.com") is Great for lots of information and checking those firewalls.  Got a lot of windows issues fixed there.

---

### Post by Paddy Landau on 2010-06-09
> **The Cog said:**
> ... just install gufw and leave it at default settings.

[LIST]
[*] gufw is a front-end to uwf.
[*] uwf is a front-end to Linux's built-in firewall.
[*] Therefore, installing gufw and leaving it at default settings is the same as doing nothing!
[/LIST]
   Actually, installing gufw is worse than not installing it, because the client may find it and make changes, leaving the system vulnerable!

As already stated, Linux's firewall is strong. There is no need to fiddle with it unless you are doing something "unusual".

---

### Post by bodhi.zazen on 2010-06-09
> **Paddy Landau said:**
> 
[LIST]
[*] gufw is a front-end to uwf.
[*] uwf is a front-end to Linux's built-in firewall.
[*] Therefore, installing gufw and leaving it at default settings is the same as doing nothing!
[/LIST]
   Actually, installing gufw is worse than not installing it, because the client may find it and make changes, leaving the system vulnerable!

As already stated, Linux's firewall is strong. There is no need to fiddle with it unless you are doing something "unusual".

GUFW is a front end for ufw

ufw is a front end for iptables

iptables is a front end for netfilter

:twisted: 

and the default settings are to allow everything. On a fresh install try :

```
sudo iptables -L -v
```

This is sufficient as with a default install there are no open ports, so there is nothing to firewall.

---

### Post by Paddy Landau on 2010-06-09
> **bodhi.zazen said:**
> ufw is a front end for iptables
iptables is a front end for netfilter
and the default settings are to allow everything.
:lol: Thanks for the correction!

---

### Post by bodhi.zazen on 2010-06-09
> **Paddy Landau said:**
> :lol: Thanks for the correction!

No problem, I noticed you were taking an interest in such things and thought you would find the information interesting.

When I tell that to my wife she gets this blank look ...

---

### Post by Paddy Landau on 2010-06-09
> **bodhi.zazen said:**
> When I tell that to my wife she gets this blank look ...
<Laughing> I'll have to try that too!

For completeness, if someone has meddled with the firewall settings, what's the easiest way to reset them to the default?

---

### Post by bodhi.zazen on 2010-06-09
> **Paddy Landau said:**
> <Laughing> I'll have to try that too!

For completeness, if someone has meddled with the firewall settings, what's the easiest way to reset them to the default?

Depends on the tool one used.

With iptables :

```
sudo iptables -F
sudo iptables -X
sudo iptables -t nat -F
sudo iptables -t nat -X
```Would do, although with most of what people do on these forums, iptables -F is sufficient.

If one used ufw, one would need to list and remove the rules 

```
sudo ufw status
sudo ufw delete allow 80/tcp 
...
```GUFW , just delete the user rules at a click of a mouse

and on ...

If you have insomnia, try :

[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

I just updated that page under the advice of a kind reader who took the time to give feedback, the page is targeted at people new to iptables.

I have a few pages on {g}ufw on my blog as well:

    [http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)
    [http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)
    [http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/](http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/)

Don't get me started on "ShieldsUp!" , lol

---

### Post by The Cog on 2010-06-10
> and the default settings are to allow everything
Oops! My mistake. You at least have to check the Enabled box.
> Don't get me started on "ShieldsUp!" , lol
Do that many people directly connect their PCs to the internet using line card or modems, rather than using routers? I don't think I know anyone who does that personally. Inquiring minds want to know.

Or is it just that no-one realises they are only scanning their router?

---

### Post by bodhi.zazen on 2010-06-10
> **The Cog said:**
> Oops! My mistake. You at least have to check the Enabled box.

Do that many people directly connect their PCs to the internet using line card or modems, rather than using routers? I don't think I know anyone who does that personally. Inquiring minds want to know.

Or is it just that no-one realises they are only scanning their router?

Those two things plus I do not like the terminology of a "stealth" port. I know what they mean by a stealth port, but I do not think most people who visit that site understand it.

As you point out, most people are behind a router, so then need to use local tools such as namp or zenmap or similar.

---

