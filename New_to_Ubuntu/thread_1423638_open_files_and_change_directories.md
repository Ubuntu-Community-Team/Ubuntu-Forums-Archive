---
title: "open files and change directories"
date: 2010-03-06
forum: New to Ubuntu
---

### Post by jklopez on 2010-03-06
[SIZE=2][COLOR=Black]I just installed ubuntu 9.10 [/COLOR][/SIZE][COLOR=Black]and i guess it's working because i'm connected to the net via usb wirelss adapter and on the desktop i see icons for my xternal harddrive , pendrive and any disk i put in the dvd drive and ubuntu did it all by it's self , i did'nt do a thing. I've read the pocket gi[/COLOR]ude and various pdf's and things on the ubuntu site and learned a little history ,basic commands ,the directories tree like structure and what not but i'm still confused about using the terminal.I can,t open anything with the terminal, point and click is easy but i want to learn how to open files,play misic,movies and programs and stuff with the terminal ,these are just a couple of the many things that i tried:
         I open a terminal and fist type: ls and get back..(blue is directoies and black is file...am i correct?).

            [COLOR=Blue]Desktop     Downloads   Music   Pictures  Templates
          
            Documents  [COLOR=Black]example.desktop      [COLOR=Blue]Public    Videos
                                         [COLOR=Black]
Then i type:  open /Desktop/maxdrive/musik[/COLOR][/COLOR][/COLOR][/COLOR][COLOR=Blue][COLOR=Black][COLOR=Blue][COLOR=Black] and get back...
                                             [COLOR=Red]
                                    XternalHard drive=maxdrive
music folder on X.H.D=musik


[COLOR=Black] ...could'nt get a file discriptor referring to console.
  or
     cd /Desktop   and get back ...  bash: cd: /Desktop:no such file or directory
  or
     ls /Desktop    and get back ... ls: cannot access /Desktop:no such file or directory. If anyone could give me  the proper command or syntac or start me in the right direction(please no more books) or online classes i will be more then grateful....please i can't stand windows 7anymore and i'm not going back..p.s. i cant make heads or tails of the man pages
o..i forgot...at linuxcommand.org theres a little practice script,hello world script and the second step is to give the shell script permission to execute the script by typing: chmod 755 (script_name) but when i do type:chmod 755 hello_world_test... i get back : chmod: cannot access `hello_world_test': No such file or directory ...help!!
[/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR]

---

### Post by patchwork on 2010-03-06
Try cd ~/Desktop or cd Desktop or cd /home/<user>/Desktop....

cd /Desktop  is not correct

---

### Post by mikeTherob on 2010-03-06
Or, if you're in the same directory as the item you wish to open, skip the /s altogether, just type the name of the file exactly as you see it when you enter ls.

---

### Post by jklopez on 2010-03-06
dude...thanxs....you guys rock  ,you have no idea..that solves my hello world script problem but how do i know what directories i have(just with ls) and how to open the rhythumbox music player from the terminal...jklopez

---

### Post by patchwork on 2010-03-06
To open rhythmbox, simply type it in the terminal.  To view your directories ( to explore) start with 
```
 cd /
```This will bring you to the root file system ( the highest level).  From here you can cd to directories and ls to view the contents.  Entering 

```
cd ..
``` will back you back up to the last directory

Happy Hunting

PS all binaries in /usr/bin (like rhythmbox or firefox ) can be started by typing the application name alone....this is equivalent to typing /usr/bin/rhythmbox

---

### Post by jklopez on 2010-03-06
thanx...thanx...thanx...thanx...your the man!!!

---

