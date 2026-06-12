---
title: "I Can't see my external hard drive!"
date: 2010-12-13
forum: New to Ubuntu
---

### Post by Bluebuddy on 2010-12-13
I installed ubuntu on my verbatim 500GB external HD using wubi. But when I boot up to ubuntu I can't see the hard drive. It should be mounted because ubuntu is installed on it. Also when I open XBMC I can view the HD. Please help. Thank you.

---

### Post by Chesamo on 2010-12-13
Ubuntu uses a different mounting system than Windows does. If you are running off the Ubuntu system, then the drive is mounted at / (open a file browser and hit CTRL+L, then type /). In the side panel of the file browser, you should also see an option for "Computer". In there, the drive is called "File System".

---

### Post by Bluebuddy on 2010-12-13
I did that before. All I see is the ubuntu insillation files.

---

### Post by guilleme on 2010-12-13
Does your home folder work? If it does, that should be your hard drive.
Now, if you're using ntfs or fat as your partition's file system, then you could boot on windows and then navigate to the drive, go to your ubuntu home folder, and check if your files are there. If they are, then your home folder is your drive (well, technically, the drive is the filesystem thing, but the home folder is where you can write and save stuff.)

---

### Post by Bluebuddy on 2010-12-13
Yes, my home folder works. I don't have a partion because it's installed useing wubi. So all my home folder files on ubuntu is saved in a .disk file in windows. Maybe I can't view the files on the external HD because I installed ubuntu on the same HD? I need to accsess files on that HD that I can normally see on windows.

---

### Post by amjjawad on 2010-12-14
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

I don't know much about wubi but check the above link, it might be helpful.

---

