---
title: "Network Profiles and Central Proxy Settings"
date: 2007-11-27
forum: Networking &amp; Wireless
---

### Post by dvwyngaa on 2007-11-27
Hi,

Maybe someone else has the same problems, but the current one I face is very frustrating. Let me explain:

1. A central proxy setting. This currently exists under the System->Prefferences->Network Proxy option, but its not very central. You change it here, but in some applications you have to set the proxy detail again and again...Is there a way past this...

2. With the Network Manager Applet, you can setup profiles for different scenarios you want, but there is nowhere where one could set the proxy server settings. For instance, at work I have a firewall and proxy which is setup, but when I go home I have an different IP for my Firewal and Proxy. It would damm nice if this was included in the profiles for NM, but I don't see it anywhere. Instead, when I go home, I have to setup my proxy server setting all over the show again. Maybe I don't know of anything that does this or I have missed a setting.

Can anyone help or should I log as a very wanted feature on Launchpad?

Thanks,

Dawid

---

### Post by kidders on 2007-11-29
Hi there,

This is a fairly common problem, but afaik there is no well-known, comprehensive solution, because it's essentially a side-effect of using open source software.

To take a simplistic example, there is no reason to expect an application built on the KDE development platform to obey a setting (be it a proxy configuration, or anything else for that matter) from a Gnome application. You see, in an environment that's as fragmented as Linux's is, the concept of system-wide settings simply can't exist. Their absence is seen by many as an *advantage*.

Anyhow, that doesn't make your proxy problem any less annoying! Off the top of my head, I can see two possible solutions...

[B]1: Environment variables & config files
[/B]Although there are no enforced standards for many things in Linux, there are certain *conventions* that developers tend to adhere to. For instance, you may find that the presence of a "http_proxy" environment variable might encourage many applications to proxy their internet traffic. Other applications may write out their proxy configuration to a .conf file.

Essentially, you may well find that of the 20 apps you might use on a daily basis, 19 of them can be taken care of using two or three common techniques. For example, if you set Gnome's proxy config option, set KDE's equivalent, set a variety of proxy-related environment variables, and alter a few config files, you may well be able to cover the majority of your applications. Although this may seem terribly complicated, the point is that all these actions are scriptable, so once you've figured out what they are, switching your whole computer from one proxy to another should be a matter of issuing a single command.

**2: Something a bit more drastic**
I haven't thought all the consequences of this option through, so there may be a few problems with it: You could try using your firewall to force applications to use a proxy, whether they like it or not. Iptables-based firewalls are very powerful, and allow you to almost arbitrarily redirect network traffic ... you could use one to force all outgoing connections through a transparent proxy running on your own machine, which in turn would be configured to forward them on to another proxy. Which proxy that happened to be would depend on where you were at the time.

The advantage in this approach is that it would be fairly system-wide. Having said that, I'm not sure connections over SSL (eg HTTPS) could be made to work with it though.

---

My tendency would be to go for option #1. You could do some research, find out how each of your applications likes to be told what proxy to use, and chain all the configuration changes together in a script. In theory, you could then run something like "proxy home" or "proxy work" to switch from one configuration to another.

I hope that helps.

---

### Post by paulau on 2007-11-29
Hi,

I'm actualy having the exact same problem. Also my user name and password dont when when connecting from a Vista machine and Leopard.

I have also tried putting the computer name before the username ie"computername\user" which didnt work.

Regards,
Paul

---

### Post by kidders on 2007-11-29
> **paulau said:**
> Hi,

I'm actualy having the exact same problem. Also my user name and password dont when when connecting from a Vista machine and Leopard.

I have also tried putting the computer name before the username ie"computername\user" which didnt work.

Regards,
PaulPlease don't hijack other people's threads. You've posted the above, word for word, twice now. I would suggest starting a thread of your own.

---

### Post by dvwyngaa on 2007-12-11
> **kidders said:**
> Hi there,

This is a fairly common problem, but afaik there is no well-known, comprehensive solution, because it's essentially a side-effect of using open source software.

To take a simplistic example, there is no reason to expect an application built on the KDE development platform to obey a setting (be it a proxy configuration, or anything else for that matter) from a Gnome application. You see, in an environment that's as fragmented as Linux's is, the concept of system-wide settings simply can't exist. Their absence is seen by many as an *advantage*.

Anyhow, that doesn't make your proxy problem any less annoying! Off the top of my head, I can see two possible solutions...

[B]1: Environment variables & config files
[/B]Although there are no enforced standards for many things in Linux, there are certain *conventions* that developers tend to adhere to. For instance, you may find that the presence of a "http_proxy" environment variable might encourage many applications to proxy their internet traffic. Other applications may write out their proxy configuration to a .conf file.

Essentially, you may well find that of the 20 apps you might use on a daily basis, 19 of them can be taken care of using two or three common techniques. For example, if you set Gnome's proxy config option, set KDE's equivalent, set a variety of proxy-related environment variables, and alter a few config files, you may well be able to cover the majority of your applications. Although this may seem terribly complicated, the point is that all these actions are scriptable, so once you've figured out what they are, switching your whole computer from one proxy to another should be a matter of issuing a single command.

**2: Something a bit more drastic**
I haven't thought all the consequences of this option through, so there may be a few problems with it: You could try using your firewall to force applications to use a proxy, whether they like it or not. Iptables-based firewalls are very powerful, and allow you to almost arbitrarily redirect network traffic ... you could use one to force all outgoing connections through a transparent proxy running on your own machine, which in turn would be configured to forward them on to another proxy. Which proxy that happened to be would depend on where you were at the time.

The advantage in this approach is that it would be fairly system-wide. Having said that, I'm not sure connections over SSL (eg HTTPS) could be made to work with it though.

---

My tendency would be to go for option #1. You could do some research, find out how each of your applications likes to be told what proxy to use, and chain all the configuration changes together in a script. In theory, you could then run something like "proxy home" or "proxy work" to switch from one configuration to another.

I hope that helps.

Kidders,

Thanks for the input...I'll, reluctantly, give option 1 a bash and hope that some good soul out there can come up with a permanent solution for the next release of Ubuntu...

Dawid

---

