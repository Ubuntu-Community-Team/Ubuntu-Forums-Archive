---
title: "NIS+NFS  sddm mounts ALL users /home"
date: 2016-09-08
forum: Networking &amp; Wireless
---

### Post by fffdddooo on 2016-09-08
Hi

I have a NFS+NIS server and Kubuntu 16.04 clients which connect to the server using automount for the /home directory.
When the computer boot sddm appear, then I log in with a NIS user and it mounts my NIS home at /home/myuser, it mouts only my user and it works fine, but when i close session and sddm appears again it seems to hang. I takes a long time for sddm to show. I've seen that the problem is that when closing session, it mounts all users homes under /home, they are mounted some minutes and then unmounted again.
If a halt the computer somethin similar happens, it mounts all users /home (when exiting session), then try to unmount them but fails and systems halt but with network file systems not cleanly unmounted, so computer is not swithed off.

Any ideas?

regards

---

