---
title: "keeping my converts happy"
date: 2007-07-12
forum: Networking &amp; Wireless
---

### Post by miesnerd on 2007-07-12
Ok, 
So Ive mostly converted my family (brother in law, parents) to Ubuntu all this summer after Ive been using it for a year.

Now, Im wondering, what's the best way for me to do remote access to fix things if they manage to screw them up ? 
(They shouldnt be able to screw them up, but I know they'll want my help at some point, so I want to set something up like VNC or NX, etc..)

Can you give me detailed instrcutions on how to do this. I can connect to their Xubuntu/Ubuntu machines via Ubuntu or Xp. Doesnt make a difference to me. Just tell me how. Im far from a networking expert, btw.

Thanks,
Miesnerd

---

### Post by kevdog on 2007-07-12
Im not sure how to answer your question.  Both VNC and Nx will work, Nx is a much bigger pain to install, but faster.  It also requires a client program to make a connection (client available in win,linux,mac varieties).  VNC works also, although sometimes the connection is fragile and slow.  Although not necessarily needing a client program to connect to the server, the client program is much faster than the web interface.

Both can be tunneled over an ssh connection to make a secure connection between client and host. (If this is important).

Their are guides how to set both of these client/server packages up in the Tutorials section of the website.

---

### Post by HermanAB on 2007-07-12
One word: SSH

The SSH daemon is running by default on most every *nix computer system.  It run over port 22.  So what you have to do at each site, is forward port 22 through their home router to their machine.

To connect to their machine:
$ ssh [email]username@their.router.ip.addr[/email]ess

Then you can securely run any command.

The problem is how to get their router IP address.  In most cases, a home IP address will remain the same for several months on end, so just write it down and show them how to read it - usually using a browser looking at the status screen of the router.  You could also configure DynDNS.

Note that when you expose port 22, the machines WILL be attacked by script kiddies, so be sure to use secure passwords of 9 characters or more.  You could configure SSH to use a different port, say 2222 to throw the kiddies off. It works because most script kiddies are dumb.

Cheers,

Herman

---

