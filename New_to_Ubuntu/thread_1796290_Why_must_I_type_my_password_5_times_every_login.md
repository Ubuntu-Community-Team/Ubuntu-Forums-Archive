---
title: "Why must I type my password 5 times every login?"
date: 2011-07-03
forum: New to Ubuntu
---

### Post by outleradam on 2011-07-03
Why must I type my keyring password 5 times every login?  How do I make this just once?  

Ubuntu 11.04

---

### Post by androssofer on 2011-07-04
> Why must I type my keyring password 5 times every login? How do I make this just once?


i am assuming your computer logs you in automatically? 

and then prompts you for the keyring password numerous times?

if so you could either disable automatic login and have to type your password at the login screen, this should stop it for you and you only need to type it in once...

or you could look at this 

[http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/](http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/)

its a bit old, but might still work on 11.04 (havent tested it...)

---

### Post by mcduck on 2011-07-04
> **outleradam said:**
> Why must I type my keyring password 5 times every login?  How do I make this just once?  

Ubuntu 11.04

You get asked for it several times because many programs try to access the keyring at the same time, or because a single program tries to access it again and again before you get it unlocked.

Anyway, there are two easy ways to solve the problem. The first is to use normal login instead of automatic one. That way the keyring will get unlocked automatically at the time you log in (as long as the keyring password and login password are set to same).

And the other way is to set the keyring password to empty one, loosing the extra security the keyring gives but also allowing the programs to access stored keys without having to unlock the keyring.

---

### Post by outleradam on 2011-07-18
^ i don't like not being able to lock my keyring, but that sounds like the best option available now.  
 
I would rather have some level of security...  so like, anyone could use the internet, but my accounts and stuff are protected.   The keyring needs some work.
 
> **androssofer said:**
> i am assuming your computer logs you in automatically? 
 
and then prompts you for the keyring password numerous times?
 
if so you could either disable automatic login and have to type your password at the login screen, this should stop it for you and you only need to type it in once...
 
or you could look at this 
 
[http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/](http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/)
 
its a bit old, but might still work on 11.04 (havent tested it...)
 neither of those are answers.  Removing the keyring would remove stored permissions.   Disabling the auto-login would make reboot and walk away not an option.
 
It would make more sense to have a keyring daemon which would merge all keyring requests into a single password window.  It seems that this would make alot of sense as it could reuse the same code which is used for the gksudo command.

---

