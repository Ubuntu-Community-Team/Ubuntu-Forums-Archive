---
title: "Keyring... hate typing password everytime"
date: 2007-05-19
forum: Networking &amp; Wireless
---

### Post by Neuralgia on 2007-05-19
is there a way I don't have to type my keyring password everytime I connect to a Wireless spot?

The only time I don't have to do that, is when the spot has no password.

I OBVIOUSLY have a password in my house/work, so on every boot, I need to type it.

Tried playing with Keyring Manager options with no luck.

Any ideas?

---

### Post by seamless on 2007-05-19
libpam-keyring will unlock your keyring when you log in. The only issue is the keyring password must be the same as your login password.

---

### Post by Neuralgia on 2007-05-19
thanks, that was exactly what i needed. i hate keyring

---

### Post by syxbit on 2007-06-03
i installed it, but it still asks for my password
any ideas?

---

### Post by msubullyfan on 2007-06-03
> **seamless said:**
> libpam-keyring will unlock your keyring when you log in. The only issue is the keyring password must be the same as your login password.

I'm having the same issue.  However, I don't know what "libpam-keyring" is.  I'm still learning...

What do I need to do with "libpam-keyring"?

---

### Post by syxbit on 2007-06-04
i think you just install it
all the HOWTO's i've read say you just need to install it, and then if your keyring password is the same as your login password, it'll work
that's not the case for me

---

### Post by julian67 on 2007-06-04
Use Windows. Run as Administrator. Never be inconvenienced again by having to remember your password 4 times in a 48 hour period. Beautiful :D

---

### Post by DocHoliday52090 on 2007-06-04
And watch as your PC melts from the onslought of erroneous services, poor resource management, and spyware waiting gleefully to hijack your OS. 

No thanks. :)

---

### Post by syxbit on 2007-06-04
anyone have a helpful idea?

---

### Post by julian67 on 2007-06-04
You have the choice of typing your password each time or typing your network credentials each time. I've read other people complaining about the same thing but I'm a little puzzled...it can't be that big a deal to type a password perhaps once a day, sometimes a few times. It's not like the thing is nagging away every 5 minutes. Keyring is a good way to store this data, which is after all *supposed* to be protected. A benefit of doing it this way is that the keys  are tied to you the user and not your machine. Using keyring makes them easily portable, easy to back up and transfer, all the while remaining secure. so different users can have their private information remain private  i.e I might be happy to let a friend/colleague/family member have a user account on and occasional use of my laptop but I don't want them having access to my various wep/wpa keys for all the different places I log in, or even to know which networks I have access to.

---

### Post by ouff on 2007-06-29
> **julian67 said:**
> You have the choice of typing your password each time or typing your network credentials each time. I've read other people complaining about the same thing but I'm a little puzzled...it can't be that big a deal to type a password perhaps once a day, sometimes a few times. It's not like the thing is nagging away every 5 minutes. Keyring is a good way to store this data, which is after all *supposed* to be protected. A benefit of doing it this way is that the keys  are tied to you the user and not your machine. Using keyring makes them easily portable, easy to back up and transfer, all the while remaining secure. so different users can have their private information remain private  i.e I might be happy to let a friend/colleague/family member have a user account on and occasional use of my laptop but I don't want them having access to my various wep/wpa keys for all the different places I log in, or even to know which networks I have access to.

You have the right to decide that you like your computer set up that way.  But I should have the ability to set mine up without a password.  I don't know why that's so hard.  Windows does it.  OSX does it.  Why can't GNU/Linux do it?  And yes, I know about pamkeyring.  I don't want to install a hack to get around entering the password.  I want it to be a legitimate option that comes with the default Ubuntu installation.  I've been reading these complaints about keyring for about a year now, and I don't know why Ubuntu developers don't get the point.  I can't really complain, because Ubuntu is awesome and free, but this doesn't seem like a hard option to add.

---

### Post by julian67 on 2007-06-30
So use a different wireless tool like wifi radar or wcid., The choice is there.

---

