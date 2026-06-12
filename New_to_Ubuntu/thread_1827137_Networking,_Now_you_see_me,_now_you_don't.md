---
title: "Networking, Now you see me, now you don't"
date: 2011-08-17
forum: New to Ubuntu
---

### Post by PaddyIndigo on 2011-08-17
Hi,
I've made some progress networking.

I can see my 3 Windows machines using the nautilus smb;//IP Address command from a terminal,  and I can sometimes see 2 of them under "places-network-windows network-workgroup" (& one of these 2 under "places-network" alongside "windows network".)  The third windows machine I can't see at all,  not even from the other windows machines - so that's not a Ubuntu issue.

However,  I can't see my Ubuntu machine from any of the windows machine.  I'd like to. Any ideas?

Thanks
Pat

---

### Post by pi.boy.travis on 2011-08-17
The Samba (SMB/Windows sharing) server software doesn't come installed by default. Just right-click on a folder you'd like to share, choose "Sharing options," and check the "Share this folder" check box. A window will appear asking if you'd like to install Samba server, just follow the instructions and reboot when it's finished. That should do the trick.

---

### Post by PaddyIndigo on 2011-08-18
> **pi.boy.travis said:**
> The Samba (SMB/Windows sharing) server software doesn't come installed by default. Just right-click on a folder you'd like to share, choose "Sharing options," and check the "Share this folder" check box. A window will appear asking if you'd like to install Samba server, just follow the instructions and reboot when it's finished. That should do the trick.

Ahh, I tried that,  and it proceeded as you predicted up to the install dialog, but then I got the same error as I get with my [printer problem]("http://ubuntuforums.org/showthread.php?p=11163112#post11163112")

[COLOR=RoyalBlue][I]E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.[/I][/COLOR]
And synaptic exits.

---

### Post by PaddyIndigo on 2011-08-18
I found the solution to the error message in [this link]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Encountered+a+section+with+no+Package%3A+header&as_qdr=all&sa=Google+Search&lang=en#1050") =

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

which seems to have fixed the error.  I'll get back with an update about whether the original issue is solved

Thanks
Pat

---

### Post by PaddyIndigo on 2011-08-18
Great thanks, it's working now, I can see, log into, create, modify and save on the Ubuntu machine.

I still have my [printer problem]("http://ubuntuforums.org/showthread.php?p=11163190#post11163190") though,  and my delinquent Windows machine still gives me a different problem every time I try to network it.  But then,  that's why I'm trying to switch to Linux:D

---

### Post by pi.boy.travis on 2011-08-18
> **PaddyIndigo said:**
> Great thanks, it's working now, I can see, log into, create, modify and save on the Ubuntu machine.

I still have my [printer problem]("http://ubuntuforums.org/showthread.php?p=11163190#post11163190") though,  and my delinquent Windows machine still gives me a different problem every time I try to network it.  But then,  that's why I'm trying to switch to Linux:D

At the risk of moving off-topic, does your printer have network support, i.e. an Ethernet port right on it? If it can set itself up on the network, Ubuntu should be able to use it easily.

---

### Post by PaddyIndigo on 2011-08-24
> **PaddyIndigo said:**
> 
I still have my [printer problem]("http://ubuntuforums.org/showthread.php?p=11163190#post11163190") though,  and my delinquent Windows machine still gives me a different problem every time I try to network it.  But then,  that's why I'm trying to switch to Linux:D

Just a postscript for anyone that gets here looking to solve similar problems.  The [printer problem]("http://ubuntuforums.org/showthread.php?p=11163190#post11163190") is also resolved (see link) and the delinquent Windows machine turns out to be a Windows firewall issue,  as yet unresolved,  but let's not pollute a Linux forum with Windoze stuff!!!

---

