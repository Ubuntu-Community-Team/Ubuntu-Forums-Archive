---
title: "Share Files with Windows Machine - Do I Need Samba"
date: 2007-05-26
forum: Networking &amp; Wireless
---

### Post by Ingla on 2007-05-26
Hello.

I'm running Dapper and have a Windows machine (separate computer in another room). I want to be able to send files from Ubuntu to XP (NTFS) and vice versa.

I know nothing about networking in Linux, although I have several Windows boxes connected via a router.

I have been looking into the subject a bit and have been under the impression that I need to learn Samba (a daunting undertaking, from what I've read). 

Meanwhile, I've seen a post ([https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)) which says," Samba is not necessary to: access shared folders, drives and printers on a Windows computer (that is, act as a client with Windows servers), you only need a smbfs plugin. See MountWindowsSharesPermanently"

However, I don't know what the author means by "access". It sounds like he means "one-way" from Windows to Linux. I want to be able to send files (write to) an NTFS drive which, by all accounts is dangerous for the Windows drive if done in any direct way.

Can this be done (safely or at all) with the smbfs plugin, or do I need to use Samba (assuming that's safe for the XP drive)? Any other ways to do this?

Also, if I'm going to use Samba, I need to find a How-to along the lines of "Samba for Newbie Idiots".

Can someone enlighten me?

Thank you very much.

---

### Post by ruy_lopez on 2007-05-26
Its only one-way in so far as you mount the Windows shares in Ubuntu. You can still transfer files to and from the Windows shared folder. If you want to send a file from Ubuntu to Windows, you just drop the file on the shared folder. And if you want to get a file from Windows, you share the folder, and drag it from the share. So its two-way, in terms of what you can do. But its one-way, in terms of which is the server and which is the client. The transferring will all take place on the Ubuntu box.

If you want to sit at your Windows box and browse the folders on the Ubuntu box, yes, you need to implement Samba.

Best to try it, see if it does what you want. Open up the properties tab for a folder in Windows and enable sharing. Then in Ubuntu goto Places-->Network and try to browse the Windows Network icon. See if you can *access* the folder.

---

### Post by tgm4883 on 2007-05-26
Only install samba if you need to access the linux machine from the windows one.

---

### Post by Ingla on 2007-05-26
Thanks for the replies.

The remaining question is safety. 

On my Linux machine, I also have a Windows hard drive (not dual boot - separate hard disk. I boot into the OS I want by changing CMOS boot sequence).

On this machine, I can mount the Windows drive from Ubuntu, of course, and transfer files from Windows to Linux. I  CANNOT transfer files TO the Windows drive (unless I mount a FAT 32 system). Even if I succeed in mounting an NTFS drive with write privileges, it is supposed to be very risky to write to it. People say it can wreck Windows.

The question is: Can I use the smbfs plugin method to copy files from Ubuntu to XP on an  NTFS file system (on a different machine), or is that dangerous too?

Thanks very much.

---

### Post by Ek0nomik on 2007-05-26
You can transfer files via SSH too.

WinSCP is the client you use in Windows to grab files from your Linux box.

---

### Post by ruy_lopez on 2007-05-26
I see, you are asking whether its safe to share a Windows folder, because its unsafe for Ubuntu (or linux in general) to write to NTFS?

When you use Windows sharing, and the Ubuntu box writes to the shared folder, its not actually Ubuntu that does the write. Ubuntu merely sends the data in a format both machines understand. Once Windows receives the data, it writes it to the filesystem. Since Windows can write to NTFS without any problems, you have no worries.

Mounting a NTFS partition in Linux  is a low-level kernel filesystem procedure.

Mounting a Windows share is something else entirely. Samba acts as a translation bridge between the two different filesystems.

All samba does is implement a protocol for sharing file and folders, the Windows kernel will take care of the low-level stuff.

In short, its safe as houses. You have nothing to worry about.

---

### Post by dagabu on 2007-05-26
I cant get access to the Ubuntu shared folders from my XP box but your instructions are Greek to me. I'm not a Linux guy but want to start with this install so please explain EVERYTHING I need to do to have access the these folders, please?

dagabu

---

### Post by ruy_lopez on 2007-05-26
On XP pick a folder you want to share.

Right click folder, choose properties, then change to the sharing tab. Enable sharing.

Now, on Ubuntu box. Navigate "Places-->Network-->Windows Network." from the taskbar.

---

### Post by dagabu on 2007-05-26
No can do, the user name password box comes up, I fill them in and... nothing! 

I have Samba downloaded but have no clue how to install it. Windows has .exe files, does Linux?

dagabu

---

### Post by dagabu on 2007-05-26
BTW, I have shared permissions on all folders, nothing left to configure. 

dagabu

---

### Post by ruy_lopez on 2007-05-26
You have to put in the password and username for the XP account. Most people don't have this enabled, in which case you would just leave the password blank.

---

### Post by Ingla on 2007-05-26
ruy_lopez, Thank you.

I didn't even have to install anything (guess the plugin comes with the distro). Windows folders were already shared for use on Windows network. So, it seems it just works.

Thanks a lot.

---

