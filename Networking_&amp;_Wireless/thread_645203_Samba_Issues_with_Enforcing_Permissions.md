---
title: "Samba Issues with Enforcing Permissions"
date: 2007-12-19
forum: Networking &amp; Wireless
---

### Post by Ashly on 2007-12-19
Hi all.

I've got a samba server enforcing permissions like so:
```
        force group = webdevs
        security mask = 0660
        directory security mask = 0770
        force directory security mode = 0770
        force security mode = 0660

```

I've mounted the server via fstab like so:
```
//10.0.0.101/webs  /home/ash/Webs  cifs    user=ash,password=troutfish1,UID=1000,GID=1000,user    0       0
```

Now the problem arises when I try and copy files to the mounted directory. If I use a simple "cp foo bar -R", it creates the highest directory, then fails to put anything in it.

If I type the same command again, it copies the files to the directory, creates any subdirectories, but fails to put any files into those.

The problem appears to be that for a brief moment after creating a directory, the permissions don't allow me to write to it. I've confirmed this because when watching the directory in Nautilus, the "read only" icon appears momentarily over the top of them after they're created.

I'd love to know if anyone has the same problem, or knows how to fix it. I'll keep fiddling and if I find a solution on my own, I'll post it here.

Edit: Turns out this is happening with a plain default samba config with no security modes/masks. What is going on? >_>

Also: Apologies, this appears to be in the wrong forum. I can't see a more appropriate one on first glance, but I just saw the description for this one and it's way off.

---

### Post by jetsam on 2007-12-19
Possibly the uid is the wrong one for user ash?  You can check this in a terminal with:
```
id ash
```
Try changing the mount to:
```
//10.0.0.101/webs  /home/ash/Webs  cifs    user=ash,password=<*your_password*>,UID=ash,GID=ash    0       0
```
I'm not sure what effect that extra "user" is having...

Then, I think you need to be careful masking out the execute bits.  Samba uses them for different purposes than unix does.  I'd actually avoid the "security" properties altogether unless you really know you need them.  I think this will work as an alternative:

```
directory mask = 0771
force directory mode = 0770
create mask = 0771
force create mode = 0660
```

Speaking of security, you should edit your password out of your post unless it's a fake.

---

### Post by Ashly on 2007-12-20
Thanks for the help.

I've tried changing the Samba config to that, but it's not working. The problem I was initially having to warrant the security properties was that Nautilus was changing the permissions of the files after the create mask was applied, so the webdevs group couldn't write to them.

Caused all kinds of problems.

I'll try editing my mount now, and will get back to you.

---

### Post by jetsam on 2007-12-20
I did some testing, and you do seem to need at least some of the "security" properties to get samba to enforce permissions on a cifs mount.  

This is what I ended up with to force group read and write permissions on both directories and files:

```
force security mode = 0660  
directory mask = 0777
force directory mode = 0770
force directory security mode = 0770
```

If that works for your situation...  

The only real concern I think with your original was that masking out the owner execute bit can cause problems with some Windows software, as Samba by default maps that bit to the Windows "Archive" property.  

I don't think that the masks and modes are causing the weird behavior you described in your post, though.  Like you said, it's happening for even the default share for you.  If the above changes to the mount don't fix it, you could try adding 'noperm' to your mount options.  This should disable client side permission checking on a cifs mount.  Server side permissions will still be enforced.

---

### Post by Ashly on 2007-12-23
You sir, with the knowledge I could be jumping to premature conclusions, are fantastic. I think that's working after all.

This problem has been making my life incredibly difficult for the last week, and I think you've fixed it. Thank you. :-)

---

