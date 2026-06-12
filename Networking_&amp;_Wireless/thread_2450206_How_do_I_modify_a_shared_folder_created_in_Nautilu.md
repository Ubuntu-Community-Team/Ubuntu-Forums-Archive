---
title: "How do I modify a shared folder created in Nautilus?"
date: 2020-09-09
forum: Networking &amp; Wireless
---

### Post by Paddy Landau on 2020-09-09
I'm running Ubuntu 20.04.

I created a folder, which I made public (chmod a+rwx), and shared it through Nautilus as a public folder open to all. This is to share with other Ubuntu machines on the local network.

I wish to modify the name of the share. However, I can't find out how to do that. The share isn't listed in /etc/samba/smb.conf, and I can't find a place in Nautilus to make the change. It would also be interesting to find out how to stop sharing the folder if I need to sometime in the future.

How can I modify or delete the share?

**EDIT: Solution:** I originally created the share using root, but forgot about that, which is why I couldn't change the share.

---

### Post by Morbius1 on 2020-09-10
> and shared it through Nautilus as a public folder open to all.
OK, you went through Local Network Share which is a samba usershare ( nautilus-share ).
> which I made public (chmod a+rwx)
More of an FYI but there was no need to do that - nautilus-share would do that automatically.
> I wish to modify the name of the share. However, I can't find out how to  do that. The share isn't listed in /etc/samba/smb.conf, and I can't  find a place in Nautilus to make the change. It would also be  interesting to find out how to stop sharing the folder if I need to  sometime in the future.

Right click the shared folder and then select Local Network Share again and you can modify name, sharing parameters, or even "unshare" the folder.

Samba usershares are defined in /var/lib/samba/usershares. The syntax is different from a Classic Samba share you would find in smb.conf and is usually not edited directly.

---

### Post by Paddy Landau on 2020-09-11
Thank you for your help, Morbius1.

I was seriously confused as to why what you suggested didn't work…

… until I realised that I'd created the share using root (sudo -H nautilus)!

When I started Nautilus in root, I could do what I needed.

So, thanks again. The problem lay with me.

---

