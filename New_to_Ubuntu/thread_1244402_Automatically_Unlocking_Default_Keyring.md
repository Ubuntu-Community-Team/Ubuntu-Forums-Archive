---
title: "Automatically Unlocking Default Keyring"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by GCoffee on 2009-08-19
Hi,

No doubt this issue has been covered many times, but i couldnt get any of the solutions to work. :(

Basically i have a newly installed copy of ubuntu netbook remix. I'm trying to make it as user-friendly as possible for a family member of mine. I've got auto login set etc.

However, when I try to automatically unlock the default keyring (not wanting to be asked what the password is and what it does every 10 minutes..) It still pops up :(

I added:

```

@include common-pamkeyring

```

to the:
/etc/pam.d/gdm file

and installed the pamkeyring thingy it still pops up :'(

Does anyone know how to unlock automatically?

Thanks,
GCoffee

---

### Post by mcduck on 2009-08-19
remove the keyring password:

1. open the keyring manager (Applications/Accessories/Passwords and Encryption Keys)

2. Go to Edit/Preferences

3. On the Password Keyrings-tab select the "Passwords:login"-keyring & click "Change Unlock Password"

Now you can change the keyring password. If you use normal login set the password to same as your login password is to unlock the keyring automatically. If you use automatic login leave the new password fields empty to remove the keyring password.

---

### Post by zeezam on 2009-12-29
> **mcduck said:**
> remove the keyring password:

1. open the keyring manager (Applications/Accessories/Passwords and Encryption Keys)

2. Go to Edit/Preferences

3. On the Password Keyrings-tab select the "Passwords:login"-keyring & click "Change Unlock Password"

Now you can change the keyring password. If you use normal login set the password to same as your login password is to unlock the keyring automatically. If you use automatic login leave the new password fields empty to remove the keyring password.

I have tried this several times but I have to manually unlock keyring for my wireless network manager.
I use karmic and automatic login.

It's irritating because have xbmc in startup programs and want to connect to wifi automaticly...

---

### Post by doas777 on 2009-12-29
you can set the unlock password to blank, but that means that your stored passwords will be unencrypted on disk and in memory, so someone with access to your system could discover them. if that is not a problem in your estimation, then just set it to blank, and ok "unsecure storage"

---

### Post by zeezam on 2009-12-29
> **doas777 said:**
> you can set the unlock password to blank, but that means that your stored passwords will be unencrypted on disk and in memory, so someone with access to your system could discover them. if that is not a problem in your estimation, then just set it to blank, and ok "unsecure storage"

Ok. I hope not my neighbors are able to crack my WPA2 wifi and sniff :)

---

### Post by zeezam on 2009-12-30
> **doas777 said:**
> you can set the unlock password to blank, but that means that your stored passwords will be unencrypted on disk and in memory, so someone with access to your system could discover them. if that is not a problem in your estimation, then just set it to blank, and ok "unsecure storage"

It seems to work now.

---

### Post by mdwittenberg on 2010-01-29
*So am I hearing this correct:*
A user must decide **between**:
[LIST]
[*]A unsecure system where any password in keyring can be easily extracted 
[*]Typing in the same password that was used for auto-login every boot
[/LIST]

Personally, this does not seem like a choice that a person should have to make. Security is paramount, yet typing in a password just for wifi seems ridiculous.

Are there any alternatives?

---

### Post by mcduck on 2010-01-30
> **mdwittenberg said:**
> *So am I hearing this correct:*
A user must decide **between**:
[LIST]
[*]A unsecure system where any password in keyring can be easily extracted 
[*]Typing in the same password that was used for auto-login every boot
[/LIST]

Personally, this does not seem like a choice that a person should have to make. Security is paramount, yet typing in a password just for wifi seems ridiculous.

Are there any alternatives?

Not really.

There are 3 choises:
[LIST]
[*]Secure system where you use password to log in. Keyring is unlocked automatically for you. (you have to type 1 password)
[*]Easy but unsecure system with automatic login and storing passwords unencrypted. (you don't need a password at all)
[*]Either log-in or keyring with password, and the other one without. You're free to do it if you want to, but it rarely makes any sense. (once again jst one password)
[/LIST]
So which ever way you choose to set up your system, you'll never have to type the same password twice (for both log-in and the keyring).

As long as your keyring password is same as your login password, the keyring will be automatically unlocked for you when you log in. And if you don't use login password, you probably don't really care abut such security anyway so storing your paswords unsecured is not a problem. After all, you without login password you have already left your whole user account and all your files unsecured... ;)

edit: Well, of course there's is the option of intentionally using different passwords for login and the keyring, which would make your passwords even extra secure but would require you to type both passwords. I'd rather go for encrypting the user home directory instead if I needed that level of security.

---

### Post by orangemoose on 2010-01-31
I completely agree with you. It has bugged me since the first day I installed Ubuntu.

It is an absurdity--but, hey, it's a free absurdity.

---

### Post by J V on 2010-01-31
I don't encrypt seahorse, firefox etc... home encryption does that for me and lets me get away without having to type in passwords...

---

### Post by andersvinther on 2010-02-24
I have got my whole disk encrypted, so using automatic login and unsafe storage is not a big problem for me...

If I ever do lose my netbook everything is encrypted...

And I only need to enter the encryption passphrase when I start up...

Works fine for me :-)

Anders

---

