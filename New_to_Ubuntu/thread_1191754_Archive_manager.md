---
title: "Archive manager"
date: 2009-06-19
forum: New to Ubuntu
---

### Post by govantim on 2009-06-19
I extracted a RAR file, now when going to PLACES it's telling me that Arhive Manager cannot open this type of file ( music, pictures video etc) :confused::confused: What have I done ??

---

### Post by bhadotia on 2009-06-19
> **govantim said:**
> I extracted a RAR file, now when going to PLACES it's telling me that Arhive Manager cannot open this type of file ( music, pictures video etc) :confused::confused: What have I done ??

First of all you tell us exactly what have you done! Where did you extract the file to and from where? What exactly are you trying to do now? Please be a little descriptive when posting threads. This helps in recognizing and solving the problem quickly.

---

### Post by gradinaruvasile on 2009-06-19
I think he means that if he clicks on Places from the upper taskbar he gets that error.

---

### Post by bhadotia on 2009-06-19
> **gradinaruvasile said:**
> I think he means that if he clicks on Places from the upper taskbar he gets that error.

Then try restarting the computer first.

---

### Post by govantim on 2009-06-19
Extracted RAR file from downloads to video, an option came up saying "open file with" and I added archive manager as a default I think, now when opening PLACES everything seems to be going through archive manager. Hope this confusing explanation helps.

---

### Post by Simian Man on 2009-06-19
I don't think it supports rar out of the box.  I remember having trouble with a rar file (who uses that file type anyway??).

Install the command line program "unrar" and use it as follows:
```

unrar e file.rar

```

You can also download 7zip which IIRC supports rars.

---

### Post by govantim on 2009-06-19
Tried restarting, still getting same when going to places

---

### Post by bhadotia on 2009-06-19
> **govantim said:**
> Extracted RAR file from downloads to video, an option came up saying "open file with" and I added archive manager as a default I think, now when opening PLACES everything seems to be going through archive manager. Hope this confusing explanation helps.

Simply change the open with to something else, for example, for video files change open with to Movie Player (or vlc!) and then all your videos will open in totem movie player (vlc). Similarly do for other file types.

---

### Post by govantim on 2009-06-19
Not happening, when opening places and right clicking anything, home folder. documents,music etc archive manager still coming up saying " archive type not supported "

---

### Post by bhadotia on 2009-06-19
> **govantim said:**
> Not happening, when opening places and right clicking anything, home folder. documents,music etc archive manager still coming up saying " archive type not supported "

Right click the item you want to open and then select properties and then go to "Open With" tab, now select the desired program you want to open the file with. Do similarly for others.

---

### Post by govantim on 2009-06-19
> **bhadotia said:**
> Right click the item you want to open and then select properties and then go to "Open With" tab, now select the desired program you want to open the file with. Do similarly for others.

wont let me do this, archive manager immediately comes up saying " archive type not supported ". Just upgraded to 9.04 jaunty thinking that a new upgrade would sort it, but to no avail.

---

### Post by govantim on 2009-06-19
Looks as though i've archived : Home Folder, Desktop, Documents, Music, Pictures and Video. How then would I un-archive them ????

---

### Post by carml on 2009-06-19
Can you explain all from the beginning i.e. what is the file are you trying to extract? To open a file .rar you need a package called unrar.:)

---

### Post by govantim on 2009-06-19
> **carml said:**
> Can you explain all from the beginning i.e. what is the file are you trying to extract? To open a file .rar you need a package called unrar.:)

I opened a file from downloads & it was a rar file, went to permissions and added open with archive manager, file extracted and went to videos. Now when opening places on the upper taskbar and clicking anything in the top box, archive manager pops up saying " archive type not supported " :confused:

---

### Post by bhadotia on 2009-06-19
> **govantim said:**
> wont let me do this, archive manager immediately comes up saying " archive type not supported ". Just upgraded to 9.04 jaunty thinking that a new upgrade would sort it, but to no avail.

Are you unable to select Properties menu by right clicking?

---

### Post by govantim on 2009-06-19
> **bhadotia said:**
> Are you unable to select Properties menu by right clicking?

Yes

---

### Post by bhadotia on 2009-06-19
> **govantim said:**
> Yes

Open a terminal (Applications>Accessories>Terminal) and post the output of these commands (replace username with your username):
```
ls -l /home
```
```
ls -l /home/username
```

---

