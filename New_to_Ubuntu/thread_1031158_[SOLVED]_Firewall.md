---
title: "[SOLVED] Firewall"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by Jeyaganeshdj on 2009-01-05
Hi Friends,


  I have installed  Ubuntu in one of my drive with 40gb capacity. The other 3 partitions each around 35 gb are windows drive. I have antivirus and firewall installed for windows.

  But for Ubuntu I have not installed the ufw firewall. Will there be a problem if anybody can hack into my system and access my drives(both windows and Linux)? Will there be any problems like spy keyloggers in my Linux environment if i am not installing firewall?

---

### Post by shifty_powers on 2009-01-05
you still have a firewall, iptables, which incidentally is oe of the most secure around.

any software you install is just a gui for iptables, so don't worry...

ubuntu is far, far harder to hack than either windows or osx...

---

### Post by efexD on 2009-01-05
I doubt you have to worry about viruses..

---

### Post by mcduck on 2009-01-05
> **shifty_powers said:**
> you still have a firewall, iptables, which incidentally is oe of the most secure around.

any software you install is just a gui for iptables, so don't worry...

ubuntu is far, far harder to hack than either windows or osx...

Well, UFW is just an interface for iptables just like most Linux firewalls are, but I suppose you are now forgetting the fact that iptables alone doesn't work as firewall. You need to give it some rules to work with before it does anything, simply having iptables as part of Linux doesn't make you secure.

So no, it's wrong to say that Ubuntu would have a firewall out-of-the-box. It doesn't. It has all the tools & features needed to *create* a firewall.

But of course that doesn't make much of a difference in default Ubuntu setup, since the default install doesn't have any services running that would respond to incoming connections. And that means that a firewall isn't even needed for anything.

---

### Post by Jeyaganeshdj on 2009-01-05
does that mean i will get virus in linux. I heard linux is immune to viruses... is that not true? Is there a way i can authnticate the incoming connections with a gui? Is any such firewall with gui available for linux? If so which firewall is best? Thanks.

---

### Post by theozzlives on 2009-01-05
I use the firewall in my router, but I figure that the very few viruses in Linux isn't gonna matter much and a hacker serious enough to hack into Linux is in for a disappointment on my system. I don't have anything of value on my machines.

---

### Post by Teabicky on 2009-01-05
Try these links for Uncomplicated Firewall...

community/Uncomplicated_Firewall_ufw

[https://help.ubuntu.com/8.04/serverg.../firewall.html](https://help.ubuntu.com/8.04/serverg.../firewall.html)

They helped me.

---

### Post by mcduck on 2009-01-05
> **Jeyaganeshdj said:**
> does that mean i will get virus in linux. I heard linux is immune to viruses... is that not true? Is there a way i can authnticate the incoming connections with a gui? Is any such firewall with gui available for linux? If so which firewall is best? Thanks.

No, it doesn't. Like I said, Ubuntu is by default secure even without a firewall. And to make things even better, there are hardly any Linux viruses around, and even those that are are more proof-of-concepts and nothing that would really get into your machine. Also there isn't any spyware/malware for Linux either. (Linux is not immune to viruses, but creating a Linux virus is very hard and making one that would work with all different Linux seems to be impossible so virus writers seem to prefer the easy life of creating Windows viruses :D)

So there really is no need to do anything, the default setup is at least as secure as fully updated Windows install with best available firewall- antivirus and antispyware apps running.

If you really want to run a software firewall, I recommend [Gufw]("http://gufw.tuxfamily.org/index.html"). Very easy & simple and works nice in Ubuntu.

---

