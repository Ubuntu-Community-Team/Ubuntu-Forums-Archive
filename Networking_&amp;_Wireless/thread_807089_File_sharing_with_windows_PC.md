---
title: "File sharing with windows PC"
date: 2008-05-25
forum: Networking &amp; Wireless
---

### Post by Apex-jb on 2008-05-25
I have having problems with sharing files. Under Places - Network, I can see this computer and Windows Network. If I click Windows Network I can see my windows work group. If I click my workgroup I can see my windows computers, but if I click one of the windows computers it doesn't show any of my shared files.

---

### Post by linuxmonkey on 2008-05-25
I have the exact same problem.  I am running Ubuntu on my WinXP box under VirtualBox.  I also tried running Ubuntu on my MacBook Pro as a dual boot.  Ubuntu works great, but I don't see my Windows shared folders.

Any suggestions?

---

### Post by Apex-jb on 2008-05-27
bump

---

### Post by Iowan on 2008-05-28
I don't (yet) have Hardy, but on this Gutsy machine, I have better luck with the Places>"Connect to Server" option.

---

### Post by buntunub on 2008-05-28
Did you check your Windows box firewall settings?

---

### Post by Apex-jb on 2008-05-29
Firewall settings on my Windows machine are fine.

How do I add Ubuntu to a workgroup, though? I can see my windows workgroup, but I am pretty sure my Ubuntu laptop is not a member of the workgroup.

---

### Post by mohenjo on 2008-05-29
As I read this post I decided to give this a try as well (I'm running Hardy on a test laptop and a Windows XP machine that's hooked up to my work domain).

I had the exact same issue as the original poster when I went the route he took, however when I went to Places -> Connect to Server and entered in the computer name, and share name, I was able to connect.

It did ask me for credentials, so you will probably need local credentials on that share.

As for adding Ubuntu to a workgroup, that's a great question!  I don't know how to do that, but I'm guessing if the machine was a member of the same workgroup as the share, you wouldn't need to go this route.

---

### Post by Apex-jb on 2008-05-29
I tried the Connect to Server, and it worked. Its a little annoying but I can live with it.

---

### Post by wdaniels on 2008-05-29
> **mohenjo said:**
> As for adding Ubuntu to a workgroup, that's a great question!  I don't know how to do that, but I'm guessing if the machine was a member of the same workgroup as the share, you wouldn't need to go this route.

You can set that in /etc/samba/smb.conf, but it's unlikely to work at all if you do that (see [Bug #229433]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/229433")).

This bug looks to be already in Launchpad ([#206439]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/206439")), so clearly gvfs has a few problems still. Hopefully it will all get fixed soon.

---

### Post by Apex-jb on 2008-05-30
Ok, now I can't get the Connect to Server option to work any more. Can someone post exactly what info I need to enter to do it?

---

