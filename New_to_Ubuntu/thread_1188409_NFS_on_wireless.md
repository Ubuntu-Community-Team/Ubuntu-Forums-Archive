---
title: "NFS on wireless"
date: 2009-06-15
forum: New to Ubuntu
---

### Post by guyminuslife on 2009-06-15
I'm trying to automatically mount an NFS drive at startup. Problem is, putting a line in my fstab to automatically mount it doesn't work. I can mount it just fine on the command line. I am pretty sure this is because I have a wireless connection that does not immediately connect to my network at startup---using Kubuntu 9.04, I have to put in a password for KWallet before it will connect me to my wireless network, so I assume that the NFS drive is not available when my system tries to mount devices in fstab.

In the meantime, I've set a cron job that checks if the drive is mounted, and if it isn't, mounts it. I don't consider this an ideal solution.

So I'm looking for a better way. Is there any way for me to automatically mount a network drive when I connect to the network in the same way that, say, a DVD is automatically mounted when I put it in the tray?

---

### Post by guyminuslife on 2009-06-16
I decided to use Autofs. Although I'm having trouble configuring it.

---

### Post by LowSky on 2009-06-16
telling us what issue you have could help us help you

---

### Post by guyminuslife on 2009-06-17
Yeah, I was going to try to figure that one out for myself, but I've hit a brick wall.

Basically, I can start up the AutoFS daemon, and it appears to be running and doing stuff, but the files that I'm trying to share on my remote system are not showing up. So, for instance, I'm trying to mount the remote directory server:/home/username in the local folder /home/guyminuslife/net. The command:

mount server:/home/username /home/guyminuslife/net

works well enough. Normally I don't have an actual ~/net directory, but the AutoFS daemon will, of course, create it.

However, the folder is empty. The daemon assures me that it's mounted, so it must be doing *something* with the local folder, but it's useless without the files.

My /etc/auto.master file looks like:

```

/home/guyminuslife/net  /etc/auto.gml

```

And the map file, /etc/auto.gml, looks like this:

```

*       -fstype=nfs             server:/home/username/&

```

I've also tried it with configurations like:

/etc/auto.master:```

/home/guyminuslife  /etc/auto.gml

```

/etc/auto.gml```

net       -fstype=nfs             server:/home/username

```

With no luck.

---

