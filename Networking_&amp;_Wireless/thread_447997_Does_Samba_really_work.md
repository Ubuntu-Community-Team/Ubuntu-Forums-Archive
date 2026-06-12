---
title: "Does Samba really work?"
date: 2007-05-18
forum: Networking &amp; Wireless
---

### Post by the lemming on 2007-05-18
I tried to install Samba so that I could access my files on my PC which is run on XP.

The Laptop can see the PC and the PC can see the Laptop on my Wireless router.  However neither can access each other.  I keep getting error messages saying that I do not have permission.

Any ideas where I am going wrong?

---

### Post by whistlerspa on 2007-05-18
You need to set up shared folders using the System - Administration - Shared Folders menu (ensuring that the read only box is unticked)

Then go the the indivual folders from nautilus and right click to get Properties. In the Permissions tag set the file accesses that you want. You can also set it so that all enclosed files also can be shared with the button at the bottom. 

I find that it works best when you do boyh of these things. 

N.B. you can't share your 'home' folder in it's entirity only it's sub-folders.

It can take a little time to set up if you have lots of sub-folders but works fine after that, albeit a little slowly at times.

---

### Post by The Pinny Parlour on 2007-05-18
No

---

### Post by The Pinny Parlour on 2007-05-18
> **whistlerspa said:**
> Y. 

N.B. you can't share your 'home' folder in it's entirity only it's sub-folders.

It can take a little time to set up if you have lots of sub-folders but works fine after that, albeit a little slowly at times.

Well what's the point then?  If one can't share the 'home' folder.  That is useless.

---

### Post by The Pinny Parlour on 2007-05-18
> **whistlerspa said:**
> You need to set up shared folders using the System - Administration - Shared Folders menu (ensuring that the read only box is unticked)

Then go the the indivual folders from nautilus and right click to get Properties. In the Permissions tag set the file accesses that you want. You can also set it so that all enclosed files also can be shared with the button at the bottom. 

I find that it works best when you do boyh of these things. 

N.B. you can't share your 'home' folder in it's entirity only it's sub-folders.

It can take a little time to set up if you have lots of sub-folders but works fine after that, albeit a little slowly at times.

Tried what you said and it doesn't work as usual.  Networking sucks on ubuntu, so doesn't printer support for that matter.  Yeah I am half cocked.  It has never worked fully at all for me.

---

### Post by jiminycricket on 2007-05-19
Have you set a password with ```
sudo  smbpasswd -a username
``` ?

[SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba#head-51f51bea37ef002e8c6d7dbfeeb486a47cdb0f88)

---

### Post by Undertwotimes on 2007-05-19
Of course you can share the home folder, in fact that is part of the default samba configuration.  Edit /etc/samba/smb.conf and uncomment the [homes] configuration section.  Take a look at the documentation for more info.

---

### Post by the lemming on 2007-05-19
> **Undertwotimes said:**
> Of course you can share the home folder, in fact that is part of the default samba configuration.  Edit /etc/samba/smb.conf and uncomment the [homes] configuration section.  Take a look at the documentation for more info.

Could you please go over that again?

Unfortunately I do not have any programming skills and my use of Linux is very limited.

---

### Post by the lemming on 2007-05-19
Don't ask because I don't know how I did it but I can now access my documents on my PC.

The only problem is that I can not see my laptop from my PC.  I was able to see it this morning but my tinkering must have done something.

Any suggestions on how I can see my Laptop (ubuntu) on my PC (windows)?

Cheers

---

### Post by The Pinny Parlour on 2007-05-19
As said before it doesn't work.  I'm yet to see a fully working ubuntu to windows (and vice versa) actually consistently work.  I hope to goodness the makers of ubuntu make networking and printers easier.

---

### Post by kknd on 2007-05-19
Samba works fine here without any further configuration. I have acess to the shared folders of the operatin systems of other people on my network.

---

