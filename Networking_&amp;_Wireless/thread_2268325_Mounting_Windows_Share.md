---
title: "Mounting Windows Share"
date: 2015-03-07
forum: Networking &amp; Wireless
---

### Post by bman on 2015-03-07
Hi,

I am on Ubuntu 14.04.2 and within the File Manager I can see my SERVER, see the folder with my media, but when I double click it gives me a failed to mount (permission denied).

On windows its fully shared and ready to go.

What is going on?

---

### Post by bman on 2015-03-08
I am not sure how to get it to work.

I had it working of course on Windows, the SERVER is Windows and I was able to access it from another Windows machine.

Is there some setting I am missing, its open to all, no permissions needed.

---

### Post by bman on 2015-03-09
Sorry to keep posting in here but I am pretty sure someone knows something that could help me figure this out.

---

### Post by skierpage on 2016-01-03
I had the same error message between Windows Vista and Ubuntu 15.10. If you want to be able to share without supplying a username and password to Windows, there are two things you may need to do on the Windows side in addition to just sharing the folder. In Windows Vista,

1. Control panel > Network and Internet > Network and Sharing Center > Sharing and Discovery section, change Password protected sharing to "Off"

2. Make sure the folder is being shared with "Everyone". Right-click the folder, Properties > Sharing [Share...] in "Choose people to share with". If you don't see "Everyone", then enter Everyone, then [Add].  The default permissions for Everyone in most areas of Windows is Read, if you want remote users to change the contents of the folder you need to fuss with that as well.

With those two I was able to share an arbitrary folder in Windows Documents and in Ubuntu Files (I think it's the Gnome nautilus program) actually view its contents. Strangely, when I tried to share my Windows CD-ROM drive, I only had to do step 1.

Note this results in pretty lax security, anyone on the network can view what you put in that folder. It would be better to be password-protected. I had never set up a user password for the default user on the Windows box, and the add a password dialog warned about changing stuff. You could create an additional Windows user named e.g. *remoteuser* and add that user in the "Choose people to share with" dialog; Ubuntu Files will/may prompt for a user and connection for the Windows share.

Hope this helps.

---

