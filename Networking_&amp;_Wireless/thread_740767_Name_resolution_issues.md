---
title: "Name resolution issues"
date: 2008-03-31
forum: Networking &amp; Wireless
---

### Post by RRosset on 2008-03-31
Hey guys. Yes yes... it's me! Bob again! hehehe, well, i don't know how to search this since i searched for networking issues for more than 2 weeks. Anyways, my problem is I can't see one of my machines in the network folder. I'm able to connect over IP but not through it's name.
I've got two machines, one called Laptop and another one called Desktop.

Honestly, i'm doing my first steps in ubuntu and linux in general. It took me 1 week to discover that i can connect trough IP, but in the other hand i'd be glad if i learn WHY i can't use the network folder.

I'm using both samba and nfs. And again. I'm able to connect through IP, my problem is I just can't see other machines under network folder.

Cheers guys!

Bob

---

### Post by Eiríkr on 2008-03-31
Samba is designed for Windows networking, and thus replicates a lot of Windows behaviours, including built-in broadcasting to announce shares.  NFS is Unixy all the way, and thus is both much lighter-weight than Samba, and it also includes no broadcast announcing.  You can set up NFS share announcing via the Avahi zeroconf daemon as I describe in [post=4387032]this post[/post], but even so, the default Gnome desktop Nautilus browser (the default in Ubuntu, but not for either Kubuntu or Xubuntu) has no ability to view NFS shares before they are mounted onto the local filesystem (usually by running the [font=courier]mount -t nfs <options>[/font] command in a terminal).  Konqueror meanwhile (the default for Kubuntu) *can* view unmounted NFS shares.  Anyway, if you just have the regular Ubuntu install and are therefore using Nautilus, you won't be able to see unmounted NFS shares even after setting up Avahi.  

Samba, meanwhile, should be viewable.  This suggests that there's a problem in your /etc/samba/smb.conf file.  Assuming that both your Laptop and Desktop machines are Linux (Ubuntu or otherwise), you'll need Samba installed and configured on both if you want two-way sharing.  If you've already done this, then please post your smb.conf files from *both* machines, and label which is which.  

Cheers,

Eiríkr

---

