---
title: "Wanting to set up remote ssh enable switch"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by Beacon11 on 2008-05-01
Hello all. There's something I want to do, but I don't know how to do it. In fact, I don't even know what I'd search for to figure out how... so if someone just wants to post a link or to to this forum, or that tutorial, I'd love it. Let me explain what I want to do:

I recently got an old Dell Inspiron 600m with a bad hard drive. I replaced the hard drive, and am going to give it to my little brothers as a present. It's decent enough to play a few games that we enjoy playing together, and I have internet (wired and wireless) working fine in Kubuntu Hardy (8.04). However, here's the deal: my dad doesn't want them browsing the internet whenever they want, from wherever they want (one's 11, the other is 14– who knows what he thinks they'll be doing...) so, here's what I thought. What if I set up a script to deny all connections except on say, one port, X (the sudo password is set up to be root, so the boys don't know it– this solution works that way). So, they can actually connect to the router, but no packets can go anywhere. This way, while I'm at college and they want to play a game, I can have them connect to the router, and then I can SSH in on port X, and unblock the rest of the ports.

Is this kind of idea possible? I figured it'd have something to do with network/interfaces, so here's the current contents of that file (it's basically empty... what does that mean?):

```

auto lo
iface lo inet loopback

```

This is basically a fresh Kubuntu installation. Any ideas are welcome! This would just be a really handy solution versus just completely locking down the internet– that would require either me giving them the password to unlock it, or me being there. I'm only there sometimes on break, and I'm certainly not giving them the root password! Thanks a lot :) .

---

### Post by kevdog on 2008-05-01
You could use a portknocker utility that after giving the appropriate port knock -- would automatically open up ports that you had previously instructed the program.  Issue another port knock sequence --- the ports will be closed.  There are other solutions, however I believe this one is quite elegant.

---

### Post by Beacon11 on 2008-05-01
Wow, I never would have thought of that! VERY nice ;) . However, that's a firewall thing, is it not? Firwalls in linux I honestly have never touched.

I found [http://www.zeroflux.org/cgi-bin/cvstrac.cgi/knock/wiki](http://www.zeroflux.org/cgi-bin/cvstrac.cgi/knock/wiki)

In that website, it sounds just like a key, looking for the right sequence to unlock. Really nice. However, they say "When the server detects a specific sequence of port-hits, it runs a command defined in its configuration file." I'm gonna need help with that command. I honestly don't know where to start! Anyone got a knockd tutorial up their sleeve somewhere? Thanks for that awesome suggestion Kev :) .

---

### Post by Beacon11 on 2008-05-01
Also, a quick note: as of right now, I can't even issue

```

sudo ifdown eth0

```

I think it's because my network/interfaces is empty. Is this the case? Or does having this file basically empty just mean my network is being managed by KNetworkManager? I mean... if I can't even issue ifdown, how can I have control over my ports?

P.S. I embellished a little on Kev's suggestion and found CryptKnock, which sounds a little less sniffable. [http://cryptknock.sourceforge.net/](http://cryptknock.sourceforge.net/)
Still stuck on the firewall bit, though...

---

