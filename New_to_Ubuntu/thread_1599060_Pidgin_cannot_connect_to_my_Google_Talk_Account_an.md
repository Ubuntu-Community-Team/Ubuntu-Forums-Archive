---
title: "Pidgin cannot connect to my Google Talk Account anymore."
date: 2010-10-17
forum: New to Ubuntu
---

### Post by DesiArnez6 on 2010-10-17
Now when I start up Pidgin, It seems that Google talk is the only one that doesn't connect. When I start it up, I get the following error at the bottom:

Protocol error, code 267: Account is locked and client does not support lockout.

Please help me if you can.

-Desi

---

### Post by SpockVulcan on 2010-10-17
If pidgin has a option to use SSL in settings for that account, enable it. That worked for me.

---

### Post by DesiArnez6 on 2010-10-18
I didn't see an option for SSL :(

---

### Post by alldunn on 2010-10-19
I am having a problem with google talk not connecting as well.  I get the message "not authorized".  I have deleted the account and re-added.  This is occurring on all four of my Ubuntu machines (1 - 10.04.1, 3 - 10.10).  Perhaps it is an issue on Goolge's side?  It is working within Gmail though.

---

### Post by SuaSwe on 2010-10-19
Is it working in other IM's, e.g. Empathy, Bitlbee, GTalk etc?

---

### Post by alldunn on 2010-10-19
> **SuaSwe said:**
> Is it working in other IM's, e.g. Empathy, Bitlbee, GTalk etc?

I just checked with a coworker that is running Windows and his Gtalk client is working.

---

### Post by SuaSwe on 2010-10-19
To clarify: is your Gmail account working on other clients aside from Pidgin? :) To be fair though, the question was mainly directed at the OP as s/he suggests only having tried Pidgin, and only on one machine.

Might still be worth trying another client in your case also, alldunn, such as Empathy, maybe? Should already be installed on Maverick.

---

### Post by alldunn on 2010-10-19
Understood.  I just tried it with Empathy on a 10.10 machine and receive "Network error" when trying to connect.  I tried it with SSL enabled and disabled.

---

### Post by SuaSwe on 2010-10-19
That's starting to sound like a Gmail error in that case, I think. My account was a bit dodgy the other day as well, logging on on Bitlbee.

What settings are you using in Pidgin? These work for me:

> 
*Basic*
Protocol: XMPP
Username: user.name
Domain: gmail.com
Resource: <left blank>
Password: ********
Local alias: <left blank>
Only 'remember password' ticked on this page

*Advanced*
Require SSL/TLS: ticked
Force old SSL: unticked
Allow plaintext auth over unencrypted streams: unticked
Connect port: 5222
Connect server: <left blank>
File transfer proxies: proxy.eu.jabber.org
BOSH URL: <left blank>
Custom smileys: ticked

*Proxy*
Proxy type: Use GNOME Proxy Settings


---

### Post by SuaSwe on 2010-10-19
I'm guessing the "Use GNOME Proxy Settings" are those found under System > Preferences > Network Proxy, which on my laptop is configured as 'Direct internet connection' with no manual specs.

---

### Post by alldunn on 2010-10-19
> **SuaSwe said:**
> I'm guessing the "Use GNOME Proxy Settings" are those found under System > Preferences > Network Proxy, which on my laptop is configured as 'Direct internet connection' with no manual specs.

My settings are the exact same.  It doesn't work on my machines here at work or at home.  Very odd.  Hopefully it will correct itself soon.:(

---

### Post by siddtharth on 2010-10-19
I was not able to connect to gtalk too. But turns out that because I had disable the networking in gnome network manager as I have it set up in /etc/network/interfaces, it was not working.
I'm connected to internet, but Pidgin thinks it is not connected to internet. I used command line to start piding in debug mode 
[pidgin -d] and I can see there it complain about cannot connect to internet. But as soon as I clicked on enable networking in network manager it was able to connect.

---

### Post by alldunn on 2010-10-19
This is what I am receiving when running pidgin -d

```
(19:30:27) jabber: Recv (ssl)(16): </stream:stream>
(19:30:27) connection: Connection error on 0xa40eb90 (reason: 0 description: Server closed the connection)
(19:30:27) account: Disconnecting account username@gmail.com/ (0x9de45c8)
(19:30:27) connection: Disconnecting connection 0xa40eb90

```

---

### Post by alldunn on 2010-10-19
OK, so I just thought to check on my wife's account and her's is working fine under a different system account on the same computer.  So obviously it is something with my account, but gtalk works fine from my Android phone.  Just not any other Ubuntu machine.  It's almost like my account has been locked, but it hasn't.  This is very frustrating and I am not too sure what else to do.

---

### Post by siddtharth on 2010-10-19
What's the domain you are connecting to ?
can you try googlemail.com instead of gmail.com which is the default.

---

### Post by SuaSwe on 2010-10-20
Silly little thing but:

[http://www.google.com/support/talk/bin/answer.py?hl=en&answer=25752](http://www.google.com/support/talk/bin/answer.py?hl=en&answer=25752)

Apparently unlocks the account in some situations?

---

### Post by alldunn on 2010-10-20
Thanks for the suggestions, but none of these worked either.  I am going to try a few other drastic things and will report back if I figure anything out.

---

### Post by alldunn on 2010-10-21
> **SuaSwe said:**
> Silly little thing but:

[http://www.google.com/support/talk/bin/answer.py?hl=en&answer=25752](http://www.google.com/support/talk/bin/answer.py?hl=en&answer=25752)

Apparently unlocks the account in some situations?

OK got it working.  I closed all of my browsers (some of which has been open for weeks) on my work desktop and followed these steps.  I am not sure if closing the browsers did it or this unlock procedure did.  The only thing I can come up with is the gmail checker firefox extension I have installed somehow locked my account.  Weird issue indeed and I am glad it is resolved.  Thanks for all the help!

---

