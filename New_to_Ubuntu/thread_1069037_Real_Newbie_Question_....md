---
title: "Real Newbie Question ..."
date: 2009-02-13
forum: New to Ubuntu
---

### Post by jeager on 2009-02-13
Just downloaded ubuntu for the first time. It loaded, did its thing and on the boot-up asked for the user name and password.

I'm afraid I don't kown it.

Any way around that, or where during the download might I have put both a user name and password in when it was requested?

Thanks for any info,
jeager:confused:

---

### Post by avtolle on 2009-02-13
During the installation, you were asked to enter your name; by default, the user name is your first name, all in lower case. At that time, you were also asked for a password, as I recall the process, and for validation of the password by entering it a second time. I take it you don't recall doing this. Wondering, if one enters ones name when requested and then proceeds, whether using the first name in lower case and then nothing for the password then proceeding will work? Obviously, I don't know.

---

### Post by jerome1232 on 2009-02-13
During the install process you were asked to chose a user name and password. There is a way to reset the password though.

When you see the grub screen, you should get a list of kernels to choose from, one will say "recovery" in the name, choose that one. If you don't ever see this grub menu I'm talking about mash the esc key while Ubuntu is first starting up to get to this menu.

You should wind up at a blue screen, select the option that says drop to root prompt, eventually you should land at a bash prompt as the root user.

If you don't remember what you picked for your username type this it'll tell you.

```
ls /home
```

To reset your users password to a new one, replace usernamehere with your real user name, it should prompt you to enter a new password, just type it in and hit enter, the characters will not be printed back to the screen this is normal just keep typing the password and hit enter.

```
passwd *usernamehere*
```

When your done reseting the password reboot the computer

```
reboot
```

---

### Post by ugm6hr on 2009-02-13
How are you booting into Ubuntu?

Using the LiveCD?  If yes - then you have a coirrupted download / CD burn.  The LiveCD does not require a password.

If you installed it already - you will have been through a detailed process requiring partitioning etc, and you can't have missed the "enter your username and password" section.  It won't have let you continue unless you did.  If this is a fresh install - just reinstall with your chosen new username / password.

---

### Post by cariboo on 2009-02-13
The OP didn't state what version he downloaded, but the Jaunty daily builds ask for a password, but there is also a count down timer, that when it reaches zero it just continues on.

Jim

---

### Post by kdreimiller on 2009-02-13
the way to change your password seems dangerously simple, from a security standpoint.  or am i missing something?  i didnt know you could change/reset your password like that.

---

