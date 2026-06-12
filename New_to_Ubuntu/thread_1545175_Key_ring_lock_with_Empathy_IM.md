---
title: "Key ring lock with Empathy IM"
date: 2010-08-03
forum: New to Ubuntu
---

### Post by ericstrom on 2010-08-03
I'm new to Empathy IM client. I thought I had it working but then I restarted my PC, opened Empathy and am now getting the following message:

Enter password for keyring default unlock

The password you entered was incorrect

I have no idea what the password is. How do I resolve this ?

---

### Post by mcduck on 2010-08-03
Unless you have changed it yourself at some point the keyring password is the same as the login password you set when you installed Ubuntu.

If the keyring password is set to same as your login password, and you use normal login, you don't need to give the keyring password separately. But if you use automatic login or have different login password and keyring password you will need to input the keyring password to unlock it when any program tries to access the keyring.

So, if the case is that you have at some point changed your login password, you need to change the keyring password to same.

If you use automatic login, you probably want to just set the keyring password to empty one, if you do that you loose the security (probably not an issue for anybody using automatic login) but you never need to input the keyring password again.

Either way, you can change the keyring password if you go to Applications/Accessories/Passwords and Encryption Keys, right-click the "Passwords:login"-keyring and select "Change Password".

---

