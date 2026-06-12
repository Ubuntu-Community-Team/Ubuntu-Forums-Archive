---
title: "How can i run WoW..?"
date: 2010-02-28
forum: New to Ubuntu
---

### Post by Revalution on 2010-02-28
I know this has probably been asked Dozens of times already but i would really like to know how to run wow on ubuntu. im running ubuntu 9.10 . i have wine to emulate it i just don't know how to .. please help =)

---

### Post by jflaker on 2010-02-28
> **Revalution said:**
> I know this has probably been asked Dozens of times already but i would really like to know how to run wow on ubuntu. im running ubuntu 9.10 . i have wine to emulate it i just don't know how to .. please help =)

Install WINE

```
sudo apt-get install wine
```

Install and run....


I ran it for quite some time and although the frame rate is not like it would be in windows directly, the framerate is respectable and usable.

---

### Post by Chlodovechus on 2010-02-28
Right click on WoW setup file and run it through Wine, it should install normally like in Windows, then run the WoW.exe with Wine. BTW Wine stands for wine is not an emulator so its net technically emulated.

---

### Post by Revalution on 2010-02-28
See the reason i need to run wow in ubuntu is because my windows crashed so i can't get into it = \ 
..so could i just download the installer and run that through wine?

---

### Post by marshmallow1304 on 2010-02-28
> **Revalution said:**
> ..so could i just download the installer and run that through wine?

Yes.

---

### Post by Revalution on 2010-02-28
When i Run the installer this pop up window keeps coming up with a big red X and idk if that means its not downloading certain files of whatever but yeah thats what keeps happening

---

### Post by Chlodovechus on 2010-02-28
Try using [Play On Linux]("http://www.playonlinux.com/en/").
Look for "playonlinux" in the Ubuntu Software Center and install it.
After you get it, load it up and click on install button.
Search for World of Warcraft and follow the instructions.
Hope it works!

---

### Post by Revalution on 2010-02-28
Thanks im trying it now :D

---

### Post by tom.swartz07 on 2010-02-28
> **Chlodovechus said:**
> Try using [Play On Linux]("http://www.playonlinux.com/en/").
Look for "playonlinux" in the Ubuntu Software Center and install it.
After you get it, load it up and click on install button.
Search for World of Warcraft and follow the instructions.
Hope it works!

+1

PlayonLinux is by far the most complete way that I have seen to install any game on your box.

Hopefully youll like it!

If you dont have any other questions, dont forget to mark the thread as solved (in the thread tools tab) :D

---

### Post by airtonix on 2010-03-01
> **Revalution said:**
> See the reason i need to run wow in ubuntu is because my windows crashed so i can't get into it = \ 
..so could i just download the installer and run that through wine?

or you can save yourself five hours of installing and patching and just mount your windows partition and run the already installed ^& patched copy of wow from there.

---

### Post by mechro on 2010-03-01
> **airtonix said:**
> or you can save yourself five hours of installing and patching and just mount your windows partition and run the already installed ^& patched copy of wow from there.

Do you mean boot and run Windows? Is it possible to run WoW through Ubuntu by mounting a Windows partition??

---

### Post by arochester on 2010-03-01
> Is it possible to run WoW through Ubuntu by mounting a Windows partition?? No.

Google: ubuntu wow

Top of Google list: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

---

### Post by Heavy_Metal_Jedi on 2010-03-01
I've recently done this successfully.  I found the quickest way is, if you still have the "WOW" folder from the Windows "Program Files" Directory drop it straight into the /home/username/.wine/drive_c/Program Files/ directory.   Once you make a shortcut for your desktop, you can increase fps by switching from DirectX to opengl by adding -opengl to the end of the shortcut that starts the game on your desktop.  Note there is a possibility this might make your mouse stutter in game play and there is a fix but it involves recompiling the wine program.  Every so often you may need to "chown -R" your WOW folder after receiving WOW updates.

After that it should be smooth sailing.

May the Force be with you

---

### Post by Mark Phelps on 2010-03-01
Just so there's no confusion in the recent discussion ...

It appears that what Heavy_Metal_Jedi did was COPY their WoW folder from MS Windows to their Ubuntu install -- not significantly different from installing it in Ubuntu.

It does not appear that they mounted their existing MS Windows partition and ran Wow from there using Wine.

So, the answer to running Wow from a mounted MS Windows partition is still -- no.

---

### Post by Revalution on 2010-03-01
Okay so i will try some of these suggestions thanks guys.. :)

---

