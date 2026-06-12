---
title: "WAN: Password Prompt after login"
date: 2007-07-17
forum: Networking &amp; Wireless
---

### Post by Prosis on 2007-07-17
I have a wireless network that is protected with a key.  When I boot into a freshly installed Ubuntu, it asks me for the key to connect (all is fine for the moment).

Then, once it's connected for the first time, it asks me for a password.  If I don't enter one, it asks me for the key every time.

Is there a way I can just connect once and never have to enter anything after logging in?  In Windows for example, you enter the key once and it remembers it and connects automatically.  Can Ubuntu do that?

Thank You

---

### Post by NilsE on 2007-07-17
The following will allow you to remember connection passwords/keys in the keyring and not get prompted by the keyring manager or network manager every time. 
```
In Synaptic install 

libpam-keyring
```
```
In terminal:

sudo echo "@include common-pamkeyring" | sudo tee -a /etc/pam.d/gdm
```

---

### Post by Prosis on 2007-07-20
It doesn't work.  Every time I login I need to enter the password again.  I've searched the web for that trick and I did it properly it's been added.  But it still doesn't work... :confused:

---

### Post by NilsE on 2007-07-20
When you enter the keyring password is it the same one you enter when you login?

If you have GDM autologin enabled or your passwords are different  this trick won't work.  It will get you to enter your password one way or the other.

---

### Post by Prosis on 2007-07-20
Ah there's my mistake...how can I change my keyring password?

---

### Post by ed67 on 2007-07-21
As nilsE said, if autologin is enabled pam won't work.  This is true. 

So, there's no way to turn on my laptop and come back later and have everything just working?

I'm finding that I either have to enter my username/pwd at login and let pam log in to keyring, or automatically login but then type in my pwd for keyring.  Yes, they're the same passwords.

I understand the logic here but for my purposes I'd like to just hit the power button and come back later to find my computer running and already hooked up to my network.  I'm the only user so it's fine.

---

