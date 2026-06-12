---
title: "How can I protect the first 64 sectors of a hard drive?"
date: 2010-01-14
forum: New to Ubuntu
---

### Post by bwallum on 2010-01-14
Hi

In dual booting Windows/Karmic using Grub2, Grub files reside on the the first 63 sectors following the first sector. Windows applications write to the 63 sectors and subsequently overwrite Grub2 files.

Is there any way of protecting the first 64 sectors of a hard drive to ensure they are not over written?

---

### Post by Paqman on 2010-01-16
Windows will overwrite Grub only when it installs it's own bootloader, which normally only happens when you re-install it. When that happens it's pretty easy to just restore Grub, you won't even lose the config files, since they reside on your actual Linux partition.

---

### Post by bwallum on 2010-01-16
It appears other Windows programmes use the space that Grub2 files reside on, notably anti-virus and restore programmes. The following is a link to the problem.

[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)

I am just trying to find out if I can protect the first 64 sectors to avoid issues with dual boot systems running Grub2. If not, then I guess I'll revert to Grub legacy.

---

### Post by MarkC502 on 2010-01-16
Your AntiVirus should not be writing to the MBR , it should scan the MBR but not write or change the contents unless somehow it is getting AV hits on your grub MBR code ( check your windows AV logs and see if it thinks it is finding bad things on the MBR - I doubt this is it though )

I found several links pointing to people having problems with diferent windows programs that came with their PC scanning the MBR and making changes thus breaking grub. You should check and see what programs are starting with your windows system and figure out which one is causing the problem and if you can just remove it and replace it with a viable alternative, I would be more than glad to suggest a free program for whatever you find is the cause of your woe.

The two specific applications I saw were an Hp ProtectTools and Novell Zenworks (ziswin.exe) but there may be others, if you can't figure it out post a list here of what software you are starting and maybe someone will know what it may be ( I have a bit -o- experience with Windows problems ). Most likely you do not need it running or installed anyway, PC's today come with 20-30 apps installed that are trials, limited time use or Proprietary management software that could be replaced by a skilled user with freeware/opensource of a higher functionality than what the PC shipped with. 

I would also turn off Windows system restore as it uses allot of disk space for the restore points while not being very good at restoring anything ( I have seen many peoples PC's where they tried to fix it with a system restore and broke other installed software worse, due to system restore not actually backing up the whole system but more like certain parts of the registry etc which is not enough for a reliable recovery with all software still functioning ). Turning it off is one of the first/best tweaks for Windows, if you need reliable backup of your system use a partition backup program to backup your whole OS not just a part of it. 


Hope this helps you figure it out. If not then post what brand the PC in question is and what starts at boot and maybe someone will know.

---

### Post by bwallum on 2010-01-17
Thanks Marc, I'll take a rain check on your offer to help out with MS probs if I may.

One of the things I do is fix viruses for people with broken Windows. It is a pain. I have been using an external drive with Ubuntu and Clam AV to pluck out the affected files without Windows running.

Then usually follows a discussion about how the virus was caught, how to avoid in the future and then logically on to installing Ubuntu. However most new comers present with a U -who? mindset and want to keep their Windows and indeed sometimes it is necessary to retain in order to run certain Windows only applications. 

I would prefer to avoid broken Grub2 altogether and the negative this places in the new Ubuntu user when you tell them it shouldn't happen, we can find the culprit I'm sure, etc, etc. They really just want a machine to work without hassle.

I guess I have around a dozen true 100% Ubuntu converts but the rest usually stick with dual boot. 

It really would be the biz to secure Grub2 from Windows interference altogether, hence this thread.

---

