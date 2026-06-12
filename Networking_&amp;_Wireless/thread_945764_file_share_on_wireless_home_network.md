---
title: "file share on wireless home network"
date: 2008-10-12
forum: Networking &amp; Wireless
---

### Post by iprolonged on 2008-10-12
Hi all,

I have two machines (one desktop, one notebook), both running Hardy. I'd like to be able to access files (mostly music) sitting on the desktop from the notebook. Ideally, it'd be nice to be able to do something like Places > Network > My Music :)

As per the post title, both machines are connected to a wireless router. I know I could probably get them connected using OpenSSH (which I've used before), but just wanted to see if there was a better way?

Thanks, and appreciate any replies!

Dave

---

### Post by blastus on 2008-10-12
I use NFS over wireless. It works great. My home theater PC is connected to a WRT310N router running DD-WRT that is configured as a "client bridge" The router maintains a wireless connection to my D-Link router which is the access point. So I don't have to mess with wireless drivers or setup or anything on my HTPC.

[SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

### Post by iprolonged on 2008-10-15
Thanks for the response, but I now have infinite further questions... :(

I installed NFS and set up my /etc/exports as per instructions, but when I try to export the share I get: "Warning: /media/BAG does not support NFS export." It's an NTFS external drive: bummer.

Would it be as easy to use Samba at this stage?

Again, thanks for the reply, really appreciate it.

Dave

---

