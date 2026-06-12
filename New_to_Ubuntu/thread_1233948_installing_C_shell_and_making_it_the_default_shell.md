---
title: "installing C shell and making it the default shell..."
date: 2009-08-07
forum: New to Ubuntu
---

### Post by mbaucco on 2009-08-07
Hello,

One of our customers wants to install the C shell and make it the default. I think I have found the way to install the C shell, but I do not know how he can make it the default shell. Can anyone point me towards a tutorial or something?

Thanks!

---

### Post by Iowan on 2009-08-07
I found [this]("http://nxadm.wordpress.com/2008/06/18/how-to-change-the-default-shell-editor-in-ubuntu/") page, but I suspect you want it as default shell whenever a new user is set up.  I suspect it's in a template, somewhere... I'm still looking...

---

### Post by decoherence on 2009-08-07
> **Iowan said:**
> I found [this]("http://nxadm.wordpress.com/2008/06/18/how-to-change-the-default-shell-editor-in-ubuntu/") page, but I suspect you want it as default shell whenever a new user is set up.  I suspect it's in a template, somewhere... I'm still looking...

here you go!

/etc/default/useradd

---

### Post by ibuclaw on 2009-08-07
If you will be using gnome's "Users and Groups" tool to add users, you may also want to edit this file too:

/etc/gnome-system-tools/users/profiles


Regards
Iain

---

### Post by mbaucco on 2009-08-10
Thanks very much, but I think I must be a little slow. This appears to show how to change the default text editor and not the shell. Am I missing something? Also, he is the only one who wants to change the shell, I do not want to make this change universal.

Thanks again!
Matt

---

### Post by mbaucco on 2009-08-19
I downloaded and installed tcsh and ran update-alternatives --all but it never asked me if I wanted to change the default shell. Can anyone help me? I just want to help one guy set his shell to tcsh.

Thanks,
Matt

---

### Post by Bachstelze on 2009-08-19
```
chsh -s /usr/bin/tcsh
```

Hmm actually, that might not be what you want. Please explain more precisely what you mean by "default shell".

---

### Post by michy99 on 2009-08-19
What if you edit the user's entry in /etc/passwd and replace /bin/bash with the c shell?

---

### Post by mbaucco on 2009-08-19
I believe he wants the default shell to be tcsh when he uses the terminal, I believe the default in Ubuntu is normally bash, right?

thanks!

---

### Post by Locutus_of_Borg on 2009-08-19
sudo -i
usermod -s csh [USER]


substitute [USER] for actual login name

---

### Post by mbaucco on 2009-08-19
Actually, chsh is what I wanted. Thanks very much! :)

---

### Post by Bachstelze on 2009-08-19
> **Locutus_of_Borg said:**
> sudo -i
usermod -s csh [USER]


substitute [USER] for actual login name

No need to sudo, the user can change his shell himself.

---

