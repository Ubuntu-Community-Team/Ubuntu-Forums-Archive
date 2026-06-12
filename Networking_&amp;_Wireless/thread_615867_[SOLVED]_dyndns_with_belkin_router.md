---
title: "[SOLVED] dyndns with belkin router"
date: 2007-11-17
forum: Networking &amp; Wireless
---

### Post by a_posse_ad_esse on 2007-11-17
This is probably a simple question, but how would I go about setting up dyndns service?  The none of the posts seem to address my particular setup.  

I have a belkin wireless g router with the service built in.  Would I simply set up 1 account, which the router monitors?  Or, should I have a separate account for each machine, even though they all share the same external ip address?

Does each machine have to be running ddclient?

What would the mount command be? i.e. mount.cifs //computerhostname@xxx.homeunix.org -o username=xxx,password=xxx?

Thank you

---

### Post by jshurst on 2007-11-20
If your router has this built in then you can just have one account for all the comptuers on the network (like you said they all share one external ip address).  I flashed my router with [http://dd-wrt.com/dd-wrtv2/ddwrt.php](http://dd-wrt.com/dd-wrtv2/ddwrt.php) and it is awesome, this added the dyndns functionality that you were talking about (if your's already has it built in then you probably don't need that).

J

---

### Post by a_posse_ad_esse on 2007-11-21
Thanks for the reply.

Here is the result thus far:
```

sudo mount.cifs //hostname/share@xxx.homeunix.com /share -o user=xxx,password=xxx
mount error: could not find target server. TCP name hostname/hare@xxx.homelinux.com not found No ip address specified and hostname not found

```

I can mount using the local ip address however.  Am I deforming the mount command?

---

### Post by a_posse_ad_esse on 2007-11-28
bump

---

### Post by a_posse_ad_esse on 2007-12-01
I guess asking my question in a different way would be "how do I use cifs to mount different machines using the same dyndns address?"

---

### Post by scxtt on 2007-12-01
are you just mounting a share from w/in your own internal network?  are you using static IPs w/in the network?

---

### Post by a_posse_ad_esse on 2007-12-03
Thank you for the reply.  Here is my current network setup:

My wife and I are both in school, and each have a laptop that is used for notes, research, etc.  These travel to several different networks on a regular basis, so a static IP would not be practical because of the need to remove network managers, etc.  The workstation and server remain on the home network.

I would like to be able to have the ability to backup/mirror files to the server and other machines, and, less importantly, access music and such from the home server.

I have also moved from cifs to sshfs, which is more secure.  I am able to mount internal machines in the same manner as before, but the problem remains of mounting them externally using hostnames.

---

### Post by a_posse_ad_esse on 2007-12-03
I looked over my post, and thought that I should include the sshfs commands in question...

This is the working command, done on the internal network
```

sshfs user@192.168.2.4:/home/user /sync/user

```

This is what I would need for the above scenario to work:
```

sshfs user@hostname:/home/user@xxx.homeunix.com /sync/user

```

This command yields a "Connection reset by peer" error.

---

### Post by scxtt on 2007-12-03
i'm not gonna say what you want to do (in the way you want to do it) is impossible, cause i know if i do, someone else is gonna say "sure, it's possible" and then i'll feel silly :p ...

they way i think you'll need to do it involves setting each server using SSH to use a different port ... the main problem w/ what you want to do, as it stands, is  that EVERY request to your dyndns IP using SSH will come in wanting to use port 22 - then the router will forward that request onto ONE machine - so you're kinda SOL if you want to use multiple machines for SSH outside of your network ...

so i'd work on getting each SSH server listening on a non-standard port and then read up on the manpage for sshfs so that you can specify a connection port ... that way each separate request on a different port can forward to its associated host.

---

### Post by a_posse_ad_esse on 2007-12-04
I am by no means attached to my methodology; what I described is simply what I thought to be the most secure and convenient method for accomplishing what I need to.  If there is a better way (or perhaps I should be less picky... a way that works), I am open to suggestions.

---

### Post by a_posse_ad_esse on 2008-02-05
I've discovered that simply using different ssh ports solves the problem.

---

