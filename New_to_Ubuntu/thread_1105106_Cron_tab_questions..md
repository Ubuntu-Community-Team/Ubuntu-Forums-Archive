---
title: "Cron tab questions."
date: 2009-03-24
forum: New to Ubuntu
---

### Post by Odd_sam on 2009-03-24
I know that using cron is a way to run terminal commands at certain time intervals. However actually using it is unknown to me. I've searched the internet for a bit and looked for a way to execute 

killall wvdial

(specifically at 6:20 AM) however nothing useful has come up. If someone could show me how to add this command to the crontab and give a brief explanation that would be great. Thanks. Also would there would be some issues with wvdial not dying when the command is executed because I know from time to time I have needed to use sudo killall wvdial to actually kill it.
(Ubuntu 8.10)

---

### Post by Bachstelze on 2009-03-24
To edit root's crontab:

```
sudo -i
crontab -e
```

That will fire up nano with root's crontab in it. Now to execute your command everyday at 6:20 am, add this to it

```
20 6 * * * /usr/bin/killall wvdial
```

then save the file and exit your root shell.

---

### Post by MrWES on 2009-03-24
> **Odd_sam said:**
> I know that using cron is a way to run terminal commands at certain time intervals. However actually using it is unknown to me. I've searched the internet for a bit and looked for a way to execute 

killall wvdial

(specifically at 6:20 AM) however nothing useful has come up. If someone could show me how to add this command to the crontab and give a brief explanation that would be great. Thanks. Also would there would be some issues with wvdial not dying when the command is executed because I know from time to time I have needed to use sudo killall wvdial to actually kill it.
(Ubuntu 8.10)

First lets change your default editor to something a bit more friendly to new users:

```
sudo update-alternatives --config editor
```

Choose #3 nano

Now edit the root cron

```
sudo crontab -e
```

On a new line add

```
20 6 * * * killall wvdial
```

Save the file.

You can check cron listing with

```
sudo crontab -l
```

That will run killall wvdial everyday  at 6:20am

Bill

---

### Post by finer recliner on 2009-03-24
> **HymnToLife said:**
> To edit root's crontab:

```
sudo -i
crontab -e
```

That will fire up nano with root's crontab in it. Now to execute your command everyday at 6:20 am, add this to it

```
20 6 * * * /usr/bin/killall wvdial
```

then save the file and exit your root shell.

just to elaborate a little bit, HymnToLife's line basically reads: on the 20th minute of the 6th hour of every day of every month on every day of the week, run the command "/usr/bin/killall wvdial"

hope that helps!

---

### Post by lovinglinux on 2009-03-24
If you want to easily setup crontab then install gnome-schedule. It's a graphical interface for crontab. 

```
sudo apt-get install gnome-schedule
```

---

### Post by Odd_sam on 2009-03-24
It works thanks all! Makes perfect sense now. Although I would not have thought to include /usr/bin/ in the command. The graphical editor is a great find I'd prefer to use that in the future just to know that I didn't screw some syntax up.

---

### Post by mashedbear on 2009-03-28
Hi - I want to use cron to run an rsync command everyday at a set time to backup /home to a second disk.

I can run this at the command line using sudo and everything works fine: 
```
sudo rsync -av --logfile=/var/log/$(date +%Y%m%d)rsync-backupHOME.log --ignore-errors --progress --delete /home /mnt/disk2/gandalf_home_backup
```

To run this from the cron do I simply add this to the root cron (which i think would be ```
sudo crontab -u root -e 
```)

Or is it better to create a bash script and set cron to execute the script. In which case if I am using sudo in the script - how would I configure cron to avoid needing to put a password in each time cron runs the script? 

Hope this makes some sense!

Thanks for any help

---

