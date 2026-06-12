---
title: "[SOLVED] Cannot get Pidgin connect to yahoo account"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by Dani Filth on 2008-12-09
Hello people,

I'm having trouble connecting to my yahoo account using pidgin. I did search the forum for related threads, and this problem has nothing to do with the recent error from yahoo's main site.

The problem is, I'm living in the dorm, and lately the guy in charge of the dorm's network changed something in the security which is to prevent downloading of mp3, avi files as well as playing online game from the dorm. But it seems he somehow blocked the network traffic for pidgin as well so I cannot connect to my yahoo account using pidgin anymore. 
I said that because when I bring my laptop to a friend's house to use the Internet then pidgin has no problem connecting to my yahoo account. And when I get back to the dorm, I try to connect from a friend's computer running WinXP and Yahoo Messenger then it has no problem as well.

So, is there a way to overcome this problem, I'm so sick of using webmessenger.yahoo.com already.

Please help, thanks in advance :D

---

### Post by CoercibleGerm on 2008-12-09
I would play with the port forwarding settings in the network tab of the preferences menu and try to manually find a range that will get you connected. IIRC, Yahoo messenger uses port 5050 for messaging as a default... try something in that range.

---

### Post by Dani Filth on 2008-12-09
Thanks for the reply, I tried the port from 5000 to 5200 but it still didn't work :confused:

---

### Post by superprash2003 on 2008-12-09
do you get any specific error?? is it only with yahoo?? do you get something like "Error resolving scs.msg.yahoo.com . Name or service not known

---

### Post by Dani Filth on 2008-12-09
The error message for Yahoo account is :
> Could not establish a connection with the server:
Connection refused.

When I tried with IRC, I got the error message :
> Couldn't connect to host.

---

### Post by CoercibleGerm on 2008-12-09
> **Dani Filth said:**
> Thanks for the reply, I tried the port from 5000 to 5200 but it still didn't work :confused:

Hmm. See if you can get anything around port 80, it's used as an alternative to 5050 in Yahoo's program. Maybe expand your range as well. If that doesn't work I'd try to talk your administrator into setting up port forwarding for pidgin on the router. Sorry my first suggestion didn't help, but if this advice doesn't work we can at least eliminate port issues.

---

### Post by attlinux on 2009-06-19
** [Couldn't connect to yahoo messenger by using Pidgin]("http://attlinux.blogspot.com/2009/06/couldn-connect-to-yahoo-messenger-by.html") **

   This morning (19 Jun 2009), I couldn't connect to yahoo messenger server by using Pidgin in Ubuntu Jaunty 9.04. I used OpenDNS for my router.

I found a tweak on internet to fix this problem:

[http://forum.ubuntu-vn.org/viewtopic.php?f=61&t=1630&start=0](http://forum.ubuntu-vn.org/viewtopic.php?f=61&t=1630&start=0)

I've done those steps:

1. Open file /etc/hosts with gedit:

**$ sudo gedit /etc/hosts**

2. Add the following line to the end of hosts:

**66.163.181.184         scs.msg.yahoo.com**

[[IMG]http://3.bp.blogspot.com/_r-zutWro6T0/Sjsvht_35RI/AAAAAAAAABY/MRSbD6jAOtE/s320/Screenshot-hosts+%28-etc%29+-+gedit.jpg[/IMG]]("http://3.bp.blogspot.com/_r-zutWro6T0/Sjsvht_35RI/AAAAAAAAABY/MRSbD6jAOtE/s1600-h/Screenshot-hosts+%28-etc%29+-+gedit.jpg")
3. Save and Close

4. Restart Pidgin

OK.

Good luck!

---

### Post by jawahirak on 2009-06-19
[B]Thanks a Lott...
bt can u explain wt actually we do here to correct d problem..i mean wt wos actually d problem..!!??[/B]

---

### Post by kouakou on 2009-06-19
Thanks for the help....that worked...
But I would really like to know what happened cos I had the same problem on pidgin using portable apps...still don't have a clue as to how I will fix that one .....
all the same Thanks a bunch...

---

### Post by zeroseven0183 on 2009-06-20
Thank you for the workaround. It worked for me too and I'm online finally.

---

### Post by zeroseven0183 on 2009-06-20
> **kouakou said:**
> Thanks for the help....that worked...
But I would really like to know what happened cos I had the same problem on pidgin using portable apps...still don't have a clue as to how I will fix that one .....
all the same Thanks a bunch...

This might help you: [http://www.pidgin.im/support/]("http://www.pidgin.im/support/") or [Pidgin cannot connect to Yahoo!]("http://www.celticwolf.com/useful-information/faqs/26-pidgin-yahoo")

> Yahoo! appears to be upgrading their servers to a new version of their software.  This new version requires a new authentication method.  The latest version of Pidgin, 2.5.6, does not support this new authentication method.  The next version, 2.6.0, will, but it has not yet been released.

Just read along.

---

### Post by inhalm on 2009-06-25
1. Open file /etc/hosts with gedit:

**$ sudo gedit /etc/hosts**

2. Add the following line to the end of hosts:

**66.163.181.184         scs.msg.yahoo.com**

[[IMG]http://3.bp.blogspot.com/_r-zutWro6T0/Sjsvht_35RI/AAAAAAAAABY/MRSbD6jAOtE/s320/Screenshot-hosts+%28-etc%29+-+gedit.jpg[/IMG]]("http://3.bp.blogspot.com/_r-zutWro6T0/Sjsvht_35RI/AAAAAAAAABY/MRSbD6jAOtE/s1600-h/Screenshot-hosts+%28-etc%29+-+gedit.jpg")
3. Save and Close

4. Restart Pidgin

OK.


after i do this step i still have an error

Could not establish a connection with the server:

Connection refused

i ping **scs.msg.yahoo.com**

[IMG]http://fotobukit.net/images/croos/creenshot.png[/IMG]

the result still same so what should i do

---

### Post by binary00mind on 2009-06-25
[CENTER][/CENTER]There is another way to fix the Pidgin problem
.The fix is out there, but thus far did not show up on my Ubuntu updates.
And i hate to go to Windows to get on Yahoo..
To solve this, One might add the Pidgin directly to repositories, and get the fix right the way, by simply reloading Synaptic Manager. And the new version ( with the updated Yahoo authentication lib´s ) will show up with the upstream.
It takes 15 seconds to do this...just go to this page and follow the instructions [http://pidgin.im/download/ubuntu](http://pidgin.im/download/ubuntu)
Now this is only for emergency..I would advice to remove this repo, after this one time update, because it might conflict with other dependencies 
Which Pidgin Developers might not know.

---

