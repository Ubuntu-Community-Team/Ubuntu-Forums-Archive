---
title: "Wubi Uninstall Safe?"
date: 2010-09-28
forum: New to Ubuntu
---

### Post by MrJLBrown on 2010-09-28
Well, this is my first thread in ubuntuforums, maybe the last unless I need critical help. What I have is a general question. I have used the Wubi installer to install 10.04 on my netbook (It's an Asus Eee PC 1005HAB running XP SP3, but that might be irrelevant). I really only have a novelty interest in Ubuntu (sorry, I can see already see lots of users wrinkling their noses in disgust) and I really like using it. Problem is yesterday after installing some updates to it I restarted and found that I couldn't boot back into Ubuntu. I chose it from the OS screen, and it would almost act normal and mention NTFS like I would choose from normally but it is yanked away and the computer restarts.

Now, I'm not really that interested in fixing it even though I suspect it's something to do with GRUB which I don't know anything of. I'm really just very cautious of uninstalling it because I don't want to kill my booting so I'd be forced to do everything from lupu until my next computer.

I'm in windows, I select add/remove programs and I see Ubuntu. If I click uninstall, and Ubuntu is removed, will I be able to safely boot back into windows next time I power on and wubi again? Thanks.

---

### Post by jtarin on 2010-09-28
I would recommend an excellent windows program called [RevoUninstaller]("http://www.revouninstaller.com/revo_uninstaller_free_download.html"). Installed it wil scan your system for installed programs then you have the option of removing them with the programs uninstaller plus some additional removal tools that are not usually done by the softwares uninstaller. You are free to use what you think best though. It's your system. I have no experience uninstalling WUBI so someone else might advise you better. I can only go by personal experience in recommending this application.

---

### Post by garvinrick4 on 2010-09-28
Mr JLBrown by your first line it seems you might be a very young person. You can use the add and remove programs to uninstall or you can go to your C: drive and find Ubuntu folder right next to Users  and use the uninstall in the folder. Wubi install boots off of the Windows grub so it will be gone and  you will boot straight into Windows. 
Here is a site about boot loaders.
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by beew on 2010-09-28
I had uninstalled WUBI before , I only used it once and decided to go for a real dual boot instead. Uninstalling Wubi was just like uninstalling any Windows program. I used the Revouninstaller like jtarin suggested. As I recall  Wubi removed itself very cleanly as Revouninstaller didn't find any registry entry or orphaned file left  which would require further cleaning after Wubi's uninstaller did its job.

P.S. Get the free version of Revo, if you download the pro version it will expire after a month.

---

### Post by wilee-nilee on 2010-09-28
> **garvinrick4 said:**
> Mr JLBrown by your first line it seems you might be a very young person. You can use the add and remove programs to uninstall or you can go to your C: drive and find Ubuntu folder right next to Users  and use the uninstall in the folder. Wubi install boots off of the Windows grub so it will be gone and  you will boot straight into Windows. 
Here is a site about boot loaders.
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708")

+1 on the un-installer in the Ubuntu file in XP.

@OP I wouldn't let a wubi install that got away, be a representative of Linux or Ubuntu at all. Open source has its good, bad, and ugly side, but what you have encountered is specific to wubi, quite likely.

You can easily dual boot and find out what you really need.

---

### Post by MrJLBrown on 2010-09-28
> Mr JLBrown by your first line it seems you might be a very young person.  You can use the add and remove programs to uninstall or you can go to  your C: drive and find Ubuntu folder right next to Users  and use the  uninstall in the folder. Wubi install boots off of the Windows grub so  it will be gone and  you will boot straight into Windows. 

Heh, yeah. I'm definitely a young Linux user considering I've only just heard about it a year ago--I'm really only twenty and I'm also a bit of an idiot about this stuff.

I think I've gotten enough help here to conclude I can safely uninstall Ubuntu. I'm also going to make note of the bootloader tool in case problems do arise.

---

