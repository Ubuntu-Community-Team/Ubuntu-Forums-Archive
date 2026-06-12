---
title: "Firefox Problem, Please Help"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by djk21108 on 2009-05-05
I'm having a bit of a problem in firefox.  I went into the password manager and deleted some of my passwords for sites that I changed my password on.  Problem is, now it won't give me an option to remember my new passwords.  What should I do?

---

### Post by Michael.Godawski on 2009-05-05
You can try to remove the old password entries in Edit > Preferences > Security > Saved Passwords and enter them again.
Not sure about this.

---

### Post by djk21108 on 2009-05-05
That doesn't seem to be an option :(

---

### Post by HuckleSmothered on 2009-05-06
Does this help?
Stolen from: [http://www.firefoxtutor.com/66/advanced-passwords/](http://www.firefoxtutor.com/66/advanced-passwords/)

   1.  Go to "Tools > Options" in the menu bar.
   2. Click on the "Privacy" icon on the top.
   3. Select the "Passwords" tab.
   4. Click on the "View Saved Passwords" button near the bottom.
   5. Navigate to the "Passwords Never Saved" section in that window.
   6. Select the password that you want Firefox to remember and click "Remove".
   7. Click "Close" when you're done

Also might want to check in the "Exceptions" in the Privacy tab. Although from the sounds of it you've probably already looked through that tab.

I would probably try removing ALL the saved passwords, close Firefox and try again.

If *that* didn't work, I would close Firefox, delete the prefs.js file, then try again.

Let us know what happens.

---

### Post by antmenj on 2009-05-06
> **HuckleSmothered said:**
> .....If *that* didn't work, I would close Firefox, delete the prefs.js file, then try again.

Would it be a good idea to just rename it in case you want it back;)

---

### Post by Paddy Landau on 2009-05-06
> **HuckleSmothered said:**
> Go to "Tools > Options" in the menu bar.
In Ubuntu, it's Edit -> Preferences. ;)

Check the following.

[LIST]
[*]Edit -> Preferences.
[*]Press the Security tab.
[*]Check the box labelled "Remember password for sites" (if not already checked).
[*]Press the "Exceptions" button and remove any site whose password you *do* want remembered.
[/LIST]
HTH

---

### Post by Ms_Angel_D on 2009-05-06
This won't fix your current issue, but it could help in the future.

I suggest checking out the firefox extension [Sxipper]("http://www.sxipper.com/") It is a password manager, form filler. I used to use roboform back in my windows days, but sxipper has replaced it quite nicely. Also it has a nice backup/restore feature.

---

