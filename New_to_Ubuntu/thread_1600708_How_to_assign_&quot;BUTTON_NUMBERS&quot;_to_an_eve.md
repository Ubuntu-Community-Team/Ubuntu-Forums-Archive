---
title: "How to assign &quot;BUTTON NUMBERS&quot; to an event?"
date: 2010-10-19
forum: New to Ubuntu
---

### Post by outleradam on 2010-10-19
I have a logitech MX Revolution. I have all mouse buttons working with the exception of two. These two mouse buttons are the forward and back buttons. the application "xev" shows that these mouse buttons do not have a "button number" assigned to them. 
 
Playing with xmodmap allows for them to be remapped to different button numbers, but I cannot get them to show up as buttons 8 and 9. It's like button8 and button9 are not assigned a X event. They trigger an event when clicked, but no button press event.
 
Before anyone starts to suggest that I use xmodmap to change the button order, using xmodmap to change the button order is not the solution. The buttons are mapped correctly, there is no button press event mapped to the button.
 
How do I assign a button number? They are registering as an input, but cannot be assigned to a function for their lack of a button number.   Buttons 8 and 9 are not triggering button8 and button9 events.

---

### Post by ubunterooster on 2010-10-19
I have a Logitech Performance MX. The forward and back buttons are used for web browsing and file browsing in Windows and Linux alike. They allow you to go back and forth between current and previous pages/locations.

---

### Post by outleradam on 2010-10-19
^^ I know that. Why did you post?  Now you ruined a perfectly good 0 post attention getter.
 
They are not generating button press events and I need to figure out why. All other buttons are working.  these two are not generating events and therefore not able to be mapped.

---

### Post by ubunterooster on 2010-10-19
Another thread, [http://ubuntuforums.org/showthread.php?t=1600755](http://ubuntuforums.org/showthread.php?t=1600755), is trying to do something similar, I assume.

---

### Post by outleradam on 2010-10-19
There is no solution in that thread yet, but thank you, that is the same problem. :( 
 
10.10 crashed my X interface. When I reinstalled, I lost these two mouse buttons.

---

### Post by outleradam on 2010-10-19
Actually, that thread was completely unrelated.

See, here's the problem...   
all of the buttons work and generate button press events
```
adam@adam-desktop:~$ xev |grep -i button
ButtonPress event, serial 36, synthetic NO, window 0x4600001,
    state 0x10, button 1, same_screen YES
ButtonRelease event, serial 36, synthetic NO, window 0x4600001,
    state 0x110, button 1, same_screen YES
ButtonPress event, serial 36, synthetic NO, window 0x4600001,
    state 0x10, button 2, same_screen YES
ButtonRelease event, serial 36, synthetic NO, window 0x4600001,
    state 0x210, button 2, same_screen YES
ButtonPress event, serial 36, synthetic NO, window 0x4600001,
    state 0x10, button 3, same_screen YES
ButtonRelease event, serial 36, synthetic NO, window 0x4600001,
    state 0x410, button 3, same_screen YES
ButtonPress event, serial 36, synthetic NO, window 0x4600001,
    state 0x10, button 4, same_screen YES
ButtonRelease event, serial 36, synthetic NO, window 0x4600001,
    state 0x810, button 4, same_screen YES
ButtonPress event, serial 36, synthetic NO, window 0x4600001,
    state 0x10, button 5, same_screen YES
ButtonRelease event, serial 36, synthetic NO, window 0x4600001,
    state 0x1010, button 5, same_screen YES
ButtonPress event, serial 36, synthetic NO, window 0x4600001,
    state 0x10, button 6, same_screen YES
ButtonRelease event, serial 36, synthetic NO, window 0x4600001,
    state 0x10, button 6, same_screen YES
ButtonPress event, serial 36, synthetic NO, window 0x4600001,
    state 0x10, button 7, same_screen YES
ButtonRelease event, serial 36, synthetic NO, window 0x4600001,
    state 0x10, button 7, same_screen YES

```even 14,15 and 16.     

But```
adam@adam-desktop:~$ xev |grep -i button
``` 8 and 9 are not working!

---

### Post by outleradam on 2010-10-20
I found the problem.  

```
adam@adam-desktop:~/.gconf/apps/compiz/plugins/commands/allscreens/options$ cat ./*.xml
<?xml version="1.0"?>
<gconf>
    <entry name="run_command1_button" mtime="1287464037" type="string">
        <stringvalue>Button9</stringvalue>
    </entry>
    <entry name="run_command0_button" mtime="1287464037" type="string">
        <stringvalue>Button8</stringvalue>
    </entry>
</gconf>

```

I had installed a fresh copy of Ubuntu and copied my home dir over the top of my dir.  Well, Gconf was snagging my buttons up and porting them to commands 0 and 1.   The commands were 
```
xvkbd -xsendevent -text "\[XF86Back]"
```
and
```
xvkbd -xsendevent -text "\[XF86Back]"
```

however...
```
adam@adam-desktop:~$ xvkbd
The program 'xvkbd' is currently not installed.  You can install it by typing:
sudo apt-get install xvkbd

```

xvkbd was not installed so it was putting those commands in the background whenver I hit a button.


So basically my buttons were being snagged by compiz, ported to the command module, and outputted as a command to a program which was not installed.  

For the future, is there an output I could have checked to see this problem?   That xbkbd command had to have gone somewhere..  maybe a named pipe?

---

