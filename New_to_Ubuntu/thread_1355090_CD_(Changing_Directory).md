---
title: "CD (Changing Directory)"
date: 2009-12-14
forum: New to Ubuntu
---

### Post by bobanshirl on 2009-12-14
I have Ubuntu 9.10 installed alongside Windows.If you have a program,or software icon on your desktop or in Downloads,how does one CD to the Dsktop or Downloads folder using the apt-get in the Terminal,with a view to installing it ,or cant this be done.

---

### Post by howefield on 2009-12-14
Open a terminal from Applications > Accessories > Terminal and type

```
cd Desktop
```

or

```
cd Downloads
```

For more read,

[http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by wojox on 2009-12-14
Open your terminal and:

```
ls -F
```

Will show your directories. Now 

```
cd Desktop
```

Or 

```
cd Downloads
```

---

### Post by bacardiandwatermelon on 2009-12-14
I'm confused :-P Are you wanting to change the directory while using apt-get?

---

### Post by Flimm on 2009-12-14
> **bacardiandwatermelon said:**
> I'm confused :-P Are you wanting to change the directory while using apt-get?
Hi. I'm not sure why you would need to change directory to use apt-get. You can install programs from any directory you want. apt-get automatically downloads and installs packages in the right place for you, you don't have to think about it.

---

### Post by Chesamo on 2009-12-14
Gentle rebuke:

I think you jumped into Linux after reading a few things without fully absorbing them. Read through [_this guide_](http://www.brighthub.com/computing/linux/articles/8729.aspx) before going much further.

---

### Post by bobanshirl on 2009-12-15
Many thanks to all who answered my thread.I found that I was using lower case instead of upper.Sorry if I confused you, I wanted the cd operation in terminal to unpack a tar which I had on my desktop.I was quite chuffed to end up with the program installed,its a first for me.

---

### Post by Flimm on 2009-12-18
> **bobanshirl said:**
> I was quite chuffed to end up with the program installed,its a first for me.Thumbs up! Welcome to the adventure of learning Linux.

---

### Post by lavinog on 2009-12-18
> **bobanshirl said:**
> Many thanks to all who answered my thread.I found that I was using lower case instead of upper.Sorry if I confused you, I wanted the cd operation in terminal to unpack a tar which I had on my desktop.I was quite chuffed to end up with the program installed,its a first for me.

also take advantage of tab autocompletion.

---

### Post by lavinog on 2009-12-20
[quote=bobanshirl]Being a complete newbie,I am afraid you will have to enlighten me as to what it is and what it does.Cheers[/quote]
Tab autocompletion is used in the terminal to complete the command for you.
for example typing **cd ~/De** then pressing tab should change the line to: **/home/user/Desktop**
It can also be used to give you a list of commands:
type **apt** then press tab twice to get a list of commands that start with apt.

With auto completion, a really long command could be shortened to less than 10 keystrokes.
If you need to copy a file named **This_file_has_a_really_long_name.blah** to your desktop
all you need to do is type **cp T[tab] ~/De[tab]**

---

