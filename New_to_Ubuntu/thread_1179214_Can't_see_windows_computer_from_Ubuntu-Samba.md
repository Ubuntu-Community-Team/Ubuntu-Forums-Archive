---
title: "Can't see windows computer from Ubuntu-Samba"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by raymondvillain on 2009-06-05
Have a wireless network.  From my windows (running Vista) laptop I can see my Ubuntu desktop (running Jaunty) and access files on it.

From the Ubuntu Desktop if I go to Nautilus>network I can see the windows machine on the list, but when I try to display the shared files on that machine I get a window from within Nautilus that says "opening VULCAN" (the name of the windows machine) and then, after a while, that window is replaced by another (actually a message box) that says "unable to mount location, failed to retrieve share list from server".

Is there some way to avoid this?

All taken care of.  See reply #5.

---

### Post by DBrocks on 2009-06-05
I know this is a stupid question, but is the windows running any shares? I think that if there are no shared folders, then Ubuntu throws up that error.

---

### Post by cmnorton on 2009-06-05
Is your Ubuntu system in the Windows systems' workgroup/domain? Look at /etc/resolv.conf.

---

### Post by raymondvillain on 2009-06-05
There are shared folders on the windows machine.  Some are in the "Public" folder and some are buried in the file system on the main drive, but these latter files have appropriate share permissions set on them.

On the Linux machine (Ubuntu Jaunty), there is a folder /etc/resolvconf but it has no files in it that make any sense to me.

/etc/resolvconf/update-libc.d/avahi-daemon is the only file in the /etc/resolvconf folder on my machine and Nautilus says it is a shell script.

I'm pretty sure my Ubuntu machine is in the same domain and also in the same workgroup.  How do I tell for sure?

---

### Post by Nixie Pixel on 2009-06-05
I have similar problems from time to time - what helped is making sure winbind is running on your Ubuntu machine (and if not, installing it):

```
sudo /etc/init.d/winbind restart
```

Also make sure that in /etc/nsswitch.conf your "hosts" line reads like this:
```
hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4
```

The important bit is having "wins" in front of "dns." 

This should help with connecting to windows shares.

---

### Post by raymondvillain on 2009-06-05
Thanks Nixie pixel I tried your suggestions but no luck.  Are there other lines in the /etc/nsswitch.conf file I ought to play around with?

---

### Post by raymondvillain on 2009-06-05
But wait!  That was it!

After 2 restarts, and sudo etc/init.d/winbind restart I can see folders on the windows machine!

Cursed Vista!  What a waste!

Thanks, Nixie Pixel!  All hail to thee!

---

### Post by cmnorton on 2009-06-06
> **raymondvillain said:**
> There are shared folders on the windows machine.  Some are in the "Public" folder and some are buried in the file system on the main drive, but these latter files have appropriate share permissions set on them.

On the Linux machine (Ubuntu Jaunty), there is a folder /etc/resolvconf but it has no files in it that make any sense to me.

/etc/resolvconf/update-libc.d/avahi-daemon is the only file in the /etc/resolvconf folder on my machine and Nautilus says it is a shell script.

I'm pretty sure my Ubuntu machine is in the same domain and also in the same workgroup.  How do I tell for sure?

Under System --> Administration --> Network, you can define your domain name there. This should show up in /etc/resolv.conf. /etc/resolv.conf should also have a search directive in it which helps when attaching to Windows-defined printers via smb.

---

