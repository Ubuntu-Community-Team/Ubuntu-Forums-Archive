---
title: "File Sharing &amp; Permissions"
date: 2008-09-09
forum: Networking &amp; Wireless
---

### Post by jdorenbush on 2008-09-09
I setup file sharing on my Ubuntu running desktop and laptop machines (which was very easy to setup). However when I drag files over from my laptop to my desktop I run into permission problems on my desktop. I am unable to modify these files.

Is there a quick fix to these permission problems?

---

### Post by Iowan on 2008-09-09
Which filesystem did you use to share files, and what does the **mount** command look like?

---

### Post by jdorenbush on 2008-09-09
> **Iowan said:**
> Which filesystem did you use to share files, and what does the **mount** command look like?

Umm. How do I determine those things? 

Sorry, I am still in Ubuntu-Noob-Training.

---

### Post by Iowan on 2008-09-09
I love it when I get disconnected in the middle of a post and lose the whole thing...

Sorry about the blunt questions.  When you shared the files, you were *probably* given an option to select NFS, FPT, SSH, or Windows Network (Samba).  The mount may have been added to your **/etc/fstab** file.  There are several options which may have affected how the file was shared - username in particular.  If the mount was shared as a different user (or root) you would have problems accessing it.  Sometimes the files are mounted read-only - which would cause problems modifying the files.  You can check the contents via **less /etc/fstab** which may/not reveal any new information.

> **jdorenbush said:**
> Is there a quick fix to these permission problems? You could probably "change owner" (chown) of the files, but you'd need to do it for each file every time you copied one.

---

### Post by jdorenbush on 2008-09-09
I guess maybe I should be more specific of how I set up the file sharing.

On desktop machine:
- In home folder I right clicked on my "Work" folder and clicked 'Sharing Options'.
- A dialog popped up called, 'Folder Sharing'.
- I checked all 3 options.
[SIZE="1"]1. Share this folder
2. Allow other people to write in this folder
3. Guest access[/SIZE]
- Then another dialog popped up and I choose to 'Choose Permissions Automatically'.

On laptop machine:
- I went to Places > Network
- I saw my desktop machine icon. I clicked on it. Then I saw my, "Work" folder.
- I dragged files from my laptop to my desktop folder, "Work".
- Everything transfered just fine.

Back to my desktop machine:
- Now all the files/folders I copied are Locked and I am not the "Owner".

---

### Post by Iowan on 2008-09-09
I lack experience sharing files that way...
As far as permissions go, my old-school suggestion would be to use a terminal to check the permissions.  ```
cd ~/Desktop
ls -al
```

---

### Post by jdorenbush on 2008-09-09
total 16
drwxrwxrwx  4 jeff jeff 4096 2008-09-09 18:58 .
drwxr-xr-x 46 jeff jeff 4096 2008-09-09 19:03 ..
drwxr-xr-x  6 jeff jeff 4096 2008-09-09 18:59 Icons
drwxr-xr-x 37 jeff jeff 4096 2008-09-09 18:58 Themes

Thats what the output was when I checked permissions in my shared folder. What way do you share files? I like this way because it is really easy.

---

### Post by cariboo on 2008-09-09
Hit Alt-F2 and type:

```
gksu nautilus
```

Enter your password when asked, By doing this you are opening Nautilus as the superuser (root) you should be able to navigate to the folders on your desktop and change permissions and ownership.

Jim

---

### Post by jdorenbush on 2008-09-09
> **cariboo907 said:**
> Hit Alt-F2 and type:

```
gksu nautilus
```

Enter your password when asked, By doing this you are opening Nautilus as the superuser (root) you should be able to navigate to the folders on your desktop and change permissions and ownership.

Jim

That worked, but its lame that each time I transfer files I'll have to change permissions. I guess that is just how it works??

---

### Post by forger on 2008-09-09
In order to be able to transfer files and use them properly, your userid and groupid numbers have to be the same for the laptop and the desktop user.
To see your file's UID/GID:
```
ls -l
ls -ln
```
> drwxr-xr-x  2 [COLOR="Red"]1000 1000[/COLOR]   4096 2007-07-14 19:59 Videos

To see your UID/GID:
```
id
```

Something like this:
**[COLOR="Red"]WARNING! Will break stuff, will have problems with permissions in /home/username directory!![/COLOR]**
```
sudo groupmod -g 1002 $USER
sudo usermod -u 1002 -g 1002 $USER
```
(you have to log out and log back in)

