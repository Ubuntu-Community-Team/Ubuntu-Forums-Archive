---
title: "cron help backing up windows files"
date: 2009-04-04
forum: New to Ubuntu
---

### Post by codie72 on 2009-04-04
hello I am trying to backup my desktop from my windows partition mainly whats on my desktop

i have cron setup  to perform my backups to USB drive
there is not a lot of information just research papers
heres what i have in my cron file

0 * * * * tar cvjf - /home/codie/Desktop/ >/media/KINGSTON/backup.tar
0 * * * * tar cvjf - /media/disk/Documents and Settings/codie/Desktop/ >/media/KINGSTON/backupwin.tar

it performs the backup however when i try and open my tar file for the windows files it shows nothing
any ideas

---

### Post by codie72 on 2009-04-04
oh and I have this partition always mounted as soon as i log on i mount it -as i work on files from both windows and ubuntu they are shortcuted between these os's

---

### Post by hyper_ch on 2009-04-04
IMHO it's better to write a shell script that does the task and then add that shell script to cron instead of putting the full command into cron.

Those two crons you made, do those scripts actually work?

And you also may want to add logging to the commands you do... so for testing add a -v option.

---

### Post by codie72 on 2009-04-04
yea it makes both of the backups - the linux files work fine but the windows ones do not 

basicly opening the tar file for linux works perfectly
and the windows one show nothing in the file.

after i did my research for work i thought i would backup my system.
i wrote a script for work and it works
thanks for the help on that last night 2

i just thought it would be nice to backup my windows stuff at home 2

---

### Post by hyper_ch on 2009-04-04
I tend to think it's because you have SPACES in your path name. As said, best to put that into a script and also escape the space in the path name.

---

### Post by codie72 on 2009-04-04
yea i prob just had spaces after i copied and pasted it from my document

i will do i will just wack it in a script.

thanks again mate

i have a background in admin and programming   - ya think i should be getting the hang of this stuff pretty quick :)

have a good one

---

