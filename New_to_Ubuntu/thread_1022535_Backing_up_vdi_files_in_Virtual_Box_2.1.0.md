---
title: "Backing up vdi files in Virtual Box 2.1.0"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by Orographic on 2008-12-26
Hi there,

I'm quite new to VB and am trying to work out how to backup a guest XP install on VB 2.1.0 in Intrepid, so I don't have to re-activate XP if I re-install Intrepid with a new version of VB.

Example: I've installed VB 2.1.0 on Intrepid and have installed a new XP VM and then installed XP. How do I backup my new XP install? 

Is this example correct:

VBoxManage clonevdi ~/.VirtualBox/VDI/WindowsXP.vdi ~/WindowsXP_Backup.vdi


I don't currently have VB installed on this Intrepid machine but where do I find the VBoxManage menu?

Thanks all.

---

### Post by Coder543 on 2008-12-26
I think you should just backup the entire virtualbox folder. Correct me if I'm wrong, somebody, but I think it is ~/.virtualbox/

---

### Post by obsrv on 2008-12-26
Don't quite understood but try installing virtualbox or virtualbox-ose and then load backup system :)

---

### Post by Coder543 on 2008-12-26
This person wants to backup an actual VM.

---

### Post by Orographic on 2008-12-27
I understand that if you copy the VB folder, the .VDI files in here cannot be restored if I re-installed intrepid with a new VB as they have different IDs associated with them?

---

