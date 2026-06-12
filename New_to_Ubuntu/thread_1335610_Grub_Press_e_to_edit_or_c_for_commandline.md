---
title: "Grub Press e to edit or c for commandline"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by Goldline on 2009-11-23
Can i avoid people from pressing e or c to edit grub.
I already have removed vulnerable entries such as 
memtest and recovery mode which allows users to drop
to root without password.

---

### Post by ranch hand on 2009-11-23
I have not even thought about this problem.  You could try uncommenting the following line in /etc/default/grub;
```

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

```
to read;
```

# Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL=console

```
and run;
```

sudo update grub

```
And then see if it did what you need it to do.

---

### Post by Goldline on 2009-11-23
Does this also work with grub version 1 haven't upgraded yet to grub 2.

---

### Post by ranch hand on 2009-11-23
Ah, that would be a problem in one way.  In another it is not a problem.

I believe if you download "startupmanager" you can protect your menu with a pasword.  SUM is not updated t owork with grub2 yet.

---

### Post by Goldline on 2009-11-24
Unfortunately, the password-setting can only be used with grub 2.
Ive read on the forums which problems grub 2 can cause so i rather 
don't upgrade to grub 2.

---

### Post by ranch hand on 2009-11-24
Oh.  I haven't used SUM for quite a while.  I knew it was being updated.

Frankly, I like grub2.

Take a look at the link in my sig.  The first 3 links in it are probably the best in depth info that you can get.

---

### Post by gmjs on 2009-11-24
The following line in the top section of menu.lst (before the list of menu entries) protects the GRUB menu just as you want to:

```
**password** your-password-here
```

Alternatively, you can use MD5 encryption to specify your password:

```
**password --md5** your-encrypted-password-here
```

Hope this helps,

Graham

---

