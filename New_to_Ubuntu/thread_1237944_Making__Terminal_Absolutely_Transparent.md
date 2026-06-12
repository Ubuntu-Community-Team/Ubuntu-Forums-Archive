---
title: "Making  Terminal Absolutely Transparent"
date: 2009-08-11
forum: New to Ubuntu
---

### Post by sumeshgupta on 2009-08-11
**[SIZE=2]Is there a way to make the Terminal absolutely transparent? I mean no panels, sliders etc. It should look as if typing is being done on the Dekstop itself and not in a window.[/SIZE]**:guitar:

---

### Post by hockeyfighter09 on 2009-08-12
I dont know what good this will do you, but the arch wiki explains how here
[http://http://wiki.archlinux.org/index.php/Configuring_Terminal_as_a_Transparent_Wallpaper]("http://wiki.archlinux.org/index.php/Configuring_Terminal_as_a_Transparent_Wallpaper")you could apply it to ubuntu it should work. :)

Also heres another link showing how to setup an aterm terminal for transparency [http://linuxreviews.org/software/x11-terms/aterm/]("http://linuxreviews.org/software/x11-terms/aterm/")

---

### Post by rsiddharth on 2009-08-12
> **sumeshgupta said:**
> **[SIZE=2]Is there a way to make the Terminal absolutely transparent? I mean no panels, sliders etc. It should look as if typing is being done on the Dekstop itself and not in a window.[/SIZE]**:guitar:
Its pretty simple . The following instructions are only relevant if your using GNOME Desktop Environment . ( ubuntu uses GNOME ) 

*Open terminal 
* Click on Edit --> Preferences .
* In the preferences Dialog box , Choose the "Background " tab .
* There are probably three options , Choose the last one - " Transparent Background " and move  the slider ( below ) to the extreme left . 
* Look if the Font Color is clear and visible with respect to your Desktop Wallpaper , If your not comfortable with the font color , you can change it . To change the font color go to "Colors"  tab ,
        
           # In "Colors" tab under " Foreground and Background " , uncheck " Use colors from system theme" . hit the color box beside " Text Color " to choose the desired color for the text in Terminal . 

* To remove the Scroll bar ( or slider ) , go the "Scrolling" tab , under " Scroll Bar : " option choose " Disabled " from the adjacent drop down options menu . 

* Close the Preferences dialog box . 
* If you wish to hide the Menu bar , either hit " shift+F9 " or go to "View" and uncheck the  "Show Menubar " 

* after you do all this , hit F11 , you go fullscreen in terminal  and now all that is there is the text that you type in terminal and your Desktop Background !!! .

---

### Post by sumeshgupta on 2009-08-12
Thanks a Ton. I tried both the solutions. They work Great.:guitar:

---

### Post by rsiddharth on 2009-08-13
> **sumeshgupta said:**
> Thanks a Ton. I tried both the solutions. They work Great.:guitar:
If your looking for a non-distractive Terminal "skin" then I suggest a  Black Background with grayish Text color  with the scrollbar/slider disabled , menu bar hidden . Going full screen will completely leave everything behind and now its you and Terminal ! .

---

### Post by colau on 2009-08-17
> **rsiddharth said:**
> its pretty simple . The following instructions are only relevant if your using gnome desktop environment . ( ubuntu uses gnome ) 

*open terminal 
* click on edit --> preferences .
* in the preferences dialog box , choose the "background " tab .
* there are probably three options , choose the last one - " transparent background " and move  the slider ( below ) to the extreme left . 
* look if the font color is clear and visible with respect to your desktop wallpaper , if your not comfortable with the font color , you can change it . To change the font color go to "colors"  tab ,
        
           # in "colors" tab under " foreground and background " , uncheck " use colors from system theme" . Hit the color box beside " text color " to choose the desired color for the text in terminal . 

* to remove the scroll bar ( or slider ) , go the "scrolling" tab , under " scroll bar : " option choose " disabled " from the adjacent drop down options menu . 

* close the preferences dialog box . 
* if you wish to hide the menu bar , either hit " shift+f9 " or go to "view" and uncheck the  "show menubar " 

* after you do all this , hit f11 , you go fullscreen in terminal  and now all that is there is the text that you type in terminal and your desktop background !!! .

+1

---

### Post by ashwinhgtx on 2009-08-17
> **rsiddharth said:**
> Its pretty simple . The following instructions are only relevant if your using GNOME Desktop Environment . ( ubuntu uses GNOME ) 

*Open terminal 
* Click on Edit --> Preferences .
* In the preferences Dialog box , Choose the "Background " tab .
* There are probably three options , Choose the last one - " Transparent Background " and move  the slider ( below ) to the extreme left . 
* Look if the Font Color is clear and visible with respect to your Desktop Wallpaper , If your not comfortable with the font color , you can change it . To change the font color go to "Colors"  tab ,
        
           # In "Colors" tab under " Foreground and Background " , uncheck " Use colors from system theme" . hit the color box beside " Text Color " to choose the desired color for the text in Terminal . 

* To remove the Scroll bar ( or slider ) , go the "Scrolling" tab , under " Scroll Bar : " option choose " Disabled " from the adjacent drop down options menu . 

* Close the Preferences dialog box . 
* If you wish to hide the Menu bar , either hit " shift+F9 " or go to "View" and uncheck the  "Show Menubar " 

* after you do all this , hit F11 , you go fullscreen in terminal  and now all that is there is the text that you type in terminal and your Desktop Background !!! .

Thanks a lot for that.:P

---

### Post by Fzang on 2009-08-17
If you use Compiz you can simply exclude the terminal from the window decoration list and it won't have any borders at all.

---

