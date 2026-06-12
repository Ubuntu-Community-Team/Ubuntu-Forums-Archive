---
title: "Login Keyring won't accept my password"
date: 2010-08-09
forum: New to Ubuntu
---

### Post by Dobbie03 on 2010-08-09
So I have logged in normally using my usual login password.  I have just installed evolotion as my email client and Ubuntu is asking for my login keyring.

So I type it in and it tells me that it doesn't match the password saved....why is that?  I just fecking logged in using the same damn password.

---

### Post by Dobbie03 on 2010-08-09
Anyone?

---

### Post by inameiname on 2010-08-09
It sounds like you are confusing the difference between your normal, Login, user password and your keyring password. Both start off the same when you install, but often people forget to change the keyring one when you change the login one. It's very easy to do so, and/or reset if you can't remember it, as it seems is the current state. 

Just go to Accessories -> Passwords and Encryption Keys, and under the Passwords tab, right click and delete whatever is under there. Then you just enter a new password, and voila. Obviously, just enter the one you currently use to log in. And if you ever want to just change it, do the same, but instead of Delete, click Change Password.

Hope that helps.

---

### Post by Dobbie03 on 2010-08-09
Thanks but I literally have no menu for Passwords.  I have gone through everything with a fine tooth comb and can't seeing anything resembling that.

---

### Post by donato roque on 2010-08-09
Ok you should find it in Applications-->Accessories-->Passwords and Encryption keys.  The application will open. If you have a default set up a single folder should be there.  Right-click with your mouse and choose change password.

It will ask for your old password here. Hope you still got it.

Then give the login password for the new password.  What this will do is open the Keyring for your applications when you login.  Otherwise you can give a different password for the Keyring.  Useful when you want to let friends use the laptop without giving them access to email and IM contacts and so on.

---

### Post by donato roque on 2010-08-09
If you can't find Passwords and Encrytions try this.

Type alt+f2. then type seahorse,enter.  The application should open.

---

### Post by inameiname on 2010-08-09
Oops, forgot the 'Applications' part of Applications-->Accessories-->Passwords and Encryption keys. Thanks for adding that, donato rogue. 

From what he said, it sounds like his problem is he either can't remember his old password, or didn't know it differs from his User password. 

Under the 'Passwords' section there, there should be at least one entry as mentioned, probably something like 'Password: default' or 'Passwords: login'. It is that in which you right click and either 'Change Password' or 'Delete' if you can't remember.

Oh, and I didn't know that about using 'seahorse' in the terminal. Cool shortcut, donato rogue.

---

### Post by Dobbie03 on 2010-08-10
Thanks guys, the seahorse thing worked a treat!!

---

### Post by inameiname on 2010-08-10
Glad you got it straight. Don't forget to mark this thread as solved (under Thread Tools in the upper right of this page).

---

