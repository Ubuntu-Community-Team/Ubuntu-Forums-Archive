---
title: "How To Provide Remote Assistance To XP User"
date: 2009-10-05
forum: New to Ubuntu
---

### Post by wah fun on 2009-10-05
Hello. I am relatively new to Ubuntu and am using version 8.04 on a box with 3 GiB Ram, AMD Dual Core 2 GHz processor.

I am trying to find out how to provide remote assistance to a Windows XP user. This is very easy to do in Windows - the remote user sends a ticket file. The expert opens the ticket file and logs in using a pre-determined password. 

Can someone tell me if this is possible with the expert using Linux? I have searched but am not finding much in the way of help. I have several family members living in other States and I would like to be able to help them even though we use different OS's.

Thank you in advance for your assistance.

---

### Post by stwschool on 2009-10-05
I've used VNC to do the remote control of Windows XP machines. The only pain is that the VNC server must be installed on the XP machine (which is a fairly easy and painless task).

---

### Post by stwschool on 2009-10-05
PS in Ubuntu you'd look for Applications -> Internet -> Remote Desktop Viewer
PPS There's loads of good freebie VNC servers for windows but off the top of my head I can't remember the names, but I'm sure a quick google will suffice.

---

### Post by steveneddy on 2009-10-05
Goodness - here it is:

