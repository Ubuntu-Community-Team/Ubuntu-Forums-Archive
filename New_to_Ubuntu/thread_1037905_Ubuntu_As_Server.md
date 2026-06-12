---
title: "Ubuntu As Server"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by akkad on 2009-01-12
why all my searches say that ubuntu is not suitable as server? where debian is !!! as long as it is debian based then why it is not? 

in fact am looking for a solid linux server that i can depend on, am happy with my ubuntu experience as desktop user so am looking forward to use ubuntu server because i dont want to utilize my time on learn new distro, instead i want to focus on my development that will be deployed over a server.

debian is a good selection as server for big corporates, ubuntu server is debian + user friendly(in someway loosing performance), then can not i configure ubuntu server by eliminating some useless features and performance eaters so it becomes like debian or at least to the debian level ???

i'll be thankful if the replies will be from the experience background more over than the personal opinion.

---

### Post by achase79 on 2009-01-12
Debian has a longer release cycle making security better by filling all the gaps with updates.  Ubuntu is Debian based but has a shorter release cycle, meaning that all the security holes may not have been all caught in one release before the next is out.

---

### Post by dmizer on 2009-01-12
That's perhaps one reason, though if you use an [LTS](https://wiki.ubuntu.com/LTS) release like Dapper or Hardy, then you get 5 years of security updates on the server version. Most people complain that Ubuntu server is too heavy, or that it comes with too much unneeded overhead. Though I find that it performs quite satisfactorily. I'm happy with it more because I am familiar with Ubuntu's quirks.

Ultimately, it probably depends on what you intend to do as your server. Any Linux system will perform quite well as a file server for example.

---

### Post by akkad on 2009-01-12
i can see that you focused on the security, is this the difference between debian and ubuntu ? what about over all performance and stability ?

---

### Post by hyper_ch on 2009-01-12
well, you get only long tested packages in debian stable. Webservers don't (usually) need to run the latest bleeding edge software. Stability is more important there. Due to long testing before it's marked as stable and also long release cycles make it very good for servers.

Ubuntu on the other end is a bit more up to date. Every 24 months you'll get a new LTS version. LTS doesn't (necessarily) mean more stable but longer support. There is also a lot of testing done for LTS releases but it does not reach up to debian (IMHO).

Summary:
- Debian has long release cycles and intense testing - but older packages
- Ubuntu LTS has a 5 year release cycle and also good testing - not as good as Debian IMHO - but it features more up-to-date software

---

### Post by stevoo on 2009-01-12
well i have used both. 

I have ubuntu on my production machine and on my laptop home , plus i am running a server edition home. 
I could have made it run lighter, but i wanted to have a gui there just in case. 

I do a lot of things there , from acting as a file server, holding my svn, having an apache server, running azureus, and some other trivial stuff. 

It has been up and running perfectly from the first day. That was 25 days ago and no crashes no memory leaks, nothing nada. Up to now offcourse :) 

So it all comes down to how you will use it.

---

### Post by hyper_ch on 2009-01-12
why not use rtorrent instead of azureus... and a server should be gui-less ;)

---

### Post by binbash on 2009-01-12
for a heavy load server ubuntu is way heavy , also release cycles are killing ubuntu server.That is why debian is better

---

### Post by stevoo on 2009-01-12
i need firefox, as i run some tests. 

I could do it headless, but the pain in doing that is great. And i would rather have a look when it is happening :)

---

### Post by jespdj on 2009-01-12
> **binbash said:**
> for a heavy load server ubuntu is way heavy , ...
In my opinion, statements like this one are based on hearsay and not on facts. Do you have any references to backup this claim?

> **akkad said:**
> why all my searches say that ubuntu is not suitable as server? where debian is !!! as long as it is debian based then why it is not?
Ubuntu is certainly suited as a server operating system; high-profile websites such as [Wikipedia are using Ubuntu](http://arstechnica.com/news.ars/post/20081009-wikipedia-adopts-ubuntu-for-its-server-infrastructure.html).

---

### Post by dmizer on 2009-01-12
> **binbash said:**
> also release cycles are killing ubuntu server.That is why debian is better

Ubuntu LTS has a 5 year release cycle. Are you suggesting that that's not long enough?

According to Wiki: [http://en.wikipedia.org/wiki/Debian#Releases](http://en.wikipedia.org/wiki/Debian#Releases) the longest life so far of a debian distribution was Sarge for 3 years. Am I missing something here?

---

