---
title: "Question?"
date: 2010-08-18
forum: New to Ubuntu
---

### Post by adam342 on 2010-08-18
Being using ubuntu and i have to say very very impressed with the OS. I have an issue with the stupid keyring box everything i boot up, i have my internet set up with mobile broadband. 

And second of all i have the cairo dock installed if i remove the Desktop icon of the bar ubuntu will shut off and will restart and not let me back in, why is that??? so i went back into failsafe mode added the icon back and it works fine now.

---

### Post by Zorgoth on 2010-08-18
My first guess would be that the reason you get the keyring box is because either you set the keyring password to be different from your user password or because you do not use a password to log in.  If you do not use a password to log in, you cannot have a keyring password unless you want that box to pop up.  If you use a differe

Not having a keyring password is insecure in the sense that someone with access to the computer could figure out any data stored in the keyring (I think this will be passwords for any networks you connect to and also remembered password for applications like Empathy if they are set to remember password).  This is an unavoidable side effect of not using a password at any point to login.

If you type your user password at each login and your keyring password is the same as your user password you shouldn't have this box and you should post about it.

What is this "Desktop" icon?  Switcher (the one you use to switch between workspaces)?

---

