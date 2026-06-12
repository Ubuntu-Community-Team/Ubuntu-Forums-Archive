---
title: "how to unlock the keyring automatically upon login?"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by legolas_w on 2010-04-30
Hi,

I have a problem after installing 10.04 while keeping my home folder. The keyring asks me for after ubuntu starts.


I left it on automatic login so Ubuntu is not asking for username and password when booted but right after boot, if it asks for kyring password.

thanks.

---

### Post by Megaptera on 2010-04-30
See if this helps ...
[http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/](http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/)

---

### Post by blazemore on 2010-04-30
If your keyring password is the same as your login password, or is blank (or you don't use the keyring), Ubuntu won't ask for the password.

You can change or delete your Gnome keyring password by going to
Applications -> Accessories -> Passwords and Encryption Keys

Right-click on the login password and click "Change Password"

---

### Post by P4man on 2010-04-30
> **blazemore said:**
> If your keyring password is the same as your login password, or is blank (or you don't use the keyring), Ubuntu won't ask for the password.

Yes it does if you set autologin. It has to, because ubuntu can not decrypt the passwords in the keyring without your password. The only solutions i know are either disabling autologin, or disabling encryption of your passwords in the keyring (see link provided above) with all security risks coming with it.

---

### Post by legolas_w on 2010-04-30
Thank you, I would rather enter the password everytime instead of exposing myself to security risks.

---

### Post by egalvan on 2010-04-30
> **legolas_w said:**
> ...I left it on automatic login so Ubuntu is not asking for username and password when booted...

> **legolas_w said:**
> I would rather enter the password everytime instead of exposing myself to security risks.

Uhmmmm, I'm a bit confused...

Are you aware that AutoLogin is itself a security risk?

(hopefully, you were only using it to test the keyring situation)

---

### Post by P4man on 2010-04-30
> **egalvan said:**
> Uhmmmm, I'm a bit confused...

Are you aware that AutoLogin is itself a security risk?

(hopefully, you were only using it to test the keyring situation)

Agreed its a risk, but not nearly as big as having autologin enabled AND your passwords on your pc unencrypted. As it is now, someone can log in as the OP but at least not access, see or modify his passwords. If you disable the keyring, anyone can view them either from a different account, root shell,  bootable cd,.. ts a big difference IMHO.

Then again, if you are going to have to enter a password to open the keyring, you might as well do it while logging in, and thus, disable autologin.

---

### Post by Megaptera on 2010-04-30
I think disable auto-login too. 
Only posted link above as that's the info that OP requested; not to encourage taking security risks.

---

### Post by ridgeland on 2010-05-12
Thanks for the link Megaptera.
I have a HTPC that with Ubuntu 9.04 I accessed remotely with VNC over SSH.  With Ubuntu 10.04 the host had to enter a keyring password!  This solved it.  The PC is behind a router that is only letting local PCs connect to it on that ssh port (not 22).

---

### Post by kalyp on 2010-05-14
> **blazemore said:**
> If your keyring password is the same as your login password, or is blank (or you don't use the keyring), Ubuntu won't ask for the password.

Hello,
I'm a little lost. I do have the same keyring password as my login password (only one password I use everywhere), and I don't have auto-login enabled (I'd like to, but have this problem: [http://ubuntuforums.org/showthread.php?t=1465877](http://ubuntuforums.org/showthread.php?t=1465877)). However I still have to log in first, then unlock the keyring (for wireless?). Any reason?

Is is possible to keep passwords for everything except wireless? I don't care if anybody can use the wireless on my computer but still want a password to protect root-kind of tasks. Just wondering! Thanks!!

---

### Post by P4man on 2010-05-16
> **kalyp said:**
> Hello,
I'm a little lost. I do have the same keyring password as my login password (only one password I use everywhere), and I don't have auto-login enabled (I'd like to, but have this problem: [http://ubuntuforums.org/showthread.php?t=1465877](http://ubuntuforums.org/showthread.php?t=1465877)). However I still have to log in first, then unlock the keyring (for wireless?). Any reason?

Hmm. it should open. Check if seahorse deamon loads on startup in system > preferences > startup  apps.

There should be an entry "Certificate and Key Storage" and one for "Secret Storage Service"
> 
Is is possible to keep passwords for everything except wireless? I don't care if anybody can use the wireless on my computer but still want a password to protect root-kind of tasks. Just wondering! Thanks!!


Yes. You can remove the wireless password from the keyring and have network manager save it in a plain text file instead. Just delete the wifi connection, create a new one and use the Unsafe password storage.

---

### Post by kalyp on 2010-05-17
Thanks a lot for your answer :)

> **P4man said:**
> Hmm. it should open. Check if seahorse deamon loads on startup in system > preferences > startup  apps.
There should be an entry "Certificate and Key Storage" and one for "Secret Storage Service"

Actually, I understood what happened. I have a fingerprint reader but for some reason I've never found the way to make it work with the keyring - meaning that I was login in with fingerprint but since the keyring doesn't recognize it, I still had to enter the password for that. If it makes sense. Right now the fingerprint is broken (since upgrade, didn't take the time to fix it yet) and I only have to enter the password once.

> Yes. You can remove the wireless password from the keyring and have network manager save it in a plain text file instead. Just delete the wifi connection, create a new one and use the Unsafe password storage.

Thanks that's just great. Exactly what I needed. I'll do that :)

---

### Post by Tholley on 2010-05-17
Actually if I'm reading this right, all you had to do is on your wireless icon up top, click on properties, then check the botton that says "available to all users", and you wont be asked for a keyring password again.

---

### Post by kalyp on 2010-05-17
> **Tholley said:**
> Actually if I'm reading this right, all you had to do is on your wireless icon up top, click on properties, then check the botton that says "available to all users", and you wont be asked for a keyring password again.

found it thanks!! it's even easier.

---

### Post by JEBB on 2010-10-28
Thanks to Megaptera (#2).  The link gave what is the answer, so far at least.

---

### Post by pickarooney on 2010-12-13
I don't know if I'm allowed post in a solved thread but I want to get rid of this keyring thing but am running XFCE so the password and encryption keys option is not available to me. If anyone knows a CLI command to run this app or another way of removing the keyring, please let me know.

---

### Post by migs73 on 2010-12-13
> **pickarooney said:**
> I don't know if I'm allowed post in a solved thread but I want to get rid of this keyring thing but am running XFCE so the password and encryption keys option is not available to me. If anyone knows a CLI command to run this app or another way of removing the keyring, please let me know.

You can post here if you want, but you are more likely to get an answer if you open a new thread as a lot of people will ignore solved threads.

---

### Post by ghelbig on 2011-05-26
> **blazemore said:**
> If your keyring password is the same as your login password, <snip>, Ubuntu won't ask for the password.

This is not true with 10.04.LTS

Is there a way to make it true?

---

