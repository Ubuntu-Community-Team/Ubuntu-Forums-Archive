---
title: "custom application launcher"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by cosine352 on 2008-12-03
Hi guys,

I usually like keep my desktop clean. So one in a while I run a command

> mv Desktop/* DesktopC

So this moves all files from Desktop to another folder DesktopC. I was trying to do a "custom application launcher" for this command. So right clicked on the panel and chose add a "custom application launcher" and put the command 
> mv Desktop/* DesktopC

But it is not working. Does anyone has any idea /
Thanks

---

### Post by cosine352 on 2008-12-03
I have solved it. I just made a script for the command and added thet to the launcher.

---

### Post by bobnutfield on 2008-12-03
I believe if you include that command in a short script, and make it executable, it will work.  For example,

> bin/bash
       mv Desktop/* DesktopC
       end

I am not a scripter, but I have done simple things like this in past and it works for me.

---

### Post by bobnutfield on 2008-12-03
Sorry for the double post.  Browser locked up.

---

### Post by muadnu on 2008-12-03
You need to put this in a script. On a terminal type 'nano cleandesktop.sh' and then paste
```
#!/bin/bash
mv Desktop/* DesktopC 
```
in it. Save, exit, and then do
```
chmod +x cleandesktop.sh
```

Now on your custom application launcher put the command
```
/home/yourusername/cleandesktop.sh
```
(here I'm assuming you created the script in your home folder, change this accordingly otherwise).

I think that should do it...

---

