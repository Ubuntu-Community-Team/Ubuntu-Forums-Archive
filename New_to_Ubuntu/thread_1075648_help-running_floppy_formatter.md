---
title: "help-running floppy formatter"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by hosmer on 2009-02-20
When I try to run floppy formatter the following message appears.

you do not have proper permissions to write to /dev/floppy/0 or
/dev/fd0----contact your system administrator about getting
permissions.

If I open the terminal and type sudo gfloppy  the formatter works.

Can some one tell me how to set things up so i have permanent permission to run the floppy formatter?

running UBUNTU 8.10

I'm new to all of this Thanks

---

### Post by Tek-E on 2009-02-20
Try using the chown command to change your permissions on the device.

---

### Post by hosmer on 2009-02-20
I'm sorry, you will have to give me step by step on this

Thanks hosmer

---

### Post by Tek-E on 2009-02-20
lol. no prob on which part? finding the terminal or the using chown to change file permissions?

EDIT: Just realized you were already in the terminal my bad!

---

### Post by Tek-E on 2009-02-20
Here is the syntax of the command
chown Owner [ :Group ] { File ... | Directory ... }

---

### Post by Tek-E on 2009-02-20
So you could do
```

chown [yourusername] /dev/fd0

```
If that doesnt do it for you. please let me know.
:)

So say your username is hosmer
```

chown hosmer /dev/fd0

```

---

### Post by hosmer on 2009-02-20
Thanks, I'll give it a go, and get back to you!

---

### Post by hosmer on 2009-02-20
Nope--didn't work

This is the message i get

chown:changing ownership of /dev/fd0: operation not permitted

hosmer

---

### Post by Tek-E on 2009-02-20
Damn!  Ill play with it for a little bit and Ill get back to you unless someone else does first.

---

### Post by Tek-E on 2009-02-20
What about
```

chmod 777 /dev/fd0

```
Now Im pretty sure your floppy drive is /dev/fd0 but I have been wrong before.  It could be /media/floppy.
Try issuing the mount command and see which one it is.

---

### Post by Tek-E on 2009-02-20
Wait... I think I know why chown didnt work the first time.
try....
```

sudo chown yourusernamehere /dev/fd0

```

Let me know.

---

### Post by Rhubarb on 2009-02-20
An easier way for getting this to work is to just run gfloppy with administrator access.

This can be done 2 ways, the easiest way would be to change the menu entry for gfloppy:-

System --> Preferences --> Main Menu
Then in that menu editor, go to Accessories, and click on "Floppy Formatter".
You can put a check in the box next to it if you want it to appear in your Applications --> Accessories menu.
Now Click on the Properties button, and change the command from:
**gfloppy**
to:
**gksu gfloppy**
Then press Close, and run the gfloppy application from the Applications --> Accessories menu.

The other method would be to allow normal non-root users to be able to run gfloppy as root.
I haven't done this myself, but if you run **visudo** it lets you make changes to your /etc/sudoers file, which lets you run apps as root with non-root users.

And indeed yes, there's a chance that Tek-E could be right, though permissions is usually only a problem when media is formatted with linux file systems.  If it's fat 16 / fat 32 there should be no permissions problems as those partition types don't support permissions.

Hope this helps.
-Rhubarb

---

### Post by hosmer on 2009-02-20
Problem solved--

Tried sudo chown [my user name] /dev/fd0
it asked for password,when i tried to type it in
it wouldn't let me

so i used system-->preferences-->Main menu etc from Rhubarb

THANKS TO ALL
you guys are great

---

### Post by Tek-E on 2009-02-20
Glad it worked out for you.
But you said it wouldnt let you type in your password.
When you type in your password using sudo.  It doesnt normally echo the characters for your password that your typing back to you.

---

