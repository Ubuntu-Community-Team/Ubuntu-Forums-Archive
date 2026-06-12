---
title: "Installing Songbird"
date: 2010-04-02
forum: New to Ubuntu
---

### Post by Garthhh on 2010-04-02
just did a fresh install [8.04] on a brand new HDD & upgraded to 9.10
I need a media player that is supported in windows also to make the transistion from itunes easier.

I downloaded & extracted songbird, 
I can't seem to change the permissions, or maybe the question should be what my next step to get it up & running here.

---

### Post by Mach1723 on 2010-04-02
> **Garthhh said:**
> just did a fresh install [8.04] on a brand new HDD & upgraded to 9.10
I need a media player that is supported in windows also to make the transistion from itunes easier.

I downloaded & extracted songbird, 
I can't seem to change the permissions, or maybe the question should be what my next step to get it up & running here.
It should, work by running the songbird file(not songbird-bin) in the extracted directory.

---

### Post by Chesamo on 2010-04-02
Even easier than that would be to install Songbird from the Songbird team's PPA.

[https://launchpad.net/~songbird-daily/+archive/ppa](https://launchpad.net/~songbird-daily/+archive/ppa)

---

### Post by @rizz on 2010-04-02
Hi there u can try this....

i) Unpack (already done i guess)
```
**[B]$ sudo tar-zvxf SONGBIRDPACKAGE**[/B]

```

ii) Take ownership
```

$ **sudo chown USERNAME ~/Songbird/***
```

iii) Change Permission
```

$ [B]sudo chmod 755 -R ~/Songbird/songbird
[/B]
```

iv) Now run it
```

$ [B]./songbird
[/B]
```

---

### Post by Chesamo on 2010-04-02
You can do that graphically, as well. Extracting the archive using File Roller (the default archive manager on Ubuntu) will automatically grant you ownership.

Also, chmod has been updated... no longer must you use numeric codes. Simply ```
sudo chmod u+x songbird
``` inside the Songbird directory and the Songbird executable will run with the command rizz mentioned.

---

### Post by Garthhh on 2010-04-02
> **@rizz said:**
> Hi there u can try this....

i) Unpack (already done i guess)
```
**[B]$ sudo tar-zvxf SONGBIRDPACKAGE**[/B]

```ii) Take ownership
```

$ **sudo chown garthh ~/Songbird/***
```iii) Change Permission
```

$ [B]sudo chmod 755 -R ~/Songbird/songbird
[/B]
```iv) Now run it
```

$ [B]./songbird
[/B]
```

0 for 2 
I already extracted the file[s]
I copied & pasted the 1st,   command not found
moved on to the 2nd
bash: syntax error near unexpected token `)'
assumed it was the open bracket, removed it 
command not found?

Why doesn't this work like other apps, where I would 
extract, 
change permissions
left click
run

I don't mind doing the occasional
but being a noob
it gets confusing fast
screenshot of the contents of the songbird folder
ok that doesn't work either, not letting me browse my computer for the file

[IMG]file:///tmp/moz-screenshot.png[/IMG]
[IMG]file:///tmp/moz-screenshot-1.png[/IMG][IMG]file:///tmp/moz-screenshot-2.png[/IMG]

---

### Post by @rizz on 2010-04-02
Well

 if u have extracted the file? ....where did you extract it? in which folder
 mention the correct file path in the sudo chown command

 in graphical mode

  simply right click on the file and select properties and then go to permissions tab

 you should get the options to change the file permissions.

 also look in the folder and somewhere in there can be an executable file that has a kind icon that resembles the diamond of cards. if u find it try double clicking on it. that works too!

---

### Post by Garthhh on 2010-04-02
> **@rizz said:**
> Well

 if u have extracted the file? ....where did you extract it? in which folder
 mention the correct file path in the sudo chown command

 in graphical mode

  simply right click on the file and select properties and then go to permissions tab

 you should get the options to change the file permissions.

 also look in the folder and somewhere in there can be an executable file that has a kind icon that resembles the diamond of cards. if u find it try double clicking on it. that works too!

I get the option to change the permissions, but it doesn't take, it changes right back
I got an upper row on the edtior this time & was able to attach the screenshot

---

