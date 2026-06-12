---
title: "sharing folders between ubuntu and mac"
date: 2007-12-10
forum: Networking &amp; Wireless
---

### Post by zorkerz on 2007-12-10
Ok so here is my situation. There are 5 of us with 5 computers. Three macs running various versions of OS X and 2 running Ubuntu 7.10. All connected to the same open wireless network. I would like each computer to have a shared folder that is visible from all others.

**First what protocol is the best to use?** SAMBA seems to be the most common but seeing as we don't have any windows machines I would like to avoid it unless it is really the best option. 

A password protecting each shared folder is ok but I would like to be able to set each one to the same thing for simplicity. I would also like to make all 5 usernames/logins the same if those are required.

I know there is a alot of info already out there already and maybe I just need a link somewhere but I have done alot of searching around and still have not been satisfied with what im able to find.

thanks

---

### Post by jonallport on 2007-12-11
As you're all using a UNIX (OS X is freeBSD after all) why not investigate NFS?

---

### Post by zorkerz on 2007-12-11
I have heard that setting up nfs is not so simple. Im not worried about doing it myself I can find a walkthrough of some sort I worried about my mac friends whose computer skills/motivation is much less. The best way I am thinking right now would be to be able to use bonjour so that all the mac people can share the exact same way they normally do.

I don't yet know if this is possible.
thanks

---

### Post by jonallport on 2007-12-12
NFS is VERY easy to setup provided there is a consistent way to identify the client (there's a config file for exported folders and one for mounts!).
i.e. Permissions can be set at the machine level (I assume you all know/trust each other) so provided there's a consistent identification (same IP address or DNS entry) there should be nothing to worry about.

I'll fire up a test box and make sure I'm not talking out of my rear, but my experience of sharing files between linux, Solaris and IRIX is that NFS was just so simple and effective.

---

### Post by jonallport on 2007-12-14
UPDATE:

Was interested by 'Bonjour', seems to be some sort of proprietary implimentation of UPnP.

Anyhoo... found this:

 [http://pl-systems-server.plsys.co.uk/weblog/paul/Server/?permalink=zeroconf.html&smm=y]("http://pl-systems-server.plsys.co.uk/weblog/paul/Server/?permalink=zeroconf.html&smm=y")

---

### Post by jonallport on 2007-12-14
Update update:

It's not UPnP, it's zeroconf - hoorah!

see [zeroconf.sourceforge.net]("http://zeroconf.sourceforge.net") also various modules/apps using zeroconf are in the repositories, mDNS for example.

---

