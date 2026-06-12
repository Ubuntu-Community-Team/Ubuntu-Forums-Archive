---
title: "help on how to make shell script for cmus executable"
date: 2011-09-05
forum: New to Ubuntu
---

### Post by moonpoppy on 2011-09-05
hi,

i want to make this on-screen notifications script executable in cmus. i can't figure out from the instructions in the script what i'm supposed to do. it tells you to sh and  alter the file but the instructions are for someone who understands coding (i only understand "hello world" and calendar). i'm not even sure if i'm supposed to chmod both the py and sh files....

i love cmus. i don't want to use another app. moc downloads but wont open on my comp - i must be  missing dependencies but i have no idea what...so cmus it is... i have a huge music collection and it reads it so quickly and great for radio streams. it leaves such a little footprint on the computer :).  and the shortcuts are a pleasure to use. :)

for me it's just missing notifications

here's the [script]("http://cmus.sourceforge.net/wiki/doku.php?id=status_diplay_notify_send.py"). 

i'm not sure if it's protocol to paste it here....if it is, please tell me and i will...

---

### Post by sisco311 on 2011-09-05
Please post a link to the instructions you are following.

---

### Post by moonpoppy on 2011-09-05
here's the[B] [script]("http://cmus.sourceforge.net/wiki/doku.php?id=status_diplay_notify_send.py").

[/B][http://cmus.sourceforge.net/wiki/doku.php?id=status_diplay_notify_send.py](http://cmus.sourceforge.net/wiki/doku.php?id=status_diplay_notify_send.py)

---

### Post by cwsnyder on 2011-09-05
The script which you are trying to make executable is a Python script, so you will have to install the Python language from the repositories.

To make the script executable after installing the script and other parts installed according to the instructions, open a terminal window (Menu >> Accessories >> Terminal) and enter the following instructions to open a root enabled Places window ```
sudo nautilus
``` You will have to enter your password when prompted after pressing the Enter key. In the newly opened window, navigate to find your script. You may need to select **V**iew >> Show Hidden Files from the window menu to find the folder where your script is stored.  Select your file, right click, select **P**roperties from the pop up menu, select the *Permissions* tab, and click on the box next to *Allow this file to run as a program*.  This will allow your shell script to execute.
> **moonpoppy said:**
> hi,

i want to make this on-screen notifications script executable in cmus. i can't figure out from the instructions in the script what i'm supposed to do. it tells you to sh and  alter the file but the instructions are for someone who understands coding (i only understand "hello world" and calendar). i'm not even sure if i'm supposed to chmod both the py and sh files....

i love cmus. i don't want to use another app. moc downloads but wont open on my comp - i must be  missing dependencies but i have no idea what...so cmus it is... i have a huge music collection and it reads it so quickly and great for radio streams. it leaves such a little footprint on the computer :).  and the shortcuts are a pleasure to use. :)

for me it's just missing notifications

here's the [script]("http://cmus.sourceforge.net/wiki/doku.php?id=status_diplay_notify_send.py"). 

i'm not sure if it's protocol to paste it here....if it is, please tell me and i will...

---

### Post by moonpoppy on 2011-09-05
thank you, but let me elaborate:

1. Copy cmus_desktop_notify.py to ~/.cmus/ and make executable.

do i change the file ending to .sh? or do it i keep it .py?

---

### Post by AlphaLexman on 2011-09-05
Use the code...
```
chmod +x status_display_notify_send.py
```[B]
EDIT:[/B] Change the filename as needed.
**EDIT2:** the filename extension does not matter due to the shebang (#!) in the script.

---

### Post by moonpoppy on 2011-09-05
i did everything you said.
the .sh commands work when i run them in terminal. but there is no notifcation for cmus.


i :save in cmus. but am i supposed to save the file that i :set? when i try to save the file i just set i get an error. it also won't allow me to save nothing, it automatically tries to save the file i set.

thank you again.
[FONT=monospace]
[/FONT]3. Set the status_display_program variable in cmus (with YOUR homedir!)   

    :set status_display_program=/home/user/.cmus/status_display_program.sh 

4. Enjoy desktop notifications from cmus! Be sure to :save.

---

### Post by moonpoppy on 2011-09-05
Error: saving '/home/myusername/status_display_program=/home/myusername/status_display_program.sh'

this is what i get in cmus. like i said the script works fine in terminal. i retitled the script that you are instructed to write to match the name of the .py script to make it .sh properly. and it again it does it in terminal, but cmus won't accept it.

---

### Post by AlphaLexman on 2011-09-05
What is the exact code you are using to execute the program ??

---

### Post by moonpoppy on 2011-09-05
1. Copy cmus_desktop_notify.py to ~/.cmus/ and make executable. 

the name of the file you download is status_display_notify_send.py
 
sudo cp status_display_notify_send.py ~/.cmus/status_display_notify_send.py

since it's vague which version of status_display_notify_send.py is supposed to be executable

in ~$ chmod +x status_display_notify_send.py
~$ ./status_display_notify_send.py
the file opens in terminal
then i cd to cmus
cmus$ chmod +x status_display_notify_send.py
sh it and the file opens in terminal


   2. Create ~/.cmus/status_display_program.sh with these contents       

i open gedit (no gksudo)
copy and paste

 #!/bin/sh                                                            
 ~/.cmus/cmus_desktop_notify.py "$*" &                                 

then change cmus_desktop file script name to match name of file
status_display_notify_send.py  "$*" &                                 

(should i rename orginal file?)

save as status_display_program.sh in the .cmus folder

then in terminal cmus$ chmod +x status_display_program.sh 

cmus$ ./status_display_program.sh 

it's fine.


 3. Set the status_display_program variable in cmus (with YOUR homedir!)
so in cmus:

  :set status_display_program=/home/myusernamehere/.cmus/status_display_program.sh 
   

 4. Enjoy desktop notifications from cmus! Be sure to :save.  

:save status_display_program=/home/user/.cmus/status_display_program.sh 

then i get Error: saving '/home/myusername/status_display_program=/home/myusername/status_display_program.sh'

should i rename the file i downloaded to what its called in step 1?
which version of the py file should i chmod? does it matter?
why won't is save in cmus?
any more insight is greatly appreciated

thanks

---

### Post by moonpoppy on 2011-09-06
finally it works
no need to :save
changed name of file i downloaded to name of file in script
did chmod of .py and .sh files in .cmus directory from home directory

it doesn't create notification for tracks on radio :(
but it works!

---

