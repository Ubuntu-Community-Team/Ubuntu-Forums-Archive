---
title: "Mount (smb) shares on user level?"
date: 2005-08-01
forum: Networking &amp; Wireless
---

### Post by tom-ubuntu on 2005-08-01
Hi Community

Another day, another question :)

What is the correct way to mount network shares (samba in my case) on a user level? Means that I do not think, that using /etc/fstab is the correct way doing this, or am I wrong?

Is there a better way? As soon as the users logs in, his directory gets mounted, and when he logs out, the will be unmounted. Is there a good way doing this?

Thanks and regards
Joe

---

### Post by strikeforce on 2005-08-01
If you want to do it on boot you can either create a bash script or you can edit your fstab.  Either way is ok the user level settings relates to who owns the folders and the related information.

Thats a different kettle of fish.  Another way to do it GUI way is in gnome is go to Places > Network >  shares are in there.

---

### Post by tom-ubuntu on 2005-08-02
Cheers, strikeforce. Then I'll keep it like I got it now. Thought theire might be an other approach on a per user setting. Thanks again!  :smile:

---

