---
title: "keyring password"
date: 2008-05-28
forum: Networking &amp; Wireless
---

### Post by Findarato on 2008-05-28
Hello everyone,

I get the following error trying to connect to my server:

```
the application "gnome-panel" wants access to the default keyring, but is locked
```

Everything was working fine till before yesterday's updates.

Any idea how I could solve this?

---

### Post by Findarato on 2008-05-29
anyone?

---

### Post by Findarato on 2008-05-30
please, anyone? I can't find anything resolving this problem on the internet :S

---

### Post by Findarato on 2008-05-31
...

---

### Post by Findarato on 2008-05-31
well, first of all thanks for your answers... 

If ever, I finally found the answer and it was quite stupid in the end, I just end up trying "1234" as the default password, and it worked... It might be because I used this password during my installation process, so you could check that out if you encounter the same problem.

---

### Post by LarryJ2 on 2008-06-01
I have the problem also except it says "Evolution wants access to the default keyring but it is locked"  The password I entered during installation doesn't get rid of the Unlock Keyring "Enter Password..." dialog.  But after blindly entering the install password, if I then close (X) the Unlock Keyring dialog,  then evolution gets mail as usual.  Must be a bug in the keyring area.

---

### Post by Gourgi on 2008-06-03
maybe this helps
[http://ubuntuforums.org/showpost.php?p=5103300&postcount=7](http://ubuntuforums.org/showpost.php?p=5103300&postcount=7)

---

### Post by p_quarles on 2008-06-03
It sounds like you just need to delete the file containing your current Gnome-keyring. This would be in a hidden folder in your home directory. Deleting the file will allow the program to create a new default keyring, and will ask you for a password to attach to it when it does.

---

### Post by LarryJ2 on 2008-06-05
That's it.   So simple....
System->Preferences->Encyption and Keyrings then 
highlight the password keyring "login" then click Remove Keyring then reboot.

Thanks!   For me at least,  my problem with Evolution asking for password can be marked as [SOLVED!]

---

