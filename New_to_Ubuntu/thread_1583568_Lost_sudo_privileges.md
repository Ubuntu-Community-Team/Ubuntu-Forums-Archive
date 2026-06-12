---
title: "Lost sudo privileges"
date: 2010-09-28
forum: New to Ubuntu
---

### Post by blamor on 2010-09-28
I'm not sure if this is the right place for this, but I am a total noob after all, so here I am..

I was going through the Google tutorials on basic Linux stuff - the ownership and permissions one, specifically.

Basically, I didn't know that the default behavior for usermod -G [groups] removed the specified user from any groups *not *listed. I know, I know- I should have read and understood the man page first, but I didn't, and I accidentally my membership to admin.

My question then, is this: is there any way before earth and heaven to restore my ability to use sudo without re-installing? I understand that the root password is disabled by default, and so here I am without any admin accounts on my machine. Perhaps using a Live CD or an equivalent to edit the sudoers file? If such a thing were possible I would rejoice.

Any help at all is greatly appreciated!

---

### Post by JohnHeikkila on 2010-09-28
You can use "su -" for root access, then you can put back the rights.
Oh, and do that in the console.

It will ask for a password which is NOT your user password. It's 'superuser' password. I am not sure if it will ask for a new password if you haven't set one for it yet, but "sudo passwd root" would change that password.
This brings us back to the sudo privileges

---

### Post by aysiu on 2010-09-28
Boot into recovery mode and drop to the root shell.

You can then add yourself back into the *admin* group.

Instructions here:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by aysiu on 2010-09-28
> **JohnHeikkila said:**
> You can use "su -" for root access, then you can put back the rights. Maybe for other other Linux distros, but not in Ubuntu. There is no root password set in Ubuntu by default. To get root access withou *sudo*, you boot into recovery mode.

---

### Post by blamor on 2010-09-28
John,

I don't think you understand; the default password for a fresh 10.04 installation is locked, so I can't use "su" for anything. Additionally, there are several groups that the first user specified during installation of 10.04 is a member of - I don't remember what they are, but I know one of them was admin, the group conferring the ability to use sudo. 

Since I've accidentally removed myself from the admin group, I cannot use the sudo command any longer. I am aware of a file (/etc/sudoers) that dictates which users have what privileges somehow, but since the only user on my machine has no admin access and the root password is locked by default, I think I'm stuck.

---

### Post by aysiu on 2010-09-28
> **blamor said:**
> 
Since I've accidentally removed myself from the admin group, I cannot use the sudo command any longer. I am aware of a file (/etc/sudoers) that dictates which users have what privileges somehow, but since the only user on my machine has no admin access and the root password is locked by default, I think I'm stuck. You're not stuck.

Boot into recovery mode.

Instructions in the link I posted earlier.

---

### Post by blamor on 2010-09-28
thanks! I saw your first post right after I posted my second! I really appreciate the help, everything is fine now

---

