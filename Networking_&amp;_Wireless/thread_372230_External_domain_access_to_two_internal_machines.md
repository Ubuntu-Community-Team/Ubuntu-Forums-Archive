---
title: "External domain access to two internal machines"
date: 2007-02-27
forum: Networking &amp; Wireless
---

### Post by quiller on 2007-02-27
I have two "servers" set up, one running Windows XP and one running Ubuntu Edgy. The Ubuntu machine is primarily a fileserver and MythTV backend, and as such it also runs MythWeb. I want to get to MythWeb (and ampache, and vnc/rdp, and blah blah blah), but I also want the same type of services to the Windows machine (primarily, ftp and vnc/rdp). I'm familiar with the tools (Webmin, cPanel, etc) that I'm using, but I don't know how to set the one domain (pointing to my public IP address at home) to differentiate to two different machines.

Any help would be great, and of course links or suggestions to guides, etc. would be great, too.

---

### Post by Floppyjoe on 2007-02-28
This would probably be done with the router.  If you have lets say two web servers at the same static IP, you could use different ports for the different web sites you are running.
For Example:
Ubuntulover.com would be directed to server #1 from port 80 the http port to whatever port on server #1.

Windowshater.org:81 would be directed to server #2 from port 81 and to whatever port you wanted on server #2.

I'm not sure how that would work for the other applications you were referring to though.
I am also not sure about SSL with two servers at the same IP.

---

### Post by quiller on 2007-02-28
I guess I should have been more specific: I'm quite familiar with DNS and how it works, but it seems (at least, I've found nothing to disprove this theory) that DNS doesn't understand or handle ports. From within the web server structure, that's not a problem, since I could use mod_rewrite or several other options to point domain1.com to IP:81 (or whatever port).

I'm pretty convinced what I want to do is just not worth the effort, at least not externally. I'm going to get a new, internal router to handle all my port forwarding, etc. I still don't know how to point multiple services to different computers, at least not within the domain-without-port-number direction. That's the real hold-up, since I can already do domain.com:### and get access, but I don't want to use port numbers by necessity... unless I have no other choice, that is.

---

