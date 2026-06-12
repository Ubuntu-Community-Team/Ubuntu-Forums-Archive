---
title: "How can i monitor transfer data for wget"
date: 2013-12-01
forum: Networking &amp; Wireless
---

### Post by jonhnw on 2013-12-01
Hello, i have a question, how can i monitoring transfer data for wget with command iptables?  I must useing wgets pid? Or how?    
Please, i need some working example.
I have Ubuntu 8.10. 
Thank you

---

### Post by Lars Noodén on 2013-12-01
Maybe you could launch wget under its own unique group, but the regular user, then track that group's activities with *--gid-owner*  See the manual page for iptables-extensions for the details on that option.  Otherwise, it would be possible to do the same with a unique user but that would be more difficult to manage than just setting group for wget.

---

### Post by sanderj on 2013-12-01
> **jonhnw said:**
> Hello, i have a question, how can i monitoring transfer data for wget with command iptables?  I must useing wgets pid? Or how?    
Please, i need some working example.
I have Ubuntu 8.10. 


Ubuntu 8.10? Really? Why? Supported ended in 2010; see [http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Table_of_versions](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Table_of_versions)

Anyway: I would use something like 

```
sudo tcpflow -i any -C -e port 80
```

HTH

---

### Post by jonhnw on 2013-12-06
How can i doing this with iptables?
thank you

---

### Post by Lars Noodén on 2013-12-10
The group part you can do with sudo if you modify sudoers.  First add a group that will be unique to this use of wget.

```

sudo groupadd wgetter

```

Then edit sudoers to allow you to use that group.

```

sudo EDITOR=nano visudo

```

You should have a line like this 

```

%johnw ALL=(johnw:wgetter) /usr/bin/wget

```

Then when you launch wget, it would be like this:

```
 
 sudo -g wgetter wget http://...

```

That will give you something unique (a group) for iptables to use.  Then you'll want to work out something with "--gid-owner wgetter" in iptables.  Probably a separate chain would do it.  Then -vL should show the bytes.  

Maybe there is a better way, but that the first one I can think of.

---

