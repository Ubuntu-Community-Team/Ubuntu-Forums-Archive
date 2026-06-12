---
title: "How to Make changes in Keyboard layouts"
date: 2010-09-29
forum: New to Ubuntu
---

### Post by Shahram A on 2010-09-29
Hello everybody

Can anyone guide me to make changes in a keyboard layout?

I like to make changes to the Farsi (Persian) keyboard layout that Ubuntu offers.
The place of characters in some keys need to be changed. For example the comma sign that has been put on the same key as number 7 needs to placed on lower keys similar to English keyboard layouts.

How can I make such changes or make a new keyboard layout and add it to the currently present keyboard layouts?

Please reply in simple terms, I am not proficient in computer software or Ubuntu.

Does anyone know of other Farsi keyboard layouts that might be available?

Thank you
Shahram

---

### Post by Hippytaff on 2010-09-29
Found this
 
>  
To install standard Persian keyboard layout on Fedora, Red Hat, and Ubuntu: 
[LIST=1]
[*]Open keyboard preferences dialog by choosing Desktop -> Preferences -> Keyboard Preferences
[*]Choose "Layouts" tab
[*]Click on "Add..." button
[*]Choose Persian keyboard layout in the dialog that appears
[/LIST]You can switch between the different Keyboard layouts by pressing the two **Shift** keys at the same time. You can modify this behavior in the "Layout Options" tab in keyboard preferences. 

 
from here - [http://farsiweb.ir/wiki/Install_Keyboard](http://farsiweb.ir/wiki/Install_Keyboard)

---

### Post by Shahram A on 2010-09-29
Thank you for your help.

However, I have already done that and the Farsi keyboard is working. 
The problem is that the Persian keyboard's layout is not efficiently setup. There are a number of Farsi Keyboard layouts across different operating systems and some custom ones as well. But I am a new user in Linux and Ubuntu, and in Ubuntu there are two very almost identical Farsi keyboard layouts.
I need to make changes in the current layout or introduce a new layout that is different from the current ones so that I would be able to type more efficiently.

Thank you
Shahram

---

### Post by Hippytaff on 2010-09-29
You can customize the farsi layout
 
[http://www.ehow.com/how_6469128_customize-keyboard-layout-ubuntu.html](http://www.ehow.com/how_6469128_customize-keyboard-layout-ubuntu.html)

---

### Post by Shahram A on 2010-09-29
> **Hippytaff said:**
> You can customize the farsi layout
 
[http://www.ehow.com/how_6469128_customize-keyboard-layout-ubuntu.html](http://www.ehow.com/how_6469128_customize-keyboard-layout-ubuntu.html)

Thank you again

I followed the above instruction which was to open the keyboard preferences layout tab.
Next it reads:
3 - Use the window onscreen to reassign the layout of your keyboard. You can click on a key with your mouse and manually reassign each one to match your needs or use a pre-created layout by selecting one from the drop-down menu. When you're finished customizing your keyboard layout in Ubuntu, click "OK."

My question is where is the window onscreen?
There is no button showing that on that tab and I did not find it in other system menus...

Thank you

---

### Post by BigRedButton on 2010-09-29
Or, if you're feeling adventurous, the files for the layouts are in /usr/share/X11/xkb/symbols. If you want to seriously customize the snot out of it you can edit the relevant file (it will be one of the two letter ones... not sure which one for persian). The syntax is pretty simple, here's an example line from a standard us keyboard:

key <AE01> {[1,	exclam 	]};

where "<AE01>" is the key: "A" meaning alphanumeric section (as opposed to the num pad) "E" being the row the key is in, starting with "A" being the bottom row and counting up, "01" being the key, counted from the left and excluding specially named keys (<TLDE>, <BKSP>, <CTRL>, etc.) basically only counting numbered and lettered keys.

the syntax for the rest of the line is simple:

{[ 1, 2, 3, 4]}

where "1" is the character to be printed normally, "2" is the shifted character, "3" is the third level character (without shift), and "4" is 3rd level with shift.

for Farsi you may possibly need to use unicode to define the characters, such as U0041 = capital "A". you can easily find these online.

you might also need to paste this line

include "level3(ralt_switch)"

at the bottom of the section you are editing if you intend to use the third level. chances are it will already be in some of the layouts... you will see where it goes.
personally I prefer this method, since it allows for more complete customization, and also allows you to make better use of the third level, basically doubling your keyboard functionality. For example, on my custom layout, +#3 +#!rd |3v3| @u+0m@+!(@||y 5u65 !n |337. (the third level automatically subs in leeT).

(I was bored one day...)

Also (maybe a given) you need to edit these as root, so in the terminal

sudo gedit

and find the file that way

---

### Post by Shahram A on 2010-09-29
To RedButton

Thank you for the information

It is somewhat advanced - I have to look in to it and see if I can try it.

Regards
Shahram

---

### Post by Shahram A on 2010-09-29
I have asked other people in the beginners chat forum. 
They introduced me to a program called xkeycaps which can be installed via the terminal by typing:
sudo apt-get install xkeycaps

Once it is installed it can be opened from the terminal command:
xkeycaps

Two windows open (GUI for the program).

I have not used it yet but it can be used to change the map of a keyboard layout. Although, I did not see the Farsi (Persian) layout in the list. But it certainly has many European languages if anyone needs it.

You can find the manual at:
[http://www.jwz.org/xkeycaps/man.html](http://www.jwz.org/xkeycaps/man.html)

---

