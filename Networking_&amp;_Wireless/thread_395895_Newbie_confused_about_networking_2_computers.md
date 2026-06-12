---
title: "Newbie confused about networking 2 computers"
date: 2007-03-28
forum: Networking &amp; Wireless
---

### Post by dpeirce on 2007-03-28
I have a home network consisting of a laptop and a desktop, both with Kubuntu 6.10 installed. Both computers connect to the internet just fine (they connected themselves :^>). I'd like to be able to browse the home directory of one computer from the other. The router is a Lynksys Wireless G. Wireless Assistant shows both an eth0 (lo) and eth1 (Linksys with 5 stars). I've followed the instructions found [http://ubuntuguide.org/wiki/Ubuntu_Edgy#Networking](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Networking) HERE but have not had success.

1) System Settings -> Sharing tells me "SMB and NFS servers are not installed". "Apt-get install samba smbfs" tells me these programs aren't available but smbclient and samba-common replace them. Adept tells me that both are installed, and shows nothing for "NFS".

2) I followed the instructions on networking, including the file edits, as far as "sudo /etc/inet.d/samba restart" and got "Command not found"; tried it naming smbclient and samba-common and got the same error message.

3) In Konqueror I tried "Right click on folder -> Share folder", but there's no "Share folder". Also there's no sharing tab in "Preferences"

4) I found [http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing](http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing) this about NFS. It doesn't seem to invole samba and I'm not trying to read any windows files; is this a better way to go? This blog is for an older Ubuntu, will these instructions work for Edgy? Would I do the same thing on the other machine(s)? [http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889) These instructions mention servers and clients; would I need both on both machines?

First, I have no idea what I'm doing so I'm following instructions blindly, and I apologize for the length of this question and my verbose confusion. Is there some easy way to browse files in one computer from another? Any extra explanation will be gratefully feceived!

In faith, Dave
[email]dave@christos.cjb.net[/email], [email]dpeirce@christian.net[/email]
Viva Texas

---

### Post by MJWhiteDerm on 2007-03-28
This message will more one of sympathy then help.

I am running a LAN with disparate computers.  We have four Windows XP boxes.  My wife and stepson each have an XP box and I have two related to work and to music / slide-scanning.  Then, there are four linux boxes.  Two are Suse Linux 10.1 boxes.  One is standard ubuntu and one is xubuntu.  I can make the Suse boxes and the Windows boxes see each other, under Samba and file browsing & transfer mostly work. (Oh, then there's my Apple G-4 Powerbook laptop ...) but I'm having trouble with the ubuntu boxes.  I invoked Samba and set up the folder for file sharing, but now I'm having trouble logging into the shared file on the ubuntu box.   It doesn't like the user id and password.  My Suse box doesn't require that.  I can't figure out what I did differently.

Have you gone into the synaptic package manager to install samba?  I will send you a screen shot by email.

Michael

---

### Post by dpeirce on 2007-03-28
Michael: The odd thing is, samba isn't in adept on my laptop, only samba-common which adept says is a replacement for samba. But samba *IS* in adept on my desktop. I replaced sources.list on the laptop with the one generated at Ubuntu.org, but it still doesn't see samba. Right now I'm going through both sources.list to see which source is in the desktop but not in the laptop.

However, maybe you and others will comment on whether I need samba or NFS, as I'm not trying to browse any windows files. Would NFS be easier?

In faith, Dave
[email]dave@christos.cjb.net[/email], [email]dpeirce@christian.net[/email]
Viva Texas

---

### Post by dpeirce on 2007-03-29
OK, now a LITTLE less confusion. I got samba loaded on both machines and did configurations in SystemSettings -> NetworkSettings and Sharing. So far as I can tell, the entries look identical on both machines. I went to System Menu -> Remote Places -> Mshome in both machines.

1) The desktop sees itself but not the laptop.

2) The laptop sees the desktop but not itself. I can't transfer any directories or files from the desktop to the laptop. I noticed that files owned on the desktop by dave/dave show up on the laptop as dave/root.

Clicking for help on the system settings widget gets me the message that there isn't any documentation available.

Any help would be appreciated!!

In faith, Dave
[email]dave@christos.cjb.net[/email], [email]dpeirce@christian.net[/email]
Viva Texas

---

### Post by afilonov on 2007-03-29
> **dpeirce said:**
> I have a home network consisting of a laptop and a desktop, both with Kubuntu 6.10 installed. Both computers connect to the internet just fine (they connected themselves :^>). I'd like to be able to browse the home directory of one computer from the other. The router is a Lynksys Wireless G. Wireless Assistant shows both an eth0 (lo) and eth1 (Linksys with 5 stars). I've followed the instructions found [http://ubuntuguide.org/wiki/Ubuntu_Edgy#Networking](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Networking) HERE but have not had success.

1) System Settings -> Sharing tells me "SMB and NFS servers are not installed". "Apt-get install samba smbfs" tells me these programs aren't available but smbclient and samba-common replace them. Adept tells me that both are installed, and shows nothing for "NFS"

2) I followed the instructions on networking, including the file edits, as far as "sudo /etc/inet.d/samba restart" and got "Command not found"; tried it naming smbclient and samba-common and got the same error message.

3) In Konqueror I tried "Right click on folder -> Share folder", but there's no "Share folder". Also there's no sharing tab in "Preferences"

4) I found [http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing](http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing) this about NFS. It doesn't seem to invole samba and I'm not trying to read any windows files; is this a better way to go? This blog is for an older Ubuntu, will these instructions work for Edgy? Would I do the same thing on the other machine(s)? [http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889) These instructions mention servers and clients; would I need both on both machines?

