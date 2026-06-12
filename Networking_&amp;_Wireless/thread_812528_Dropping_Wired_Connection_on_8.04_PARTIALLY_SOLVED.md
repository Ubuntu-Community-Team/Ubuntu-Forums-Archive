---
title: "Dropping Wired Connection on 8.04 PARTIALLY SOLVED"
date: 2008-05-30
forum: Networking &amp; Wireless
---

### Post by GrapeSoda on 2008-05-30
Hey all,

It seems like there are a number of general wireless issues with the upgrade to Hardy Heron, as well as a number of wired issues.  The biggest wired issue seems to be a sudden permanent/semi-permanent loss of wired connectivity a few days after the 8.04 installation.  See the following posts (first is mine from a couple of hours ago):

[http://ubuntuforums.org/showthread.php?p=5074570#post5074570](http://ubuntuforums.org/showthread.php?p=5074570#post5074570)

[http://ubuntuforums.org/showthread.php?t=812190&highlight=wired](http://ubuntuforums.org/showthread.php?t=812190&highlight=wired)

[http://ubuntuforums.org/showthread.php?t=804705&highlight=wired](http://ubuntuforums.org/showthread.php?t=804705&highlight=wired)

For some reason, the default network-manager not only refuses to see your wired card, it also refuses to let you configure eth0 and eth1 (assuming 0 is the wired and 1 is the wireless)- instead, you get a message saying that neither of them exist.

After some digging for a solution, I came across a post by abh83 in the following post:

[http://ubuntuforums.org/showthread.php?t=778911&highlight=wired](http://ubuntuforums.org/showthread.php?t=778911&highlight=wired)

abh83 suggest using Wicd instead of network-manager.  I went to the link provided ([http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)), followed the instructions, and installed wicd.  It automatically uninstalled the network-manager, and I was able to run it and with some tweaking (i.e. getting used to its setup, adding the OpenDns servers as my default DNS lookups) I was able to restore my wired connectivity.  Below are the steps I took, directly from the website:

1) Open up Synaptic Package Manager (System > Administration > Synaptic Package Manager)

2) Go to Settings > Repositories > Third Party Software

3) Click Add, then add the following line:

       deb [http://apt.wicd.net](http://apt.wicd.net) heron extras

NOTE: This can be installed on other versions: just replace hardy with the appropriate adjective (gutsy, feisty, etc)

4) Install wicd
   a) Refresh the Package Manager
   b) Search for wicd
   c) Right-click, select "Mark for Installation"
   d) Apply the changes
   e) Close Synaptic

NOTE: This automatically uninstalls network-manager

5) Add wicd to the startup bar
   a) Go to System > Preferences > Sessions
   b) In the "Startup Programs" tab, click "New"
   c) Under name put "Wicd" and under command put /opt/wicd/tray.py

6) Restart 

Everything is looking good for the moment, but I'd like to offer some words of caution:

1) Although there seems to be a solution for this loss of wired connectivity, there's still no understanding for the loss of connection in the first place.  Yes, the issue seems to reside in Heron's default network-manager application, but it's dangerous to assume that it is the source of the problem.  Please consider wicd as a band-aid, a temporary solution until the true issue can be unearthed.

2) Note: if you follow these steps and then open the Network Tools from System -> Administration, you are still unable to configure eth0 and eth1 because they still "don't exist".  However, a) they will show up in ifconfig, and b) you can still select them in the drop down menu and perform the standard network tests with them.

These two things make me very nervous- although I'm glad to know that I have a wired connection, you can bet I'll be forwarding several bug reports to the appropriate folk.  Hope this helped, and if I find out anything else I will bump the thread.

---

