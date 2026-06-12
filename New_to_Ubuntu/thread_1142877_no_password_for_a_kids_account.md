---
title: "no password for a kids account"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by nutpants on 2009-04-29
I need to make an unprivileged user account for a 4 year old child..
i need to make it with out a password..
she wants her own profile..

how do i do this..ubuntu 9.04

thanks.
nuts

---

### Post by LowSky on 2009-04-29
go to system>admin> user and group

create new user, and dont make a password

---

### Post by bapoumba on 2009-04-29
You would be surprised how kids can like and use passwords, even pre-school kids ;)

Edit: LowSky, as far as I know, you cannot make an account without a password.

---

### Post by unutbu on 2009-04-29
Maybe the 4-year old would consider having a password cool. However, if not, perhaps AutoLogin would work: [https://help.ubuntu.com/community/AutoLogin](https://help.ubuntu.com/community/AutoLogin)

---

### Post by bapoumba on 2009-04-29
> **unutbu said:**
> Maybe the 4-year old would consider having a password cool. However, if not, perhaps AutoLogin would work: [https://help.ubuntu.com/community/AutoLogin](https://help.ubuntu.com/community/AutoLogin)
Ah, yes thanks. Forgot about it.

My kids had passwords as soon as they could recognize the letters and type their own first name (around 3).

---

### Post by kanikilu on 2009-04-29
[http://onlyubuntu.blogspot.com/2008/06/howto-enable-empty-password-login-in.html](http://onlyubuntu.blogspot.com/2008/06/howto-enable-empty-password-login-in.html)

It's not as easy as it could be, but some (including myself) would argue that making it harder is a good thing since it's bad practice to have password-less accounts...

// Edit - Another option along the lines of auto-login, would be to have a timed login - set it to something reasonable (say 5-10 seconds) which will not delay the login for very long, but will give you enough time to login with another user account so you don't all end up using the same account.

---

### Post by Didius Falco on 2009-04-29
The easiest way is to just set up an account with a password for her, and set it up to log in automatically.

Go to the Fast User Switcher and set up an unprivileged User account for her by Right-clicking and choosing "Edit Users and Groups". You'll need to add a password, but don't worry. You'll set it up so she logs in automatically in a second.

After you've created the account, go back to the Fast User Switcher and Right-click. This time choose "Set Up Login Screen". Go to the "Security" tab and tick the "Enable Automatic Login" radio button. This will release the drop-down box just below it. Choose her username and and then close it.

Another optional thing you can do is use one of the Face Browser  themes under the "Local" tab, so she can just pick her name from the drop-down list.

I hope this helps, and I look forward to voting for her one day! :)

---

### Post by LowSky on 2009-04-29
> **bapoumba said:**
> Edit: LowSky, as far as I know, you cannot make an account without a password.

You know what your right, I just tried it. Auto login will work, you can even set it up to auto login on a timer, in the event the kids log out...

---

### Post by ibuclaw on 2009-04-29
> **kanikilu said:**
> [http://onlyubuntu.blogspot.com/2008/06/howto-enable-empty-password-login-in.html](http://onlyubuntu.blogspot.com/2008/06/howto-enable-empty-password-login-in.html)

It's not as easy as it could be, but some (including myself) would argue that making it harder is a good thing since it's bad practice to have password-less accounts...

// Edit - Another option along the lines of auto-login, would be to have a timed login - set it to something reasonable (say 5-10 seconds) which will not delay the login for very long, but will give you enough time to login with another user account so you don't all end up using the same account.

Wouldn't that mean that **all** users can login without a password?

Wouldn't that be a security risk?

Regards
Iain

---

### Post by bapoumba on 2009-04-29
> **kanikilu said:**
> 
It's not as easy as it could be, but some (including myself) would argue that making it harder is a good thing since it's bad practice to have password-less accounts...

I agree with that.
It's been a game for them too, pick hero names for passwords, account pic id, wallpaper etc. ;)

---

### Post by Didius Falco on 2009-04-29
> **tinivole said:**
> Wouldn't that mean that **all** users can login without a password?

Wouldn't that be a security risk?

Regards
Iain

Looking at the setup screen for that, it's on a per-user basis, so it would only work on the accounts that someone with Sudo privileges enabled.

But I did get a chuckle out of the mental image of a 4 year old in a trench coat and a fedora sneaking up to the pc...

---

### Post by sisco311 on 2009-04-29
> **bapoumba said:**
> 
Edit: LowSky, as far as I know, you cannot make an account without a password.

Of course you can, it's linux! :)
(but they still have to hit Enter for the empty password.)

It's a little tricky:
[thread=513820]HowTo: Create a Passwordless / Guest Login (Simple Method)[/thread]


EDIT:
And, I agree with you, it's never to soon to teach a child good security habits.

---

### Post by Spiritous on 2009-04-29
AutoLogin...?

---

### Post by bapoumba on 2009-04-29
> **sisco311 said:**
> Of course you can, it's linux! :)
(but they still have to hit Enter for the empty password.)

It's a little tricky:
[thread=513820]HowTo: Create a Passwordless / Guest Login (Simple Method)[/thread]


EDIT:
And, I agree with you, it's never to soon to teach a child good security habits.

Okay, thanks :)
(You still have to create the account with a password. Under Linux, you cannot create one without the pwd as far as I know. The need for a password can be removed afterward. I should have been more clear. Instead of "make an account", I should have written "create an account". I'm so much not thinking that it is right to have a user without an account that I forgot autologin..).

---

### Post by sisco311 on 2009-04-29
> **bapoumba said:**
> Okay, thanks :)
(You still have to create the account with a password. Under Linux, you cannot create one without the pwd as far as I know. The need for a password can be removed afterward. I should have been more clear. Instead of "make an account", I should have written "create an account". I'm so much not thinking that it is right to have a user without an account that I forgot autologin..).

Well, you can create a disabled account with useradd, but this is another story...

One can argue that the locked password is still a password with a value which matches no possible encrypted value. :confused:

:)

---

### Post by bapoumba on 2009-04-29
Eheh :)
Cheers !

---

