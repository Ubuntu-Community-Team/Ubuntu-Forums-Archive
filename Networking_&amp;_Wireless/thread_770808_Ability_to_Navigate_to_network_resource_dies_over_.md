---
title: "Ability to Navigate to network resource dies over time.  Mounted shares still work."
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by Mysticle31 on 2008-04-27
This is a problem that plagued me when I used windows and it carried over to Ubuntu.  Basically, the ability to see the other computers in Network Neighborhood or the Network area in Nautilus dies, but I can still enter a path manually and it works.

I have 3 machines.  A Ubuntu Gutsy Laptop, A Ubuntu Gutsy Desktop, and a Vista Tablet (which is the devil and deletes my contacts every time it turns around)

I got Samba set up in the Desktop.  It hosts documents, pictures..etc over the network.  The desktop can see all three computers, and all three computers can see each other and the desktop.  I mount the samba shares and create symbolic links on the client computers to make it seamless for the user.  That all works.  I won't access Network Neighborhood or the Network area in Nautalus in order to browse for an unmounted resource for months.

Well, now I need to access the network area to get access to resources that I did not mount, and  I can't.  The desktop sees no other computer, the Ubuntu laptop sees no other computer, the vista tablet sees itself.  The ability for the computers to "see" each other just dies.  It did something similar when I was on XP.  Seems like a black magic to me!

All of the mounted shares still work.  I can enter the path to a resource and it will work, I just can't navigate to it.

Any ideas?

---

### Post by Iowan on 2008-04-27
Find this section in your (desktop) smb.conf:```
# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
;   domain master = auto

```Try uncommenting that last line, save the file and restart Samba.
Another option:```
local master=yes
os level= 65
preferred master= yes
```

---

### Post by Mysticle31 on 2008-04-27
> **Iowan said:**
> 
Another option:```
local master=yes
os level= 65
preferred master= yes
```


Bingo!  :popcorn:  Thank you much!

What did this do anyway?

Also, how come when I go into Windows Network in Nautalus under Network (smb:///) it displays nothing.  It doesn't even try to load the page or scan for other computers or whatever it does.  However if I just go to Network and not click on the windows network icon (Network:///) it will display the hosts and the aforementioned windows network icon?

---

### Post by Iowan on 2008-04-29
The master browser (not related to Master Blaster ;) ) is the machine that keeps a list of who's on the network. The first version DEMANDS to be master (my book mentions yes/no answer - doesn't cover auto). The second version is more political... I'd like to be elected boss, and I'd like to cast 65 votes for me. In case of a tie - I win.

I'll need some research to cover smb:/// (haven't done that yet).

---

