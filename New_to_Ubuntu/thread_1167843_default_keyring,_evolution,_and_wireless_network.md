---
title: "default keyring, evolution, and wireless network"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by akimatsu123 on 2009-05-23
Hi,

I am finding that I can't save any passwords on my system, whether it be wireless passwords or passwords to my email accounts in evolution because it keeps asking for a default keyring password that i didn't set and don't have.

What is the password, or how can i get rid of this problem? Whenever i click to save passwords, i get the alert:

**Application 'evolution' (/usr/bin/evolution) wants to access the default keyring, but it is locked**

Some solutions to the problem mentions deleting default.keyring under /home/me/.gnome2/keyrings/ but I don't see a default.keyring file in that folder, only a login.keyring

Thanks

---

### Post by gandaran on 2009-05-23
well the keyring works two ways, with password or no password, if you want to use a keyring password every-time you use evolution then set one when it asks you too, if you don't want a password then when it asks you to set one don't enter any just click the apply or okay button without filling anything.
to reset the keyring profile, go to /home/user/.gnome2/keyrings delete all configuration files there and now you can start all over again storing your evolution passwords.

---

### Post by mcduck on 2009-05-23
> **gandaran said:**
> well the keyring works two ways, with password or no password, if you want to use a keyring password every-time you use evolution then set one when it asks you too, if you don't want a password then when it asks you to set one don't enter any just click the apply or okay button without filling anything.
to reset the keyring profile, go to /home/user/.gnome2/keyrings delete all configuration files there and now you can start all over again storing your evolution passwords.

Actually the default mode is *not* to ask password every time keyring is accessed, or even ask it every time it's opened.

The default mode assumes people use login password on their system. As long as login password is same as keyring password, the keyring will then open automatically and you'll never even know it's there. :D

Of course if you choose to disable the login password the keyring won't unlock automatically any more and you end having to type the password every time. In that case you should set the keyring password to empty one. And doing that definitely doesn't require trashing all your keys, it can be done with the keyring manager (Applications/Passwords and Encryption Keys).


***


What comes to the original poster's problem, couple of things come to mind. Have you changed your login password at some point? Latest Ubuntu version automatically creates the keyring password and sets it to same as your login password. If you have changed the login password your keyring password is probably same as the *old* login password. You should change the password to same as your current login password.

Other possibility (if you are using older Ubuntu version) is that when you first time did something that stored a key into the keyring the keyring manager opened a window to ask you to set the keyring password. Old windows users have the habit of clicking through dialogs without paying much attention to them, so you might have set some rather random password. In that case your only option is to remove the keyring files and start from scratch again.

(and yes, you clearly have at some point used the keyring manager, as no .keyring files exist by default, the file is created when you use the keyring manager first time!)

---

### Post by akimatsu123 on 2009-05-23
> **mcduck said:**
> 
What comes to the original poster's problem, couple of things come to mind. Have you changed your login password at some point? Latest Ubuntu version automatically creates the keyring password and sets it to same as your login password. If you have changed the login password your keyring password is probably same as the *old* login password. You should change the password to same as your current login password.


Yes, that's what happened. I changed my password. Evolution is able to store passwords when I type my old password into the dialog. How do i go about changing the password stored in the default keyring?

---

### Post by mcduck on 2009-05-23
> **akimatsu123 said:**
> Yes, that's what happened. I changed my password. Evolution is able to store passwords when I type my old password into the dialog. How do i go about changing the password stored in the default keyring?

Open Applications/Accessories/Passwords and Encryption Keys. Go to Passwords-tab, right-click the "Passwords:login"-entry and select "Change Password".

(this is still assuming you are using Ubuntu 9.04, the previous versions had slightly different user interface for keyring management)

---

### Post by akimatsu123 on 2009-05-23
thank you very much, problem solved :D

---

### Post by Wharf Rat on 2009-05-23
Thanks!  Solved my problem too.

---