### Post by carml on 2009-06-19
Can you open a terminal and type```
sudo apt-get install unrar
```.
You're going to be prompted for your password,write it even if you don't seen what are you typing (it's a security feature) and then post here the reseult of the command?

---

### Post by govantim on 2009-06-19
> **bhadotia said:**
> Open a terminal (Applications>Accessories>Terminal) and post the output of these commands (replace username with your username):
```
ls -l /home
```
```
ls -l /home/username
```

Still coming up " Unable to open documents " archive not supported

---

### Post by govantim on 2009-06-19
> **carml said:**
> Can you open a terminal and type```
sudo apt-get install unrar
```.
You're going to be prompted for your password,write it even if you don't seen what are you typing (it's a security feature) and then post here the reseult of the command?

unrar already the newest version

---

### Post by michy99 on 2009-06-19
1. Left click on a folder to bring up menu.
2. Select "Open with Other Application"
3. Select 'File browser"
4. Click 'Open'

That should fix it.

---

### Post by govantim on 2009-06-19
> **michy99 said:**
> 1. Left click on a folder to bring up menu.
2. Select "Open with Other Application"
3. Select 'File browser"
4. Click 'Open'

That should fix it.

If I left or right click archive manager immediately comes up saying it can't open the folder as the archive type is not supported.

---

### Post by michy99 on 2009-06-19
> **govantim said:**
> If I left or right click archive manager immediately comes up saying it can't open the folder as the archive type is not supported.

Ok, you have somehow messed up your file associations in nautilus. I'll have to do some research to see how to fix it.

---

### Post by bhadotia on 2009-06-19
> **govantim said:**
> Still coming up " Unable to open documents " archive not supported

No post what outputs the commands give here.

---

### Post by govantim on 2009-06-19
> **bhadotia said:**
> No post what outputs the commands give here.

left click places, I get the drop down menu, left or right click anything in the top box archive manager opens with a pop up with a no entry sign saying it could not open the desired menu ( music etc ) I then have to click the ok button which puts me back into archive manager

---

### Post by bhadotia on 2009-06-19
> **govantim said:**
> left click places, I get the drop down menu, left or right click anything in the top box archive manager opens with a pop up with a no entry sign saying it could not open the desired menu ( music etc ) I then have to click the ok button which puts me back into archive manager

Dude I think you misunderstood. Open a terminal and then copy and paste the following commands one by one:
```
ls -l /home
```
```
ls -l /home/username
```
In the above command replace username with your user name.

Now copy and paste the outputs of both the commands in your post here. To do this simply highlight the all the text in your terminal window and then right click and select copy (Ctrl-C does not work in the terminal Shift-Ctrl-C does) and then paste here as usual.

---

### Post by twright on 2009-06-19
Right, I know what you did. You have associated file system links with archive manager :lolflag:

To fix it you need to press Alt+f2, type nautilus, right click any folder then select open with another application and finally select nautilus.

Good luck :-)

---

### Post by michy99 on 2009-06-19
Ok, I have a couple of things that might work. First I need to see what you have in this file. In a terminal, enter this and post the result here.```
cat ~/.local/share/applications/mimeapps.list
```

---

### Post by govantim on 2009-06-19
> **bhadotia said:**
> Dude I think you misunderstood. Open a terminal and then copy and paste the following commands one by one:
```
ls -l /home
```
```
ls -l /home/username
```
In the above command replace username with your user name.

Now copy and paste the outputs of both the commands in your post here. To do this simply highlight the all the text in your terminal window and then right click and select copy (Ctrl-C does not work in the terminal Shift-Ctrl-C does) and then paste here as usual.

stephen@stephen-desktop:~$ ls -l /home
total 4
drwxr-xr-x 84 stephen stephen 4096 2009-06-19 18:45 stephen
stephen@stephen-desktop:~$ ls -l /stephen
ls: cannot access /stephen: No such file or directory
stephen@stephen-desktop:~$

---

### Post by govantim on 2009-06-19
> **michy99 said:**
> Ok, I have a couple of things that might work. First I need to see what you have in this file. In a terminal, enter this and post the result here.```
cat ~/.local/share/applications/mimeapps.list
```

stephen@stephen-desktop:~$ cat ~/.local/share/applications/mimeapps.list

[Added Associations]
video/x-msvideo=realplay.desktop;totem-gstreamer.desktop;
video/3gpp=totem-gstreamer.desktop;totem-xine.desktop;
image/jpeg=ooo-impress.desktop;
audio/mpeg=kde-kbtobexclient.desktop;
application/x-extension-bin=nautilus-cd-burner-open-iso.desktop;wine.desktop;file-roller.desktop;nautilus-autorun-software.desktop;
video/x-matroska=totem-xine.desktop;realplay.desktop;
application/x-cd-image=vlc.desktop;realplay.desktop;
application/x-executable=file-roller.desktop;wine.desktop;nautilus-autorun-software.desktop;
application/x-shellscript=wine.desktop;
application/x-ms-dos-executable=wine.desktop;
inode/directory=file-roller.desktop;nautilus-folder-handler.desktop;firefox.desktop;userapp-nautilus-IPRJVU.desktop;
stephen@stephen-desktop:~$

---

### Post by bhadotia on 2009-06-19
> **govantim said:**
> stephen@stephen-desktop:~$ cat ~/.local/share/applications/mimeapps.list

[Added Associations]
video/x-msvideo=realplay.desktop;totem-gstreamer.desktop;
video/3gpp=totem-gstreamer.desktop;totem-xine.desktop;
image/jpeg=ooo-impress.desktop;
audio/mpeg=kde-kbtobexclient.desktop;
application/x-extension-bin=nautilus-cd-burner-open-iso.desktop;wine.desktop;file-roller.desktop;nautilus-autorun-software.desktop;
video/x-matroska=totem-xine.desktop;realplay.desktop;
application/x-cd-image=vlc.desktop;realplay.desktop;
application/x-executable=file-roller.desktop;wine.desktop;nautilus-autorun-software.desktop;
application/x-shellscript=wine.desktop;
application/x-ms-dos-executable=wine.desktop;
inode/directory=file-roller.desktop;nautilus-folder-handler.desktop;firefox.desktop;userapp-nautilus-IPRJVU.desktop;
stephen@stephen-desktop:~$

Do this: In the terminal:
```
gedit ~/.local/share/applications/mimeapps.list
```
Remove these words :
```
  file-roller.desktop;firefox.desktop;userapp-nautilus-IPRJVU.desktop;
``` 
from the last line i.e.
```
 inode/directory=
```
Or simply remove this file , but you will loose all other custom associations. But looking at your other associations I find that they are also somewhat messed-up:D. So removing this file is best for you. Don't worry it will be automatically regenerated. To remove it give the following command:
```
rm ~/.local/share/applications/mimeapps.list
```

---

### Post by michy99 on 2009-06-19
Ok, I think we can fix this. Open the file for editing by entering```
gedit ~/.local/share/applications/mimeapps.list
```Find the last line that says```
inode/directory=file-roller.desktop;nautilus-folder-handler.desktop;firefox.desktop;userapp-nautilus-IPRJVU.desktop;
```Remove the part that says 'file-roller.desktop;' so it reads```
inode/directory=nautilus-folder-handler.desktop;firefox.desktop;userapp-nautilus-IPRJVU.desktop;
```Save the file and the reboot the computer. Hopefully this will fix it. If not, I have one other thing to try.

---

### Post by ugm6hr on 2009-06-19
This looks like your best bet.
> **bhadotia said:**
> 
```
rm ~/.local/share/applications/mimeapps.list
```

You have been adding and changing file associations incorrectly.

---

### Post by govantim on 2009-06-19
> **bhadotia said:**
> Do this: In the terminal:
```
gedit ~/.local/share/applications/mimeapps.list
```
Remove these words :
```
  file-roller.desktop;firefox.desktop;userapp-nautilus-IPRJVU.desktop;
``` 
from the last line i.e.
```
 inode/directory=
```
Or simply remove this file , but you will loose all other custom associations. But looking at your other associations I find that they are also somewhat messed-up:D. So removing this file is best for you. Don't worry it will be automatically regenerated. To remove it give the following command:
```
rm ~/.local/share/applications/mimeapps.list
```

---------------------------------------------------------------------------
stephen@stephen-desktop:~$ rm ~/. local/share/applications/mimeapps.list
rm: cannot remove `.' directory `/home/stephen/.'
rm: cannot remove `local/share/applications/mimeapps.list': No such file or directory

---

### Post by michy99 on 2009-06-19
No space between . and local

```
rm ~/.local/share/applications/mimeapps.list
```Also, you may have to reboot for it to take effect.

---

### Post by govantim on 2009-06-19
TO ALL CONCERNED, SORTED :lolflag:  I CAN'T THANK YOU ENOUGH FOR YOUR TIME AND YOUR PATIENCE, KEEP UP THE GOOD WORK, THANKS AGAIN  ):P

---

### Post by bhadotia on 2009-06-19
> **govantim said:**
> TO ALL CONCERNED, SORTED :lolflag:  I CAN'T THANK YOU ENOUGH FOR YOUR TIME AND YOUR PATIENCE, KEEP UP THE GOOD WORK, THANKS AGAIN  ):P

No problem. Anyway i was just getting bored of my foolish cousin irritating me;)

---

