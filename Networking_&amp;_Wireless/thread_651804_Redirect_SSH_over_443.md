---
title: "Redirect SSH over 443"
date: 2007-12-28
forum: Networking &amp; Wireless
---

### Post by thecapuchin on 2007-12-28
I don't know if this is something that anyone here has run into before, but I've recently had to install a new wireless router and have been running into issues with something that had previously been really easy to configure.

Here's the situation, when I'm at work, the only ports that I have access outbound are ports 80 and 443.  Now, what I've done in the past is use the following command to connect to a machine at home 

ssh -p 443 -XC [email]username@domain.com[/email] 

Now, my old router (a D-Link DI-624) died recently and I've just replaced it with a Linksys WRT54G.  The D-Link had the ability to accept traffic on port 443 and dump it inside to a host on port 22.  Port redirection was really easily setup, but for some reason, with the Linksys, I can't for the life of me figure out how to do this.

Does anyone had any suggestions?  And please, if you need more info, or if I've been unclear somehow, let me know.

Thanks in advance all.

---

### Post by mightyteegar on 2007-12-28
The WRT54G doesn't support port redirection.  However, you could always run your SSH daemon on port 443.  You could also try using a third-party firmware.

---

### Post by thecapuchin on 2007-12-28
Thanks for the information.  I'll move over to 443 on the server too.

Much obliged.  Sucks that the WRT54G doesn't do it more easily.

---

### Post by eastpole on 2008-03-10
> **mightyteegar said:**
> The WRT54G doesn't support port redirection. ...  You could also try using a third-party firmware.

Yes, just to confirm, DD-WRT v23 sp2 (the mini build) on the WRT54GL  (L for linux) is fine with this and I do it for exactly the same reasons. If the micro build (suitable for WRT54G models designed to run Wind River OS instead of Linux) I'd love to know that for sure. 

eastpole

---

### Post by kevdog on 2008-03-10
Yes just flash the router firmware with dd-wrt to add a ton of new features.  Depending on the version number of your WRT54G you can either use the mini (micro), standard, or VPN/VOIP build.  All versions must be first flashed with the micro addition.  Depending on the router version (since different versions have more RAM -- which is the limitation), you may then flash with the enhanced standard or VPN/VOIP packages (if you want).

---