[http://www.realvnc.com/products/free/4.1/download.html](http://www.realvnc.com/products/free/4.1/download.html)

have the remote XP person DL and install this. You must know the IP address of the remote machine. Just send them to [ipchicken.com]("http://www.ipchicken.com/") and message you the IP address right before you connect.

make sure you have xvnc4viewer installed.

```
sudo apt-get install xvnc4viewer
```

So, in terminal type:

```
vncviewer[COLOR=Red] **ip.address.of.remote**[/COLOR]:0
```replace [COLOR=Red]**ip.address.of.remote **[COLOR=Black]with the actual IP address of the remote machine.[/COLOR][COLOR=Black]You should connect to the remote machine in a new window.

Simple, really.

I also think you can use Remote Desktop Viewer or Terminal Server Client to connect  to remote machines. Try it out.

Have fun!

EDIT:

xvncviewer man pages:

[http://pwet.fr/man/linux/commandes/xvnc4viewer](http://pwet.fr/man/linux/commandes/xvnc4viewer)
[/COLOR][/COLOR]

---

### Post by steveneddy on 2009-10-05
> **stwschool said:**
> I've used VNC to do the remote control of Windows XP machines. **The only pain is that the VNC server must be installed** on the XP machine (which is a fairly easy and [COLOR=Red]**painless**[/COLOR] task).

> PS in Ubuntu you'd look for Applications -> Internet -> Remote Desktop Viewer
PPS There's loads of good freebie VNC servers for windows but off the top of my head I can't remember the names, but **I'm sure a quick google will suffice**.

It's such a pain to install software? Why would you even say that? What's so painful about it? DL and double click on Windows? Then in the same sentence you say it is painless. Make up your mind.

**Just Google for it** isn't an answer either.

If you are going to answer the OP, give a good reference or point him/her in the **right** direction.

The OP already told us they were new to this, you only drop them deeper in the hole by giving vague generalities and tell them to look on Google for the answer.

---

### Post by halitech on 2009-10-05
Only issue I find with using programs like VNC is that 1. you need to know the IP address and after doing tech support for 10 years, its not always easy to get the customers to give it to you. 2. If the customer has a router, getting the external IP doesn't help if the router is not set up to forward the port and the internal is useless as you can't connect to an internal IP.

What I've started using is LogMeIn ([http://secure.logmein.com](http://secure.logmein.com)) which is a program that the XP user would install and then the "support" person logs into the logmein website and can remotely control the system. No need to find out IP addresses, no need to configure routers and if the person has 2 computers behind the same router, you can still support both without having to do funky things to the router and ports.

---

### Post by jimsheep on 2009-10-05
> **steveneddy said:**
> It's such a pain to install software? Why would you even say that? What's so painful about it? DL and double click on Windows? Then in the same sentence you say it is painless. Make up your mind.

**Just Google for it** isn't an answer either.

If you are going to answer the OP, give a good reference or point him/her in the **right** direction.

The OP already told us they were new to this, you only drop them deeper in the hole by giving vague generalities and tell them to look on Google for the answer.

dude, chill. at least he's trying to help.

[QUOTE=halitech]...What I've started using is LogMeIn ([http://secure.logmein.com](http://secure.logmein.com))...[/QUOTE]
+1. works like a dream.

---

### Post by steveneddy on 2009-10-05
> **halitech said:**
> Only issue I find with using programs like VNC is that 1. you need to know the IP address and after doing tech support for 10 years, its not always easy to get the customers to give it to you. 2. If the customer has a router, getting the external IP doesn't help if the router is not set up to forward the port and the internal is useless as you can't connect to an internal IP.

What I've started using is LogMeIn ([http://secure.logmein.com](http://secure.logmein.com)) which is a program that the XP user would install and then the "support" person logs into the logmein website and can remotely control the system. No need to find out IP addresses, no need to configure routers and if the person has 2 computers behind the same router, you can still support both without having to do funky things to the router and ports.

He stated that he is helping family, not customers. They should have no issues giving the IP to the OP.

Unless the "customer" purposely has the port blocked there is no reason why VNC won't work through a home router. Now if multiple machines have a VNC server installed and running on the inside of the router, I can see where this would be an issue.

I gave the OP the "linux" or geeky way of performing this task.

But that logmein.com, I will check that out. Looks promising.

EDIT:
So the Windows user DL's the logmein app and just give the password to the remote user.

Looks easy peasy, even for a Windows user.

---

### Post by halitech on 2009-10-05
> **steveneddy said:**
> He stated that he is helping family, not customers. They should have no issues giving the IP to the OP.

Unless the "customer" purposely has the port blocked there is no reason why VNC won't work through a home router. Now if multiple machines have a VNC server installed and running on the inside of the router, I can see where this would be an issue.

I gave the OP the "linux" or geeky way of performing this task.

But that logmein.com, I will check that out. Looks promising.

EDIT:
So the Windows user DL's the logmein app and just give the password to the remote user.

Looks easy peasy, even for a Windows user.

When I referred to customers, I meant customers/family members in a generic way in that not all of them can enter the correct commands to get their IP addresses, not that they would have a problem giving the info.

All the routers I've set up have not worked with the default settings when trying to connect using vnc so unless I've had the misfortune of buying the wrong routers, port forwarding needs to be configured for VNC to work. All the family and friends I support have multiple computers behind routers so configuring things to work with them means a visit onsite. Not disputing that VNC is hard, its pretty easy to install and setup on the computer itself, more the router where the issue comes up.

Logmein is nice especially if you supporting the same people all the time because you can get it set up on 1 account (yours) and add the people and then you have instant access at any time (especialy handy for me with my folks as they tend to forget about doing windows updates so I can just log in and do it for them after midnight when I know they are asleep and they are none the wiser :) )

---

### Post by durand on 2009-10-05
To get an external IP, you just need to go to whatismyip.com, the only problem is with internal ips and port forwarding stuff which can be a pain.

---

### Post by freak42 on 2009-10-05
> **halitech said:**
> Only issue I find with using programs like VNC is that 1. you need to know the IP address and after doing tech support for 10 years, its not always easy to get the customers to give it to you. 2. If the customer has a router, getting the external IP doesn't help if the router is not set up to forward the port and the internal is useless as you can't connect to an internal IP.

What I've started using is LogMeIn ([http://secure.logmein.com](http://secure.logmein.com)) which is a program that the XP user would install and then the "support" person logs into the logmein website and can remotely control the system. No need to find out IP addresses, no need to configure routers and if the person has 2 computers behind the same router, you can still support both without having to do funky things to the router and ports.

You can also initiate the connection from the vnc server, you just need a vnc-client in **listening mode**, that way your customers can connect to you (and you certainly can provide the right ip and do the port forwarding.) You can even create a batch file that initiates the connection upon clicking on it, so your customers only need , an installed vnc server and the batch file to click on. works like a charm.

---

