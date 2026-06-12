---
title: "Video files with samba windows-ubuntu, some work some don't"
date: 2007-07-10
forum: Networking &amp; Wireless
---

### Post by Osamabingandhi on 2007-07-10
I've made my ubuntu machine public so i don't have to punch my password everytime i want to access files from my windows machine.

After that i have problem accessing some video-files on my ubuntu-computer. I use windows-media center and want to play all my downloaded videos from ubuntu.

Anyone got any ideas what is wrong? I can play most videos but some just don't work. Is there any settings in windows or ubuntu that makes some files not accessible from windows. All files on windows work under ubuntu and i can do anything, but not the other way...

Any suggestions?

my smb.conf has this at the bottom:

[ubuntu]
comment = Public Folder
path = /home/ubuntu
available = yes
browsable = yes
public = yes
create mask = 0777
directory mask = 0777
force user = nobody
force group = nogroup
writable = yes

and this somewhere:

security = share

---

### Post by Gausian on 2007-07-10
why not just tell windows to remember your password.  then your not public and dont have to punch in your pass everytime.

---

### Post by Osamabingandhi on 2007-07-10
I'm protected by a router but i don't think the public part is the problem. Something else is not as it should....I have to log in manually when i start ubuntu and startx....that is also annoying but ubuntu i use and sit infront of, window is just for games and movies from my sofa

---

### Post by EndPerform on 2007-07-10
Samba *should* be starting by default, so you should just need to power on your Ubuntu box.  As far as some of the videos not working from Ubuntu to Windows, you could try to copy the files from Ubuntu to the local Windows machine and see if they play.  If not, then you might be missing a codec on Windows.

---

