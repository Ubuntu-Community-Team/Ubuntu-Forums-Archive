---
title: "Client hangs when NFS mount isn't available"
date: 2017-03-20
forum: Networking &amp; Wireless
---

### Post by usndmac on 2017-03-20
I have nfs shares set up on a PC running Debian.

My clients mount the shares in fstab with only the nfs option like this:
192.168.###.###:/Music /home/mac/tunes nfs

If I take the client to another network, the client takes a long tome to boot, but, eventually does boot and of course the shares aren't there.
Is there an option that will tell it not to wait if the share isn't available? I could shorten the timeout...but, that doesn't seem like the best approach.

If, connected to my net, and the Debian PC is shutdown BEFORE the client, the client appears to hang when it is shutdown.

I'm assuming I need other options for the fstab mount, but after reading the man pages for fstab it's not clear any options would help with this issue, or that other options may cause other issues.

What am I missing?

---

### Post by SeijiSensei on 2017-03-20
If you're moving the client around a lot, you might be better off mounting the share manually after booting rather than through /etc/fstab:

```
sudo mount server:/share /mount/point
```

Otherwise you can write a bash script that checks to see if the server exists and only mounts the shares when it is available.  You can run the script at boot by referencing it in /etc/rc.local.

Another option is to [change the timeout option]("http://manpages.ubuntu.com/manpages/wily/man5/nfs.5.html") in /etc/fstab.  

>  timeo=n        
The  time  in  deciseconds  (tenths of a second) the NFS client waits for a response before  it  retries  an  NFS  request.

You'll probably also need to set "retrans=1" so the client will only try to mount the share once before giving up.

---

