---
title: "How to connect to a Windows share?"
date: 2008-11-08
forum: Networking &amp; Wireless
---

### Post by Jephir on 2008-11-08
Hi, I recently moved to Ubuntu and I am having some trouble connecting to a Windows share on my home network. I go to Network > Windows Network > WORKGROUP, but then there is nothing there. On other Windows computers on the network, they can see all the computers on the network, but on Ubuntu it doesn't see anything. Any help would be greatly appreciated.

---

### Post by oceallaighm on 2008-11-09
I would suggest checking your hosts and host name files and see if Ubuntu is in the same Domain or WorkGroup as the Windows machines.

In my case my share is a Samba WorkGroup on Ubuntu Server 8.04, I was able to connect to the shared folders from my old laptop running Ubuntu Desktop 8.04 just by changing those 2 files and rebooting.

On my new laptop running Ubuntu Desktop 8.10 x86_84, however I cannot see the Windows Network in the File Browser. I can ping my Samba server and connect to it using PuTTY, I can see the mounted drives with PuTTY. But to all intents and purposes the network is not showing.

Let me know how you get on, I was thinking that I might have an issue specific to the x86_64 version.

---

### Post by Jephir on 2009-05-30
I've found what's causing the problem. Natilus cannot connect to network shares requiring a login, it must be done from the terminal.

---

### Post by coffeecat on 2009-05-30
> **Jephir said:**
> I've found what's causing the problem. Natilus cannot connect to network shares requiring a login, it must be done from the terminal.

That's not true on my network. I can reliably connect to a smb share requiring a password with Nautilus. There must be some other issue preventing Nautilus log in for you. If you are not seeing your shares in Network, try this: Open a Nautilus window, click the notepad icon to the left of the location bar so that you get an address bar rather than a breadcrumb trail and type in:

smb://servername/sharename/

You will then be prompted for the login password.

By 'servername' I mean the hostname of the machine with the smb share you want to connect to. There is a strange problem in Jaunty with samba such that sometimes my smb shares appear in Network and sometimes not, but I can always connect just fine with the smb:// address in Nautilus.

---

### Post by Jephir on 2009-05-30
> **coffeecat said:**
> That's not true on my network. I can reliably connect to a smb share requiring a password with Nautilus. There must be some other issue preventing Nautilus log in for you. If you are not seeing your shares in Network, try this: Open a Nautilus window, click the notepad icon to the left of the location bar so that you get an address bar rather than a breadcrumb trail and type in:

smb://servername/sharename/

You will then be prompted for the login password.

By 'servername' I mean the hostname of the machine with the smb share you want to connect to. There is a strange problem in Jaunty with samba such that sometimes my smb shares appear in Network and sometimes not, but I can always connect just fine with the smb:// address in Nautilus.

Using the smb:// address in Nautilus for me results in this error:

> **Could not display "smb://time-capsule/netshare/".**

Error: Failed to mount Windows share
Please select another viewer and try again.

Instead of using Nautilus, I've been using [this guide (https://help.ubuntu.com/community/MountWindowsSharesPermanently)]("https://help.ubuntu.com/community/MountWindowsSharesPermanently") to connect to a Windows share and it works perfectly.

---

### Post by Iowan on 2009-05-30
[Here]("http://ubuntuforums.org/showthread.php?t=288534") is another How-To that may be useful (or at least informative).

---