First, I have no idea what I'm doing so I'm following instructions blindly, and I apologize for the length of this question and my verbose confusion. Is there some easy way to browse files in one computer from another? Any extra explanation will be gratefully feceived!

In faith, Dave
[email]dave@christos.cjb.net[/email], [email]dpeirce@christian.net[/email]
Viva Texas

1. Samba and NFS are different things. Samba is for Windows networking, NFS is UNIX Network File System.

For NFS, you need following steps.

1. Install nfs-kernel-server. You need it on machine with shared folders. Make sure it's running.
2. Modify /etc/exports file. This file should list your shares. You can only create one share per logical drive. Each share has one line like this:

/ 192.168.1.1/24(rw,no_root_squash,async)

Which means that you share your root directory (/) to all machines in network 192.168.1 in read/write mode, with full root access, asynchronously.
After modifying file, reexport you filesystems using command:

exportfs -r

Create a mountpoint directory on other computer:

mkdir /mnt/mountname

Now you should be able to mount this share on other computer using command:

mount machinename:/ /mnt/mountname

Note: all commands should be run under root account or using sudo.
File ownership and permissions: NFS uses group and user IDs, not names. So if you have different IDs for the same username on different machines, you might have access problems.

Careful with sharing removable media (CD, USB disks etc.) You won't be able to unmount them while they are shared. For CDs, Samba is a better option.

For Samba, you'd better read HOWTO. For example, this one:

[http://www.ubuntuforums.org/showthread.php?t=202605](http://www.ubuntuforums.org/showthread.php?t=202605)

---

### Post by dpeirce on 2007-03-30
Afilonov, thanks for your information. 

The thing is, I've got samba working partway. I noticed something on the link you provided about permissions, and have changed the permissions on both machines to show read/write for user and group; that got me able to drag a file or directory from the desktop to the laptop, but I can't drag or copy anything back nor can I see the laptop from the desktop. In the process I noticed the permissions on my laptop are different; usually I'm user dave in group dave but in my laptop (new) I'm user dave group root. I'm wondering if that has anything to do with it; however, the laptop's user management app apparently won't let me change my group to dave.

It's kind of frustrating: I have a GUI system settings widget with networking and sharing, networking and networking tools in the system menu, and sharing in konqueror, and no instructions for any of it. Looks like with all those apps I could set up a network and share stuff back and forth. Is it possible to do that rather than going to the command line?

Not to complain, exactly :^>, but with all those GUI apps there should be a graphical way to do it. But I'll keep your info on NFS (NFS shows in some of those widgets too!).

In faith, Dave
[email]dave@christos.cjb.net[/email], [email]dpeirce@christian.net[/email]
Viva Texas

---

### Post by afilonov on 2007-03-31
> **dpeirce said:**
> Afilonov, thanks for your information. 

The thing is, I've got samba working partway. I noticed something on the link you provided about permissions, and have changed the permissions on both machines to show read/write for user and group; that got me able to drag a file or directory from the desktop to the laptop, but I can't drag or copy anything back nor can I see the laptop from the desktop. In the process I noticed the permissions on my laptop are different; usually I'm user dave in group dave but in my laptop (new) I'm user dave group root. I'm wondering if that has anything to do with it; however, the laptop's user management app apparently won't let me change my group to dave.

It's kind of frustrating: I have a GUI system settings widget with networking and sharing, networking and networking tools in the system menu, and sharing in konqueror, and no instructions for any of it. Looks like with all those apps I could set up a network and share stuff back and forth. Is it possible to do that rather than going to the command line?

Not to complain, exactly :^>, but with all those GUI apps there should be a graphical way to do it. But I'll keep your info on NFS (NFS shows in some of those widgets too!).

In faith, Dave
[email]dave@christos.cjb.net[/email], [email]dpeirce@christian.net[/email]
Viva Texas

That's strange. You shouldn't have group root ever. You have to have admin group though. If you don't have it, you'll have to go to command line. You'll have to use root account to change your group settings.

Try to run command:

sudo -s

in terminal. If it works, you can change your groups from root account.
1. List all groups of your account:
groups dave
2. Run usermod command to change groups:
usermod -g dave -G "<list of groups from p1, separated by comma>"
don't forget to add group admin in -G list. And don't include root
3. You need to change group on all files in your home directory:

chgrp -R dave ~dave

Logout, login. You should be OK.

---

### Post by dpeirce on 2007-03-31
I have a question in to the laptop manufacturer's support asking about the strange root setup. I'll check back when I hear from them. There may be some weird reason why they did it that way.

sudo -s does work. Both root and adm are in my groups. 

In faith, Dave
[email]dave@christos.cjb.net[/email], [email]dpeirce@christian.net[/email]
Viva Texas

---

### Post by likwid on 2007-04-01
There is a root group by default in edgy, not sure about other releases.

---

### Post by afilonov on 2007-04-01
> **dpeirce said:**
> I have a question in to the laptop manufacturer's support asking about the strange root setup. I'll check back when I hear from them. There may be some weird reason why they did it that way.

sudo -s does work. Both root and adm are in my groups. 

In faith, Dave
[email]dave@christos.cjb.net[/email], [email]dpeirce@christian.net[/email]
Viva Texas

That's wrong. You should have the following groups:

dave adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin

Order may be different, but dave should be your primary group and listed first when you type:

groups

You should not have root group, only root is allowed to have it.

from command prompt.

---

