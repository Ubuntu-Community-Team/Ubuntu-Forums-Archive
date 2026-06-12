---
title: "Installing Wine"
date: 2011-07-21
forum: New to Ubuntu
---

### Post by grantmcduling on 2011-07-21
Hi, I run the latest version of Ubuntu (11.04) and have just downloaded Wine v  1.3 with the icon appearing in my dock. I downloaded it from Ubuntu software centre as described on the winehq site. All seems to have worked OK except when I try to run the application from the doc, I get a message saying it's blocked as it is an executable bit. Is there a way to get around this or is it best to leave it well alone.

---

### Post by ronnielsen1 on 2011-07-21
Right click on the exe file. Left click properties. Click permissions tab and make sure that Allow executing file as program is clicked. You can also do this from terminal by entering chmod a+x nameofprogram.exe

---

### Post by androssofer on 2011-07-21
> **ronnielsen1 said:**
> Right click on the exe file. Left click properties. Click permissions tab and make sure that Allow executing file as program is clicked. You can also do this from terminal by entering chmod a+x nameofprogram.exe

as ronnielsen1 put it, you dont launch wine itself per-se, u right click on the exe file u want and choose to run it with wine... tho i havent used it on unity yet so dnt know how to launch an already installed (in wine) windows program... as the wine list (pun!) wont b under "applications" like in the gnome days...

---

### Post by ronnielsen1 on 2011-07-21
You can also automatically associate the exe to open up automatically with wine if you click wine under the open with tab. You still have to make sure that the file is marked executable

---

### Post by grahammechanical on 2011-07-21
The installation of wine will put three or four utilities in your system.

1) Configure wine - it does just that
2) Browse c:drive - again it does what it says
3) winetricks - if you have installed this
4) Uninstall wine software - more accurately Add/Remove programs, for this also installs programs that run under wine.

When you run this utility you will see an install button. Click on that and browse to the CD drive or folder where the program is and select the setup.exe file or something like that.

This will install the program in C:drive as is done in Windows. It will also put an icon in the Dash which will load the program putting an icon into the Launcher which can then be fixed into the Launcher. It works for me. No problems with not having the executable bit set.

Regards.

---

### Post by grantmcduling on 2011-07-22
Thanks for all the suggestions. I believe I need to change the permissions for the Wine Windows Program Loader. I have located it in usr/share/applications but when I right click on the icon and go into properties, then permissions, I am told that I am not the owner so can't change the permissions.  any ideas  how I can do this?

---

### Post by jfreak_ on 2011-07-22
> **ronnielsen1 said:**
> Right click on the exe file. Left click properties. Click permissions tab and make sure that Allow executing file as program is clicked. 

+1million

Just do this manually every time on every .exe file (Usually setup.exe suffices)

---

### Post by mcduck on 2011-07-22
> **grantmcduling said:**
> Thanks for all the suggestions. I believe I need to change the permissions for the Wine Windows Program Loader. I have located it in usr/share/applications but when I right click on the icon and go into properties, then permissions, I am told that I am not the owner so can't change the permissions.  any ideas  how I can do this?

No, you don't need to change the permissions of any Wine-related file,m they are already correct if you installed Wine through Software Center (or any other of the Ubuntu's package management tools).

Instead you need to make the .exe file you are trying to run with wine executable. Which is done by right-clicking on the file, selecting "Properties" and going to the Permissions-tab.

Keep in mind that to mark a file as executable it has to be located on some Linux file system. So if the program you try to run is on Windows partition or some optical media, you'll need to copy it  into your Linux partition first. (windows file systems can't handle such things as Linux permissions and ownerships, and optical media fileystems are read-only by design)

(also, as a general advice, you really don't want to mess with the permissions of any of the system files/directories. Especially if you are not absolutely sure about what you are doing and why. The ownerships and permissions of any system file are what they are for a good reason, and changing them will break things.)

---

### Post by androssofer on 2011-07-22
> **grantmcduling said:**
> Thanks for all the suggestions. I believe I need to change the permissions for the Wine Windows Program Loader. I have located it in usr/share/applications but when I right click on the icon and go into properties, then permissions, I am told that I am not the owner so can't change the permissions.  any ideas  how I can do this?

sounds like time to unleash the terminal to me ;)

open terminal and do:

```
cd /usr/share/applications/
```

then:

```
sudo chmod +x wineprogramLoaderName
```

shud do the trick :)

repeat for any exe files u wanna launch...

---

### Post by grantmcduling on 2011-07-22
Many thanks for all the suggestions. I have it working now. Another terrific result from this forum.:o

---

