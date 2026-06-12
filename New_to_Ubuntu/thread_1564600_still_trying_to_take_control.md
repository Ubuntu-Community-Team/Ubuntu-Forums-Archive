---
title: "still trying to take control"
date: 2010-08-30
forum: New to Ubuntu
---

### Post by hutchman on 2010-08-30
really new user, who can only log in with no permissions.  I goggled commands & found this.  "  [SIZE=2][FONT=&quot]( tar -c /dir/to/copy ) | ssh -C user@remote 'cd /where/to/ && tar -x -p'" [SIZE=1]its description says[/SIZE]  "[/FONT][/SIZE]  [FONT=&quot][SIZE=2]Copy (with permissions) copy/ dir to remote:/where/to/ dir"  my question is, will this give me the permissions I need to do stuff if copied to the right place?:confused:[/SIZE]
[/FONT]

---

### Post by pricetech on 2010-08-30
Uh, no.

How did you end up with no permissions ??  Have you tried using sudo ??  If you installed Ubuntu yourself, then just use the credentials you set up with when sudo asks for your password.

---

### Post by hutchman on 2010-08-30
I guess I wound up like this because I not only forgot my password but also the keyring password. I have tried resetting it without much luck, & I would reinstall o/s but apparently an ISO is not the same as a live cd ? & I dont know what sudo is ? I just went and read about sudo & it appears to be over my head. When I said I'm really new, I meant to say really, really new !

---

### Post by v1ad on 2010-08-30
well the goal of the password is not to forget the password, so your out of luck.... --reinstall!!!!! in console what sudo does is runs the command under root privileges. but if you forgot the password your still screwed.

usage

sudo apt-get install program_name

---

### Post by Ozymandias_117 on 2010-08-30
> **hutchman said:**
> I guess I wound up like this because I not only forgot my password but also the keyring password. I have tried resetting it without much luck, & I would reinstall o/s but apparently an ISO is not the same as a live cd ? & I dont know what sudo is ? I just went and read about sudo & it appears to be over my head. When I said I'm really new, I meant to say really, really new !

Here is a way to reset your password.

At the GRUB menu (When you first turn on your computer, and it has several options of Linux) select the one closest to the top that says "Recovery Mode" in it. When it pulls up the box with the blue background, select "Drop to Root Shell". You will then need to change your password using ```
passwd *username*
```


And an ISO is an image of a disk, once you burn it, it will be a LiveCD.

---

### Post by hutchman on 2010-08-30
Thanx, Okay, made a dropbox, not sure what it is. I guess I should tell you I'm not on the pc with ubuntu cause I cant seem to get online with it.

---

### Post by Ozymandias_117 on 2010-08-30
> **hutchman said:**
> Thanx, Okay, made a dropbox, not sure what it is. I guess I should tell you I'm not on the pc with ubuntu cause I cant seem to get online with it.

Dropbox synchronizes files between a folder on your computers and their server. It's for backups and being able to access things elsewhere.

---

### Post by v1ad on 2010-08-30
hmmm i should try that, if it is that easy i will be suprised.

---

