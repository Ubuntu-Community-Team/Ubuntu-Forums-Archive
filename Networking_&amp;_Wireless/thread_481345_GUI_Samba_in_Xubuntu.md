---
title: "GUI Samba in Xubuntu?"
date: 2007-06-22
forum: Networking &amp; Wireless
---

### Post by PaganImmolator on 2007-06-22
Ok I haven't used linux in a long time. Last time I did set up Samba (5years ago or more) it was all via the shell. I am now using Xubuntu and I want to set up Samba to browse some shared folders across a Windows XP network. 

The only thing I have done so far is to enable Samba when I clicked on "shared folders" in the menu. I can see that the smbd app is running now in task manager via root. 

Ok so I looked through theXubuntu GUI trying to find something similar to the "Network Neighborhood"  in Windows but I couldn't find anything. Is there a package that enables a GUI network browser? 

Also I seem to recall when I set up Samba that I had to do more than just turn on smbd. Are there any other things I need to turn on?

---

### Post by kevdog on 2007-06-22
Try installing webadmin.  This gives you a sudo GUI interface to add/delete users with SAMBA.

---

### Post by PaganImmolator on 2007-06-22
> **kevdog said:**
> Try installing webadmin.  This gives you a sudo GUI interface to add/delete users with SAMBA.

When you say users does that also mean machines? What I am really trying to do is browse machines but I don't remember enough of Samba to recall how the smbd.conf (or whatever it is) uses labels. 

Thanks

edit: also I cannot find a samba webadmin package under the synaptic package manager. There are some other webadmin packages but I don't see how they would apply.

---

