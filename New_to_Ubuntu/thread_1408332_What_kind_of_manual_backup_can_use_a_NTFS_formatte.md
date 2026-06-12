---
title: "What kind of manual backup can use a NTFS formatted HDD?"
date: 2010-02-16
forum: New to Ubuntu
---

### Post by nooby on 2010-02-16
I know nothing about backups. But I want to save changes in my Ubuntu 9.10 and one way would be to make new iso of it and start anew from that one. But that takes about 1GB soon enough. 

If I knew what directories the changes end up in on the "live user sessions" and if I manually saved them on the NTFS and then at boot used Terminal command to get them back? That would work well and not take more space than the changes are themselves? 

How does one do such? What does one write in the CLI to find out where all the changes went and how does one tell the path to them?

Here is an example from googled to ask same thing. But this is slack and I trust that ubuntu is Debian and not Slackware. 

[http://www.pendrivelinux.com/slax-savingrestoring-settings/]("http://www.pendrivelinux.com/slax-savingrestoring-settings/")

> For example, type configsave /mnt/sda1/slaxconf.mo to save your configs in USB flash drive into slaxconf.mo file. It will save all changed files from /root, /etc, /home and /var directories.

...
To restore your previously saved backup, use "configrestore" command. 

You can also save settings to the root directory of your existing disk partition (for example to /mnt/hda1/slaxconf.mo). 

All settings found in the root folder of any of your disk partitions ( under the name slaxconf.mo) will be restored automatically when SLAX boots.

**How does one do this in Ubuntu 9.10?**

---

### Post by Hospadar on 2010-02-16
There are many many ways to do backup, and few of them are particularly easy.

The method you linked to is primarily for live systems (like when you boot off a livecd or thumbdrive).  If you browse around the community docs in my sig you'll find a little information on persistant live sessions.  I know when I boot off a USB stick, somewhere along the line I have the option to save sessions.

However, it sounds like you want to back up an already installed linux.  There's really no easy way to backup configuration changes other than just saving everything that changed from the last backup (since there's no hard and fast rule about what is a configuration file and what's just an ordinary file.  Probably your best option is to use a backup system like [backupPC]("https://help.ubuntu.com/community/BackupPC"), which isn't trivial to set up, but once set up is very powerful.

It might for your purposes be best to just periodically burn your entire home directory to a dvd or something similar to that.  Any sort of backup solution, especially one which provides incremental steps backwards is going to end up using a fair amount of space.

---

### Post by nooby on 2010-02-16
Thanks, I read through most of these documents and they don't seem to be for newbies. I failed to find them mention if one can do the back up to a NTFS HDD and restore it from that one. 

The problem with all these are that one first has to get them from the "universe" and then do the restore. So it only works if one have internet going. Okay sometimes they exists on the CD/DVD but then you need a DVD player and the disk. 

What I need is a simpler manual system where one have a kind of CLI commands that says. 

Sudo copy and save what have changed since ubuntu started this live user session and save them on the NTFS HDD in this path directory. 

Then next time I boot up the ubuntu I just do the opposite. 

Copy from NTFS path this directory to the directories they where copied from last time. 

A kind of simple text script I can have in an email on gmail or on the ntfs hdd and copy and paste to the cli and it do its thing. 

To accomplish this one should not need to have any other permissions than to be a "live session user" 

What I can do allready now is to save anything I find on the net. 

What I have not tested is what I can save from the home and the other directories unique to the "live session user".

I need example on how does one "ls" what have changed. 
and do a copy to a path and to copy back from that path when I want to restore it. 

that way I would always be able to save and restore any changes. 

All the links I read so far are way too complicated and you need to be root or a regular user with permissions.

---

