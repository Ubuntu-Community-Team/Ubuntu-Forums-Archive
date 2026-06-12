---
title: "Wireless Driver"
date: 2005-11-12
forum: Networking &amp; Wireless
---

### Post by PJG on 2005-11-12
Where can I find a driver for a Belkin F5D7050 USB Network Adapter? I'm a neophyte with linux and need something simple.

---

### Post by Lambert on 2005-11-12
You need to use a module called ndiswrapper. It simply is a module that uses the windows driver for you device in linux. There are many posts in this forum on using ndiswrapper.

There is a graphical method of installing the driver. If you have internet access on the ubuntu machine, install ndisgtk. Click on system>Admin>windows wireless drivers.
Have your windows drivers handy and follow the prompts

Not knowing how new you are in linux, if you don't know how to install apps read [COLOR=Blue][this]("https://wiki.ubuntu.com/SynapticHowto?highlight=%28synaptic%29")

[COLOR=Black]You can also install from the command line. Two sites to look for instructions plus many posts throughout here on accomplishing it through CLI.

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu)
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)
[/COLOR][/COLOR]

---

