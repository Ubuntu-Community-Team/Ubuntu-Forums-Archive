---
title: "Keyring annoyance"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by Gp. on 2009-03-09
Everytime my laptop starts up, it asks for my password for a keyring or something for my network adapter?

How do I stop this?

---

### Post by avtolle on 2009-03-09
If you enabled auto login to bypass entering your user name and password on start up, the keyring will ask for your password for the network adapter. The easiest solution, IMO, is to disable auto login, enter user name and password once at the start screen, and then go forward from there.

---

### Post by vanadium on 2009-03-09
I prefer autologin, and thus I prefer disabling the password of the keyring:

System - Preferences - Encryption and Keyrings, Password keyrings tab. Click "login", then "change unlock password": provide no new password.

This decreases the security of your system. The balance between security and convenience is one you must decide for yourself.

---

### Post by avtolle on 2009-03-09
> **vanadium said:**
> I prefer autologin, and thus I prefer disabling the password of the keyring:

System - Preferences - Encryption and Keyrings, Password keyrings tab. Click "login", then "change unlock password": provide no new password.

This decreases the security of your system. The balance between security and convenience is one you must decide for yourself.
Good point made in your final paragraph. Due to where my systems are located (office environment, third party access to them in the form of cleaning crews, etc.), I opt for a bit more security over convenience. It is, as you state, up to each user to make that decision.

---

### Post by Gp. on 2009-03-09
> **vanadium said:**
> I prefer autologin, and thus I prefer disabling the password of the keyring:

System - Preferences - Encryption and Keyrings, Password keyrings tab. Click "login", then "change unlock password": provide no new password.

This decreases the security of your system. The balance between security and convenience is one you must decide for yourself.

I have the Encryption and keyrings section, but nothing else you described.

There are two tabs. Encryption and PGP Passphrases.

On Encryption, there is only one option. Default key is set to "None. Prompt for a key".

---

### Post by Scubdup on 2009-03-09
I think I had the same problem (or set I wanted to change) as you:

[Internet connection password requested at startup]("http://ubuntuforums.org/showthread.php?t=1059812")

Mcduck's advice in that thread sorted me out:-

> **mcduck said:**
> Don't delete the keys from the keyring, just the keyring password.

Open the Keyring manager, then go to Edit/Preferences. On the Password Keyrings-tab select the "login"-keyring, and click "Change Unlock Password"-button. Then type your old keyring password but leave the fields for new password empty and click "Change".

Hope that helps

---

### Post by vanadium on 2009-03-09
@Scubdup: That is what I also said.

@Gp: That looks like you are working with an older Ubuntu version. It is not so long ago that you could not change the keyring pasword other than deleting and recreating it. You might be helped with this [http://mexpolk.wordpress.com/2008/02/06/ubuntu-change-default-keyring-password/](http://mexpolk.wordpress.com/2008/02/06/ubuntu-change-default-keyring-password/) which instructs you to install seahorse and use that to change your password (=set it to blank)

---

### Post by hostilejosh on 2009-03-09
what is a key/keyring?

---

### Post by Gp. on 2009-03-10
> **vanadium said:**
> @Scubdup: That is what I also said.

@Gp: That looks like you are working with an older Ubuntu version. It is not so long ago that you could not change the keyring pasword other than deleting and recreating it. You might be helped with this [http://mexpolk.wordpress.com/2008/02/06/ubuntu-change-default-keyring-password/](http://mexpolk.wordpress.com/2008/02/06/ubuntu-change-default-keyring-password/) which instructs you to install seahorse and use that to change your password (=set it to blank)

Negative. I am using Ubuntu 8.10.

---

### Post by vanadium on 2009-03-10
There are five tabs in 8.04: Password keyrings, Encryption, PGP Passphrases, Key Servers and Key Sharing. Someone using 8.10 will need to step in.

---

### Post by ddalley on 2009-03-10
I have this problem with a new USB install of Xubuntu.

The problem is that I don't have "login" listed in "Passwords".

Now what do I do?

---

### Post by A.Collier on 2009-03-12
I have this same problem using 8.10. I have changed my login password, but the keyring asks me for a password to unlock it when I open my evolution mail. Unfortunately it's still the old password. How do I change it? I also don't have a password tab under the Encryption and Keyrings Menu.

---

### Post by A.Collier on 2009-03-12
Never mind. I figured it out. I was looking under System-->Preferences-->Encryption and Keyrings, when I should have been in Applications-->Accessories-->Passwords and Encryption Keys. There I was able to change the unlock password, and on restart, no prompt to unlock. I'll keep my fingers crossed. 

Is there any security problem with keeping my login and keyring password the same?

---

### Post by vanadium on 2009-03-12
> Is there any security problem with keeping my login and keyring password the same?
If they know your login password, they also know your keyring password.

Do not be too frantic about this: make the balance for yourself between security you need and convenience. If I'd keep nuclear secrets on my computer, I would use long and different passwords. Goes without saying that I would be using disk and memory encryption as well.

---

### Post by mcduck on 2009-03-12
> **ddalley said:**
> I have this problem with a new USB install of Xubuntu.

The problem is that I don't have "login" listed in "Passwords".

Now what do I do?
It's not listed in "Passwords". You need to go to Edit/Preferences, and it's in the "Password Keyrings"-tab of *that* dialog..

---

