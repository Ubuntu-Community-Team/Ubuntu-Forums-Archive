---
title: "why the key locker?"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by ELD on 2009-02-06
I have only recently started using the latest ubuntu and when i try and saves passwords it now asks me for another password to store that password in some locker or something..uh what the frack?

Why can't it just be simple :S

---

### Post by ELD on 2009-02-06
It's not simple though, if i use many different things that require passwords, i can easily get confused by what password i am using for what.

Before programs stored my passwords fine without the need for this stupid locker!

---

### Post by LowSky on 2009-02-06
if you leave the keyring lock password blank you will never ever see it again. Which is what I do. MAybe not the safest thing but it doesnt annoy me

---

### Post by ELD on 2009-02-06
I will try that then maybe.

I just don't see why it is needed, we could store our passwords in the applications fine before, now it wants us to stick them in a locker...seems really pointless to me.

---

### Post by ELD on 2009-02-12
Okay this reall does bug me i thought the whole idea of when admin is needed the screen darkens asking for admin password, why the key locker now as well, it even comes up when i want my pc to connect to wireless, it's starting to do my tits in.

---

### Post by tarps87 on 2009-02-12
The locker is call gnome keyring in gnome or kwallet in kde, it was in hardy and I believe it was also in gusty. If you use auto login it will ask you for your password when it trys to connect to the internet however if you login manually it doesn't. You can change this be removing the keyrings password. The idea in it is one central, secure location where all the passwords are stored, this means you only need to remember on password, in the keyring manager you can set it so selected applications do not require you to enter your keyring password.

---

### Post by ELD on 2009-02-12
It worked fine before, i had auto-login and never needed to enter yet another password to even connect to my wireless, seems pretty dumb to me.

---

### Post by LowSky on 2009-02-12
yeah I hate it too, just do what I did, got to /home/.gnome2/keyring (I think that is the path...On Windows at the moment) and delete the file. 

Next time you log in the key rin manager will ask you to set a password. Don't type anything, just hit ok, and it will give you some warning, just tell it to go to hell, and your all set it will never bother you again.

---

### Post by ELD on 2009-02-12
Thanks i might just do that (also on windows atm). I am glad i am not the only one.

It seems so dumb for example login to pidgin, i have my password saved into it, why should i need to enter another password to get into it.

It is overcomplicating things to the point where it just isn't needed!

---

