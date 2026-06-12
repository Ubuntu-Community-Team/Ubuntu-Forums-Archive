---
title: "Citrix web client connection problem on Hardy x86"
date: 2008-08-04
forum: Networking &amp; Wireless
---

### Post by ahbart on 2008-08-04
I have problems with Citrix linux client (10.6) on Ubuntu hardy x86. 
It worked in the past with other version of Ubuntu and it worked a while on Hardy, but suddenly stopped working. And I do not know what the reason is. The quote from below is from another archived post from a while ago. But the problem has not been solved for me and some other people.
source: [link]("http://ubuntu-utah.ubuntuforums.org/showthread.php?t=376735&page=10")

Is there anyone who can help me/us with this?


>  
 Re: Using Citrix Client 10.0 - help, anyone have this working
Quote:
Originally Posted by mkasun View Post
I have tried to get the new Citrix client working and I can connect to the server at work but when I try to launch an application I get a window that says "Citrix Presentation Server" and the tile bar has
Connected to server ; 40; STACD4C......

after awhile it times out and a dialog box comes saying
Network or dialup problems are preventing communications with the server.
An attempt to automatically restore the connection will begin after a delay to let the network recover.

If the problem persists, contact your network administrator.
Hello Mkasun and others,
I have exactly the same problem. last week it worked great, but now it suddenly stopped working with the above messages.
Is there a solution for this?
Bart


---

### Post by brimlar on 2008-11-22
Are you connecting through a Citrix Access Gateway?

I've noticed this problem only occurs in this situation.  If I connect through the normal web interface, this problem doesn't present itself.

I seem to recall seeing something on the Citrix forums where they said a patch has to be applied to the Access Gateway in order to resolve this issue with the "Unix client" (which is what this client is, their *nix client) -- but I can't seem to find that page now, despite looking.

I'm also looking for a fix.

---

### Post by ahbart on 2008-11-22
No I never managed to configure the access gateway unix client. I always use the web interface with citrix/ica plugin. I did this in the past too and back then it worked for me. So it is the web interface that is giving me trouble here.

---

