---
title: "Problem with NFS and updating"
date: 2014-06-28
forum: Networking &amp; Wireless
---

### Post by bearboy518 on 2014-06-28
Hello all, good day to you.  I have 3 computers running Ubuntu and have never really had any problems, but I need help.  I have recently updated the software on my quad core computer (i also have a duo core and a laptop) and now I can not mount any drive from it, the connection just times out. I can mount other drives TO it, though.  I have done the same updates on the duo core, but I haven't rebooted. anything from the quad core will no longer mount.  The connection just times out.  I'm not sure what to do.  Everything worked fine before.  I have included a screenshot so maybe that will help.  Any advice or help would be greatly appreciated.  Thanks again!

addition:

I noticed this message when booting my laptop today.

exportfs: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.1.0/24:/home".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x


 * Exporting directories for NFS kernel daemon...        * Starting crash report submission daemon                                                    [ OK ]o 

I checked my other computers and they both throw out a message correlating to filesystems listed in /etc/exports.  Does anyone know how to solve this problem? I don't want to just start adding things when I dont know what they are.  Thanks!

---

