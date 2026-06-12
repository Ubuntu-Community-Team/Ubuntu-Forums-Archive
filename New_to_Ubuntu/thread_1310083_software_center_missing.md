---
title: "software center missing"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by kree8or on 2009-11-01
Hi, I've read about the software center and it sounds great. My problem is that "software center" isnt where its supposed to be! I've re-installed it using the packages manager, and it installs but it still doesnt show up under the applications menu. any ideas? tearing my hair out here!

p.s. i'm using karmic kola

---

### Post by wrgb2 on 2009-11-01
I assume your using the Gnome desktop.  Go to System > Preferences > Main Menu.  Make sure Applications is highlighted in the left-hand pane, then check at the bottom of the right-hand pane, there should be an entry for Ubuntu Software Center -- make sure there's a check mark next to it and it should show up in the proper place.

Randy

---

### Post by philinux on 2009-11-01
> **kree8or said:**
> Hi, I've read about the software center and it sounds great. My problem is that "software center" isnt where its supposed to be! I've re-installed it using the packages manager, and it installs but it still doesnt show up under the applications menu. any ideas? tearing my hair out here!

p.s. i'm using karmic kola

Open a terminal, apps>access>terminal.

Issue this command. If it's installed correctly it should run.

```
software-center
```

---

### Post by kree8or on 2009-11-01
> **wrgb2 said:**
> I assume your using the Gnome desktop.  Go to System > Preferences > Main Menu.  Make sure Applications is highlighted in the left-hand pane, then check at the bottom of the right-hand pane, there should be an entry for Ubuntu Software Center -- make sure there's a check mark next to it and it should show up in the proper place.

Randy

OK, i've run software-center from the terminal and it runs fine, but it doesnt show up in the right hand pane. I've added it manually and it works fine. Thanks for your help

---

### Post by kree8or on 2009-11-01
> **philinux said:**
> Open a terminal, apps>access>terminal.

Issue this command. If it's installed correctly it should run.

```
software-center
```

Thanks,it works!

---

### Post by philinux on 2009-11-01
> **kree8or said:**
> OK, i've run software-center from the terminal and it runs fine, but it doesnt show up in the right hand pane. where is it situatedin the file system so i can add it manualy

Either,

1. open synaptic, locate alacarte and mark it for re-installation.

or

2. sudo apt-get install --reinstall alacarte

---

### Post by jthirt on 2009-11-02
I have the same issue on a French 64bit upgrade from 9.04. 

I had a look at the French forum but no luck there!

Perhaps something to do with the number of items as I have 10 in the Applications menu. On my other instances of 9.10 where the Software center shows I have less.

I suppose I'll have to add it manually.

---

### Post by tubunu on 2009-11-03
I had software center just right after fresh install, then it disappeared just yesterday and I can't get it back in the menu. It shows as installed in Synaptic, even so I reinstalled it using 
```
sudo apt-get install --reinstall software-center
```
but it still doesn't show up in the menu. When I right-click Applications and select Edit Menus, software center isn't there at all! so I cannot select it. 

Any clues?

---

### Post by tubunu on 2009-11-07
Bump

---

### Post by jthirt on 2009-11-08
@ tubunu

You need to create a new menu item entry with the following values:

Type: Application
Name: Ubuntu Software Center
Command: /usr/bin/software-center
Comment: Lets you choose from thousands of free applications available for Ubuntu
Icon: /usr/share/icons/hicolor/48x48/apps/softwarecenter.png

For the icon, you must click on the icon (top left)

That way, the menu entry will be recreated.

I hope this helps!

Cheers
JT

---

### Post by tubunu on 2009-11-13
Hey, jthirt, thanks a lot! That worked. :)

What I'm wondering though is why it disappeared from the menu. I've recently had to do a new clean install of Karmic and the Software Center disappeared again from the menu even though it's installed in Synaptic. What's going on?

---

### Post by zapman on 2009-11-13
I have the same problem. Just noticed it. I did an update today, maybe it's related.

---

### Post by tubunu on 2009-11-14
> **jthirt said:**
> 
You need to create a new menu item entry with the following values:

Type: Application
Name: Ubuntu Software Center
Command: /usr/bin/software-center
Comment: Lets you choose from thousands of free applications available for Ubuntu
Icon: /usr/share/icons/hicolor/48x48/apps/softwarecenter.png

I'm sad to say that after I created the menu item as advised and thinking it finally worked, after I rebooted my PC this morning the Software Center is gone again! What's going on? I never removed ANY package after a fresh install and I did a clean install after a clean install thinking I accidentaly did delete something. Now the problem's back again! It's rather annoying.

---

### Post by luctor on 2009-11-16
Same problem here.
Software Center just disapeared from the menu.
Did a reinstall of it but that didn't help.
It runs fine though, I use [ALT-F2] -> software-center

Strange bug ..

---

### Post by Claus7 on 2009-11-21
Hello,

> **philinux said:**
> Open a terminal, apps>access>terminal.

Issue this command. If it's installed correctly it should run.

```
software-center
```

it worked for me too.

Regards!

---

### Post by Abadon125 on 2009-11-21
> **luctor said:**
> Same problem here.
Software Center just disappeared from the menu.
Did a reinstall of it but that didn't help.


Did you try re-creating the link in the edit menu window as was posted earlier in this thread?

---

### Post by 1996tbird on 2010-02-04
Thanks for your help. Im a noob and this is fun but some of your solutions seem cryptic.
 
noobie clarification:
If you want the icon back use preferences> main menu> add> Browse find the icon file: /usr/share/icons/hicolor/48x48/apps/softwarecenter.png

then change the command to software-center and close. make sure it's checked and it will appear on the menu.

I need to reboot to see if it's still there.

---

