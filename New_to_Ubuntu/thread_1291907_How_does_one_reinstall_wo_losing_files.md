---
title: "How does one reinstall w/o losing files?"
date: 2009-10-15
forum: New to Ubuntu
---

### Post by franklin_m on 2009-10-15
Hello,

I've got a display problem with my Dell Mini 10V running Netbook Remix 9.04 (see my other posting for details).

The only solution posted thus far is to "reinstall." However, I have email and other files that I don't want to lose.

How can I reload the netbook remix w/o losing anything? If not, then how can I minimize what I lose?

Thanks so much. Have to take the computer on the road this weekend, so I'll be attempting this in the next day or so.

Thanks,
Frank

---

### Post by nothingspecial on 2009-10-15
[[COLOR="Magenta"]Here is how[/COLOR]]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by nothingspecial on 2009-10-15
[SIZE="3"][COLOR="Red"]Woah - you don`t need to reinstall[/COLOR][/SIZE]

gah, I hate it when people suggest that when it is entirely unnecessary.

Just ```
killall maximus
```

Then go to system > preferences > startup applications and uncheck maximus.

---

### Post by 3rdalbum on 2009-10-15
You don't need to create a seperate /home partition in order to keep your data.

Back up the contents of your home directory, INCLUDING the hidden files in it as these contain your e-mail. You might need to do this from the live environment if you can't get into the installed system.

Now install Ubuntu using the Manual Partitioning option, and make sure you tell it not to format the partition. You need to set the mount point of the partition as "/".

When you boot into your installed system, it should still contain the contents of /home. Even if it hasn't retained the /home (due to bugs or user error) then you've got a backup that you can just copy back into the new system.

---

### Post by franklin_m on 2009-10-15
For Nothing special...

My problem is that when I boot into GUI, what comes up is nothing but the desktop. No menus, no nothing, so can't get to the startup stuff.

Is there another way to kill maximus?

Frank

---

### Post by achase79 on 2009-10-15
ctrl+alt+F1 then login and type killall maximus then do a ctrl+alt+F8 to return to GUI

---

### Post by franklin_m on 2009-10-15
Achase...

Thanks! Will try it tonight.

Frank

---

### Post by franklin_m on 2009-10-15
Achase,

I tried the cntrl-alt-F1 then login then killall maximus, then cntrl-alt-F8 to get back.

Didn't solve the problem. Any other ideas?

Frank

---

### Post by franklin_m on 2009-10-16
3rd Album,

I tried that, and when it booted into Linux, I had all sorts of error messages related to the display.

Any ideas?
Frank

---

### Post by marshmallow1304 on 2009-10-16
> **franklin_m said:**
> I tried the cntrl-alt-F1 then login then killall maximus, then cntrl-alt-F8 to get back.

Isn't it F7 instead of F8?

---

