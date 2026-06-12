---
title: "Auteria"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by Leo Dragonheart on 2009-01-23
I just downloaded this game and it says I need these two Libraries:

- SDL version 1.2 or newer
- Mesa3d 3.4 or newer

Can someone please tell me where I can get them, and also tell me how I can start thee game... Thanx.

I am still really new to this so please tell me step by steep what to do...

---

### Post by Kobalt on 2009-01-23
Try installing the following packages from the Synaptic package manager : 
libsdl1.2-dev
libgl1-mesa-dev

---

### Post by Leo Dragonheart on 2009-01-23
I tried what you said but I got this error. What should I do? I haven't installed them yet...

---

### Post by Leo Dragonheart on 2009-01-23
Could someone please tell me how I can launch this game I have downloaded now? Thanx...

---

### Post by Leo Dragonheart on 2009-01-23
I am sorry for spamming... I know I need to be more specific...This is what I have downloaded... and the second one is like greek to me...

---

### Post by snova on 2009-01-23
Install these packages: libsdl-image1.2 libsdl-sound1.2 libvorbis0a libtheora0

That's hopefully all you need. Then just click on it (the **auteria** file), it should run.

If it doesn't, then make sure both the auteria and auteria.bin files are executable (right click on them, Properties, Permissions, I think).

If it *still* doesn't, then show us the output of:

```
cd Downloads/auteria
ldd auteria.bin
```

---

### Post by Leo Dragonheart on 2009-01-23
all the files you said are installed... I checked to see if they were executalble and the results are the first screenshot... The output of the last thing you said to do is the second screenshot...

---

### Post by taurus on 2009-01-23
Just run the darn thing and see what happens.

```
./auteria
```

---

### Post by Leo Dragonheart on 2009-01-23
Please tell me how to run it...

---

### Post by taurus on 2009-01-23
> **Leo Dragonheart said:**
> Please tell me how to run it...

Don't you even see the command to run it in my previous post?

```
cd ~/Desktops/auteria
./auteria
```

---

### Post by Leo Dragonheart on 2009-01-23
Yes I saw the command... the problem is I don't know where to put it.... I am sorry.If I am suppose to put it in the terminal it says no such file or directory...

---

### Post by taurus on 2009-01-23
Look at my post #10.  You type those lines, one at a time, at a terminal.

---

### Post by Leo Dragonheart on 2009-01-23
Thank you... the game is running... I now know how to run a program like that thanx... I had to change the "Desktop" to "Downloads" because that is where my files download to but yes the game is running now. Thank you very much for your help...and I am sorry for any stress I may have caused. I just didn't know how to launch the program... all is good Thanx again.

---

### Post by Leo Dragonheart on 2009-01-23
Is there a way I can set it up to launch without using the terminal?

---

### Post by snova on 2009-01-23
> **Leo Dragonheart said:**
> Is there a way I can set it up to launch without using the terminal?

Just click on it.

---

### Post by taurus on 2009-01-23
Place a cursor in the upper panel and click the right button.  Then, Add to Panel... -> Custom Application Launcher -> Add.  In the **Name:**  you can put down whatever you want.  And for the **Command:** field, you need to include the whole path to that game, **~/Desktops/auteria/auteria**.  You don't have to add anything for the **Comment:** if you don't want to.  You can choose an icon (the square box on the left) from the list for it if you wish.  When done, click **OK** and that should do it.

Now, click on the icon to see if the game starts.

---

### Post by Leo Dragonheart on 2009-01-23
Thanx for all the help...I have the launcher set up now and I am downloading the 67 updates...just an update to let you know I got the launcher set up right. I opened the properties window like you said and for the command I just clicked Browse and went to where the file was... on my computer it was /home/leo/Auteria/auteria/auteria. :-)

---

