---
title: "I cant edit my softare sources"
date: 2010-01-25
forum: New to Ubuntu
---

### Post by Dobbie03 on 2010-01-25
I have tried accessing my software sources via both the system settings and through the terminal and both times I am asked for my passwords but in the terminal I am denied and in the software sources screen nothing happens.

I tried using  "su" in terminal and entered my password but that was denied also, what do I do?

---

### Post by mikewhatever on 2010-01-25
First, check the CapsLock key. Linux is case sensitive so if you type in all capital letters, it's not going to work. If that doesn't help, resetting your password is an option.
[https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)

---

### Post by Dobbie03 on 2010-01-25
Caps Lock is not the issue, is there some way that I am not signed as root (or whatever its called?) my password works when I try other things.  I also couldnt install a .deb file before.

---

### Post by LuisGMarine on 2010-01-25
What happens when you type this command into a terminal?
```

sudo kate /etc/apt/sources.list
```

Since you said you are running Kubuntu by the thread name, kate is the KDE equivalent of gedit on the GNOME desktop.

In Ubuntu you don't sign is as the root user, instead you temporarily call on its powers to do system administrative tasks.  This help keep people from forgetting they are on the root user account and completely messing up their system.  

If indeed you type in your password and you are 100% sure that its right and it doesn't work, follow that link to reset it.

---

### Post by Dobbie03 on 2010-01-25
> **LuisGMarine said:**
> What happens when you type this command into a terminal?
```

sudo kate /etc/apt/sources.list
```



That worked perfectly.  Thank you.

---

### Post by ankspo71 on 2010-01-25
Hi,
I have noticed that 'sudo' does not accept correcting mistakes with the backspace key while entering the password. So if you have a password that is difficult to type in then I recommend using gksudo instead. It allows you to correct mistakes in passwords.

```
gksudo kate /etc/apt/sources.list
```it will also work with updating your sources list

```
gksudo apt-get update
```I think kate is your default text editor, if not, replace kate with one you have.
Hope this helps.

Edit: I'm too late. I see the problem has already been solved :-)

Edited again: Hmm. Interesting... Now that I am using Lucid testing release, I no longer have the problem that I mentioned earlier (^ up there ^). The tty login prompt and sudo now accepts using the backspace to correct mistakes in the passwords.

---

### Post by Dobbie03 on 2010-01-25
Thanks anyway :)

---

