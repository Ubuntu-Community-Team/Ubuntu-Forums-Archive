---
title: "Ubuntu has locked me out"
date: 2010-03-14
forum: New to Ubuntu
---

### Post by Donald1715 on 2010-03-14
I installed Ubuntu 9.10 with the dual boot setting. That was fine except for a display glitch... Then Ubuntu made me make an ADMIN password... fine, I kept it simple as I'm just experimenting with it... I made it 12345678. Ubuntu neither asked, and I did not set a LOGIN name. Last time I rebooted and tried to boot into Ubuntu, I was asked for a LOGIN name and there is NO login name. So I'm locked out and SOL. Any suggestions before I dump it and reinstall? I'm here VIA WinXP in order to write this message.

Oh, I tried ignoring the login name and just hit enter... no luck. Tried the 12345678 password, no luck... tried a blank login name and the 12345678 password... no luck. So I'm SOL.

D

---

### Post by Elfy on 2010-03-14
Hi - if you don't know the username you can find it by starting in recovery mode and going to a root prompt

```
ls /home
```

should tell you what users there are.

While in recovery mode - reset the password

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

If you do not see a menu when you boot - press shift as grub loads.

You will see a list - the second option should be a recovery session.

---

### Post by Ryan Dwyer on 2010-03-14
If you installed it using Wubi (from within Windows) then your username might be the same as your Windows username.

---

### Post by Donald1715 on 2010-03-14
I just fixed it by booting to WindowsXP, uninstalling Ubuntu using AddRemove programs, dumping the recycle bin... then reinstalling Ubuntu. This time I noticed it automatically assigned me a Login name, which I then changed and set a password. All seems well now, and I am here in the forum thru Ubuntu. However, I was surprised to find that Ubuntu has forced it's original automatically assigned Login name despite my changing it in the installer... -shrug- no biggy I guess as I wrote them both down just in case. What threw me the first time around was that it took several reboots until Ubuntu started asking for a Login name.

---

