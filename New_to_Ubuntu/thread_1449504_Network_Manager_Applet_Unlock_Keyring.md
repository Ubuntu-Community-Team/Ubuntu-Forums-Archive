---
title: "Network Manager Applet Unlock Keyring"
date: 2010-04-07
forum: New to Ubuntu
---

### Post by golfnut324 on 2010-04-07
I'm getting the following message box every time I boot:

Unlock Keyring
Enter password for default keyring to unlock

The application 'NetworkManager Applet' wants
access to the default keyring but is locked.

Password____________________________________


How do I get rid of this?
Thanks again for helping a noob!

Craig

---

### Post by Temposs on 2010-04-08
Did you set the machine to login automatically without typing your password?

---

### Post by iponeverything on 2010-04-08
> **golfnut324 said:**
> I'm getting the following message box every time I boot:

Unlock Keyring
Enter password for default keyring to unlock

The application 'NetworkManager Applet' wants
access to the default keyring but is locked.

Password____________________________________


How do I get rid of this?
Thanks again for helping a noob!

Craig

The only way that I know is to remove the password from the keyring. 

Go to:

Applications -> Accessories -> Passwords and  Encryption keys
Then go to Edit -> Preferences in "Passwords and  Encryption keys" Then in the "Password Keyrings" tab, Click on the "Change Unlock Password" - and change it so there is none.

---

### Post by uRock on 2010-04-08
> **golfnut324 said:**
> I'm getting the following message box every time I boot:

Unlock Keyring
Enter password for default keyring to unlock

The application 'NetworkManager Applet' wants
access to the default keyring but is locked.

Password____________________________________


How do I get rid of this?
Thanks again for helping a noob!

Craig

Go into network manager again, click edit on your current config and when the next window opens,check the "Available to all users" box in the lower left hand corner, click close(apply), enter password one last time.

Cheers,
Ronnie

---

### Post by golfnut324 on 2010-04-08
> **uRock said:**
> Go into network manager again, click edit on your current config and when the next window opens,check the "Available to all users" box in the lower left hand corner, click close(apply), enter password one last time.

Cheers,
Ronnie


Thanks, worked like a charm!

---

