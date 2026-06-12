---
title: "How do I remove &quot;Unlock Keyring&quot; message at bootup"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by jacatone on 2009-01-19
I'm running Ubuntu 8.10. For some reason, I get the following window when I bootup into Ubuntu:

Unlock Keyring

The application 'NetworkManager Applet' (/usr/bin/nm - applet) wants access to the keyring, but it is locked.

How do I remove this? Thanks.

---

### Post by cmnorton on 2009-01-19
It's either or...

Under ~/.gnome2/keyrings

if there is default.keyring, delete it. It will be re-created the next time, and you can specify the correct password.

If there is none, create it in Applications --> Accessories --> Passwords and Encryption Keys --> Edit --> Preferences

and give it a known password, like yours. 

If you set it to no password, then Network Manager will connect with wireless without prompting you.

I had the second problem.

Before performing the delete step, search these forums and/or Google for this, because there is more discussion on it, especially on what happens when you delete the default keyring. I cannot remember all the details, so continue looking to be safe.

---

### Post by mister_pink on 2009-01-19
Basically the keyring is used to store your wireless network keys securely. It is set to the same as your login password when you install ubuntu, and so normally you won't have to enter it (it's unlocked automatically when you log in). However if you change your password it doesn't get updated, so you'll have to manually change it. 

If you don't know your old password then you'll have to do as the previous poster said - this will result in losing the network keys you have stored. Otherwise, go to Applications, Accessories, Passwords + Encryption keys. Then go to Edit, Preferences, and select the one called login, then Change Unlock Password. You are allowed to set it to blank if you wish, wireless keys will then be stored unencrypted but you'll never be bugged again.

---

### Post by cmnorton on 2009-01-19
> **mister_pink said:**
> Basically the keyring is used to store your wireless network keys securely. It is set to the same as your login password when you install ubuntu, and so normally you won't have to enter it (it's unlocked automatically when you log in). However if you change your password it doesn't get updated, so you'll have to manually change it. 

If you don't know your old password then you'll have to do as the previous poster said - this will result in losing the network keys you have stored. Otherwise, go to Applications, Accessories, Passwords + Encryption keys. Then go to Edit, Preferences, and select the one called login, then Change Unlock Password. You are allowed to set it to blank if you wish, wireless keys will then be stored unencrypted but you'll never be bugged again.

Thank you for this reply. I went back to my default keyring and added my changed password, rebooted, and was not prompted when Network Manager connected me to my wireless network.

---

### Post by jacatone on 2009-01-19
How do I set it to "no password"? I don't see an option for that.

---

### Post by Dumbestcrayon on 2009-01-19
> **jacatone said:**
> How do I set it to "no password"? I don't see an option for that.

When you select Change Password
Put in your old password and leave the two New Password spots blank.

---

