---
title: "unknown file on desktop"
date: 2010-03-02
forum: New to Ubuntu
---

### Post by audiomick on 2010-03-02
Hallo.
A computer that I look after has aquired a document on the desktop that can't be opened or removed.

It appeared in connection with plugging in the daughters phone via USB, and bears the model name of the phone as it's file name, i.e. M7500.volume.2
It cannot be opened by anything, can't be dragged into the trash or deleted with a right click, is not visible in /home/user/desktop in nautlius or gksu nautilus.

Apparently, the daughter could transfer files to the phone before this thing appeared, and since it has appeared, she can't anymore, and also can't move files to her mp3player, which was also possible before.

If I try and open it with gedit, it fails and shows the path 
x-nautilus-desktop:/// M7500.volume.2

Does anyone have an idea what this might be and how I can get rid of it?

---

### Post by Paddy Landau on 2010-03-02
A similar thing happened to me. It sounds silly, but I restarted the computer and it went away.

---

### Post by audiomick on 2010-03-02
Thanks Paddy. Unfortunately this one has been hanging around for a while...:(
Anyone else?

---

### Post by Sir Jasper on 2010-03-02
Hi audiomick,

I believe your knowledge is greater than mine, but have you tried:
sudo rm -f (path to file)? I tend to drag and drop the file or folder [-r] to the terminal.

My regards

---

### Post by Arijit_Kundu on 2010-03-02
can you right click on it and see the propertise, what kind of file it is?

---

### Post by Arijit_Kundu on 2010-03-02
may be this will help
[http://ubuntuforums.org/showthread.php?t=1105695]("http://ubuntuforums.org/showthread.php?t=1105695")

---

### Post by fatality_uk on 2010-03-02
G'day Mick. Was it a Samsung M7500?
When it's plugged in and you type lsusb -v is it in that list?

---

### Post by sailor2001 on 2010-03-02
have you tried renaming the file with a different extension?

---

### Post by audiomick on 2010-03-02
> **Sir Jasper said:**
> Hi audiomick,

[COLOR=Red]I believe your knowledge is greater than mine[/COLOR], but have you tried:
sudo rm -f (path to file)? I tend to drag and drop the file or folder [-r] to the terminal.

My regards
Dunno about that...;)
I tried
```
sudo rm path/to/file
```with no success, but not the -f option. I will look into that.

[QUOTE=Arijit_Kundu]can you right click on it and see the propertise, what kind of file it is? 

  may be this will help
[http://ubuntuforums.org/showthread.php?t=1105695](http://ubuntuforums.org/showthread.php?t=1105695)  [/QUOTE]
can't get to see the properties any way I know. Right click shows the name, but no file type and unknown permissions.

I am aware of the udev rules thing, and you are right, maybe that will regain the access. I couldn't try the "lsusb" today, but I will next time I am where the computer is.

[QUOTE=fatality_uk]G'day Mick. Was it a Samsung M7500?
When it's plugged in and you type lsusb -v is it in that list? 	[/QUOTE]
yes, it is that phone, but as I mentioned, unfortunately I couldn't do a "lsusb" today. Are you aware of any specific issues pertaining to that phone?

[QUOTE=sailor2001]have you tried renaming the file with a different extension? 	[/QUOTE]I didn't succeed in doing that, although I am not sure if I did it right. I need to do that on my machine to make sure I what I think should work really does. That problem is that I have no icons on my desktop, and do name changing in nautilius, but the file in question doesn't show up in nautilus at all, even via "gksu nautlius".

Thanks for the replies so far. :p

---

### Post by Sir Jasper on 2010-03-02
Hi again,

sudo rm -f /home/audiomick/Desktop/M7500.volume.2

Is what I meant by (path to file).

If I had that file on my desktop I would usually drag and drop the location into the terminal as my typing is not so hot.

Good luck

---

### Post by philinux on 2010-03-02
@audiomick

Try running fsck from the recovery mode.

```
fsck -v /dev/sdxX
```

Where sdxX is your home partition or root if you dont have a separate home.

---

### Post by Paddy Landau on 2010-03-02
I clutching at straws here, but I would like to eliminate the obvious.

[LIST]
[*]Does it show in your Places menu?
[*]Is the phone still plugged in (I presume not)?
[*]Would you look at the file /etc/fstab and see if it contains anything pertaining to the phone.
[/LIST]
Also, go to a terminal, and use the following two commands (note the capitalisation).
```
cd ~/Desktop
ls -lA | fgrep -i m75
```I don't expect it to list anything, but if it does, post the output.

---

### Post by audiomick on 2010-03-02
> **Sir Jasper said:**
> Hi again,

sudo rm -f /home/audiomick/Desktop/M7500.volume.2

Is what I meant by (path to file).

If I had that file on my desktop I would usually drag and drop the location into the terminal as my typing is not so hot.

Good luck
The drag and drop thing might be worth a go. I tried to open the file with gedit to see what it would do or if it would show me anything. I couldn't open it and it quoted a path in the error message along the lines of "x-ubuntu-desktop-nautilus:/// M7500.volume.2". I am not sure of it exactly, and can't check again as the computer is at the owner's place. It was, however, a path that I had never seen and couldn't make any sense of. I will try the drag and drop thing though.

[QUOTE=philinux]Try running fsck from the recovery mode.[/QUOTE]do you suspect data corruption, or do you think that the -v might tell me something? The system does have a separate /home.

[QUOTE=Paddy Landau]```
ls -lA | fgrep -i m75
```[/QUOTE]that should print out the path, right? Worth a try...
I didn't look for it in Places specifically, but I don't think it was there. I will check the fstab. No, the phone wasn't plugged in.

I will try and get back to the computer within the next couple of days and see if I can make any progress. If anyone else has an idea, I would be pleased to hear it.
Once again, thanks for the replies.

---

### Post by LewRockwellFAN on 2010-03-03
Maybe you could just boot from another OS (possibly the live CD you probably installed with) and delete it from there?

---

### Post by 3rdalbum on 2010-03-03
I think the icon is a figment of Gnome's imagination, and you won't be able to drag it to the terminal or get rid of it.

Does the icon leave the screen when you unmount the phone?

---

### Post by audiomick on 2010-03-03
> **3rdalbum said:**
> I think the icon [COLOR=Red]is a figment of Gnome's imagination[/COLOR], and you won't be able to drag it to the terminal or get rid of it.

Does the icon leave the screen when you unmount the phone?
I am pretty sure that this sums it up well. The icon is there all the time, whether the phone is plugged in or not, through repeated restarts.

---

### Post by MinimalBin on 2010-03-03
Do a *file* check on it and let us know what kind of file is it.

```
file <file>
```

---

### Post by Pritamsng on 2010-03-03
its was happened with me also..

---

### Post by Paddy Landau on 2010-03-03
> **audiomick said:**
> [QUOTE=philinux;8905625]Try running fsck from the recovery mode.do you suspect data corruption, or do you think that the -v might tell me something? The system does have a separate /home.[/QUOTE]
Run it on both partitions (root and home), perhaps from a Live CD. You may want to add some extra options:
```
fsck -CMfv /dev/sda1 /dev/sda2
```Obviously, replace [FONT=Courier New]sda1[/FONT] and [FONT=Courier New]sda2[/FONT] with the correct partition names. If you're not sure of the partition names, let us know before you run the command.

---

### Post by audiomick on 2010-03-03
> **MinimalBin said:**
> Do a *file* check on it and let us know what kind of file is it.

```
file <file>
```
Thanks for that, didn't know that one. I will try it when I get back to the computer in question.

[QUOTE=Paddy Landau]Run it on both partitions (root and home), perhaps from a Live CD. You may want to add some extra options:
     Code:
     fsck -CMfv /dev/sda1 /dev/sda2 
[/QUOTE]
Thanks Paddy, I'll try that too. What does the -f option do? I can't see it in the man page...

---

### Post by Paddy Landau on 2010-03-03
> **audiomick said:**
> What does the -f option do?
Look at the manual for e2fsck. It forces a check even if the file system seems clean. Valid for ext2, ext3 and ext4 file systems.

---

