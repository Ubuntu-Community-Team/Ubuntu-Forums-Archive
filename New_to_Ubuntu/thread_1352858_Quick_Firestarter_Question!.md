---
title: "Quick Firestarter Question!"
date: 2009-12-12
forum: New to Ubuntu
---

### Post by Volcom350Z on 2009-12-12
Hows it going , Ubuntu newb here again trying to get Firestarter to work.

When I try to enable firestarter it says ....

Failed to start the firewall

The device eth1 is not ready

Please check your network device settings and make sure your internet connection is active.

any help would be greatly appreciated!

---

### Post by lovinglinux on 2009-12-12
Do yourself a favor, remove Firestarter and install gufw.

Open "Applications >> Acessories >> Terminal" then run this:

```
sudo apt-get purge firestarter
sudo iptables -F
sudo iptables -X
sudo apt-get install gufw
```

To open gufw, go to "System >> Administration >> Firewall Configuration".

Keep in mind you don't need and shouldn't run Firestarter or Gufw all the time. They are just firewall managers, which allows to create the firewall rules. The real firewall is always running in the background.

---

### Post by rolnics on 2009-12-12
I've just had a quick search I assumed you're like me and still running 8.04 so here are a couple of links that might help.

[Forum thread with a similar issue]("http://ubuntuforums.org/showthread.php?t=439836")

[Ubuntu Geek]("http://www.ubuntugeek.com/gufw-simple-gui-for-ufw-uncomplicated-firewall.html") explaining how to install a graphical setup for Firestarter.

I hope that helps

---

### Post by Volcom350Z on 2009-12-12
thanks alot guys!

---

### Post by lovinglinux on 2009-12-12
[QUOTE=Volcom350Z]sweet thanks alot youve been a big help, now when its on enabled, and deny oncoming traffic , I should be more "Safer" now when i browse the web?[/QUOTE]

No. In fact, you are probably not safer by using a firewall anyway. Ubuntu does not come with any server running so all ports are closed by default, which means you don't even need a firewall. Any unrequested connection attempts will be rejected anyway, even without a firewall, unless you install and start a sever application like a web server, BitTorrent client, ssh server, samba server or vnc server (remote desktop).

So running a firewall would be like closing ports that are already closed.

In regard to be safer while browsing, a firewall won't help you because a browser requests connections to the outside world, it does not accept incoming connections. Any request made by you (for example when you type a web site address) is allowed. Any data transfer related to this connection request is also accepted.

I recommend that you read [Ubuntu Security](http://ubuntuforums.org/showthread.php?t=765421) tutorial.

---

### Post by Volcom350Z on 2009-12-12
Hey thanks a lot man I appreciate it, you are very knowledgeable.

---

### Post by karmicgaz on 2009-12-12
Not really a reply, just a piggyback question, I haven't opened any ports for any reason and do not run firestarter etc but for normal surfing and/or transmission bittorrent should I run some kind of firewall manager? Or let ubuntu 9.1 handle it?

---

### Post by lovinglinux on 2009-12-12
> **Volcom350Z said:**
> Hey thanks a lot man I appreciate it, you are very knowledgeable.

Not really, but thanks :)

Anyway, to protect your browsing activity use [NoScript](https://addons.mozilla.org/en-US/firefox/addon/722), [AdBlock Plus](https://addons.mozilla.org/en-US/firefox/addon/1865) and [Better Privacy](https://addons.mozilla.org/en-US/firefox/addon/6623). See [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567) for additional stuff.

> **karmicgaz said:**
> Not really a reply, just a piggyback question, I haven't opened any ports for any reason and do not run firestarter etc but for normal surfing and/or transmission bittorrent should I run some kind of firewall manager? Or let ubuntu 9.1 handle it?

You need to open the port for the BitTorrent client to accept unrequested incoming connections if you want to get decent speeds, so using a firewall won't help you either. You would be closing the ports that are already closed and opening the only port capable of accepting remote connections.

For more info see the security section of [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923).

---

### Post by 3rdalbum on 2009-12-12
> **karmicgaz said:**
> Not really a reply, just a piggyback question, I haven't opened any ports for any reason and do not run firestarter etc but for normal surfing and/or transmission bittorrent should I run some kind of firewall manager? Or let ubuntu 9.1 handle it?

I started writing a description of what a firewall does and how your system would appear with and without it, but maybe there's a better explanation.

Firewalls are good when they are built into ADSL/cable routers because then you can run file sharing services across your network without anyone from the Internet being able to access them. But personal firewalls, that run on a single computer only, are virtually useless on Ubuntu. They are only useful on Windows, which listens to incoming ports that it has no business to be listening to. Ubuntu doesn't do that. It only listens to incoming ports when you actually install and run a program that needs to be listening (for instance, a web server).

---

