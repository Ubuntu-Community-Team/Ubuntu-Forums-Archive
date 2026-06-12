---
title: "Question about vnc"
date: 2014-06-03
forum: Networking &amp; Wireless
---

### Post by edszr on 2014-06-03
Hi all,

I'm running ubuntu 14.04 LTS.  Is there a default vnc package that comes pre-loaded on ubuntu?  I've used vnc in the past and over the weekend I decided to play around with realvnc.  I loaded it up but I couldn't get it to do what I wanted so I removed it.  I guess when I removed it, I hoped my original vnc would still be there, but my vncviewer command returns:

No command 'vncviewer' found, did you mean:
 Command 'jvncviewer' from package 'vnc-java' (multiverse)
 Command 'gvncviewer' from package 'gvncviewer' (universe)
vncviewer: command not found

I never remember installing vnc in the first place (before messing with realvnc), that's why I'm wondering about a default package.  I'd like to get back to where I was before the realvnc debacle.

thanks in advance for any help.

Ed

---

### Post by steeldriver on 2014-06-03
Default VNC viewing is provided by the remmina remote desktop client

[http://packages.ubuntu.com/trusty/remmina](http://packages.ubuntu.com/trusty/remmina)

---

### Post by slickymaster on 2014-06-03
Moved to the **Networking & Wireless** sub-forum.

---

### Post by edszr on 2014-06-03
Thanks @[**[COLOR=#C61919][B]steeldriver**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1627500").  It looks like I do have remmina installed, but command line vncviewer still isn't found...I wonder what the heck I was using for command line vnc....

---

### Post by edszr on 2014-06-03
Maybe the question I should be asking is ... how do I get vnc installed in such a way that I can use the -via option.  So from a command line, I used to be able to type:

vncviewer -via machine1 machine2:6

and that would connect me to a vnc session on machine2.

Thanks for any help.

Ed

---

