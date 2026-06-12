---
title: "Problems browsing Windows shares with Gnome Nautilus"
date: 2008-06-13
forum: Networking &amp; Wireless
---

### Post by aldeby on 2008-06-13
Ever since I installed Ubuntu Linux Hardy 8.04 I'm facing problems in browsing Windows shares with samba.

Even though I can see the Windows Group and the Windows Hosts when I click on them I only get an empty window. No shares are listed.

Through smbtree utility I managed to figure out the main problem was that I was using OpenDNS domain name servers. For some weired reasons OpenDNS dns try to resolve also local hosts and thus Samba cannot locate the local networked computer on which the shares are.

The error showed in smbtree when this output was shown:

timeout connecting to 208.69.34.132:445

clearly 445 is the Netbios port and 208.69.34.132 is an external IP linked to OpenDNS.

Reverting to my ISP DNS partially solved my problem.

Now smbtree does no more show all the computers in the network, however with GNOME Nautilus I can see them all and enter them. Nonetheless inside I can only see two folders: print$ ad public. I had configured several other shares restricted to a particular user, but these are not shown!

I noticed I can access these restricted to login shares by typing in the complete path i.e. smb://pc1/folder1 however I cannot actually access these folders (and no login prompt is shown) unless I substitute the shared pc (pc1) with its IP address.

Only this works:

smb://192.168.1.1/folder1

[SIZE="3"]Any idea on how to display shared folders without **Everyone** ownership (whose access is restricted to a login)?
Any idea on how to access those folders without needing to know the server IP address?[/SIZE]

I wonder why there are all these problems with Hardy... the previous version, Gutsy worked flawlessly with Windows shares.

---

### Post by panteraz on 2008-06-26
same problem here...

---

### Post by michaelzap on 2008-06-26
Samba can definitely be a bit troublesome with Windows shares, but I seem to have gotten it to work after reading a bunch of forum posts and trying different things. I also find that Firestarter can block Samba communications, so try turning it off (if you're using it) while debugging problems. What I think got it working properly for me can be found in this thread:

[http://ubuntuforums.org/showthread.php?p=5155923#post5155923](http://ubuntuforums.org/showthread.php?p=5155923#post5155923)

Note that in the host line of /etc/nsswitch.conf wins must come before dns (if it's the other way around it doesn't work).

I can see Windows shares now, including those for which I don't have access, and I'm prompted for a username and password when I try to access such unmounted shares in Nautilus (I mount the ones I use all the time at login with a username and password in /etc/fstab).

---

### Post by techmin on 2008-07-13
use this method to solve the problem:

sudo gedit /etc/samba/smb.conf

Find:

# What naming service and in what order should we use to resolve host names
# to IP addresses
;  name resolve order = lmhosts host wins bcast    <&#8212;- change this line to:

name resolve order = lmhosts bcast wins host

save and exit.

A this point restart you network service:

sudo /etc/init.d/networking restart

---

