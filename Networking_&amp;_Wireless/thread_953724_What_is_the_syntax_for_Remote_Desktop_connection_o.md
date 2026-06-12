---
title: "What is the syntax for Remote Desktop connection over  a WAN?"
date: 2008-10-20
forum: Networking &amp; Wireless
---

### Post by bwallum on 2008-10-20
Hi

I can find the ip address to a router from an internet server, lets say that is 111.111.111.111. I can find out the ip address of a computer behind a router, lets say that is 222.222.222.222. I understand that I should use port 59xx. I understand that the computer I want to connect to will have a name something like fred-desktop and that I can ```
vinagre fred-desktop:0
```to connect over a LAN.

What I don't understand is the syntax needed in a WAN communication. Can you tell me how I should form the full connection address over the Internet please?

---

### Post by bwallum on 2008-10-23
Would it be in order to 'bump' this please?

---

### Post by ssharps711 on 2009-02-09
Bump. I need to know how to do this as well.

---

### Post by dmizer on 2009-02-09
You'll need to configure port forwarding on your router: [http://portforward.com/routers.htm](http://portforward.com/routers.htm)

You'll find that remote desktop over WAN is unusably slow. I suggest forwarding X11 with SSH, and opening individual GUI applications from the command line as needed. More information here: [https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

---

### Post by dimamali on 2009-05-04
I know it's a later answer but i hope it helps!
As dimzer said, remote desktop over wan is uneusuably slow and you can certainly do the same job with OpenSSH
There's a great how-to here:
[COLOR="Navy"]_[http://principialabs.com/beginning-ssh-on-ubuntu/](http://principialabs.com/beginning-ssh-on-ubuntu/)_[/COLOR]
the syntax to connect over wan is
**ssh user@user's_external_ip -p user's_external_port**
and if you also need to open some apps using Xorg you just add the option -X
**ssh -X user@user's_external_ip -p user's_external_port**

---

### Post by bwallum on 2009-05-04
Thanks guys,

It was a nicely timed nudge. I have been speaking yesterday with my volunteer Ubuntu friend to set up remote desktop control over the public internet.

I will get on with trying your methods, I can confirm that the remote-desktop route is so slow as to render it unusable. That put me off, to be honest, but I like the ssh approach with the option of evoking Xorg or not.  Thank you very much for the syntax steer. I will spend next week doing some serious investigation and report back. Thank you very much for your help to date.

Rgds
Bob

---

### Post by Dragonbite on 2009-05-04
> **dimamali said:**
> I know it's a later answer but i hope it helps!
As dimzer said, remote desktop over wan is uneusuably slow and you can certainly do the same job with OpenSSH
There's a great how-to here:
[COLOR="Navy"]_[http://principialabs.com/beginning-ssh-on-ubuntu/](http://principialabs.com/beginning-ssh-on-ubuntu/)_[/COLOR]
the syntax to connect over wan is
**ssh user@user's_external_ip -p user's_external_port**
and if you also need to open some apps using Xorg you just add the option -X
**ssh -X user@user's_external_ip -p user's_external_port**

Is adding -X the best way or only way to run X over SSH? I've just been running SSH in CLI but there are times I wish I could get into the Desktop Environment of the system.

I'll be kicking myself if it is this easy, but glad to know!

---

