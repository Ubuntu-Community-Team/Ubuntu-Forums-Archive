---
title: "Help needed with Terminal command/phrase please"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by tjsilver on 2009-11-05
Hi,

Using the 'terminal' window, I need to 'sudo' move a folder from my desktop to /var/www.

I just don't seem to be able to define the folder on my desktop as the source - whatever I think might work, I keep getting 'mv: cannot stat'

What should I be typing please?

Tim

---

### Post by yeats on 2009-11-05
when you do a

```
ls
```

is the folder you're trying to move on that list?  You can type partial filenames/commands and hit TAB to autocomplete (if there's more than one file/folder/command with the same beginning characters you have to type in enough to make it unambiguous), which will allow you to select the right one.

---

### Post by sisco311 on 2009-11-05
+1 for tab completion.

you can drag the folder in the terminal to get the full path to it.

you may also want change the DocumentRoot to point to a directory in your home:
[https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual Hosts]("https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual Hosts")

---

### Post by yeats on 2009-11-05
> you can drag the folder in the terminal to get the full path to it.

Great tip - I never knew that! :-)

---

### Post by tjsilver on 2009-11-05
Thanks for replies.

So I 'ls''d and Desktop was there, so I 'ls Desktop''d and my files/folders were listed. Does that help?

Tim

---

### Post by NoaHall on 2009-11-05
Can you post the full command that you are trying to do? It's possible there's a space in the name.

---

### Post by yeats on 2009-11-05
> **tjsilver said:**
> Thanks for replies.

So I 'ls''d and Desktop was there, so I 'ls Desktop''d and my files/folders were listed. Does that help?

Tim
Sounds like you're not in the right directory when doing the mv command...

You can change directories with cd:

```
cd *directory*
```

---

### Post by Old *ix Geek on 2009-11-05
Please tell us:

1) WHERE are you when you're attempting to do this? Type:
```
pwd
```
and post the result.

2) Post the EXACT command you're attempting to do the file moving with when you're in the directory in #1.

---

### Post by heshoots67 on 2009-11-05
You need to define a special command/ name "sudo" now you can finish it.

---

