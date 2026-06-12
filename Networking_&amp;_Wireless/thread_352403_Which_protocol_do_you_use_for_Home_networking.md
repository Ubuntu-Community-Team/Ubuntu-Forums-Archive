---
title: "Which protocol do you use for Home networking?"
date: 2007-02-03
forum: Networking &amp; Wireless
---

### Post by jingo811 on 2007-02-03
I'm trying to figure out the simplest way to share files in my home network, yet still be able to control that only certain trusted PCs can access my share without having to go trough too much technical FAQs.
So I followed hermans tutorial on [OpenSSH]("http://users.bigpond.net.au/hermanzone/p11.htm") and understood the basic stuff rather quick but then I want my NIC to be in DHCP always not STATIC ip, and SSH didn't support Windows PCs accessing Linux folders unless I installed some 3rd party program.  Which I'm too lazy to do.
  So I'm thinking of using the other networking solutions instead that's not as powerful as SSH.  Like NFS and Samba but I'm not sure which one suits my needs best?
[COLOR="Red"]
My needs:[/COLOR]
1.)  Simple installation.
2.) Easy managed security.
3.) easy Folder sharing between Windows and Linux machines.

---

### Post by kidders on 2007-02-03
> **jingo811 said:**
> SSH didn't support Windows PCs accessing Linux folders unless I installed some 3rd party program.If you need Windows compatibility, samba is your only realistic option, imo.

---

### Post by quark_77 on 2007-02-03
I have investigated a similar problem as I'm trying to persuade my parents to use Linux... but I can't quite get them to leave Windows... Anyway, here are the options:

Use SAMBA and share folders using server message block (SMB). These will appear as \\Computer\share as any standard windows share.

Use NFS and install Microsoft Windows Services for Unix on each of you windows machines ([http://www.microsoft.com/technet/interopmigration/unix/sfu/default.mspx](http://www.microsoft.com/technet/interopmigration/unix/sfu/default.mspx)) and then map NFS shares from Ubuntu to network drives on Windows.

FTP: read/write is unsecure unless you use an SSL tunnel i.e. FTPS using another FTP program (doesn't integrate well into windows itself). FTP unsecured is unsupported, if you have a wired network this might be easy...

OpenSSH is probably the best option in terms of security; however, you'd have to install PuTTY on Windows, plus you have to use it from the command line & it exports the shell, not just file transfer. OK for admins, completely loses people just wanting to save a word document.

One I don't think you suggested: WebDAV. You'll have to investigate this one. All I know about it is it works over http/https, can be set up using Apache, can SSL. WebDAV [http://en.wikipedia.org/wiki/WebDAV](http://en.wikipedia.org/wiki/WebDAV) is known under windows as "Web Folders". This might be the best option.

I think SAMBA is by far the most straightforward for direct integration into Windows...

Hope this helps, have fun!

Quark_77

---

### Post by kidders on 2007-02-03
> One I don't think you suggested: WebDAVWebDAV is a nice, cross-platform suggestion. Windows has a *very* flaky implementation of it though. :-(

---

### Post by jingo811 on 2007-02-03
Tnx for the tips ppl, I think this made my decision easier.  Samba it is.
Another thing previously I tried to install NFS and Samba stuff by terminal and Synaptic.  Since the Ubuntu Guide didn't say much about how to control and secure those protocols I didn't go all the way so now there are these files sleeping dorment.
Are they posing as a security threat by just being in my puter or should I try to completely uninstall all NFS files?

> I'm trying to persuade my parents to use Linux... but I can't quite get them to leave Windows...Hehe I tried this also but things got ugly when the NIC got hickups and connected/disconnected randomly as if possessed by the Excorcist.  It seems like MOBOs with 2 built-in NIC ports confuses Ubuntu if you don't configure it manually.
  However things got solved but the momentum is against me since my first switcharoo attempt.  Now I'm waiting for the perfect moment and then I'm gonna give them the 
**"No need for defragmenting"** defense.

---

