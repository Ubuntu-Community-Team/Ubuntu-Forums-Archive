---
title: "Double work with gnome network manager"
date: 2006-10-29
forum: Networking &amp; Wireless
---

### Post by awarberg on 2006-10-29
Hello

I've installed Ubuntu 6.10 on my Dell Inspiron 6400. Gnomes network manager allows me to connect to my wpa2 encrypted wireless network.

The program uses a keychain manager to safely store the network key  for my network. But the keychain requires a password in addition to my Ubuntu user password. 

So now I have to type in 2 passwords, instead of just 1, whenever I login to my laptop. I fail to understand why this is necessary. Why isn't my Ubuntu login (ie password) sufficient to protect the network keys?

In my opionion this is double work and leaves me with a bad experience of gnome network manager.

That aside, the network manager seems quite good - definitely better than that on windows. It should be a part of the default ubuntu installation, imo. (The built-in network tools can't show you a list of wireless networks, for instance.)

Best regards
Andreas

---

### Post by chuckao on 2006-10-30
Yes, it is boring!!!

But we have a hope (probably with the new version of NM)!
[http://live.gnome.org/NetworkManagerToDo](http://live.gnome.org/NetworkManagerToDo)

System-wide Configuration (Target: NM 0.7)

Obviously nobody likes to have to unlock the keyring on every login. Wireless networks can't be used until somebody logs into the machine, because NetworkManager stores the authentication information on a per-user basis. While there are various (we think) legitimate reasons for this behavior, there is a need to configuration information to be accessible outside of user sessions.

The current plan allows for users to "publish" configuration information for specific wireless networks to all users of the system, or make the data "system-wide". To preserve the same interface with which NM currently retrieves configuration information (the NetworkManagerInfo dbus API), a system-wide configuration daemon will be used. This daemon must:

    * have no UI, since it must run at system start up without X
    * Access system configuration information like GConf mandatory/default settings, KDE configuration, text files
    * Cooperate with user-session NMI instances, like applets 

David Zeuthen has written up some thoughts about how these system-wide configuration daemons should interact with DBUS. These appear quite useful for NetworkManager as well, since NM, HAL, gnome-power-manager, etc all have the same needs in this area.

---

### Post by awarberg on 2006-10-30
I'm glad you are working on this.

Best regards
Andreas

---

