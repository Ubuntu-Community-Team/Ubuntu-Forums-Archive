---
title: "Accessing my grandma's computer remotely"
date: 2007-10-06
forum: Networking &amp; Wireless
---

### Post by BlahBlahX on 2007-10-06
My grandma has a new PC, but she used to have old powerbook running MacOS 8.6. She wants to have a simple, easy computer experience, that is fool proof. 

Im setting up a stripped down linux mint (ubuntu variant) install for her, but if there are problems, I want to be able to access her computer remotely from my house (I don't live near her) in case she has problems.

I want to be able to get into the x server of her computer from my mac at home (if needed I can do it through a linux vm, but that seems impractical.)

How can I set this up? 

PS: She doesn't know much about computers, so I have to be able to install the remote access software an reliably connect to her computer when need be.

PSS: Security for the remote connection would be important, but I don't need any fancy stuff.

---

### Post by mikeize on 2007-10-07
Looking for the same sort of thing here.  All of the remote access solutions I've found so far, are way more complex than I'd like-- and all I really need is file access!  (which is less than what you need, presumably).  I hope there's a simple solution for you, post back if you find one in the meantime.

-mike

---

### Post by Lambert on 2007-10-07
See this page

[http://wiki.linuxquestions.org/wiki/Remote_desktop_connection](http://wiki.linuxquestions.org/wiki/Remote_desktop_connection)

---

### Post by callan79 on 2007-10-07
> **BlahBlahX said:**
> Im setting up a stripped down linux mint (ubuntu variant) install for her, but if there are problems, I want to be able to access her computer remotely from my house (I don't live near her) in case she has problems.

Hi There,

I'm not sure what would specifically suit your circumstances, however I've set up several of my clients/friends with Ubuntu so far and they are all working well. All my clients use ADSL Broadband, with an ADSL Router.

For remote access, I enable Remote Desktop on Ubuntu (on the System >> Preferences menu), and I also install SSH so I have command line access. I use the Remote Desktop if they need help with the GUI, and I use SSH if I just need to get in and move some files around or edit configuration files.

To allow access from outside, I forward ports 5900 (Remote Desktop) and 22 (SSH) on their ADSL Router.

For security, some routers enable you to specify rules for port forwarding and only allow this from known IP Addresses. If this is not possible, you can limit access to SSH using the the file ( /etc/hosts.deny ).

Let me know if you think this is what you need, and I'll be happy to help further.

Cheers
Callan

---

