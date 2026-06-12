---
title: "I can't download from UBUNTU SOFTWARE CENTER"
date: 2010-01-21
forum: New to Ubuntu
---

### Post by MindController on 2010-01-21
Hi! I've got a problem with 9.10. I can't download any software from ubuntu software center. on only one. It's said
Canonical does not provide updates for Gstreamer extra plugins. Some updates may be provided by the Ubuntu community.
I can't listen mp3.
Pls help

---

### Post by MelDJ on 2010-01-21
have you tried: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) ?

---

### Post by MindController on 2010-01-21
i've tried but i still have this problem. Pls help

---

### Post by MelDJ on 2010-01-21
what happens when you type sudo apt-get install ubuntu-restricted-extras ?

---

### Post by running_rabbit07 on 2010-01-21
> **MelDJ said:**
> what happens when you type ```
sudo apt-get install ubuntu-restricted-extras
``` ?
Code tags are helpful.

---

### Post by MelDJ on 2010-01-21
> **running_rabbit07 said:**
> Code tags are helpful.

i never knew how to use them :)

---

### Post by MindController on 2010-01-21
```

Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
The following packages were automatically installed and are no longer required:
  libxvidcore4 ttf-liberation libmp3lame0 libfaac0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 163 not upgraded.

```
Here it is.

---

### Post by running_rabbit07 on 2010-01-21
> **MelDJ said:**
> i never knew how to use them :)
Just highlight the code, then click the pound sign in the screenshot.

---

### Post by running_rabbit07 on 2010-01-21
> **MindController said:**
> ```

Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
The following packages were automatically installed and are no longer required:
  libxvidcore4 ttf-liberation libmp3lame0 libfaac0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 163 not upgraded.

```Here it is.

You shouldn't have any problems with MP3s. What program are you using to open them?

---

### Post by MelDJ on 2010-01-21
the codecs are already installed. you should be able to play the mp3's. have you tried installing other software? or pressing ok when the notification comes up?

---

### Post by Sef on 2010-01-21
> what happens when you type sudo apt-get install ubuntu-restricted-extras ?Actually what one should type is this code:

```
sudo apt-get update && sudo apt-get install ubuntu-restricted-extras
```.

That insures that the repositories to be downloaded are up-to-date.

---

### Post by Mornedhel on 2010-01-21
> **Sef said:**
> Actually what one should type is this code:

```
sudo apt-get update && sudo apt-get ubuntu-restricted-extras
```.

That insures that the repositories to be downloaded are up-to-date.

You're missing an "install" in there.

---

### Post by Sef on 2010-01-21
> You're missing an "install" in there.

Thanks for catching that error.

---

### Post by MindController on 2010-01-22
> **MelDJ said:**
> the codecs are already installed. you should be able to play the mp3's. have you tried installing other software? or pressing ok when the notification comes up?
I have tried but same like before. I can't install anything From UBUNTU SOFTWARE CENTER. Means I can't see nothing like install button or something like that. I'm using Rhythmbox to play the mp3. not only mp3 but also video too. Thanks for helping guys

---

### Post by running_rabbit07 on 2010-01-22
When you run Update Manager, does it work? What about Synaptic Package Manager? I am wondering if maybe your sources list is messed up some how.

---

### Post by warfacegod on 2010-01-22
> **MindController said:**
> I have tried but same like before. I can't install anything From UBUNTU SOFTWARE CENTER. Means I can't see nothing like install button or something like that. I'm using Rhythmbox to play the mp3. not only mp3 but also video too. Thanks for helping guys

Right click your Applications, Places, System menu and select Edit Menus. In the window that opens, highlight Ubuntu Software Center and click properties on the right. In that window will be a spot called Command: that will say /usr/bin/software-center. Change that to say "gksu software-center". Then try using Ubuntu Software Center again.

---

### Post by MindController on 2010-01-22
> **warfacegod said:**
> Right click your Applications, Places, System menu and select Edit Menus. In the window that opens, highlight Ubuntu Software Center and click properties on the right. In that window will be a spot called Command: that will say /usr/bin/software-center. Change that to say "gksu software-center". Then try using Ubuntu Software Center again.
After i did as u told. But still have this problem. Check my screen short.
[IMG]http://img109.imageshack.us/img109/8232/myphoto.png[/IMG]

---

### Post by warfacegod on 2010-01-22
I've never seen that not work.

In:

System> Admin.> Software Sources> Ubuntu tab and make sure Software restricted by copyright or legal issues (Multiverse) is checked.

Next go to:

System> Admin.> Synaptic Package Manager> Edit> Fix Broken Packages

While you are there, search for Gstreamer and get the good, bad, and ugly plugins.

---

### Post by k64 on 2010-01-22
> **MindController said:**
> I have tried but same like before. I can't install anything From UBUNTU SOFTWARE CENTER. Means I can't see nothing like install button or something like that. I'm using Rhythmbox to play the mp3. not only mp3 but also video too. Thanks for helping guys

System > Administration > Synaptic Package Manager. You're better off there.

---

### Post by MindController on 2010-01-23
> **warfacegod said:**
> I've never seen that not work.

In:

System> Admin.> Software Sources> Ubuntu tab and make sure Software restricted by copyright or legal issues (Multiverse) is checked.

Next go to:

System> Admin.> Synaptic Package Manager> Edit> Fix Broken Packages

While you are there, search for Gstreamer and get the good, bad, and ugly plugins.

Done! i changed the server to United States from our country server. I can't brother. many thanks for helping me. Please help again.

---

### Post by warfacegod on 2010-01-23
> **MindController said:**
> Done! i changed the server to United States from our country server. I can't brother. many thanks for helping me. Please help again.

Glad to hear it. Don't forget to mark as solved under thread tools. Enjoy!

---

### Post by MindController on 2010-01-23
> **warfacegod said:**
> Glad to hear it. Don't forget to mark as solved under thread tools. Enjoy!
Nuh....i mean i still have this problem......... i cant download from there.
sorry for misunderstanding!

---

### Post by tjsummers51l on 2010-01-23
I had a similar problem. I uninstalled the ubuntu software center from synaptic package manager and reinstalled it. that worked for me.

---

### Post by warfacegod on 2010-01-23
Give it a try. Mark it for complete removal then install it again. Doing this can't make anything worse. If that doesn't work then go to your Terminal and type:

sudo apt-get install gnome-app-install

That will install Add/Remove Applications which is what Ubuntu S.C. replaced. Personally I prefer Add/Remove over S.C.

Ubuntu Software Center has been having a fair amount of problems, and in my opinion shouldn't have been shipped with 9.10. Your situation seems to be one of the more extreme cases.

---

### Post by MindController on 2010-01-25
>  	
I had a similar problem. I uninstalled the ubuntu software center from synaptic package manager and reinstalled it. that worked for me. 

Work! Thanks for the information brother.
Guys Thanks for helping me especially @warfacegod and @tjsummers51l

---

### Post by warfacegod on 2010-01-26
Glad to help.

---

