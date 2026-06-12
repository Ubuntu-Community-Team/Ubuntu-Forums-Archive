---
title: "Gnome proxy settings not global anymore"
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by polluxx on 2008-05-18
Hi.

I normally use a SOCKS proxy for all internet connections via an SSH tunnel. 
Now, until recently, one of the great things in Hardy was, that once I set the correct port and DNS name in the Gnome "Network Proxy Settings", i.e. I set them globally within Gnome, all the other apps seem to "pick them up" correctly. That is, I don't explicitly need to change the Network connection settings in Firefox, nor do I need to change anything to make both aptitude and evolution work.
Recently, setting a global SOCKS proxy stopped working. Firefox still picks up the correct settings (if set to "Use system proxy settings" in the Connection Settings), however wget, aptitude, evolution and basically any other application accessing the network stopped working.
Has anyone experienced something similar. Maybe I am missing something very obvious? 
I know that it did work before in Hardy, however I don't recall changing anything in particular with respect to global proxy settings. In particular I never had to change anything in apt.conf (that was the great thing in Hardy over previous versions, for once the global proxy settings really seemed to be global).
Thanks for any help!

---

### Post by polluxx on 2008-05-26
Bump.

After one week of research on the net, I'm still at a loss.

Again, global SOCKS proxy settings **did work** before in Hardy for evolution, aptitude and so on.
For some reason this stopped, e.g. evolution isn't able to retrieve mails through the SOCKS proxy anymore. The proxy settings are correctly passed on to Firefox only.

Am I the only one who has that problem?

---

### Post by bingnet on 2008-08-14
I found this thread while experiencing the same issue with eeebuntu 8.04

---

### Post by Dougga on 2009-09-16
I'm seeing something similar when configuring Evolution to access Gmail.  I have the machine set to use the network proxy but find that my firewall is now blocking packets on port 80 with a destination of google ip's. 

Also, Evolution has network proxy configuration which is set correctly so no port 80 traffic should be coming from this machine at all (browser or evolution).

Something's amiss.

---

