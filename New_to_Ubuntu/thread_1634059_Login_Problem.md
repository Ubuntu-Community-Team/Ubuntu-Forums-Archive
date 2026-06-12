---
title: "Login Problem"
date: 2010-11-30
forum: New to Ubuntu
---

### Post by Deedlebag on 2010-11-30
Whenever I log into my account when I start my computer, it plays the login sound and then goes back to the login screen. I'm using Ubuntu 10.10 and I've never had this problem before. It just recently started doing this today and I have not a clue why. I just installed Ubuntu 3 days ago and I left for the weekend and when I came back it started doing this. Help is much appreciated

---

### Post by jtarin on 2010-11-30
At the Grub2 prompt select "rescue mode" and see if you can get to the desktop. If you can then create a new user and then try booting  with the standard kernel and see if you can login as the new user.

---

### Post by Deedlebag on 2010-11-30
Well assuming rescue mode is the same as Safe-Mode, I was able to get to the Desktop but when I try to make a new user, nothing happens (when I press the New User button) or most buttons on the Users & Groups

---

### Post by jtarin on 2010-11-30
[Documentation for adding newuser.]("https://help.ubuntu.com/8.04/serverguide/C/user-management.html")

---

### Post by Deedlebag on 2010-11-30
Well it seems that to get to my main account normally, i have to use the new account I created, then log out, then log into my main account.

---

