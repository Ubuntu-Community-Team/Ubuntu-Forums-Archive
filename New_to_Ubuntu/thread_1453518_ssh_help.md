---
title: "ssh help"
date: 2010-04-13
forum: New to Ubuntu
---

### Post by Stord on 2010-04-13
I would like to set up a remote desktop so i can access my windows 7 computer from my ubuntu computer. I would eventually like to do this using freenx, but first i have to attempt to establish an ssh connection.

I installed freeSSHd on my windows 7 computer and the server is running. I created a user named user and allowed it to do ssh. Now, im not sure what to do on the ubuntu side.

I have tried 
ssh -l user [EMAIL="Xtra-PC@xx.x.xx.xxx"]Xtra-PC@xx.x.xx.xxx[/EMAIL] where the xx thing is the windows 7 IPV4 address. The connection times out. Basically, i have no clue of which number im supposed to use. I assume the xtra-pc is supposed to be the username of my computer, and the xx is the ipv4 address. Ive also tried the default gateway and the dns server address and those i get a connection refused on port 22.

So how am i supposed to use this command? Thanks :)

Edit: Oh, and im connecting to a network on a college campus.

---

### Post by sydbat on 2010-04-13
> **Stord said:**
> I would like to set up a remote desktop so i can access my windows 7 computer from my ubuntu computer. I would eventually like to do this using freenx, but first i have to attempt to establish an ssh connection.

I installed freeSSHd on my windows 7 computer and the server is running. I created a user named user and allowed it to do ssh. Now, im not sure what to do on the ubuntu side.

I have tried 
ssh -l user [EMAIL="Xtra-PC@xx.x.xx.xxx"]Xtra-PC@xx.x.xx.xxx[/EMAIL] where the xx thing is the windows 7 IPV4 address. The connection times out. Basically, i have no clue of which number im supposed to use. I assume the xtra-pc is supposed to be the username of my computer, and the xx is the ipv4 address. Ive also tried the default gateway and the dns server address and those i get a connection refused on port 22.

So how am i supposed to use this command? Thanks :)

**Edit: Oh, and im connecting to a network on a college campus.**This is likely your problem. I imagine there is a firewall in place. Talk to your campus IT people and see if they will allow what you are doing. If they are OK with it, find out what ports they have open for ssh, etc.

---

### Post by undecim on 2010-04-13
If your SSH server (the computer you are trying to connect to) is on a different network than the one you are connecting from, then you won't be able to connect to it.

Your only option then, since you can't set up port forwarding on your college campus network, would be to have the server connect to another SSH server that you can access from another network and use SSH's port forwarding feature. But this means that you need a third computer that you can connect to.

---

### Post by Stord on 2010-04-13
I thought if im establishing an  ssh server on my own personal windows 7 computer then i could connect to it no mattter the network. Im trying to connect my two personal computers together... Question, which number was i supposed to have used, the dns server, the ip address of my computer??

---

### Post by FiReiSFuN on 2010-04-13
The problem may be that your college campus has a firewall, probably blocking port 22 (the ssh port). I'm confused as to which computer is on the college campus, and which isn't. If you are trying to connect from outside the network to inside, I'm afraid they probably will not let you do that. If you are trying to connect from inside the network to outside, that *may* be possible. Need more details to help though.

---

### Post by dwarfolo on 2010-04-13
> **FiReiSFuN said:**
> The problem may be that your college campus has a firewall, probably blocking port 22 (the ssh port). I'm confused as to which computer is on the college campus, and which isn't. If you are trying to connect from outside the network to inside, I'm afraid they probably will not let you do that. If you are trying to connect from inside the network to outside, that *may* be possible. Need more details to help though.

The correct sintax would be

ssh -l user xxx.xxx.xxx.xxx

or

ssh [email]user@xxx.xxx.xxx.xxx[/email]

but as suggested if you are not on the same network and/or your campus box is behind a firewall you are out of luck.

One option could be hamachi, but it's been a while since I've used it last time and I've not idea if it still support Linux.

---

### Post by dwarfolo on 2010-04-13
> **Stord said:**
> I thought if im establishing an  ssh server on my own personal windows 7 computer then i could connect to it no mattter the network. Im trying to connect my two personal computers together... Question, which number was i supposed to have used, the dns server, the ip address of my computer??

No, it's not "automagic" ^^
Your box at the campus should be accessible from the outside in order to establish ssh connection.
if this is the case then xxx.xxx.xxx.xxx is the IPV4 pubblic address of your win7 ssh server.

Or the campus firewall/router shoulkd be (unlikely) configured to forward IP traffic coming to it on port 22 to your box on the same port.
In this second case xxx.xxx.xxx.xxx should be the IPV4 pubblic address of the router/firewall of the campus.

---

### Post by tom.swartz07 on 2010-04-13
I am also on a University network. 

Depending on your IT department, you probably won't be able to ssh in from outside of the network.


ALTHOUGH!!

You could connect to your computer with ssh using this:
```
ssh user@"computer-name".local
```

you could add whatever flags on the ssh command, just as long as you follow the syntax "name".local. This will allow you to use the local network servers as a type of Pseudo-DNS server, rather than getting a specific IP for your computer (which may change on a daily basis)

---

### Post by Stord on 2010-04-13
Both computers are in the inside, on the same network. Ill try your suggestions and get back...

---

