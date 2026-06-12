---
title: "help with securing VMWare network"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by tappad on 2007-04-22
Hi everyone!

I have some pretty simple questions :)

Ok here is what i have:

* 1 server with 3 Network cards
* 1 Wireless network
* 1 Wired network
* 1 Internet connection

And i wish to use wmware to secure everything.

And here is how im thinking.

Use the server as router/DNS from the internet and route via 1 network card to the wireless network and the other to the Wired. These will be in seperate 'zones' where the wired network will be protected from the wireless (impossible to reach).
So far nothing to strange, i have been looking at IPCop, witch does this.

However, since i dont really want to use a single computer only as a firewall/dns i figured this could be done with vmware. That way i could also setup a LAMP server on the same pysical machine and connect it to my TV and also use it as a Media Center, using vmware machines. 

Now, the problem i have is securing the server it self. Im planning on running Ubuntu desktop edition on it. Mainly for the media center functions and vmware. The main ubuntuinstallation should only be accessed on the same network as the Wired computers. This gives a problem of making sure that all traffic on all cards passes through the Virtual Firewall in vmware.

Any thoughts anyone ?
Maybe someone is using a vmware firewall and have some usefull tips?

Best regards,
David Johansson

---

