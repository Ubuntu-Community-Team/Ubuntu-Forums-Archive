---
title: "fireFox problem"
date: 2010-04-01
forum: New to Ubuntu
---

### Post by frank cox on 2010-04-01
I hate to make another post but I thought the problem was solved.

I am confused as how to get the permissions correct in Firefox. The only way I can get it to browse and use the bookmarks is to start firefox with sudo, I can't even create new ones.
I tried deleting and reinstalling the program so I am concerned I have managed to lock myself out of installing any programs.

Your assistance would be appreciated.

---

### Post by wojox on 2010-04-01
Here you go [Firefox optimization and troubleshooting thread]("http://lovinglinux.megabyet.net/?page_id=220#Firefox-doesn%27t-start-through-regular-command/menu-but-starts-using-%22sudo-firefox%22--2")

---

### Post by frank cox on 2010-04-02
> **wojox said:**
> Here you go [Firefox optimization and troubleshooting thread]("http://lovinglinux.megabyet.net/?page_id=220#Firefox-doesn%27t-start-through-regular-command/menu-but-starts-using-%22sudo-firefox%22--2")

Thanks but I had already  tried that. I tried again to change the permissions with the command given. I changed $user to my user and it seemed to accept the command.  I am out of options . The one thing I can't seem to get is the permissions. I will have to reformat and that means talking my machine into town to accesses a hi speed line and all the time.
I am about to decide this system is smarter than me and the gui for the permissions seems absolutely worthless, I wonder why its there. Maybe Ubuntu is not for everyone.

---

### Post by lovinglinux on 2010-04-02
> **frank cox said:**
> Thanks but I had already  tried that. I tried again to change the permissions with the command given. I changed $user to my user and it seemed to accept the command.  I am out of options . The one thing I can't seem to get is the permissions. I will have to reformat and that means talking my machine into town to accesses a hi speed line and all the time.
I am about to decide this system is smarter than me and the gui for the permissions seems absolutely worthless, I wonder why its there. Maybe Ubuntu is not for everyone.

The command is...

```
sudo chown -R $USER:$USER ~/.mozilla
```

Don't replace anything. Just copy and paste the command above. The value **$USER** is automatically replaced using the environmental variables. If you want to replace it manually, then you must replace the entire variable, including the $ symbol. For example, for  me it would be...

```
sudo chown -R lovinglinux:lovinglinux ~/.mozilla
```

---

### Post by @rizz on 2010-04-02
hi frank cox,

  I am sorry that you feel this way about ubuntu( though i beg to differ!). Still i can understand where you are coming from, not getting the browser to work can be frustrating!!!

So you say that you have tried the chown command......well whats the result?

Can you tell us if the ownership change from root to user? or does it remain the same.....

---

### Post by frank cox on 2010-04-07
> **lovinglinux said:**
> The command is...

```
sudo chown -R $USER:$USER ~/.mozilla
```Don't replace anything. Just copy and paste the command above. The value **$USER** is automatically replaced using the environmental variables. If you want to replace it manually, then you must replace the entire variable, including the $ symbol. For example, for  me it would be...

```
sudo chown -R lovinglinux:lovinglinux ~/.mozilla
```

Thank you ! That did it!

---

### Post by mikewhatever on 2010-04-08
> **frank cox said:**
> Thank you ! That did it!

I think it's worth mentioning that the reason you've had this problem is because you had run *sudo firefox*. Hope you won't step on the same broom again.:)

---

