---
title: "Wireless Password entry on boot."
date: 2009-03-03
forum: New to Ubuntu
---

### Post by Webbnuts on 2009-03-03
Hi there,

I am a Ubuntu newbie, but am really pleased I've made the jump!  I have one question though, I have to enter my keychain password every time i switch the machine on so the wireless network will connect.  Is there a way to automate this?

Many thanks in advance,

Sam.

---

### Post by avtolle on 2009-03-03
Have you selected the autologin feature? If so, you will be asked for the keychain password every time. You could disable the auto login feature under sessions, and sign in with your user name and password, and, IIRC, avoid the keychain question. HTH.

---

### Post by ssam on 2009-03-09
or you can change the keyring password to be an empty password, then it can be automatically unlocked when needed.

---

### Post by ming0 on 2010-05-10
> **ssam said:**
> or you can change the keyring password to be an empty password, then it can be automatically unlocked when needed.

Is this much of a security risk -- aside from someone being physically on your computer? In other words, I am not as concerned about physical security as I am about malware/malperson/whatever sneaking in from the network. 

I wish I could disable the keyring just for wifi -- I could care less who has access to my wifi passwords.

---

### Post by Scunnered on 2010-05-10
It is easy to have your wireless password to be activated at login.  This naturally does have security implications but provided that you accept these then you can automatically login and have your wireless connection activated at the same time.

As my laptop spends the majority of its life in my home I have done the following :

1. Selecting System > Administration > Login Screen and unlocking the screen will let you login automatically.

2. By right clicking on the Wireless Network connection action and selecting Edit connections you then click on wireless and highlight your connection and click edit.At the foot of the page there is an option of available to all users. 

You will see that having completed the exercise that you are disconnected from the wireless connection so restart the system and everything will work automatically.

When you take your system from your place of security just reverse the process to keep your system safe.

I hope that this is of assistance.

---

