---
title: "Keyring password on startup - I have to input it 5 or 6 times."
date: 2011-05-07
forum: New to Ubuntu
---

### Post by Boris-- on 2011-05-07
So, each time my computer starts, I have to input my keyring password 5 to 6 times (I suppose this many apps need authorization). Can it be done so that I input it only one time?

---

### Post by hakermania on 2011-05-07
5 or 6 times???
Is this good?
I have to input it only to connect to the internet and I can also disable this by making the network available to all users easily (but I don't because I don't want it to be available to all users xD)
Can you please tell us which applications are requesting for password?

Also, please notice that an attempt of giving the wrong password results to another prompt requesting for password. Are you sure this isn't the problem?

---

### Post by rx007 on 2011-05-07
yeah me too, i am sure i have input my password correctly, but it still pops several times.

---

### Post by gandaran on 2011-05-07
> **Boris-- said:**
> So, each time my computer starts, I have to input my keyring password 5 to 6 times (I suppose this many apps need authorization). Can it be done so that I input it only one time?
you can even set it to never ask for passwords.
go to system » preferences » passwords and keys, remove/clear up every keyring there including login or default then next time you login enter the wireless or email password but for the keyring password either set one or use a blank password, just click the okay button if you prefer the unsecured option.

---

### Post by hakermania on 2011-05-07
I assume that this must be very annoying!
Can you give more info about the programs that require your password or (OMG) you blindly give it (DANGER)?

---

### Post by Boris-- on 2011-05-08
> **hakermania said:**
> I assume that this must be very annoying!
Can you give more info about the programs that require your password or (OMG) you blindly give it (DANGER)?

Well, just off the top they are:

gm-notify (gmail checker)
ubuntu one
wireless network
empathy
google calendar.

So there is no way that I can just write the password one time? Definitively not going for the unsecured no-password option but writing the same password for 5 times fells stupid.

---

### Post by gandaran on 2011-05-08
> **Boris-- said:**
> Well, just off the top they are:

gm-notify (gmail checker)
ubuntu one
wireless network
empathy
google calendar.

So there is no way that I can just write the password one time? Definitively not going for the unsecured no-password option but writing the same password for 5 times fells stupid.
theres something wrong with the keyring setup, follow my instructions and set new keyring password, should fix your problem with new keyring profile.

---

### Post by geazzy on 2011-05-08
> **gandaran said:**
> you can even set it to never ask for passwords.
go to system » preferences » passwords and keys, remove/clear up every keyring there including login or default then next time you login enter the wireless or email password but for the keyring password either set one or use a blank password, just click the okay button if you prefer the unsecured option.

What if I use Natty?

---

### Post by donato roque on 2011-05-08
> you can even set it to never ask for passwords.
go to system » preferences » passwords and keys, remove/clear up every keyring there including login or default then next time you login enter the wireless or email password but for the keyring password either set one or use a blank password, just click the okay button if you prefer the unsecured option. 

I have mine set up so so that login password is the same as the keyring password. When I give the login password at the start of my session it simultaneously opens the keyring. 

I don't really recommend leaving the keyring or login password blank.

---

### Post by felipeochoa0918 on 2011-05-08
I'm having the same problem. I think one of them might be related  to the screensaver (the second or third prompt, after typing my password goes straight to screensaver). I had the same problem on 10.10, but I could just "esc" my way out of having to type it in. Now the prompts are more insistent. I don't mind terribly getting 7 (last count) prompts. I would like to know what it is I'm unlocking for whom.

Unfortunately
[https://bugzilla.gnome.org/show_bug.cgi?id=574315#c4](https://bugzilla.gnome.org/show_bug.cgi?id=574315#c4)

It sounds to me like the solution is to put all your passowrds in the "login" keyring and do away with auto-login. You'll be typing your password anyway, so there's very little savings in using auto-login. You could also set your keyring password to blank, but that seems insecure IMO.

---

