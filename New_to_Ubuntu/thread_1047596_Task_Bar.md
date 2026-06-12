---
title: "Task Bar"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by 70plymouth on 2009-01-22
I was wondering if there was a simple way to customize my task bar. (With Apps, Places, System and time/date) I just don't like the look of it, its very boring sitting there all white. I don't know enough about Linux to customize things myself, I've been mainly relying on applications to make it look better. 

I guess my questions is what is/if there is a cool looking way to reorganize my task bar.

Another quick question is what is a good app to monitor my system temperatures/cpu/RAM.

Thanks

---

### Post by drs305 on 2009-01-22
If you are talking about the panels (upper and lower), you can right click on them and add icons for various apps. Right click, Add to Panel. You can select from the List you see in the bottom half or double click on Application Launcher to see a larger list of apps.

You can also make your own startup icons by selecting Custom Application Launcher and entering a name and the command you want to start.

You can also drag icons from the Main Menu dropdown items to the panel and release them.

If you want to edit the default *dropdown* menus, right click on the main menu icon and select "Edit Menus". You can also enter the edit mode by typing the following in a terminal:
```

alacarte

```
You can deselect and add items to the drop down menus, and if you decide you don't like what you did you can hit the "Revert" button to take the drop down menu back to the defaults.

---

### Post by 70plymouth on 2009-01-22
I just mean different designs and appearance. Its so bland as a white panel. Is there anything I can do to make it possibly transparent, different text, different borders etc.

---

### Post by Michael.Godawski on 2009-01-22
hi,

you can right click on the task bar then select properties and go to Background.

There you can set the transparency and a background.

---

### Post by m_duck on 2009-01-22
To change the font, goto System -> Preferences -> Appearance and choose the Font tab. Changing the "Application Font" will change the font used for the task bar. However it will also change the fonts for other things as well.

EDIT: To change only the text on the task bar, you can download the "gnome-color-chooser" ```
sudo apt-get install gnome-color-chooser
```Choose the panel tab, and there you can set the font and colour for your panel.

---

### Post by Patricrawley on 2009-01-22
Some themes on Gnome-look.org also change the appearance of the panels. Like ClearGlow for instance, so looking on there never hurts. If you want more ideas on themeing your system I would recommend looking through the January 2009 Desktop thread in the community cafe section of these forums.

---

### Post by MikeBrown on 2009-01-23
About your system monitor question (which seems to be getting overlooked) 
I suggest gkrellm. 
I believe it's in the synaptic packages manager or type "sudo apt-get install gkrellm" in terminal (without quotes)

---

### Post by m_duck on 2009-01-23
> **MikeBrown said:**
> About your system monitor question (which seems to be getting overlooked)
I missed that #-o Another good system monitor (if a bit more complicated to set up) is conky. A giant thread with screenshots and configs is [here](http://ubuntuforums.org/showthread.php?t=281865).

---

