---
title: "Has anyone got Samba to work?"
date: 2007-02-04
forum: Networking &amp; Wireless
---

### Post by msimon1960 on 2007-02-04
Just a bit of a 'shout-out' to the community to see if anyone has got SAMBA to work with 6.06/6.10?

The official documentation is loaded with obvious errors.  I'm not getting anywhere with it.

Matt.

---

### Post by gradedcheese on 2007-02-04
I've used it in 6.06 and am now using it in 6.10.  What specifically are you having trouble with?

---

### Post by sympeltun on 2007-02-04
samba gave me problems too, it actually caused me to almost delete my entire partition (22.4 gb worth of files) but i was lucky and saw that it didnt happen in time. i'm actually looking forward to the replies on this forum since it'll hopefully help answer my doubts as well.

---

### Post by msimon1960 on 2007-02-04
I've installed 6.06 and 6.10 on a couple of differet computer (A p3, an AMD 1800, and a P4 dual) in the course of trying to get samba to work.

two problems:

1. The shared folder is not recognized by the other Ubuntu machines or Windows boxes I have in the house.  The browse feature doesn't appear to work very well.  Even on the server itself I can only browse to it if I keep double clicking on the icons until the system responds.

2. Permissions -- I just want one big shared folder than everyone in my family can use -- create folders, read and write files as they choose.  Security is of zero concern.  I can create a shared folder but every workstation is locked out from write access.

The official documentation on setting up a Samba share is riddled with errors.  Even as a newbie I found lots of errors in the first 3-4 pages.

Could you step me through setting up a simple samba share?

Matt.

---

### Post by gradedcheese on 2007-02-04
Ok.  The file you'll need to edit is /etc/samba/smb.conf (as sudo)

Scroll to the end of the file to add a share.  For example, for a 'everyone' share with a little security (ie: they must be users samba knows about) you can add:

```
[sharedfiles]
  comment = shared files for everyone
  path = /path/to/actual/directory
  valid users = @users
  force group = users
   create mask = 0660
   directory mask = 0771
   writeable = yes
   vfs objects = recycle
```

The name in square brackets is the name of the share, what follows below are its settings (until the next share name is found).  @users means anyone in the smb users can access it.  Now, you want to add people to the smb users:

sudo adduser user_name_here
sudo smbpasswd -a user_name_here

This creates a user on your machine and then adds them to samba's users list.

I'm afraid I can't tell you how to make a share that lets anyone access it (even those without accounts) because I never do that :)  However I bet you want to look at the 'valid users' option in the docs and see what you can put there for that.

After smb.conf changes, do:

sudo /etc/init.d/samba restart

---

### Post by dmizer on 2007-02-04
the wiki documentation for samba is shy of what's really needed.

try the first to links in my sig.  first link is to set up the samba server, and the second link is for connecting to windows computers with your ubutu box.

---

### Post by msimon1960 on 2007-02-04
> **dmizer said:**
> the wiki documentation for samba is shy of what's really needed.

try the first to links in my sig.  first link is to set up the samba server, and the second link is for connecting to windows computers with your ubutu box.

DMizer -- I found your thread earlier and went through it meticulously on a clean 6.06 install.  Nothing.  Name resolution appeared to be the problem -- even on the server itself it was barely able to resolve the names when trying to browse under 'Places->Network Servers'.

I'll try it one more time and post the results here.

Matt.

---

### Post by msimon1960 on 2007-02-04
Dmizer

wins support = yes ?

Is the winbind package required for this to work or does Samba have some sort of embedded system that acts like a WINS server?

---

### Post by dmizer on 2007-02-05
yes, the winbind package is required, along with configuring /etc/nsswitch.conf in order for name resolution to work.

however, if you're working in a dhcp environment, your smb.conf file should have the wins support = no.  this option should only be turned on if you want your linux samba server to be set up as your netbios domain name server, and this only works in a static network.

samba domain name resolution comes from the "name resolve order" option like so:
```
[global]
        name resolve order = hosts [COLOR="Red"]wins[/COLOR] bcast
```

name resolution is sometimes a problem in an all linux environment.  also disabling ipv6 can help that as well.  finally, checking your dns server addresses and making sure that your router is NOT listed as your primary dns server will also help.

---

