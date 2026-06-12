---
title: "[SOLVED] Proxy problems and Synaptic package manager"
date: 2008-01-13
forum: Networking &amp; Wireless
---

### Post by absolutezero1287 on 2008-01-13
I'm on Ubuntu 7.10

I wanted to use a proxy and decided to install Tor and Privoxy. Everything went good for a while. I was on the net anonymously and everything. Until I wanted to install Vidalia. I had to compile it from it's source. When I tried to get the needed packages (qt4-dev-tools and qt4-designer) I got an error saying that there was some type of connection error. I figured that this had to do with Tor. So after tinkering for a few hours I decided it best to uninstall Tor and Privoxy. I did just that, rebooted and tried my luck with Synaptic again. It didn't work. Uninstalling Tor should have done the trick but it didn't. Can anyone help?

---

### Post by csat on 2008-01-13
There is an interesting article [=>HERE<=](http://www.ubuntugeek.com/how-to-install-tor-with-vidalia-gui-on-ubuntu.html) so that you can review or re-install all stuff.

---

### Post by absolutezero1287 on 2008-01-13
That article is very interesting and all but Synaptic isn't working at all.
It says something about not being able to connect to localhost 127.0.0.1: 4001. I figured that this had something to do with Tor's settings. But they stayed that way even after the uninstall. The error message is given below.

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-core_4.3.2-0ubuntu3.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-core_4.3.2-0ubuntu3.1_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

---

### Post by csat on 2008-01-13
There is another tutorial [=>here<=](http://ubuntuforums.org/showthread.php?t=95527) for a try.

Anyway consider also that some sites have built-in features to refuse TOR users.  I don't know if this is the case for getting such info from synaptic update routine.

I'd try to complete remove tor routine and configure my browser with anonymous or transparent proxy so that I could see if I'd get the same error as was getting with tor.  Just an idea to debug it.

---

### Post by absolutezero1287 on 2008-01-13
I must have been a bit unclear. The thing is that I uninstalled Tor and Privoxy and my computer stayed with Tor's configurations. So, my internet works, but Synaptic does not. Basically. How do I return my connections to default?

---

### Post by kostkon on 2008-01-13
> **absolutezero1287 said:**
> I must have been a bit unclear. The thing is that I uninstalled Tor and Privoxy and my computer stayed with Tor's configurations. So, my internet works, but Synaptic does not. Basically. How do I return my connections to default?

Since you can access the web I believe that a proxy has been set in *Synaptic* (in your case a local proxy, that's why it has the 127.0.0.1:4001 address). Open *Synaptic*, go to its Settings and delete the proxy.

Just to be sure, go to *System -> Preferences -> Network Proxy* and see if a proxy has been set there, also.

---

### Post by absolutezero1287 on 2008-01-13
It says "direct connection to the internet" there was no proxy configured.

---

### Post by absolutezero1287 on 2008-01-14
I fixed the problem. Thanks everyone for all your input. It's very appreciated.
I fixed it by going into System>Administration>Network and changing my computer's IP from localhost (127.0.0.1) to my actual IP.

I discovered my real IP by going to whatismyip.com

Here's a link to some posts about my problem.
[http://ubuntuforums.org/showthread.php?t=182018](http://ubuntuforums.org/showthread.php?t=182018)
[http://forums.techguy.org/unix-linux/671259-proxy-problems-synaptic-package-manager.html](http://forums.techguy.org/unix-linux/671259-proxy-problems-synaptic-package-manager.html)

---

