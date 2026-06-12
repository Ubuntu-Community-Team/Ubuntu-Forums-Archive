---
title: "How do I get rid of this annoying message??"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by jrozo17 on 2010-05-09
Ok, so about a couple days ago this message just started popping up everytime I log in. I can either click cancel of type in my password to make it go away, but its still annoying.](*,) 

I want to know how can I make it go away permanently? And why does it pop up in the first place? Please use "small" talk ;)

Thanks!

[IMG]http://i792.photobucket.com/albums/yy209/jrozo16/Screenshot.png

---

### Post by omatoots on 2010-05-09
The answer is in this thread: [http://ubuntuforums.org/showthread.php?t=1456691&highlight=turn+login+screen](http://ubuntuforums.org/showthread.php?t=1456691&highlight=turn+login+screen)
And I will quote the answer from wwarsin in case you're very frustrated and don't want to follow the url: click System -> Preferences -> Screensaver. Then on the Screensaver Preferences box Uncheck "Lock screen when screensaver is active"

It drove me crazy, too. Good luck

---

### Post by jrozo17 on 2010-05-09
> **omatoots said:**
> The answer is in this thread: [http://ubuntuforums.org/showthread.php?t=1456691&highlight=turn+login+screen](http://ubuntuforums.org/showthread.php?t=1456691&highlight=turn+login+screen)
And I will quote the answer from wwarsin in case you're very frustrated and don't want to follow the url: click System -> Preferences -> Screensaver. Then on the Screensaver Preferences box Uncheck "Lock screen when screensaver is active"

It drove me crazy, too. Good luck

Thats not quite what I was looking for, sorry. :( I'm talking about when I boot up my computer or ever log in, not when I come out of the screen saver. Any ideas?

---

### Post by themusicalduck on 2010-05-09
I've had this problem too since 10.04. I think it needs the password for the keyring so that it can login to my twitter accounts through gwibber :/ I'd much rather it just accessed it automatically though.

---

### Post by buntudawg on 2010-05-09
Don't know if this thread is of any use to you?

[http://ubuntuforums.org/showthread.php?t=1317096&highlight=unlock+login+keyring+message](http://ubuntuforums.org/showthread.php?t=1317096&highlight=unlock+login+keyring+message)

---

### Post by amauk on 2010-05-09
Applications > Accessories > Passwords & encryption keys

"Passwords" tab
expand list

Right click "unlock password for default keyring"
Select "Properties"

"Key" tab
blank out "password" entry

Close
(probably have to log out & back in again, to take effect)

Your keyring will now unlock automatically on login

---

### Post by _0R10N on 2010-05-09
> **jrozo17 said:**
> Ok, so about a couple days ago this message just started popping up everytime I log in. I can either click cancel of type in my password to make it go away, but its still annoying.](*,) 

I want to know how can I make it go away permanently? And why does it pop up in the first place? Please use "small" talk ;)

Thanks!

[IMG]http://i792.photobucket.com/albums/yy209/jrozo16/Screenshot.png

Let me guess, this message started to show up after you changed the password for your user. If that's your case, then you could take a look to the Encryption and Keyrings window under you Preferences menu. You can also run seahorse.
I found this link 
[http://pherricoxide.wordpress.com/2009/02/22/ubuntu-keyring-password-change/](http://pherricoxide.wordpress.com/2009/02/22/ubuntu-keyring-password-change/)

I didn't tried it, so if you want to try it yourself, backup your files first.

---

