---
title: "Ubuntu Live USB Query."
date: 2011-03-08
forum: New to Ubuntu
---

### Post by Pagnell on 2011-03-08
I have setup a live USB stick of Ubuntu Netbook with a 2gb persistence and it is working fine. However, I find the 'Install or Try' prompt window on every boot very annoying. Is there any way of removing this and just getting the stick to boot to the login prompt?

Cheers in advance and apologies if it has already been covered.

---

### Post by maqtanim on 2011-03-08
Welcome to the community! :)

As you are using the live USB, this "Install or Try" prompt will always be there unless you install it.

---

### Post by Pagnell on 2011-03-08
Thanks for the reply. Shame, I thought there might be some way to remove it as I just want to use this Live build in work for browsing and such so I don't have to use the crappy slow version of XP it has on it. I don't want to install it. No problem though, I will just have to press the try button on every boot.

Another question, is there a way of stopping it auto logging into the temp live session and let me choose my username and login as normal? I have created a user ID which is held in the persistence. Also, I have no sudo access and don't have permission without the root password to edit sudoers. Any way around that?

Cheers in advance. :)

---

### Post by Pagnell on 2011-03-08
> **maqtanim said:**
> Welcome to the community! :)

As you are using the live USB, this "Install or Try" prompt will always be there unless you install it.

Just found a way around it, the following command run under sudo will remove both the 'Try/Install' window and the Install icon from the desktop.

> sudo apt-get purge ubiquity

---

