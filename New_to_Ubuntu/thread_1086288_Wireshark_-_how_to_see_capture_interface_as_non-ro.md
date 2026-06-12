---
title: "Wireshark - how to see capture interface as non-root?"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by amylase on 2009-03-03
Hi everyone,

I am doing an internet protocol subject at university. I'm playing with Wireshark (previously known as Ethereal) at home. I basically went through Synaptic and installed everything that contained the word Wireshark (including -dev). The analyzer is up and running now. The problem I have is this:

If I start the analyzer as a normal user (not root), the analyzer does not list any capture interfaces. (In otherwords, as non-root I have a analyzer that does not analyse. It can open up saved captures from tutorials which is good but I'd like the analyser to work as well).
On the other hand if I start the analyzer as root, I see all the interfaces to play with.

I am new to Linux and do not want to do things as root. **How do I get Wireshark to work (showing me all the capture interfaces) as a normal (non-root) user?**

Thanks very much.

---

### Post by Nxion on 2009-03-04
> **amylase said:**
> Hi everyone,

I am doing an internet protocol subject at university. I'm playing with Wireshark (previously known as Ethereal) at home. I basically went through Synaptic and installed everything that contained the word Wireshark (including -dev). The analyzer is up and running now. The problem I have is this:

If I start the analyzer as a normal user (not root), the analyzer does not list any capture interfaces. (In otherwords, as non-root I have a analyzer that does not analyse. It can open up saved captures from tutorials which is good but I'd like the analyser to work as well).
On the other hand if I start the analyzer as root, I see all the interfaces to play with.

I am new to Linux and do not want to do things as root. **How do I get Wireshark to work (showing me all the capture interfaces) as a normal (non-root) user?**

Thanks very much.

There really is no way to do that. wireshark is required to have root to have access to the NIC to capture packets but to read previous captures just use wireshark with out root.

EDIT:

I take that back, Check this out:

[http://wiki.wireshark.org/Security#head-ac69042aeeb98cdaed2ec2ff1bd2c983fa03cffd]("http://wiki.wireshark.org/Security#head-ac69042aeeb98cdaed2ec2ff1bd2c983fa03cffd")

---

### Post by amylase on 2009-03-07
> **Nxion said:**
> 
I take that back, Check this out:

[http://wiki.wireshark.org/Security#head-ac69042aeeb98cdaed2ec2ff1bd2c983fa03cffd]("http://wiki.wireshark.org/Security#head-ac69042aeeb98cdaed2ec2ff1bd2c983fa03cffd")

Fabulous. Thanks Nxion.

---

### Post by Nxion on 2009-03-09
No problem, dont forget to make the thread as solved :)

---

### Post by willjcroz on 2009-08-05
Another way (possible since kernel version 2.6.26) is to use capabilities...

```
sudo apt-get install libcap2-bin

setcap cap_net_raw=+ep /usr/bin/dumpcap
```

(credit due here: [COLOR="Blue"][http://www.wensley.org.uk/info](http://www.wensley.org.uk/info)[/COLOR] )

I was over the moon when I found out this was possible! Why is this kind of thing not enabled by default in Ubuntu?

---

### Post by fduppa on 2010-02-19
this has made my day =o)

---

### Post by ekidmose on 2012-09-12
> **willjcroz said:**
> Another way (possible since kernel version 2.6.26) is to use capabilities...

```
sudo apt-get install libcap2-bin

setcap cap_net_raw=+ep /usr/bin/dumpcap
```(credit due here: [COLOR=Blue][http://www.wensley.org.uk/info](http://www.wensley.org.uk/info)[/COLOR] )

I was over the moon when I found out this was possible! Why is this kind of thing not enabled by default in Ubuntu?

Did the trick on Linux Mint 13 Cinnamon 32bit! 
libcap2-bin was already installed(probably with wireshark, I guess..)
So I only had to run: 
```
sudo setcap cap_net_raw=+ep /usr/bin/dumpcap
```

Thanks a bunch! :D

---

### Post by overdrank on 2012-09-12
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

