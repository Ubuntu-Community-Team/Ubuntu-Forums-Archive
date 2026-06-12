---
title: "i cannot install themes!!"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by Rockanium on 2009-03-23
i try to drag the file into the themes folder
                          /usr/share/themes

but it says:
    Error while moving "icknessblack".
    There was an error moving the file into /usr/share/themes.
    Error moving file: Permission denied

why does it say premission denied?

p.s i am a linux noob

---

### Post by cariboo on 2009-03-23
Right-click on your desktop and select Change Desktop Background, then click the Theme tab and drag your theme to the window.

Jim

---

### Post by gandaran on 2009-03-23
> **Rockanium said:**
> i try to drag the file into the themes folder
                          /usr/share/themes

but it says:
    Error while moving "icknessblack".
    There was an error moving the file into /usr/share/themes.
    Error moving file: Permission denied

why does it say premission denied?

p.s i am a linux noob
making changes to the root file system you need root permission, open terminal and type **sudo nautilus**, now you can move the file with this root nautilus window.
some themes sometimes get blocked when you copy/paste to  /usr/share/themes with the nautilus root window and wont work, but if you use the move command line there is no problem, place the extracted theme file in your home user folder or cd to desktop if it's on desktop directory then type this code **sudo mv *'theme file name'*  /usr/share/themes** easy and done!

---

### Post by VCoolio on 2009-03-23
The replies above should get it fixed. You should know that drag and drop a file in the themes window copies it to /home/[you]/.themes. This is the default and easiest way to install themes. But root apps, like synaptic or a root nautilus / root terminal / root gedit do not use this folder. If you want these apps to use the same theme as your user desktop, you should copy them to /usr/share/themes (too). For icon themes goes the same, except the folders are /home/[you]/.icons and /usr/share/icons.

---

### Post by mvalviar on 2009-03-23
Remember that if you want to run nautilus with root permission use ```
gksudo nautilus
``` as a rule of thumb use sudo for command line applications and gksudo for graphical user interface application.

When using nautilus with root permission do so with care. Remember to close it once your done. One miss click can mean a disaster.

---

### Post by gandaran on 2009-03-23
> **mvalviar said:**
> Remember that if you want to run nautilus with root permission use ```
gksudo nautilus
``` as a rule of thumb use sudo for command line applications and gksudo for graphical user interface application.

When using nautilus with root permission do so with care. Remember to close it once your done. One miss click can mean a disaster.
no, sudo or gksudo will open the root window just fine, only deference with sudo you type the password in terminal, with gksudo a password graphical window  opens up, gksudo is more for running a menu or desktop application launcher, so if you are running/typing on the terminal it's best to use sudo nautilus!

---

### Post by mcduck on 2009-03-23
> **gandaran said:**
> no, sudo or gksudo will open the root window just fine, only deference with sudo you type the password in terminal, with gksudo a password graphical window  opens up, gksudo is more for running a menu or desktop application launcher, so if you are running/typing on the terminal it's best to use sudo nautilus!

Actually you really should always use gksudo for graphical applications. Sudo and gksudo have more differences tan just the way yu input your password..

While sudo *does* run GUI apps with root permissions, it doesn't load root users environment variables correctly for them. This means that you are running apps as root but using your normal user's variables and configuration files. In some cases this will result to your user's files becoming owned by root, which can cause lots of problems or even make you unable to log in at all.

Some GUI apps run fine with sudo instead of gksudo, others don't. Trying to find out (and remember) which ones are fine and which ones will break things would be quite impossible. It's better to just use gksudo for *all* graphical applications.

(Same kind of thing applies to ways of running a root session in a terminal, "sudo su", "sudo -s" and "sudo -i" all give you root permissions but only "sudo -i" loads root's environment correctly.)

---

### Post by gandaran on 2009-03-23
> Actually you really should always use gksudo for graphical applications. Sudo and gksudo have more differences tan just the way yu input your password..
I haven't noticed any and I don't believe there are any!
> While sudo does run GUI apps with root permissions, it doesn't load root users environment variables correctly for them. This means that you are running apps as root but using your normal user's variables and configuration files. In some cases this will result to your user's files becoming owned by root, which can cause lots of problems or even make you unable to log in at all.
I have been using ubuntu since 7.04 always using sudo to open any root graphical application (and will continue to do so) and had no problem yet!

---

### Post by finer recliner on 2009-03-23
> **gandaran said:**
>  I have been using ubuntu since 7.04 always using sudo to open any root graphical application (and will continue to do so) and had no problem yet!

gksudo was created with the **intention **to be used with GUI applications. **sudo was not**. I suggest you follow the appropriate documentation below to avoid potential issues in the future. In the end, I guess it's your choice.


[https://help.ubuntu.com/community/RootSudo#Graphical%20sudo](https://help.ubuntu.com/community/RootSudo#Graphical%20sudo)

---

### Post by mcduck on 2009-03-23
> **gandaran said:**
> I haven't noticed any and I don't believe there are any!

I have been using ubuntu since 7.04 always using sudo to open any root graphical application (and will continue to do so) and had no problem yet!

You are free to do so if you wish. But you really shouldn't give that kind of advice to anybody else. It's not a question of believing or opinion. :)

You can find countless threads on these forums where people are asking for help because they can't login any more because of wrong permissions on ~/.dmrc. This is often a result from running GUI apps with sudo.

---

### Post by halitech on 2009-03-23
> **gandaran said:**
> I haven't noticed any and I don't believe there are any!

I have been using ubuntu since 7.04 always using sudo to open any root graphical application (and will continue to do so) and had no problem yet!

you can also use pure alcohol in your car but just because you can doesn't mean you should or there isn't the chance that you will damage something by doing so.

> **finer recliner said:**
> gksudo was created with the **intention **to be used with GUI applications. **sudo was not**. I suggest you follow the appropriate documentation below to avoid potential issues in the future. In the end, I guess it's your choice.


[https://help.ubuntu.com/community/RootSudo#Graphical%20sudo](https://help.ubuntu.com/community/RootSudo#Graphical%20sudo)

I agree, sudo and gksudo were both designed for specific needs in mind and should be used accordingly.

---

