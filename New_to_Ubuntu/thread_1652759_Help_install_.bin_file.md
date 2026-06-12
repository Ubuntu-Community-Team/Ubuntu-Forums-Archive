---
title: "Help install .bin file"
date: 2010-12-25
forum: New to Ubuntu
---

### Post by hunter99507 on 2010-12-25
I just downloaded braid from the humble bundle promo. I am new to ubuntu and i would like to know how to install it.  The file name is "braid-linux-build2.run.bin" Thanks

---

### Post by hunter99507 on 2010-12-25
So a quick google search told me how to install it. It works fine. I guess my question now is can someone tell me exactly what i did so i can understand how i installed it?  This is what i did:
```
cd
chmod +x braid-linux-build2.run.bin
./braid-linux-build2.run.bin
```Reference > [http://www.reddit.com/r/linux_gaming/comments/epq1e/how_to_install_braid_cortex_command_and/](http://www.reddit.com/r/linux_gaming/comments/epq1e/how_to_install_braid_cortex_command_and/)

So i guess what i dont understand is what does chmod +x do? Also what does ./ do?  Thanks

---

### Post by I_can_see_the_light on 2010-12-25
chmod +x means that you're changing the permission for execution of the file. To disallow execution you change the + to a -

./ just means that you want to execute the file :)

---

### Post by I_can_see_the_light on 2010-12-25
chmod +x means that you're changing the permission for execution of the file. To disallow execution you change the + to a -

./ just means that you want to execute the file :)

---

### Post by hunter99507 on 2010-12-25
> ./ just means that you want to execute the file :smile:

So is ./ means that u execute the file or is it "."? Does "." mean that u install it and the "/" means the directory?

So for example ./install.sh

"." means install,"/" means the directory,and "install.sh" means the file?

Am i understanding this correctly?

---

### Post by lisati on 2010-12-25
> **hunter99507 said:**
> So is ./ means that u execute the file or is it "."? Does "." mean that u install it and the "/" means the directory?

So for example ./install.sh

"." means install,"/" means the directory,and "install.sh" means the file?

Am i understanding this correctly?
./ at the start of a file name tells the computer to look for the file in your current working directory. If you type in install.sh instead of ./install.sh the system will look elsewhere before running it.

---

### Post by tango_ninja on 2010-12-25
You did the terminal version of right-clicking the file > Properties > Permissions > Allow executing of file as program.

---

### Post by 3rdalbum on 2010-12-25
The ./ means "in the current directory". Program names come first so basically you did "Run install.bin in the current directory". The program in question is an installer.

---

