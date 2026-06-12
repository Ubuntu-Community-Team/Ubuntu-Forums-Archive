---
title: "Re-adding menus to panel 8.10"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by drsmooth on 2009-02-11
I was wondering if anyone can give me advice.

I installed Intrepid on 2 identical computers. My laptop and my friends. 

She accidentally deleted the Applications, Places and System menus from her panel (Don't ask!!!).  

I have looked for days on the Internet to find a way to re add them to her computer. I am one who like to find a solution on my own but in this case I am stumped. 

Is there a way to re-add these menus? Can I transfer something from my computer?

I am probably overlooking a very simple solution as I am very new to Ubuntu/Linux.

---

### Post by cdtech on 2009-02-11
Here is a method for restoring your panel to default:

Press ALT+F2 and in the run dialog box, type "gnome-terminal" then click on Run.

When the Terminal window opens, enter the command:
```
sudo apt-get install gconf2
gconftool-2 --recursive-unset /apps/panel

```
Then enter:
```
rm -rf ~/.gconf/apps/panel
```
And enter one more command:
```
pkill gnome-panel
```
This will retore to its original state. Be sure to backup your config files if you modify the panel, the files can be found here:

~/.gconf/apps/panel

Hope this helps ya.........

---

### Post by drsmooth on 2009-02-12
Sorry I hope no one is posting a reply to me now. If you are, thank you for taking your time to help I am a supreme dummy!!!! I found a solution.

After pulling out my hair for days all I had to do was right click on the panel, click on "add to panel", and choose to add "Main Menu". I have been to add to panel before but as a NooB I didn't know what "The Main Gnome Menu" was. As I said I am still learning. 

I finally decided to add it figuring, 'I can always remove it'.

---

### Post by cdtech on 2009-02-12
Cool, remember to backup your panel directory when you modify it. It will save a lot of frustration if you want it back later.......

Good luck

---

### Post by drsmooth on 2009-02-12
> **cdtech said:**
> Here is a method for restoring your panel to default:

Press ALT+F2 and in the run dialog box, type "gnome-terminal" then click on Run.

When the Terminal window opens, enter the command:
```
sudo apt-get install gconf2
gconftool-2 --recursive-unset /apps/panel

```
Then enter:
```
rm -rf ~/.gconf/apps/panel
```
And enter one more command:
```
pkill gnome-panel
```
This will retore to its original state. Be sure to backup your config files if you modify the panel, the files can be found here:

~/.gconf/apps/panel

Hope this helps ya.........

This works even better than my solution! 

My solution brings up one icon that lumps everything that was previously in the "Apps", "Places" and "System" menus into one menu.

Yours, restored everything back to what it was. I can finally give her back her laptop! 

Thank You for the solution!

---

### Post by prshah on 2009-02-12
> **drsmooth said:**
> 
She accidentally deleted the Applications, Places and System menus from her panel 

You can also just right click the panel, choose add to Panel and choose "Menu Bar" (Not "Main Menu").

Resetting _all_ panel settings to their default just to get back the main menu is like swatting a fly with a sledgehammer.

---

### Post by mcduck on 2009-02-12
> **drsmooth said:**
> 
My solution brings up one icon that lumps everything that was previously in the "Apps", "Places" and "System" menus into one menu.

That was simply wrong menu applet, there are two installed by default and more available.

"Main Menu" is a single-button menu, win2000-style.

"Menu bar" is Gnome's default, with three separate menus for Applications, Places and System.

..and I agree with the above poster that resetting all panel configurations just to add one simple applet back to the panel is serious overkill. :D

---

### Post by cdtech on 2009-02-12
> Resetting _all_ panel settings to their default just to get back the main menu is like swatting a fly with a sledgehammer.
That's funny. :lolflag:

As an absolute beginner we sometimes have huge fly's.

---

### Post by drsmooth on 2009-02-12
> **prshah said:**
> You can also just right click the panel, choose add to Panel and choose "Menu Bar" (Not "Main Menu").

Resetting _all_ panel settings to their default just to get back the main menu is like swatting a fly with a sledgehammer.


Thanks! I tried that out on my computer and it worked. It added a second instance of menus to my panel, easy enough to delete though. It is funny some of the biggest problems have the easiest solutions! Well big problem for me at least.

---

### Post by blackjak on 2009-02-12
What about if I have deleted desk1 and desk2 buttons?
Is there any way to put them again on the panel without reseting everything to its original state?

---

### Post by kanikilu on 2009-02-12
> **blackjak said:**
> What about if I have deleted desk1 and desk2 buttons?
Is there any way to put them again on the panel without reseting everything to its original state?
I assume you are referring to the workspaces. If so, just right-click on the panel, go to Add to Panel, scroll to the bottom of the list and select the Workspace Switcher and then click Add.

---

### Post by drsmooth on 2009-02-12
Oops question already answered.

---

### Post by blackjak on 2009-02-12
Thanks a lot, kanikilu, I did not know what it is called.:P

---

