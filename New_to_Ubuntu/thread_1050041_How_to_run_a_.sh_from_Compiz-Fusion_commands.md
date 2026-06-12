---
title: "How to run a .sh from Compiz-Fusion commands"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by 11010110 on 2009-01-25
Hi everyone, 

In Compiz-Fusion there is a feature that allows you to run terminal commands and give them a key binding. I want ctrl+alt+u to unmount my external hard drive. so i made a umount.sh file with a simple umount command (sudo umount /media/"My Book") and i was wondering how i could input a command into the CF commands section in order for it to open up a terminal and execute this script. i tried "gnome-terminal e- sh ~/Documents/UMOUNT.sh" but all that does is open up a terminal and nothing executes and the drive remains mounted. when i run the script contents alone or tell the terminal to run the script after it is open then everything works fine. I just want it streamlined and key bound. 

Am I even going about this the right way? sorry if i wasnt clear lol

Thanks in advance everyone.

---

### Post by emarkd on 2009-01-25
your script is software, so just makes sure it's set to be executable (chmod +x UMOUNT.sh) and then call it directly.  No need for the terminal.  That's what the first line of the script, the #!/bin/sh, handles.

---

### Post by 11010110 on 2009-01-25
i am an extreme novice at anything programming or script related lol so i just put in exactly what i listed above. How  do i set it to be executable? and what was the #!/bin/sh you referred to? 

thanks a lot for the reply!

---

### Post by emarkd on 2009-01-25
sure.  anytime you write a script, the first line should be

#!/bin/sh

this basically calls a shell to handle executing the script.  as you gain more experience, you'll learn that you can invoke other shells, but for now that line should get anything you want to do to work.  also, after you write the script and save it, go to your terminal and run:

chmod +x myscript.sh

or whatever you called it.  This makes the script executable and basically turns your text script into real, executable software.  Then you can just run it like you would any other software, which includes calling it directly from compiz.

---

### Post by 11010110 on 2009-01-25
ok i understand now. i added the #!/bin/sh and made it the first line of the script and then i did the chmod +x and everything seemed to work... but when i put the path into compiz-fusion it doesnt do anything. nothing comes up and the drive remains mounted. Am i doing something wrong?

Thanks again for the help thusfar.

---

