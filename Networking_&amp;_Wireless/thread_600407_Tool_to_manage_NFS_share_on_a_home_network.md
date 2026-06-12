---
title: "Tool to manage NFS share on a home network?"
date: 2007-11-02
forum: Networking &amp; Wireless
---

### Post by zoubidoo on 2007-11-02
My home network is growing and it is starting to become an effort to manage.  Is there a tool that will make managing NFS shares simpler?

I have a dozen or so partitions on 4 machines.  Several of them are shared with NFS.  At the moment I have no overview and sometimes have to log into each machine to check things over.

So I'm looking for a solution that:
[LIST=1]
[*] will give a good overview (show all the partitions and the remaining space).
[*] is robust when some machines are not switched on
[*] doesn't require a major overhaul (like lvm)
[*] provides an interface either GUI/curses/web
[/LIST]

I found this blueprint which looks promising, but no further info. [https://wiki.ubuntu.com/UbuntuEasyFilePrintServer](https://wiki.ubuntu.com/UbuntuEasyFilePrintServer)

Webmin is one approach. Ebox looks simpler.  Does anyone have any other suggestions?

---

### Post by zoubidoo on 2007-11-02
I have done some more reading and it looks like what I'm trying to do is quite common for large installations.  People seem to use tools like nagios   [http://www.nagios.org/](http://www.nagios.org/) for monitoring and puppet [http://reductivelabs.com/projects/puppet/](http://reductivelabs.com/projects/puppet/) for configuration management.

It would be nice if nagios and puppet were integrated and there was a GUI to make it idiot-proof.

---

