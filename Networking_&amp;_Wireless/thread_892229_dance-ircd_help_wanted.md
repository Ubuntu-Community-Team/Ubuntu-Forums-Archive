---
title: "dance-ircd help wanted"
date: 2008-08-16
forum: Networking &amp; Wireless
---

### Post by NullHead on 2008-08-16
I'm attempting to run my own IRC server using dance IRCd. This sounds good and all, but it's allot harder than I first thought ... 

The server its self seem to be running and working just fine, but I seem to be missing NickServ and the other utilities and commands that are common to the popular Freenode.net. 

I seem to have gotten dance-services running with out error, but I seem to lack the functionality desired. 

Here is the question: 

Could somebody give me any pointers/guide links to aid my in my quest for IRC server happiness?

I'd sure appreciate any help anybody could give me! 

Thanks,

NullHead

---

### Post by usererror on 2008-11-07
Did you get this working at all?  I am in the same boat but with IRCD-HYBRID.

The NickServ is an additional download but i can't get it to install on my server because it doesn't recognize IRCD-HYBRID...

---

### Post by NullHead on 2008-11-07
> **usererror said:**
> Did you get this working at all?  I am in the same boat but with IRCD-HYBRID.

The NickServ is an additional download but i can't get it to install on my server because it doesn't recognize IRCD-HYBRID...

I just plain gave up ... Sorry to say. I also tried Hybrid IRC, but that wouldn't even let me accept connections from the internet; just me LAN. 

I have failed my quest of IRC server happiness :(

---

### Post by usererror on 2008-11-08
I have IRCD-HYBRID working.  I als could not connect the first time right after it installed.  I had to go into the ircd.conf file and change the server IP address.

By default it is set to 127.0.0.1 which would only allow the local connection you were experiencing.  Re-install the package and give it a shot!

What I need to figure out now is how to password protect channels somehow.

---

### Post by NullHead on 2008-11-19
Okay, I have hyperion installed and I can't get the channel bots working ... nickserv, chanserv etc ... 

Does anybody have any ideas about that?

---

