---
title: "Trouble connecting to multiple Windows Domains"
date: 2007-07-28
forum: Networking &amp; Wireless
---

### Post by luvr on 2007-07-28
I'm using Ubuntu 7.04 on a Dell Latitude D820 laptop, in a corporate environment.
I run Windows XP SP2 as a client Operating System, via VMware Workstation 6.

The corporate network has multiple Active Directory domains, which I will refer to as *"DOMAIN1,"* *"DOMAIN2,"* etc. in this post.

My Windows XP SP2 system (let's call it *"VMWKST1"*) belongs to *DOMAIN1,* as does my user account (say, *"XPUSER1"*).

Now, from my Ubuntu system, I can connect to the Windows shares on the Windows XP client: I select *"Places* -> *"Connect to Server..."* I select *"Windows share"* as the service type, I type *"VMWKST1"* (i.e., the name of my XP system) for the server name, type the share name, specify my user name (*"XPUSER1"*), and the domain *DOMAIN1.* Then when I want to open or browse the folder, the system will ask me for my password, and it will display the folder contents just fine (provided, of course, that I type the correct password).

Similarly, I can connect to a share on any other machine that sits in *DOMAIN1* without any problems.

**HOWEVER,** connecting to a server that sits in a *DIFFERENT* domain (e.g., *"DOMAIN2,"*) does **NOT** work: When I try to browse or open the folder, the system will **not** ask me for my password, but it will simply display a window saying: ***"The folder contents could not be displayed.** Sorry, couldn't display all the contents of <sharename>."*

Also, connecting with a user account from a different domain (e.g., *"DOMAIN2,"*), even to a server that belongs to *DOMAIN1,* doesn't work either, and gives me the same error.

So, it looks like my Ubuntu system cannot reach any objects that sit in any domain other than *DOMAIN1.* My Windows XP (i.e., my client OS) connects to all servers, using any authorised user account, just fine.

Would anyone happen to have any idea what could be going on here? Any ideas what I could do about it?

---

