---
title: "Networking with Windows"
date: 2008-11-23
forum: Networking &amp; Wireless
---

### Post by LDRoamer on 2008-11-23
I am a newbie with this stuff. Trying to network my Hardy 8.04 computer with my windows network but nothing is working.  When I try to share a folder I get:

'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.

Also I cannot browse any of the windows computers on the network. All I get is a blank folder which does not display the shares.

Any help appreciated.

---

### Post by Olivier2371 on 2008-11-23
On windows share folder do you have any file at all?

---

### Post by LDRoamer on 2008-11-23
You bet I do! Gigs of stuff there. My windows computers browse the network fine but my ubuntu computer is blind, can't see a thing. 

I can see the windows network (called cleverly mshome). However when I click on the icon all I see is an empty folder and it doesn't show me the shared folders. 

As noted when I try to share an ubuntu folder it won't let me giving me the error that I noted.

> **Olivier2371 said:**
> On windows share folder do you have any file at all?

---

### Post by LDRoamer on 2008-11-23
Just a quick update. I can now share my ubuntu folders and my windows computers can see them. I follow a post I found to add a password to samba using a "sudo" command in a terminal window. Once I did that and rebooted it started working.

However Ubuntu still does not see the shared folders that are on my windows computers. 

Any help appreciated.

---

### Post by LDRoamer on 2008-11-23
One further update. I can access the windows boxes using Gnome Commander but not with nautilus. Not sure what is wrong but must be something that I can reconfigure?

---

