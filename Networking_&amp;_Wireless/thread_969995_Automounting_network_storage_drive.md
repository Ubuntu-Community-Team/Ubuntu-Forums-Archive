---
title: "Automounting network storage drive"
date: 2008-11-03
forum: Networking &amp; Wireless
---

### Post by Pirate King on 2008-11-03
Hey there, I'm not really sure if this is the correct spot for this or if my title is even one I should be using.

A little while ago my brother and I built a network storage server using RAID, running Windows Server 2003. In Ubuntu, I can mount it when I go to Network, but I wanted it to automount or at least be seen as a local drive (like how you can map the partitions in Windows). 

Anyway, I looked at a few tutorials on editing the fstab file for this to work, but I've been having trouble getting it working. What I've come up with is this on the end of my fstab file:

> 
//10.0.0.60/Asterix  /media/Asterix  cifs  username=Administrator,password=*****  0  0

//10.0.0.60/Obelix  /media/Obelix  cifs  username=Administrator,password=*****  0  0

I just added the stars to hide the password but it shows in the fstab file.

I get the response:

> 
mount error 113 = No route to host
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
mount error 113 = No route to host
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)



I've also tried its name (UBENANTU-D5Z5ZA) instead of 10.0.0.60, and it yields the same results. 

Also, when I go to Network and open up UBENANTU-D5Z5ZA, there's also drives e$ and f$ (for some reason?). I think they're just the same as Asterix and Obelix - they don't appear in Windows.

Anyway, I hope someone has a suggestion in how to get this working. Anything is appreciated.

Thanks very much in advance, friendly Ubuntu forumers! =)

---

### Post by Mordac85 on 2009-04-14
<Bump>

I'm trying to test a media center PC pulling video & music sources from my main Kubuntu box (always on) where they are shared to the rest of the family w/samba.  The idea is to turn on the media PC and not have to manually run a mount command before I can use it.

It's not just ubuntu b/c I have the same problem with other distros.  So why does *nix have such a problem with persistent drive mapping?  I just can't find a reliable method for automatically mounting that is smart enough to wait for the network to be available.  And it appears that it's not important enough for developers to address.
[list][*] **_netdev** - Not a vaild option for fstab
[*] **mount -a in rc.local** - Doesn't end up with the share mounted even though "sudo mount -a" works fine
[*] **Other rc scripts** - same as rc.local, a flash of a terminal screen but no mount succeeds[/list]
If anyone has any other ideas I'd love to be able to solve this one.  I've never used NFS before but would this be easier using NFS instead of samba/cifs?

---

### Post by Mordac85 on 2009-04-16
OK, not really solved, but a reliable workaround until some dev guru decides to change this 'feature' of not waiting to mount network sources unitl AFTER the network is up.

Add this to your /etc/crontab
```
@reboot root sleep 10;mount -a
```Adjust the sleep time as needed for your network to come up.

---

