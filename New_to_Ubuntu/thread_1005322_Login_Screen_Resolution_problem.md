---
title: "Login Screen Resolution problem"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by daci007 on 2008-12-08
hello ther...!
i'm daci i'm new in this forume,i just installed ubuntu 8.04 hardy,but i have problem in resolution ,the resolution of desktop work great,but the login screen too big,i can't even see wher i put the user name and the password,any tip to fix this.....
my screen : plug n play and my monitor has been 100% detected
graphic card : nevdia gforce 7200 GS

---

### Post by mapes12 on 2008-12-08
You need to edit your xorg.conf file. It's located: Places>Computer>Filesystem>etc>X11.

Back up the original before you start. Then to edit it Applications>Terminal type ```
sudo gedit /etc/X11/xorg.conf
```

Scroll down the page until you get to Section "Screen". Then under that a SubSection "Display". You will see just under this the line Virtual with a screen resolution like 1240  768 or something like that. You need to change those numbers to the screen res you want your login to be. VERY IMPORTANT - keep the numbers in exactly the same place as the originals. In other words don't change where they are positioned on the page. For example, if you want to change 1024 to 1288 insert your cursor between the 1 and the 0, enter 288, press delete 3 times to delete 024. Then save the file. 

Restart and your login screen should be fixed.

I had the very same problem in 8.04 and the above actions fixed the problem

---

### Post by daci007 on 2008-12-08
thanx a lot for help,i did just like you told me but i coudn't find the best resolution for my "plug n play " screen,i tried so many resolution but i coudn't find the best one for my login screen,can you give me a perfect 
resolution for my loging screen....and thanx again

---

### Post by alienexplorers on 2008-12-08
load startup manager from synaptic and run it.  Next edit /etc/gdm/gdm.conf and look for server-standard and add to the end of the line after audit, -dpi 96.....  Save and restart.

---

### Post by daci007 on 2008-12-08
thanx for help):P

---

