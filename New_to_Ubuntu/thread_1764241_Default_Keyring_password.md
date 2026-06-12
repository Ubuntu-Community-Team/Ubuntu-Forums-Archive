---
title: "Default Keyring password"
date: 2011-05-21
forum: New to Ubuntu
---

### Post by Mccfuzz on 2011-05-21
I've been using Ubuntu about one day and I've been trying to set up Evolution mail to send e-mail.  When I came do a test send/receive after I'd in-putted the server password it then asked me for  'a default kering password'.
I've no idea what this is,  what it's for and I especially don't know the password as I was never asked to invent one.
Tried the one I gave for entering other drives etc but that is obviously not the one.

Any ideas...!

Yourd Mccfuzz

---

### Post by syntr on 2011-05-21
I'd assume it's your account password.

---

### Post by Mccfuzz on 2011-05-21
No this window appears after I've inputted the account password.

The full message reads:
"evolution (/us/bin/evolution) wants access to the default keyring but it is locked"

---

### Post by mcduck on 2011-05-21
The default keyring password is the same as the login password you set when you installed Ubuntu.

The keyring is used to store passwords, encryption keys other stuff like that for all the programs, keeping the data securely encrypted when the keyring is locked. If you use a normal login (typing your password in the login screen), the keyring gets unlocked automatically as long as the keyring password and login password are same. If you use automatic login or have different login password and keyring password, you need to type in the keyring password to unlock it when some program tries to access the keyring. It's also possible to set the keyring password to empty one, that way you'll never have to unlock it even with automatic login, but you'll of course loose the security it would provide.

To manage the stored keys or change the keyring password you can use the "Passwords and Encryption Keys"-tool in the System Settings.

---

### Post by Wim Sturkenboom on 2011-05-21
> **mcduck said:**
> ... If you use a normal login (typing your password in the login screen), the keyring gets unlocked automatically as long as the keyring password and login password are same.
...

That does not always seem to work. I had an automatic login in lubuntu 11.04 so I set a password for the passphrase for my wireless connection. After reconfiguring to have a non-automatic login (same password), it still kept prompting me to unlock when connecting to the wireless.

---

### Post by mcduck on 2011-05-21
> **Wim Sturkenboom said:**
> That does not always seem to work. I had an automatic login in lubuntu 11.04 so I set a password for the passphrase for my wireless connection. After reconfiguring to have a non-automatic login (same password), it still kept prompting me to unlock when connecting to the wireless.

Have you at some point changed your login password, then? If you do that you need to change the keyring password as well.

Also I believe Lubuntu uses LXDM as it's desktop manager instead of GDM, and at some point LXDM had a bug that caused it to not unlock the keyring. As far as I know that should be fixed by now.

---

### Post by Mccfuzz on 2011-05-21
Hi thanks for the  help.  I've sorted the problem now.
I did it by deleting the password folder in 'password and encryption'.
The next time I tried to use the e-mail it simply asked to invent a new keyring password so I reset it using the password I used for opening files etc.

I've still no idea why the Keyring option exists or what it's for

---

### Post by Miljet on 2011-05-21
> I've still no idea why the Keyring option exists or what it's for

I thought that mcduck explained pretty well what the keyring is and what it is used for. See his post above.

---

### Post by Wim Sturkenboom on 2011-05-22
> **mcduck said:**
> Have you at some point changed your login password, then? If you do that you need to change the keyring password as well.
No, install was about an hour old when I changed from automatic to a non-automatic login ;)

> **mcduck said:**
> Also I believe Lubuntu uses LXDM as it's desktop manager instead of GDM, and at some point LXDM had a bug that caused it to not unlock the keyring. As far as I know that should be fixed by now.Not sure; can't check it anymore as I removed it and I'm now running chrunchbang which I straight away set up for non-automatic login like I usually do for my other systems.

---

### Post by temporos on 2011-05-22
> **mcduck said:**
> Have you at some point changed your login password, then? If you do that you need to change the keyring password as well.

I changed my login password, but neither the old nor new passwords work when trying to unlock my default keyring now.

---

### Post by audiomick on 2011-05-22
> **Mccfuzz said:**
> Hi thanks for the  help.  I've sorted the problem now.

I've still no idea why the Keyring option exists or what it's for

One of the things it does, as an example, is remebers and provides the password  for a WLAN connection that you might have set up, so that the computer can automatically connect when it sees that network.

---

