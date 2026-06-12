---
title: "Strange problem"
date: 2011-01-16
forum: New to Ubuntu
---

### Post by lbhymshr on 2011-01-16
All right.
So i started off with Ubuntu 9.10. It worked great for some time, but after a few days mozilla couldnt open sites that did not end in .com. Put in other words, any site that eded as .org (wikipedia) or .net or any but .com wasn't accessible (message was : firefox couldn't connect to the site). A few days later to this Ubuntu wasn't able to get updates. And so i thought there was some problem with 9.10 and i traveled back to windows.

So Ubuntu 10.04 came. I installed it. The above problem repeated. Then came 10.10 and the problem repeated it self after a few days. Funny thing is for about a week i get no such issues, this all starts after i have used ubuntu for about a week. and it has persisted in all the versions. Windows platform doesn't show this problem. So is my PC UBUNTU resistant or somethin'??

Please help guys!!

---

### Post by TeoBigusGeekus on 2011-01-16
Have you tried with a different browser (opera, chromium, midori, etc.)?

---

### Post by pbpersson on 2011-01-16
Can you get to [http://www.fsf.org](http://www.fsf.org)   ?

If not, what happens if you ping it?

If that does not work, what happens if you do an nslookup?

Here is a sample session I did here to illustrate what I mean:

```
phil@phil-ubuntu-desktop:~$ ping www.fsf.org
PING fsf.org (140.186.70.131) 56(84) bytes of data.
64 bytes from www.fsf.org (140.186.70.131): icmp_seq=1 ttl=44 time=100 ms
64 bytes from www.fsf.org (140.186.70.131): icmp_seq=2 ttl=44 time=90.6 ms
64 bytes from www.fsf.org (140.186.70.131): icmp_seq=3 ttl=44 time=120 ms
64 bytes from www.fsf.org (140.186.70.131): icmp_seq=4 ttl=44 time=107 ms
64 bytes from www.fsf.org (140.186.70.131): icmp_seq=5 ttl=44 time=95.3 ms
^Z
[1]+  Stopped                 ping www.fsf.org
phil@phil-ubuntu-desktop:~$ nslookup fsf.org
Server:		174.23.183.164
Address:	174.23.183.164#13

Non-authoritative answer:
Name:	fsf.org
Address: 140.186.70.131

phil@phil-ubuntu-desktop:~$
```

---

### Post by erilidon on 2011-01-16
Sounds like a failing NIC

---

### Post by pgibson on 2011-01-16
I'd like to add my voice to lbhymshr's, because I've been having a not dissimilar problem lately.

lbhymshr, have you tried other browsers?  I've never used chromium before today, but today it's the only one that has gotten me far enough along that I can load ubuntuforums, log-in, and post.  Every other browser simply will not finish loading the pages.

For mr problem is on both my computers upstairs: a dell dimension 4100 running xfce 10.10, and my less ancient dell Inspiron 2200 running Ubuntu 9.10.  Both are connecting wirelessly to the router downstairs in my living room, but show typical signal strength.  Indeed, the problem seems to be more or less specific to browsers because my synaptic and "ubuntu software center" both seem to be solidly normal, as does apt-get.

It seems to be somewhat site dependent too ... ubuntuforums has been all but inaccessible, but, for example the debian home page was a snap.  Today it's been so bad that I've taken to just loading one browser after another from the repositories. (seamonkey, arora, midori, conqeror, reconk, epiphany, and galleon.  Dillo seemed to do fine, but when I logged in, simply took me back to the login page.  Elinks was simply way beyond my inherently feeble nature and I couldn't get any information entered into any boxes.  (I even completely uninstalled firefox and the .mozilla file in order to get around this ... no avail.)

Does anyone know if there is a config setting that all these browsers except chromium might be sharing, or where we might look for other problems?

PS. lbhymsh, if possible, you might want to change the subject to something a bit more descriptive, like "

---

### Post by pgibson on 2011-01-16
pbpersson,

For what it's worth, I'm able to get to fsf.org easily on both firefox and chromium.  (Can't get chromium for my 9.10 machine, it appears :)).  I've mimicked your code and pinged and nslookup'd the site on both machines too, if that output would be helpful?

Astoundingly, after countless minutes "loading", on my 9.10 machine, instead of logging me in to ubuntuforums, Firefox has instead opened a notice that says
> You have chosen to open 
login.php 
which is a : PHP file 
from: http//ubuntuforums.org 
What would you like Firefox to do with this file? etc.  Bit unusual, that. ;)

[Addendum:  When I posted this reply, I received a notice also saying something about .php.: 
> vBulletin Message
Invalid Thread specified. If you followed a valid link, please notify the administrator, though the above reply clearly went through.]

---

### Post by pgibson on 2011-01-16
Rolling back the kernel from ...22 to ...19 in grub seems to have provided a workaround, too (on my 9.10 machine), though desktop effects cannot be enabled.  I'll have to try that turning them off with kernel ...22.

Also, I think I'd like to put all this under a different subject heading.  I thought I was adding a voice to a similar problem, but now it feels like I'm at a meeting that was rescheduled and no one put a note on the door at the gathering place. :(

---

### Post by lbhymshr on 2011-01-16
@TeoBigusGeekus: yups i tried opera in all the cases, same result...haven't tried chromium though

@ erilidon: Sudn't a failing NIC have the same issue when on windows platform?

@pgibson: Wow even I used to get a lot of messages like yours
"You have chosen to open 
login.php 
which is a : PHP file 
from: http//facebook.com 
What would you like Firefox to do with this file? 			 		(Save/Cancel)". And if by subject you mean the title, I don't know what to call it for this seems genuinely strange.

@pbpersson : no as i said i can't get to any site that doesn't end in .com (m making this post from windows, sorry). 

so as for specs, i have a self assembled desktop with 2.86Ghz dual core, ASUS mother board, 3 GB worth of RAM etc. don't know if that helps. 
Somewhere some thread mentions a problem quite similar to mine and guys over there say it might be an IPv6 issue. 

See but the thing is everythngs very smooth for about a week and by everythng i mean everythng. no problem whatsoever. all this starts after about a week all of a sudden and den degrades over time. is it problem related to updates I get? No because i had this problem on every version 9.10 onwards. Is it a failing NIC, i think not for if i install a fresh copy of the OS everythngs works fine again.

---

### Post by Clever_Username on 2011-01-16
Is there any kind of software firewall you were using?

---

### Post by pgibson on 2011-01-17
> **lbhymshr said:**
> @TeoBigusGeekus: yups i tried opera in all the cases, same result...haven't tried chromium though

I'm updating my 9.10 box to 10.04 so I can use chromium on it and get online (chromium's not available from the repos till 10.04).
 
I had a mental hiccup, so I didn't finish the "subject line" comment.  It is strange, but most of the "how to get help on this forum" sort of things I've read usually say that the more specific the subject is, the more likely it's going to be noticed by someone who has the knowledge to help.  Maybe something like "Browsers stopped working," or some such.

---

