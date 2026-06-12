---
title: "I messed up visudo, how do I restore it?"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by nayeret43 on 2009-02-18
Here is what I did:

I typed in 
```
 sudo visudo
```

Then at the end of line 8 I think, I added:
```
 ,insults
```

Because I read somewhere that you can have your Terminal return insults if you type in the wrong sudo password if you type that.

Now, every time I try to use the *sudo visudo* command, the Terminal returns this:

```

>>> sudoers file: syntax error, line 8 <<<
sudo: parse error in /etc/sudoers near line 8

```

Or any other time I try to use the *sudo* command, it is not enabled, in other words, I am locked out of my own system as root.

What should I do?

Thanks!

---

### Post by albandy on 2009-02-18
Load the recovery mode in grub and when loaded select root
a terminal will apear
type nano /etc/sudoers
delete what you changed and save the changes
exit nano
type exit in the terminal and select resume in the menu.

---

### Post by Cypher on 2009-02-18
Edit the file without going through visudo
```

sudo vi /etc/sudoers

```
Going through visudo ensures that your file is intact, but if you put bad info in there, it can cause you problems like you have right now..

---

### Post by nayeret43 on 2009-02-18
**Cypher**: I am not able to use the *sudo* command, my system will not let me use it, I tried doing what you said, and again the Terminal returned this:
```

>>> sudoers file: syntax error, line 8 <<<
sudo: parse error in /etc/sudoers near line 8

```

---

### Post by nayeret43 on 2009-02-18
> **albandy said:**
> Load the recovery mode in grub and when loaded select root
a terminal will apear
type nano /etc/sudoers
delete what you changed and save the changes
exit nano
type exit in the terminal and select resume in the menu.

That did it!! Thanks!!!

---

### Post by heavylifting on 2010-07-11
Thanks for this, I got stuck at the beginning cause I am running Ubuntu 10.04 and I was pressing ESC instead of SHIFT for Grub2, since Grub2 is default with 10.04.

---

