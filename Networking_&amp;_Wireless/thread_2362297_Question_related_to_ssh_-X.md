---
title: "Question related to ssh -X"
date: 2017-05-26
forum: Networking &amp; Wireless
---

### Post by sp40140 on 2017-05-26
I want to launch gui application from host and have it display on client. I can do that when I initiate the ssh connection with -X option.

Is it possible to do launch gui application from host and have it display on client AFTER initiating ssh connection  but WITHOUT -X option?
Is there a way to change the settings once connected to be able to do this?

Why am I not simply using -X option? 
I want to ssh from ipad. and the apps (terminus) I use, I don't think they allow me to tweak the command and add -X to it.
If you are aware of a way to do this, I am open to it as well.

---

### Post by TheFu on 2017-05-26
If the local machine runs an X/Server then you don't need to use an ssh-tunnel with automatic X-forwarding.  However, the x-protocol is not secure and you'll need to manually setup the DISPLAY environment correctly.

You can run multiple ssh connections from most clients, so you should be able to start another with the -X option.  I know nothing about apple that is useful to you.  Does it have an X/Server?

For more details: [http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications](http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications)

---

### Post by sp40140 on 2017-05-26
> **TheFu said:**
> If the local machine runs an X/Server then you don't need to use an ssh-tunnel with automatic X-forwarding.  However, the x-protocol is not secure and you'll need to manually setup the DISPLAY environment correctly.

You can run multiple ssh connections from most clients, so you should be able to start another with the -X option.  I know nothing about apple that is useful to you.  Does it have an X/Server?

For more details: [http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications](http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications)
So, I am fine with ssh and ssh -X from desktop/laptops as clients. 

And I don't think this is specific to apple/ipad. I think it's more to do with how a third party ssh app was developed. I checked it's settings and there is nothing in there for X/server or display.

But since I can successfully do ssh. I was hoping that once I log in using ssh, I can set-up the env so that I can run the application on ubuntu host and see the gui on ipad (or even android).

Quick Edit:
That's a helpful link (bookmarked it). I have tried setting up DISPLAY env variable but it didn't help!

---

### Post by TheFu on 2017-05-26
I don't think android has any X/Server, so you are stuck.  Doubt an ipad does either.

X/Windows has **nothing** to do with ssh.  ssh came 10 yrs later and added the ability to tunnel X-protocol traffic between an existing X-client (remote) and X-Server (local).  The architecture for X/Windows client/server is backwards from what most C/S architectures use.

Without an X/Server running on the machine with the display you want to see it on, you cannot do this.

---

### Post by sp40140 on 2017-05-26
> **TheFu said:**
> I don't think android has any X/Server, so you are stuck.  Doubt an ipad does either.

X/Windows has **nothing** to do with ssh.  ssh came 10 yrs later and added the ability to tunnel X-protocol traffic between an existing X-client (remote) and X-Server (local).  The architecture for X/Windows client/server is backwards from what most C/S architectures use.

Without an X/Server running on the machine with the display you want to see it on, you cannot do this.
OK. Now this explains it. I guess I am out of luck. I will look around if iOS has XServer or not. No big deal though. It was more of a convenience thing than anything else.

Cheers,

---

### Post by TheFu on 2017-05-26
So .... there are a few ways to get around the limits, but those are probably more hassle then they are worth unless you are a huge nerd.  For example, you could use a remote desktop.  

That would demand a full VPN to be secure, since no remote desktop that runs on iOS or Android is secure without it.

On Android, you could do that or run a Linux desktop inside a chroot. That will provide an X/Server, but it has very large overhead and still requires running a remote desktop on Android to access the Linux choot instance ... then ssh -X into other machines from it.  I did it for a few months, then decided that having a chromebook was 10000x better and switched years ago.

---

### Post by sp40140 on 2017-05-26
Thank you. I use Team Viewer. It has iOS and android apps so it works. But I am becoming more paranoid and am looking into ssh with 2048 bit key!
I don't have powerful enough mobile devices which can take the load of running full linux desktop.
I guess for now, I can keep using TV.

---

