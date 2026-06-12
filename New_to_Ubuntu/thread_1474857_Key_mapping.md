---
title: "Key mapping"
date: 2010-05-06
forum: New to Ubuntu
---

### Post by saamirahman on 2010-05-06
Hi I'm using Lucid Lynx on an old Toshiba Satellite M55. The '1' key  doesn't work on this computer, so I'd like to configure a key  combination that prints '1' on the screen. For example, if I press  ALT+2, the screen should print '1'. Any help would be much appreciated. I  am currently using character map to copy '1' onto the clipboard and  CTRL+v to print '1'...which is of course very inconvenient and also  hilarious. :P

Thanks!

---

### Post by Sef on 2010-05-06
Moved to ABT.

---

### Post by dracayr on 2010-05-06
You might want to read this: [http://www.columbia.edu/~djv/docs/keyremap.html](http://www.columbia.edu/~djv/docs/keyremap.html)

I'll post more once I figure out how this works in your case ;)

EDIT2: don't follow EDIT1. apparantly there's only a definition for what should happen when a key is pressed with shift, not when it's pressed with alt. You could, though, make the caps lock key into your new 1 (or maybe shift+caps lock). To do this, find out your keycode of caps lock by running xev in a terminal, focusing the appearing window, and pressing caps lock. On the terminal, some output should appear, and among that the keycode (mine is 66). to change caps lock into 1:```
xmodmap -e "keycode  66 = 1 exclam 1 exclam onesuperior exclamdown onesuperior"
```. That will make caps lock into a 1 with full functionality, including exclamation mark, etc. However, on my computer, for some reason, the caps functionality is still enabled (it will output a 1 and produce uppercase letters). You'd have to change that somewhere in gnome probably. For that reason, I'd change the context menu button to 1 (who needs it anyay?). (on my keyboard, that's keycode 135.




EDIT1 (use the above method, not this): Ok, so I think I know how it works now:
enter 'xmodmap -pke' (without the quotes) in a terminal. One line of the output should look like this:
keycode  11 = 2 quotedbl 2 quotedbl twosuperior oneeighth twosuperior

now the different words after the equality sign ('2', 'quotedbl', '2', and so on) are the results you get when you press the key '2' with different modifiers. I'm not sure which one is the word responding to alt, and it's probably different on your keyboard anyway, so you'll have to experiment there. You can now copy that line, replace one of the words (the one you think corresponds to Alt) with 1. then execute ```
xmodmap -e "*modified line here*"
``` in the terminal (note the quotes around the line). I'f you've made an error (replaced the wrong word), then you can always use that command with the unmodified line to set the settings back to default.

dracayr

---

### Post by saamirahman on 2010-05-07
Thanks Dracayr!

I changed the context menu to print 1. How can I make the change permanent, and should I ever want to revert to defaults, how would I do that?

---

### Post by dracayr on 2010-05-07
execute this command in your home directory:```
xmodmap -pke > .Xmodmap 
```, then edit the newly created file .Xmodmap to include your changed key code. (to revert to the old settings, simply deleting the file should work, but if you want, you can also backup the unchanged file). I saw that .Xmodmap both with a capital X or with a lower-case x. So either it doesn't matter, or you'll have to experiment.

dracayr

---

