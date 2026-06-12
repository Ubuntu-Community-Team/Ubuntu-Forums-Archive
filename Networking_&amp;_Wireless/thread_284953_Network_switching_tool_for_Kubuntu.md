---
title: "Network switching tool for Kubuntu"
date: 2006-10-26
forum: Networking &amp; Wireless
---

### Post by hardhu on 2006-10-26
Hello everybody,
since I move with my laptop almost everyday from my home network to the university one and I use sometimes the wireless interface, some others the wired one, I would like to have a tool that allows me to keep two different network configurations, home and university, to switch easily between them changing ip address, gateway and domain name servers, using for example an applet, and to easily enable or disable both interfaces allowing for integrated wep or wpa configuration on the fly for the wireless one.
I have been using for a while (k)netswitch to this purpose, but this tool seems not to be anymore developed. Are there any alternatives?

---

### Post by x64Jimbo on 2006-10-26
Network Manager. Check my sig.

---

### Post by hardhu on 2006-10-26
> **x64Jimbo said:**
> Network Manager. Check my sig.

NetworkManager is a very beautiful software, but does it integrate well with kde? I have found this statement at [http://fedoraproject.org/wiki/Tools/NetworkManager:](http://fedoraproject.org/wiki/Tools/NetworkManager:)

"Unfortunately, KDE currently lacks the libraries that would be required to write a desktop control applet. Specifically, the necessary QT-DBUS bindings are not yet ready. QT-DBUS bindings are currently expected to be available as part of KDE 4.0." 

Is this still true also in kubuntu?

---

### Post by x64Jimbo on 2006-10-26
Take a look at the NetworkManager site:
"The most important pieces of NetworkManager are desktop-environment and distribution agnostic, functioning just as well in Gnome, KDE, Xfce, etc. across distributions like Fedora Core, Ubuntu, SuSE, Debian, and Gentoo."
I don't think it could be said any clearer than that. :)
Here's more info on NetworkManager from the Wiki
[https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

---

### Post by hardhu on 2006-10-27
> **x64Jimbo said:**
> Take a look at the NetworkManager site:
"The most important pieces of NetworkManager are desktop-environment and distribution agnostic, functioning just as well in Gnome, KDE, Xfce, etc. across distributions like Fedora Core, Ubuntu, SuSE, Debian, and Gentoo."
I don't think it could be said any clearer than that. :)
Here's more info on NetworkManager from the Wiki
[https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

Ok, I will give it a try. May I ask you another suggestions about whcih packages to install: I see in Edgy there are

network-manager
knetworkmanager
network-manager-gnome

are all of them necessary or for kubuntu only the first two ones?

---

### Post by x64Jimbo on 2006-10-27
The first two should do it for you.

---