### Post by kevdog on 2008-05-01
There are a few port knocker utilities that can be used.  The one Im trying to implement is the following:
[http://cipherdyne.org/fwknop/](http://cipherdyne.org/fwknop/)

Ive written the author and have gotten some feedback.  I think I know how to set it up, however honestly I haven't done it yet (just learned about it about 1 month ago).  I haven't even upgraded to Hardy yet -- just too dang busy at work.  This knocking program incorporates gpg keys for encryption -- so if your interest is in security -- like mine -- I really like this solution.  

There are other programs however as suggested on this page:
[http://www.portknocking.org/view/implementations](http://www.portknocking.org/view/implementations)

Sorry however I haven't really tried any of these implementations.  The classic implementation was knockd:
[http://www.zeroflux.org/cgi-bin/cvstrac.cgi/knock/wiki](http://www.zeroflux.org/cgi-bin/cvstrac.cgi/knock/wiki)

Many of the implementations are older (not that that is a bad thing, however getting some support for these implementations may be tough).  fwknop (again shameless plug but never used), is currently maintained, so the author of the project is available for questions if you run into any problems.

Hopefully I'll beat you to the setup.  If you beat me however, it would make a great HOW-TO in the Tutorial Section.

---

### Post by Beacon11 on 2008-05-01
Oh huh... reading that CryptKnock page, it sounds like it just uses iptables. If I'm correct, this basically means no action needed from me, right? Install and *bam* it works? I'm gonna experiment a little, and if it works, I'm gonna install Hamachi to run at boot, so that I can still unlock it even from behind a router (which is will be), without having to worry about saying "Okay mom, I need to unlock the little boys' computer... so to do this, open a console. No mom, it's in that little menu on the bottom. Okay, now do..." I guess I could setup port-forwarding with a static IP, but I don't want to. Besides, Hamachi will work wherever the computer is. I'll update this when I've got results.

---

### Post by Beacon11 on 2008-05-01
Oh... we totally posted at the same time... I hit "submit" and there were two posts! I'm hoping to get to this today, and I agree- whoever gets this working needs to put up the tutorial!

---

### Post by kevdog on 2008-05-01
Yes, one of the features of the port knocker utilties is that they can modify the iptables (basically open or close ports on the firewall).  However they are capable or more, such as running an executable on the remote machine.  How do you the thing the classic cdoor hacker program was used?  cdoor installed on client machine through virus (or whatever was used).  client remained dormant until knock sequence was received --- cdoor clients (thousands of infected machines) -- released a massive DNS attack on victim server to shut it down.  Quite historical if you think about it.

In your case and my case, we simply want it to modify the iptables to open up incoming/outgoing ports.  If you are smart, you can also add another knock sequence that would close the ports you had previously opened.

---

### Post by Beacon11 on 2008-05-01
Yeah, nice :) . Reading that CryptKnock README, it looks like you supply an "open" password and a "close" password, and that's it. Basically...
Client sends PKey to Server.
Server sends PKey to Client.
Client sends encrypted "open" password to Server.
Server unlocks
*check mark*

For my purposes at least, I think this better than fwknop, because fwknop uses OS fingerprinting and a bunch of *crazy stuff*... and it just sounds like more than I need.

---

### Post by Beacon11 on 2008-05-01
Ugh... bad news for CryptKnock. It compiled fine (after installing a few libraries) but when I run it I get a huge *** stack smashing detected ***.... heh... I emailed him a second ago, we'll see if he replies. If he doesn't within a relatively short amount of time, fwknop seems to be in active development and I might be able to get it working. I'll be in touch.

---

### Post by Beacon11 on 2008-05-02
Hey Kev. Port Knocking is usually implemented to open a certain port to a certain IP address, right? Do you know of any way I can have the knock completely open up the computer, to all IP addresses? I mean... the purpose for this is to play games together, but if we play a game with a server including other players... it just won't work if all that's unblocked is MY IP. What do you think, will I have to rewrite the program for this? Or if I go the really simple route of knockd, which just executes a script on the correct knock (I think), I could probably write a script to unlock the iptables myself. I've never done this, but I figure it can be done. It sounds like the other ones directly manipulate iptables... so maybe I'll have to just go the simple route of knockd, and see what I can get out of it.

---

### Post by Beacon11 on 2008-05-02
Crap... now I'm reading that directly manipulating iptables majorly screws NetworkManager:
[https://help.ubuntu.com/community/IptablesHowTo#head-928fdd039d2c99bd1a98a40c3c5747fb6c581aee](https://help.ubuntu.com/community/IptablesHowTo#head-928fdd039d2c99bd1a98a40c3c5747fb6c581aee)
Is this still the case with 8.04? I don't want to mess up my installation... *sigh*. Anyone have any input here?

---