---

### Post by jdorenbush on 2008-09-09
> **forger said:**
> In order to be able to transfer files and use them properly, your userid and groupid numbers have to be the same for the laptop and the desktop user.
To see your file's UID/GID:
```
ls -l
ls -ln
```


To see your UID/GID:
```
id
```

Something like this:
**[COLOR="Red"]WARNING! Might break stuff, use at your own risk!![/COLOR]**
```
sudo groupmod -g 1002 $USER
sudo usermod -u 1002 $USER
```
(you have to log out and log back in)

I REALLY wish I would have read this after you edited your post. That WARNING would have came in handy earlier.

I need help getting both my systems back up and running. I am using a friends computer to type this message. After logging out and back in on my desktop and laptop I ran into TONS of errors. Its a total mess. Help :(

After clicking through all the errors messages I ended up on a desktop w/o any panels, just my desktop icons. The styling of the environment looks like something from Windows 98. I can't even press a key w/o getting an error message, so it is impossible to type. I hit any key and I am returned with an error message.

EDIT: Now when I reboot and login, it just goes to an all white screen, nothing more. I have a completely nonfunctional system now.

EDIT 2: I started a new thread. I don't believe this is Networking related anymore.
[http://ubuntuforums.org/showthread.php?t=915576](http://ubuntuforums.org/showthread.php?t=915576)

I really hope I can get this fixed soon. My computers are completely unusable for the time being.

---

### Post by forger on 2008-09-10
I thought of the risks after I typed it, sorry
Boot using a live cd, and mount your root partition, change the **etc/passwd** and the **etc/group** files, there are your userid and groupid

I think I know what the problem was, I edited the command, but never mind, don't try it again, let's get your computer up and running

---

### Post by jdorenbush on 2008-09-10
See, [http://ubuntuforums.org/showthread.php?t=915576](http://ubuntuforums.org/showthread.php?t=915576)

"What is a Live CD? How do I mount to the root, change the files and all that? I am a real noob so I don't understand all the commands yet."

---

### Post by john q. public on 2008-09-10
cariboo907 your the greatest!!!

i have been punching in code, getting errors, blah blah... added a new hard drive the other day, knew there had to be an easier way.... now i can use my new hdd... 

once again... thank you... i was beginning to question how much i like ubuntu....

thank you thank you thank you....

if you ever get to cleveland, ill buy you a beer!

D

---

### Post by jdorenbush on 2008-09-12
So... back to file sharing.

Now for some reason file sharing isn't working at all.

I have a brand new install of Ubuntu Hardy on my desktop.

And [after fixing my ID # problem]("http://ubuntuforums.org/showthread.php?p=5777879"), I have a repaired version of Ubuntu Hardy on my laptop.

*Keep in mind the steps below worked fine before, but for some reason, they don't work now.*

Desktop:
- Right click on folder > Sharing Options
- Tick all 3 boxes

Laptop:
- Places > Network

...nothing shows up though anymore.

---

### Post by TXPhisher on 2008-09-28
I think what he was getting was a write permission error trying to transfer files from the windows pc to the linux home folder share.  When you right click and share the folder, it does not allow write access -- or at least it didn't when I tried it (although I did not enable the final 2 boxes, only share this folder)

Sooo I think the solution would be in a samba configuration file somewhere.  The goal being to enable read/write not just read file sharing of the home folder.

I'm currently digging on this, I'll let you know if I find anything.

edit: I forgot to add, after checking the share this folder box, you need to log out and back in for the changes to take effect.

---

### Post by TXPhisher on 2008-09-28
Alright I figured out a workaround.
1) Open up a console and type 'sudo gedit /etc/samba/smb.conf'
2) Scroll towards the bottom and there is a section on home folder file sharing, uncomment from the following lines:
 comment = Home Directories 
browseable = yes 
read only = no<--Change this to no
create mask = 0700
directory mask = 0700 

Now save and quit, type 'sudo /etc/init.d/samba restart' into the console, and get on the windows machine.  Start -> Run -> \\ip of server\username ie. \\192.168.1.2\john, Login using your linux username/password.

Things should work from there.  You can also go ahead and uncheck the file share you did manually by right clicking the drive, it's all been done manually now. :guitar:

---

