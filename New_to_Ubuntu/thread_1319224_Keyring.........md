---
title: "Keyring........"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by nusry on 2009-11-08
What is the Keyring used in Ubuntu 9.10??

plz explain me...

---

### Post by nusry on 2009-11-08
anybody there.....

---

### Post by quickdraw on 2009-11-08
I always understood the keyring to be a process that saves passwords used for system administration and certain programs - like Evolution.

---

### Post by Somme on 2009-11-08
[LIST=1]
[*]Don't bump your thread so often
[*]The answer can be found on [Launchpad]("https://answers.launchpad.net/ubuntu/+question/614")
[/LIST]

---

### Post by bacardiandwatermelon on 2009-11-08
What are you wanting to know? what the package name of the keyring is or how it works?

---

### Post by rsinha on 2009-11-08
The keyring is an application that stores credentials (like passwords, Wireless secrets) for various applications. It is usually protected with a password that is required to unlock it. Certain applications (e.g. Empathy, the chat client) use the keyring to store your IM passwords if you select Save password. At every boot, the Empathy client would request the keyring application for the passwords to login to your IM accounts.

You would get a request similar to "App empathy needs access to the keyring, allow? ". 

Hope this clears it up!

---

### Post by ursoouindio on 2009-11-08
Ok, I have just made a fresh install of Karmic Koala and this Keyring thing is bothering me everytime I turn on my notebook.

I use a WPA2 secured wireless connection but would like to connect automatically, without always having to enter the password for the keyring.

What kind of customization I have to make?

Thanks

---

### Post by Paqman on 2009-11-08
> **ursoouindio said:**
> 
What kind of customization I have to make?


Just set the login window so that you have to enter your password to log in. You'll only be prompted for a password to unlock the keyring if you've not had to provide your password since booting.

---

### Post by ursoouindio on 2009-11-08
hmm
I see.

I would prefer anyhow to not enter any password everytime I start Ubuntu, but I think that entering my password at the login is a little better.

Thanks

---

