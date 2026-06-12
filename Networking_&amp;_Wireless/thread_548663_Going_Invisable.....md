---
title: "Going Invisable...."
date: 2007-09-11
forum: Networking &amp; Wireless
---

### Post by toasty_ghosty on 2007-09-11
Hello,
  I am trying to connect to my windows network here at work and I just noticed something and I wonder if there is a way to fix it. I am visible on the network. Is there a way to make me invisible? Right now if someone clicks on me you can access my pc. It's limited, but you can do it none the less.

---

### Post by prabbit237 on 2007-09-11
Yeah, the best way of making yourself invisible is to disconnect from the network and quit trying to sneak into your employer's system.

---

### Post by toasty_ghosty on 2007-09-11
Thats not it at all. We've had people just looking through and messing with things and I just wanted to know how I could prevent that from happening. I have no intention to "hack".

---

### Post by az on 2007-09-11
The only way that Ubuntu listens to the network is if you installed packages that do so.  Have you installed samba or NFS (for file sharing with windows?)  If so, you would need to reconfigure Samba or outright remove it (or remove NFS).

---

### Post by toasty_ghosty on 2007-09-11
i've recently uninstalled Samba, and I was thinking of uninstalling samba-common, but it said it affected the ubuntu desktop. Should I uninstall that anyway?

---

### Post by az on 2007-09-12
> **toasty_ghosty said:**
> i've recently uninstalled Samba, and I was thinking of uninstalling samba-common, but it said it affected the ubuntu desktop. Should I uninstall that anyway?

No.  I believe that you are able to see other shares, but they cannot see you, unless you are running the Samba Daemon.

Just like ssh.  The ssh-client is installed by default, so that you can ssh into another machine, but nothing is listening unless you install the ssh-server.  By default, nothing listens to the network unless you install it.

---

