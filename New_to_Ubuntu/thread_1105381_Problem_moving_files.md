---
title: "Problem moving files"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by abeautifulplace on 2009-03-24
Hello, I'm trying to install a rainlender skin, but when I try to move the skin file to rainlender's skins folder, I get a 'permission denied' error. I am the only user on my computer, and It doesn't prompt me for my password or anything.
How can I go about moving this file?

---

### Post by kanikilu on 2009-03-24
Where are you trying to move the files to? Also, how are you trying to move them (command line or GUI file browser)? Most likely cause is an ownership or permissions problem.

Probably the easiest solution would be to start a root-owned nautilus window by pressing ALT+F2 and then type *gksudo nautilus*. Enter your password when requested, and a new file browser window will come up. Now you should be able to copy/move those files.

// Edit - BTW, just because you are the only person that uses the computer, that doesn't mean you have access (by default) to all the system files. Generally speaking you can use sudo (or in this case gksudo since you're running a GUI application) to temporarily act with root access and by-pass these restrictions. You can read more about sudo here, if you want: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by abeautifulplace on 2009-03-24
Thank you so much :)

---

### Post by stchman on 2009-03-24
> **abeautifulplace said:**
> Hello, I'm trying to install a rainlender skin, but when I try to move the skin file to rainlender's skins folder, I get a 'permission denied' error. I am the only user on my computer, and It doesn't prompt me for my password or anything.
How can I go about moving this file?

Unless your user owns the folder you are trying to move the files to you will get a access denied message.  You need to use sudo to move files to protected areas.

Ubuntu's permissions protect it from attacks from malicious code.

---

