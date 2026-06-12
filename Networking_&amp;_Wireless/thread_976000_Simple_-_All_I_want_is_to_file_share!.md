---
title: "Simple - All I want is to file share!"
date: 2008-11-08
forum: Networking &amp; Wireless
---

### Post by Bondy_uk on 2008-11-08
Ok sorry for the noob post but this is really getting on my nerves...

I have 8.04 installed on my desktop and 7.10 on my laptop. All I am trying to do is copy some files from one to the other.

Samba is running. I share the directories/folders, can see them on the other, and can copy 'some' of the files.
Yet for some unknown reason its deciding itself which ones I can copy an which ones I cant (permission denied or whatever). Within the same folder even, I can copy some and not others.

Whats going on?

](*,)

Oh and also, why is the 'shared folders' program/gui no longer in System > Administration in 8.04?

Where is the gui for administration of samba/sharing?
It seems a bit stupid to have taken it out without a replacement

---

### Post by Bondy_uk on 2008-11-08
> **Bondy_uk said:**
> 
Oh and also, why is the 'shared folders' program/gui no longer in System > Administration in 8.04?

Where is the gui for administration of samba/sharing?
It seems a bit stupid to have taken it out without a replacement

Ok so I tried to add it in under 'Edit Menus' > New Item and put the command 'gksu shares-admin'

But guess what, even though it asked for my password, it was completely grayed out and you cant do anything with it.

So is there another app/gui for this? as it also let you change the workgroup

---

### Post by TerryP on 2008-11-08
For a GUI, did you try installing the system-config-samba tool?  It's listed in Synaptic.

---

