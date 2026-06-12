---
title: "Wireless works except at school..?"
date: 2008-06-13
forum: Networking &amp; Wireless
---

### Post by Jarmungie on 2008-06-13
Hi guys, great forum! I am new to Ubuntu and have found a lot of help here already.

I finally had to register and stop lurking because I am having a problem I couldn't find referenced anywhere else. I am using a wireless connection with hardy heron on my inspiron 6000 and it is working fine in most places. It works great at home (WEP encrypted), my girlfriend's house (also WEP) and my neighbor's unsecured network. However, at school we have an unsecured network and I can not connect. At first I thought I just wasn't close enough, so I went up and tried right outside the Librarian's office (where the router is located) and still I couldn't connect. The network is visible and when I connect it appears to get halfway there (one of the bulbs lights up) but it doesn't connect and doesn't tell me why. 

I have the intel 2200 wireless card with the ipw2200 driver. Again, school is the only place it doesn't work, everywhere else it works great. Does anyone have any ideas what may be causing this?

I doubt I can get physical access to the router but I am an IT major so I am going to find out more specifics about the wireless set up. If anyone has any ideas on what to try in the mean time I would appreciate replies. I have already tried the wireless trouble shooting tips on ubuntu.com

Thanks!

-Jarmungie

---

### Post by pytheas22 on 2008-06-13
What happens if you try to connect at school using Windows?  Do you have to log in or anything or does it just connect?  Also, if the router filters MAC addresses to decide who can have a connection (as my university did), are you sure that your wireless card is registered?  If your laptop is dual boot, can you connect using Windows?

---

### Post by MyR on 2008-06-14
> **Jarmungie said:**
> ... and my neighbor's unsecured network. .... 
nice.

Perhaps your school's IT personnel would be best able to help you.  Try to find out if anyone using Linux can connect.  I suspect the problem is on their end.

peace

---

### Post by Jarmungie on 2008-06-14
I currently do not have a dual boot set up on my laptop because I have xp on my desktop ( although I am falling in love with ubuntu and will probably be setting up a dual boot on that). Actually, the whole reason I ended up installing ubuntu in the first place is because xp was giving me  a hard time and I just got fed up with it. I'm happy it worked out that way, though...

So anyway, I can not try connecting with xp but I know that the network is not secured or encrypted in anyway and it is not necessary to log in or anything. I know some schools will have an unsecure network but you will have to log in through cisco or some other program to actually get online - this is not the case here. It should be an open network.

I think I will have to fire off an e-mail to the IT guys and see if they have any idea why I can't get on. If anyone else has any ideas though please post, otherwise I will let you know how it works out.

BTW, I don't typically use up my neighbor's internet but I wanted to see if, for some strange reason, I wasn't able to get onto open networks or something like that - and also to make sure that most other hotspots would be available to me. I will let you know what happens and thanks for the replies.

-j

---

### Post by pytheas22 on 2008-06-14
If they don't filter connections or anything as far as you know, then I guess that getting in touch with the school's IT people is the only solution.  I don't know of any way that the school's router could know which operating system you're using when you try to connect and deny you an IP address based on that, so I doubt the problem has to do with the fact that you're running Linux.  The only other things I can think of is that possibly the school's router uses a frequency that your card doesn't support (not likely), or it's Network Manager's fault.  You could try using a different wireless manager like [wicd]("http://wicd.sourceforge.net") to rule out NM, or connect from the command line, e.g.:
```

sudo iwconfig INTERFACE-NAME mode managed channel CHANNEL-NUMBER essid NETWORK-NAME
dhclient INTERFACE-NAME
```

---

### Post by Jarmungie on 2008-06-17
Well, I haven't made much progress yet. I talked to the IT guy but all he said was that they aren't allowed to do any work on student computers so I guess unless I have any specific questions they won't be much help. However, when I went into manual configuration in network manager and put in the school's wireless ssid and then connected, it seemed to connect! The icon showed the blue network bars and iwconfig showed that I was connected to the right network but when I tried to open firefox, check my mail, or pidgin, nothing. Close but no cigar.
:confused:
So I'm not sure where to go from here other than to just keep tooling around with network manager and see if I have any success. Another thought I had was to try setting up NDISWrapper and trying to connect..is there any reason to suspect this might help or work in some way? Linux set up the appropriate ipw2200 driver out of the box so I'm not sure why I think this might work, but maybe its worth a try..? Any and all ideas are appreciated!

-J

---

### Post by syko21 on 2008-06-17
You said it appeared to connect when you did it manually. Perhaps it is a proxy issue then? I know my school uses a proxy and I have to set it through system -> preferences -> network proxy. That's the only way it'll work.

---

### Post by Jarmungie on 2008-06-18
Thanks for that, I will inquire on thursday and find out if they use a proxy. All I would need to configure that is the proxy IP and port, correct? Is it tricky to set up the network proxy? I am new to ubuntu ;) but I am a quick learner. 

-j

---

### Post by pytheas22 on 2008-06-18
> I talked to the IT guy but all he said was that they aren't allowed to do any work on student computers

Point out that you're not asking him to do any work on your computer; you just need information on how the network works and if there's any special configuration required to connect.  In my experience, most IT support people stop wanting to talk to you when you mention Linux because they know nothing about it, but if you make it clear that you're not trying to make him support Linux, but just get the information necessary for you to help yourself, he shouldn't have any reason not to give it to you.  On the other hand, if there is anyone at your school who knows Linux (staff or another student who has dealt with the wireless issue), try to get in touch with them.

> The icon showed the blue network bars and iwconfig showed that I was connected to the right network but when I tried to open firefox, check my mail, or pidgin, nothing. Close but no cigar.

First of all, any idea why it appeared to connect that time but in the past has failed outright?  Did you do anything differently before trying to connect that last time?

Second, if you had an IP address (did you check?) and appeared connected but just couldn't access the web, it could be a DNS problem.  The easiest way to check is put an IP address into the Firefox address bar instead of a name--e.g. 64.233.167.99 should bring you to google.com.  If you're able to connect by plugging in the IP, it's almost surely a DNS problem, which is easy to fix.

Otherwise, you could install Wireshark (in repositories) and use it to figure out where the packets are going.  It's useful if you're trying to discover why you appear connected but can't access the Internet, because you can find out where the packets are dying.
> 
Is it tricky to set up the network proxy?

If the proxy is your problem, I think you can set up everything easily using the GUI at System>Administration>Network.  But I'm sceptical that a proxy server is the issue, because if it were, Windows users would probably also have to enter special information to be able to connect.  But as far as you know, they just connect without an issue.  But I could be wrong.

---

### Post by Fr0z3n.0n3 on 2008-06-18
I once had a very similar problem with a school network. Blue bars in the tray icon, but Firefox, etc couldn't connect to the internet. As a workaround (why it worked I am not sure, being largely unfamiliar with the intricacies of networking) I used a proxy.

Try saving a list of proxy IP-port pairs on your laptop while you're at home and plugging them in to Firefox (don't set the system proxy, we're trying keep as many variables constant as possible).

It is by no means a solution, but it may help while the real problem can be discerned.

---

