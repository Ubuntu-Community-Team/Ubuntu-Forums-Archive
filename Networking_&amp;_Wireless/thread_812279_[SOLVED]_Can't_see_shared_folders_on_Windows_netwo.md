---
title: "[SOLVED] Can't see shared folders on Windows network"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by elperrillo on 2008-05-29
Hi people, here's my problem hopefully somebody will be able to help me, I set up Ubuntu LTS 8.04 server at work. And installed SAMBA, WINBIND and KERBEROS 5. Everything is working fine, I can even see my server in the windows domain list, and access its shared folders (Ubuntu server shared folders)...

However, here's my problem... 

In nautilus I can see shared folders on Windows-based servers but I cannot on regular Windows-based computers, it just displays a blank page, however if I do it in nautilus using a path e.g. smb://machinemane/sharedfolder it works but asking me for a password, I enter it and I am in.

This used to work with Gutsy but it is no longer working in Hardy, it sees to be a really nasty bug, some posts mention something about GVFS which I already have installed on system, to no avail. 

Can somebody help me please??? I am desperate, I have tried absolutely everything before recurring to the forum, I've spent three days trying to figure it out and nothing!!! :confused:

---

### Post by elperrillo on 2008-05-30
Update: When I do...

kinit username@domain
Password *********

It tells me...
[B]
"KDC reply did not match expectations while getting initial credentials"[/B]




Can somebody please help me for the love of GOD?????!!!!!!!! :(

---

### Post by elperrillo on 2008-06-02
Come on, there has to be somebody that kows this. If not I am going to have to go to Fedora, and I really don't want to do that because I am allready used to ubuntu, However this is suposed to be an upgrade from an Existing Fedora server that I have, I just cannot make it work in Ubuntu.


Can anybody help me please???? I am desperate I have allready spent a week working on this non stop.

---

### Post by elperrillo on 2008-06-03
I cannot believe nobody was able to answer this very common question, since everybody in Hardy should be having the same problem, I finally applied a non-official patch that I found on a ubuntu website and now I am able to see my shared drives. The patch works by replacing a file on the gvfs directory, the file is called 

gvfsd-smb-browse

Just look for it on the web, go to google and search for the name of the file and the word "patch" ad you will find it. Afer replacing it change the permission on it so it can be executed, reboot your ubuntu box and you are good to go. I hope this helps everyone who is having the same problem. and I hope the developers fix this very important and enbarrasing (for Ubuntu) bug!!!! This should be priority #1 on their list.

---

### Post by mrbannerman on 2008-06-03
This patch worked well until the latest GVFS update yesterday. Now I am back to not seeing the Windows Shares on Vista.

---

### Post by elperrillo on 2008-06-04
What a P-O-S...   Do you hwave the original file? before you patched it? maybe you can put it back in there and try doing that update again? I do not know if it will do the update again, you would have to find that out but it is worth a try.

---

### Post by dmizer on 2008-06-04
all i have to offer is a cli solution.  a cli solution which i implemented in breezy, and have not touched since (i am currently running hardy on this machine).

if you follow the directions in the second link in my sig, you will get much better, and much more reliable functionality from samba.  configure it once, and forget about it.

edit:
alternatively, if you're dead set on a gui only configuration, this is your problem ->

the gvfs update overwrote your patch.  to fix, all you have to do is reapply your patch.  keeping in mind that, every time there is an update, you'll have to reapply your patch.  if that does not work, then there's always the cli solution.

---

### Post by mrbannerman on 2008-06-04
I have tried reapplying the patch but it didn't work for me. I can live with not seeing the Vista shares but it is a pain.
Morris

---

