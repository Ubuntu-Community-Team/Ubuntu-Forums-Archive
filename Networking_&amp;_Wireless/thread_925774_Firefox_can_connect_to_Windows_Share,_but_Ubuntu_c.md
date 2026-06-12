---
title: "Firefox can connect to Windows Share, but Ubuntu can't mount it"
date: 2008-09-21
forum: Networking &amp; Wireless
---

### Post by manbeard on 2008-09-21
I am experiencing a strange problem. I am new to Linux.

The GOAL: Mount a Windows Shared Folder

The ISSUE: I can successfully see all three of my networked machines on my workgroup. However, they don't show any shared folders (all three computers have shared folders that I should be able to access). I can view those shared folders with Firefox, by typing in a URL such as:
smb://192.168.1.113/Users/MyUserName/

(Using the computer's IP address worked whereas using the Windows computer name did not.)

However, I cannot seem to mount the drive in Ubuntu to make it available to me like a folder.

What could cause this problem and how can I resolve it? I REALLY hope it's not a firewall issue. Thanks!

---

### Post by manbeard on 2008-09-21
Okay, I figured out a way to solve my problem, sort of.

1. I went to Places->Connect To Server
2. I chose "Custom Location" (NOT "Windows Share")
3. I typed in smb://vistaComputerName/SharedFolder/
4. (Optional) I checked "Add Bookmark" and typed a name for the Network Shortcut
5. I clicked "Connect" and typed in my Vista username's password, and it worked!

I don't know why the shared folders are not showing up under "Windows Shares". Perhaps Ubuntu just needs to prompt me for the computer's username/password and it would grant me those permissions.

Even doing this, there are some strange occurences of folders being read-only to some degree (I can delete files in some folders, but not write them). Weird!

If there is a more proper way of getting this to work through the "Windows Shares" system (which I assume is how I should be doing this kind of thing!), any help would be appreciated.

---

