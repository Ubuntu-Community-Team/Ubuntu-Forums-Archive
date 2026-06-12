---
title: "Login password/Login keyring problem"
date: 2011-02-15
forum: New to Ubuntu
---

### Post by Primus1 on 2011-02-15
Hi, the last two days when I start my computer I login with my computer password but then a box comes up saying "the password you use to login to your computer no longer matches that of your login keyring"

With luck I drag a old password out of my head and must hit on the right one because it accepts it and my computer is all logged in and fine.

Anyone know what's happened? I haven't been using any program which requires this "keyring" thing, or done anything different with my computer, puzzling.

---

### Post by maryeliezka on 2011-02-15
It happened to my Ubuntu Maverick too. I'm so confused so i change back the password to the old one. Is there any one who can help us?

---

### Post by Primus1 on 2011-02-15
Hi, I'm using Ubuntu Lucid.

---

### Post by Primus1 on 2011-02-17
Only me and [maryeliezka]("http://ubuntuforums.org/member.php?u=1218952") with this problem?

---

### Post by mcduck on 2011-02-17
If you change your login password, the keyring password isn't changed automatically, you ahve to do that yourself (if you want to, of curse. Some people prefer having separate password for login and keyring).

Anyway, it's easy to do, just go to System/Preferences/Passwords and Encryption Keys, right-click on the "Passwords:login"-keyring and select "Change Password". Type in the old password and set the new one to same as your login password.

(If you are using 10.04 or older Ubuntu verson the same tool can be found in Applications/Accessories/Passwords and Encryption Keys)

---

### Post by Primus1 on 2011-02-17
Hi, I haven't changed my login password, this keyring thing just popped up out of the blue.

---

### Post by mcduck on 2011-02-17
> **Primus1 said:**
> Hi, I haven't changed my login password, this keyring thing just popped up out of the blue.

Then have you perhaps set your system to use automatic login? Besides, you mentioned that you used *old password* to unlock it, which pretty much sounds like you have at some point changed the password ;)

The keyring will be unlocked automatically if you use normal login, and the keyring password is the same as login password.

If you use automatic login, or have different password for login & keyring, you need to give keyring password to unlock it when some application tries to access the keyring.

(If you want to use automatic login without having to enter the keyring password, you can set the keyring to store the passwords in unencrypted format, without a password. To do that just follow the instructions for changing the keyring password, but leave the fields for new password empty. You'll get a warning about using unsafe storage, but it really makes no difference if you are already using automatic login anyway.)

---

### Post by llamabr on 2011-02-17
[http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/](http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/)

maybe this will help you

---

### Post by mcduck on 2011-02-18
> **llamabr said:**
> [http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/](http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/)

maybe this will help you

It won't, unless he has actually removed that package himself. It's been included by default for a long time now.

---

### Post by Primus1 on 2011-02-18
Thanks for the replys. When it asked for a password I though that at some point I must have know this keyring password, then I thought the only thing I could do is to try one of the passwords in my memory - we all carry lots for different things don't we? old email pass and others we hardly ever use. Luckily I soon tried one that worked, massive stroke of luck.

The only thing I changed recently is installing BBC iPlayer. Would that cause such a problem? It loads at  start, perhaps it is asking access to this keyring thing.

No I have not removed the package mentioned.

---

### Post by mcduck on 2011-02-18
More likely the keyring is accessed by Network Manager. Although quite many of Ubuntu's default apps use the keyring; Ubuntu One, Empathy, Evolution, all the remote desktop tools, Nautilus if you have any network shares, Gibber, and the list goes on. Pretty much every Gnome application that uses passwords of some kind.

Anyway, whatever might have caused your problem, if your keyring password isn't the same as your login password is, you should follow my instruction and change it so both passwords are the same. After that the keyring should unlock automatically when you log in to your desktop.

---

### Post by Primus1 on 2011-02-18
Ok, I'll do that, thanks :)

---

### Post by Primus1 on 2011-02-20
Thanks [mcduck]("http://ubuntuforums.org/member.php?u=17309") both passes the same now and the problem solved.

---

### Post by pjorge1036 on 2011-02-21
> **mcduck said:**
> If you change your login password, the keyring password isn't changed automatically, you ahve to do that yourself (if you want to, of curse. Some people prefer having separate password for login and keyring).

Anyway, it's easy to do, just go to System/Preferences/Passwords and Encryption Keys, right-click on the "Passwords:login"-keyring and select "Change Password". Type in the old password and set the new one to same as your login password.

(If you are using 10.04 or older Ubuntu verson the same tool can be found in Applications/Accessories/Passwords and Encryption Keys)
Thanks for this info I was trying to figure out how to do this but being new to Ubuntu and Linux I was Lost... now I feel silly since it was so simple.:D

---

