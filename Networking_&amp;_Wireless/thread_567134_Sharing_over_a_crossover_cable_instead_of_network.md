---
title: "Sharing over a crossover cable instead of network"
date: 2007-10-04
forum: Networking &amp; Wireless
---

### Post by Draddy on 2007-10-04
Hello, 

So I was using my Ubuntu computer to as a network server at my old house....

so now i've moved and my ubuntu computer no longer has access to the internet. 

So I bought a crossover cable, and I cannot figure out how to share files that way...

is there a tutorial for that? (I love the "similar threads" btw.....)

I want to be able to share files on ubuntu machine with my MacBook Pro running OS X 10.4.10 ..


thanks!

---

### Post by soul_rebel on 2007-10-04
you could get by by assigning both machines an IP address. Then you can use any file-sharing programs you know, eg ftp, samba, etc... depending on what you want to achieve and what the mac can do.

to temporarily assign a "local" ip the command is
```
sudo ifconfig eth0 192.168.1.1
```
then set 192.168.1.2 on the second machine (i don't know how on mac os)

I hope I was helpful

---

### Post by Draddy on 2007-10-04
Thanks! 

I did that, but before hand, it would show up as a local computer, and I could click on it, connect, and use it like an external harddrive....

Is there a way to be able to use it that way?

---

### Post by soul_rebel on 2007-10-04
i think you did that using the SMB network file sharing protocol, which is the one used by Windows. Since now you are on a mac, things are different and I can't help you there. But I am pretty sure that it is possible to "mount" SMB shares on the mac too.

---

### Post by Draddy on 2007-10-04
> **soul_rebel said:**
> i think you did that using the SMB network file sharing protocol, which is the one used by Windows. Since now you are on a mac, things are different and I can't help you there. But I am pretty sure that it is possible to "mount" SMB shares on the mac too.

Yup! good guess.. I am using SMB and it worked great going to my mac at home.

The only difference is now I am using a cross-over cable instead of a wireless network to connect to it.... is there something I can just switch over so it is visible to an individual computer instead of workgroup?

---

### Post by soul_rebel on 2007-10-05
"visible" it already is... It's more a matter of looking the right way. I don't know enough about the mac to help you.

---

