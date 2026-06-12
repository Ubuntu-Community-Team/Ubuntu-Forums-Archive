---
title: "[SOLVED] Cannot see windows workgroup"
date: 2007-04-27
forum: Networking &amp; Wireless
---

### Post by pappo on 2007-04-27
I installed Feisty 7.04 and was able to see all windows shares on my network, and the XP computer could see my Ubuntu shares.
Then I wanted to share my printer so I "apt-get install samba" and after configuring smb.conf for my workgroup i started "Places-->Network so I could acces a windows share.
I can't see the workgroup at all.  I can see, and move files from the XP computer to the Ubuntu box, but cannot see any XP shares.
I can see all windows shares with 'smbclient -L <PC NAME>"
I can see all windows shares with smbtree, but not with Nautilus.

I don't want to remove samba since I am sharing my printer and that works fine.


Any ideas?

---

### Post by dbott67 on 2007-04-27
You may need to install winbind:
```
sudo apt-get install winbind
```

And then edit your /etc/nsswitch.conf file:
```
sudo gedit /etc/nsswitch.conf
```
find this line (it may not be exactly that)

```
hosts:          files dns mdns
```and add wins, so now it looks like

```
hosts:          files dns mdns wins
```

Read through this [thread]("http://ubuntuforums.org/showthread.php?p=2438836#post2438836") (post #2) and this [one]("http://ubuntuforums.org/showthread.php?p=2539757#post2539757") for further explanations & details.  The basic problem is 'name resolution', which is cured by installing winbind.

---

### Post by pappo on 2007-04-27
dbott67

That was the fix.  Thanks.
I don't understand how adding samba messed up the nautilus browsing ?
It was working fine until I messed with it.  Isn't that always the way it goes.......LOL

Thanks again.  Ubuntu forums ROCK.

Regards,
pappo

---

