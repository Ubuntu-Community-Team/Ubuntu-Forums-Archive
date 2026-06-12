---
title: "Help with editing user privileges..."
date: 2009-03-20
forum: New to Ubuntu
---

### Post by delta44 on 2009-03-20
Hi all,

I am on my 3rd day converting to unbuntu and so far I have loved it, of I still have a lot to learn. The problem I am currently having is editing user privileges. I use the user settings tool to try to change them but when I click on the "User Privileges" all the options are grayed out. I know the user is on admim, is there something through the terminal I should do? Thanks for any help!

---

### Post by SunnyRabbiera on 2009-03-20
Make sure you hit "unlock" when using apps like this, I assume you are using "users and groups"?

---

### Post by delta44 on 2009-03-20
Wow I feel really newbish right now but where is the unlock?

---

### Post by delta44 on 2009-03-20
Nevermind! Found it, thanks for the help!

---

### Post by kanikilu on 2009-03-20
If you want to do it through a GUI, try opening a root-owned nautilus window:

- Press ALT+F2
- Type *gksudo nautilus* in the dialog box that opens
- Enter your password when prompted

You should now have the ability to change permissions as needed (they shouldn't be gray).

If you want to do this from the command line, check out the manual pages for chown and chmod.

// Edit - Nevermind, I was confused about what you were trying to do...

---

### Post by SunnyRabbiera on 2009-03-20
> **delta44 said:**
> Nevermind! Found it, thanks for the help!

No prob.

---

