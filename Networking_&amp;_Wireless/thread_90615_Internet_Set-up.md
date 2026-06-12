---
title: "Internet Set-up"
date: 2005-11-15
forum: Networking &amp; Wireless
---

### Post by theswan on 2005-11-15
Hello everyone,
Im new to Ubuntu. Upon install, I skipped on the part about setting up the network. Now, i can't make internet connection work in Ubuntu....=(

Im still on dual-boot to windows now where i can have internet. In windows xp, i have this option to view all wi-fi connections within my range and i can select on one to connect to. i was hoping something like that in Ubuntu.

Also, i've been trying to read on some notes about Ubuntu...and when it comes to installation its always like in the terminal as commands like 'sudo...' something something... do you mean that its unlike windows that you got the exe installer file that you can execute?

Any help please? Thanks

---

### Post by suRoot on 2005-11-15
From the menu, click "System -> Administration -> Networking" to configure your network card.

Under linux, you have a few options for installing software.  Many packages come as pre-compiled binaries which you can install using apt-get, eg:

```

apt-get install software_package_name
```

You can also install other binary formats like .deb or .rpm using dpkg or alien, you may want to browse the forums for info about those formats, or post a specific question if you're having problems installing.

You can also install pretty much anything from source, meaning you download the source from the web which is usually compressed as a gzip or bzip (.tar.gz , .tgz, .bzip2) file, which you then install using (typically)

```
./configure
make
make install
```

Downside to building from source is that you bypass the package management system of the distribution (think add/remove programs under windows).  However, you can have more control over the install by building from source by specifying flags specific to your build.

---

### Post by Lambert on 2005-11-15
If you're new to linux be ready to read and search. Things work differently such as installing programs. It's all good though and there are reasons why it's set up the way it is.

Synaptic is a graphical program for installing programs. There is basically a repository of all the packages that you can install on your system. 

[https://wiki.ubuntu.com/SynapticHowto?highlight=%28synaptic%29](https://wiki.ubuntu.com/SynapticHowto?highlight=%28synaptic%29)

Notice the link inside that page Adingrepositories.

90% of the programs you need (if not more) can be found here. If you need something not there, you can download a .deb file and use dpkg to install it.

Your card may need a driver set up for it. The support for linux drivers is not there yet from the manufactures. If you can't connect by system>admin>networking then post back here with as much detail about the card and your network settings.

model#
manufacture
encryption yes no if yes then wep or wpa
dhcp or static ip assignment

key or ssid is not needed.

I have a couple links in my signature you can look at to help you get started. Once you're connected, go to synaptic and look for a document called newbiedoc. This should be enough general information to get you started.

Don't shy away from the command line. It's a little intimidating at first but well worth learning.

---

