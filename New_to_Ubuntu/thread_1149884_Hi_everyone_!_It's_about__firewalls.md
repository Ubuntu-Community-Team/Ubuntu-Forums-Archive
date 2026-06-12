---
title: "Hi everyone ! It's about  firewalls"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by aroha on 2009-05-05
I want to first thank everyone as you guys have been very friendly and helpful, I am totally "newbie" at this OS.
I am running Ubuntu 9.04 on my notebook...
I have always heard that this OS does not require an "antivirus" installed, but setting up a "firewall" is highly recommended.
Is this true ?
How can that be done ?

Do we have an "UFW firewall" pre-installed already ?
How to make it work properly if not an expert at all ?

Thank you very much :)
Aroha !

---

### Post by spcwingo on 2009-05-05
You could give gufw a shot.  It's nothing more than a gui for ufw.  It can be grabbed here:

[http://gufw.tuxfamily.org/index.html]("http://gufw.tuxfamily.org/index.html")

---

### Post by dabang on 2009-05-05
This is what I do:

```
sudo ufw enable
sudo ufw default DENY
```

This will enable ufw firewall (installed by default) and set it's default policy to "deny". I don't know the details, but it sounds good ;-). Maybe someone else can shed some light?

---

### Post by Mortus Pryde on 2009-05-05
By default from what I hear you are pretty secure. All ports are closed and can not be accessed on the outside. You will only really benefit from a firewall if you are running applications that "Listen" for attempts to connect, say a server or peer to peer application, and you want to limit who and what can access it. Alternately you can use the firewall to limit outgoing connections to block websites, or attempts to connect to other servers.

One example is say you are running peer to peer file sharing on a network, but you want only people on your network to have access to connect to your computers peer to peer program. You can then set your firewall to block all IP addresses not origionating from your network.

Another is if you have Ubuntu on your childs computer and you want to prevent them from connecting out to certain websites, or linking to the previous example you don't want them connecting to peer to peer file shares outside your network. You can configure the firewall to block that website and also to only allow that computer to connect to peer to peer file shares with IP addresses origionating on your network.

---

