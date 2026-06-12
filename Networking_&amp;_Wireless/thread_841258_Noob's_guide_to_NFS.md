---
title: "Noob's guide to NFS?"
date: 2008-06-26
forum: Networking &amp; Wireless
---

### Post by KenBW2 on 2008-06-26
Can someone please provide me with/point me to a really, really easy to follow guide to setting up an NFS share. Gutsy used to do this in the GUI, but it seems to have been removed in favour of SMB - I don't have any Windows PCs on my network, so I don't need a Windows-compatible sharing system.
Any help appreciated :)

---

### Post by nixscripter on 2008-06-26
I can give you the short version here:

1. Set up an exports file, **/etc/exports**, with the directories and hosts that can mount them. See the exports man page for more details.

2. You'll need portmap, which I believe comes with the system. Start it with: ```
sudo /etc/init.d/portmap start
```

3. You'll need an NFS daemon. I believe unfsd is the package of choice in this case, which can be installed with the Synaptic package manager. Again, once you have the exports file, start it up: ```
sudo /etc/init.d/unfsd start
```

That should be it. The exports file appearance (e.g. permissions of mounted volumes) depends on what you're using it for. A page containing some common options (a page in a much larger, more complex document) can be found here: [http://www.faqs.org/docs/linux_network/x-087-2-nfs.exports.html](http://www.faqs.org/docs/linux_network/x-087-2-nfs.exports.html)

EDIT: options and more information about the daemon can be found here: [http://linux.die.net/man/8/unfsd](http://linux.die.net/man/8/unfsd)

Hope this helps.

---

### Post by a0m0a on 2008-06-26
> **KenBW2 said:**
> Can someone please provide me with/point me to a really, really easy to follow guide to setting up an NFS share. Gutsy used to do this in the GUI, but it seems to have been removed in favour of SMB - I don't have any Windows PCs on my network, so I don't need a Windows-compatible sharing system.
Any help appreciated :)

Hi! I found a good guide from here. 

Check this URL. 

[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

Have a nice day!

---

### Post by KenBW2 on 2008-06-26
Looks like I've manageed it using this guide:
[http://www.ubuntugeek.com/mount-network-file-systems-nfssamba-in-ubuntu.html](http://www.ubuntugeek.com/mount-network-file-systems-nfssamba-in-ubuntu.html)
Seems the problem was that I was using hostnames when I should've been using IP addresses. Not sure why but there you go.

My next issue is how can I get my DVD and CD drives mounted in the same way? I tried to do it the same as I did my ~/ directory but it moans about permissions. I'm using an eeepc so that functionality could come in very useful...

Thanks again

---

