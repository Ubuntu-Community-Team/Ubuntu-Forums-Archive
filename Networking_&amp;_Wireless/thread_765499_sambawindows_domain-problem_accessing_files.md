---
title: "samba/windows domain-problem accessing files"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by snorkytheweasel on 2008-04-24
I have 2 linux computers which are part of a Windows Domain. Both are listed in Active Directory.

**Using Konqueror and Dolphin as file managers**, 
both of the Ubu 7.10 PCs
[LIST]
[*]can "see" any Windows computer in the domain
[*]can access shared files & folders on any of the Windows computers.
[*]can "see" each other - including seeing shared directories
So far, so good, but each Ubu box

[*]***cannot access*** each other's files and directories
[/LIST]
**Using Windows Explorer**, 
Windows PCs
[LIST]
[*]can "see" both Linux PCs
[*]can "see" and access shared directories and files on other windows PCs
So far, so good, but Windows computers

[*]***cannot access*** shared files and directories on the Linux computers
[/LIST]

Error conditions:
[LIST]
[*]**Using Dolphin as a file manager**
[LIST=1]
[*]I can "see" shared directories on the other Linux machine, but if I click on a shared directory, the error message returned is:
[FONT="Courier New"]smb://is-computername/home/directoryname does not exist[/FONT]
[*]Then dolphin opens the directory (the one that doesn't exist), but it is empty.
[/LIST]


[*]**Using Konqueror as a file manager**,
[LIST=1]
[*]the error message returned is
[FONT="Courier New"]the file or folder smb://is-computername/directoryname does not exist[/FONT]
[*]Then Konqueror opens the directory (the one that doesn't exist), but it is empty.
[/LIST]


[*]**Going the other direction, using Windows Explorer, windows computers **
[LIST=1]
[*]can "see" each of the Linux PCs
[*]can see shared directories and printers on the Linux boxes
When I attempt to open a shared directory, windows prompts me for a user name and password. User name and password are the same on each Linux PC and in active directory. However, when I enter the user name and password, the dialog box blinks and asks again, ad infinitum.
[/LIST]
[/LIST]
Summary:
[LIST]
[*]Linux-to-Windows file access is one-way
[*]Linux-to-Linux file access is "No way. Jose"
[/LIST]
IMHO, it shouldn't be that way. I must be doing something wrong (again).

Is this fixable?

---

### Post by FSHero on 2009-03-24
I am having a very similar problem. Unfortunately, I have not time to talk atm, but I'll say this:

I'm dual-booting Kubuntu Hardy (8.04) amd64 and Windows Vista (SP1). I've got an NTFS partition and a home ext3 partition.

Using K-menu -> System Settings, choosing Sharing option, clicking File Sharing on LHS bar, I can add shares.

I try to add shares from the NTFS partition: e.g. a folder /media/data/download using Samba, but no other computer can access this.

Bizarrely, if I add a share from my ~ (ext3) partition, e.g. /home/fshero, I _can_ access this from any computer.

So for now, my workaround is to store files I want to share on my /home partition; too bad it's only 2GB in size!!!

- Minesh

(I'll keep an eye on this; perhaps this Saturday after I finish a project write up I can talk more!)

---

### Post by FSHero on 2009-04-02
Please see [http://ubuntuforums.org/showthread.php?t=1113933](http://ubuntuforums.org/showthread.php?t=1113933) for more details on my problem. Some things work, some don't.

---

