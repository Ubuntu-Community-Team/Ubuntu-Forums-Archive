---
title: "Deleting theme"
date: 2010-04-09
forum: New to Ubuntu
---

### Post by littlboz on 2010-04-09
I downloaded a theme called SlicknesS-black by following this tutorial: [http://www.youtube.com/watch?v=gl-tmGfQrzs](http://www.youtube.com/watch?v=gl-tmGfQrzs)
I am trying to uninstall it but I can't figure out how to do it. I think I moved the file around after I typed the code in the terminal, it works, I just don't want it.

I realized the best way to install themes is to drag and drop them into the appearance preferences window. I did this with SlicknesS-blue and I can click delete and it deletes.

I use ubuntu 9.10 64-bit

---

### Post by bwhite82 on 2010-04-09
Can you outline the steps you took to install it? No offense, don't want to watch a video right now.

---

### Post by littlboz on 2010-04-09
> **Soldierboy said:**
> Can you outline the steps you took to install it? No offense, don't want to watch a video right now.

1. go to gnome-look.org
2. download SlicknesS-black
3. unzip
4. type in the terminal: sudo cp -r $HOME/Desktop/SlicknesS-black /usr/share/themes
5.Type in the terminal: sudo chmode 755 /usr/share/themes/SlicknesS-black/Slickness-black.jpg
6. Go to appearances and click on slickness black

---

### Post by littlboz on 2010-04-09
I also went into the home file and went to .themes and moved the file to the trash. It didn't do the trick. I think I need a command for the terminal.

---

### Post by littlboz on 2010-04-09
> **littlboz said:**
> I also went into the home file and went to .themes and moved the file to the trash. It didn't do the trick. I think I need a command for the terminal.


Alright, I found it but now it states "the folder contents could not be displayed. 'You do not have the permissions necessary to view the contents of "'root.'"" which is rather odd because I am using the only account ever made on my ubuntu so why would it be restricted?

whooooooppps wrong thread, sorry guys

---

