---
title: "Different user accounts with different languages?"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by kramer65 on 2009-05-11
Hello,

Since we live with some different nationalities in a house I want to setup a pc with different user accounts in which one should use English, one Dutch, one Spanish, etc.

Is this possible?

---

### Post by Peter09 on 2009-05-11
Does 
System->Administration->Language Support

help you?

---

### Post by kramer65 on 2009-05-11
I'll give it a go.. (will be back in a couple minutes.. :-)  )

---

### Post by kramer65 on 2009-05-11
Unfortunately that didn't work. It says in the language support window that you can change the language for all _new_ users and for the login screen. Unfortunately that setting changes the language of also the currently existing users.

Do you know of any other way of changing language settings of different accounts? Or is it just possible to set the language of the whole system?

---

### Post by Peter09 on 2009-05-11
Try Options and language at the users login screen.

---

### Post by kramer65 on 2009-05-11
That comes in the direction of what I want. It is now possible to run a seesion in one language and another in a different language. However, I now have to change the language manually every time I get to the login screen and confirm my choice for "this sesion" or "for ever" (had some different wording but this is what it kinda said). This is not very user friendly because if people set it to "for ever" it is not very friendly for the other people..

Ideally I would like to have the language adjusted to the custom user account language settings.

Any other ideas?

---

### Post by connorh123 on 2009-05-11
Is there somewhere you can click apply changes when you do that?

---

### Post by kramer65 on 2009-05-11
Yes, but it then changes language for all accounts..

---

### Post by kramer65 on 2009-05-11
Hello,

I've given up on accomplishing what I initially wanted and listed it as an [idea at the brainstorm]("http://brainstorm.ubuntu.com/idea/19765/").

I now have a new problem though. When I type my username and password I get an error message saying that I don't own some kind of file. Have a look at the attachment.

How can I get rid of this again?

---

### Post by Peter09 on 2009-05-11
go to your home directory and do

> sudo chown *owner* .dmrc

where owner is your username

and then

```
chmod 644 .dmrc
```

---

### Post by kramer65 on 2009-05-11
Do you mean I have to go to /home/ or to /home/myusername/  ?

---

### Post by Peter09 on 2009-05-11
goto /home/<your user name>

---

### Post by kramer65 on 2009-05-12
Alright I did that but I still get the same error when logging in..

Quite annoying since I wanted to make things easier, but it just got more annoying. Could anybody help me with getting rid of this error?

---

### Post by Miljet on 2009-05-12
If it helps, this is what mine looks like.

```
jack@jack-laptop:~$ cat .dmrc


[Desktop]
Session=default
jack@jack-laptop:~$ ls -l .d*
-rw------- 1 jack jack   28 2009-05-12 14:07 .dmrc
```

---

### Post by Artemis3 on 2009-05-12
Check permissions of the folder for your user, do: ls -l /home it should be drwxr-xr-x (755) and the .dmrc file itself (inside that folder) should be -rw-r--r-- (644) or -rw------- (600) as shown above.

You can change it with chmod 755 youruserfolder and chmod 644 .dmrc

---

### Post by connorh123 on 2009-05-12
In Language Support, you can keep the same language. It gives you that option.

---

