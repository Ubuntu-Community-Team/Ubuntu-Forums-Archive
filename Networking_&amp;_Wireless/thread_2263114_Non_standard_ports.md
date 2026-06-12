---
title: "Non standard ports"
date: 2015-01-29
forum: Networking &amp; Wireless
---

### Post by Juan_Perez on 2015-01-29
Hi !

I list the ports open in a server with Netstat -taupen. Most of them are well known ([http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers](http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers)). However, there are a few  (36842,36844,36936,49723,49718,45986,41926,46295) which seem to be non standard. The program description is mostly java, but that is not very descriptive for a newbie like me...


[IMG]http://i.imgur.com/rPjuOgJ.png[/IMG]


Do you have any idea what these ports are used for ? Is it dangerous to have them open ?

Thanks !

---

### Post by Lars Noodén on 2015-01-29
netstat lists the process ids.  You can use [ps](http://manpages.ubuntu.com/manpages/trusty/en/man1/ps.1posix.html) to look up the full descriptions of individual java processes

```

 ps w --pid 21510 

```

That will tell you which JAR is being used and maybe give you an idea of which application it is.

---

### Post by Juan_Perez on 2015-01-29
That does the trick,
thanks !!!

---

