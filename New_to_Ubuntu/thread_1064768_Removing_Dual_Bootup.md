---
title: "Removing Dual Bootup"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by Ant01 on 2009-02-09
My windows is not booting from the Grub so I want to remove windows from the dual bootup and rather run it under virtual boot. Can someone please help me in how to change the grub not to load in dual bootup mode?

---

### Post by Nepherte on 2009-02-09
You could remove the windows entry in grub. Open it:
```
gksudo gedit /boot/grub/menu.list
```
and remove the windows entry. It typically looks something like this:
```
# (4) Windows
title Windows XP Professional SP3
rootnoverify (hd0,0)
makeactive
chainloader +1
```
You could however try to fix the problem. What error do you get when trying to boot of the windows partition?

---

### Post by lovelyvik293 on 2009-02-09
please correct me if m wrong:-
1. you have a dual boot system.
2. with windows not booting with the grub.

Now if the windows in not booting with the grub then your grub is not in dual boot.

---

### Post by Ant01 on 2009-02-09
> **Nepherte said:**
> You could remove the windows entry in grub. Open it:
```
gksudo gedit /boot/grub/menu.list
```
and remove the windows entry. It typically looks something like this:
```
# (4) Windows
title Windows XP Professional SP3
rootnoverify (hd0,0)
makeactive
chainloader +1
```
You could however try to fix the problem. What error do you get when trying to boot of the windows partition?

I was having problems with my windows, i think it was corrupt so I ran repair on the installation disk again. Now when I click on the windows on Grub, it starts to load then bombs out and reboots

---

### Post by lovelyvik293 on 2009-02-09
You can wipe out the windows installation with the partition editor and then remove the grub entry as Nepherte told in earlier post.

---

### Post by Ant01 on 2009-02-09
> **Nepherte said:**
> You could remove the windows entry in grub. Open it:
```
gksudo gedit /boot/grub/menu.list
```
and remove the windows entry. It typically looks something like this:
```
# (4) Windows
title Windows XP Professional SP3
rootnoverify (hd0,0)
makeactive
chainloader +1
```
You could however try to fix the problem. What error do you get when trying to boot of the windows partition?
[B]
I tried editing the grub menu but get a blank menu.lst?[/B]

[IMG]http://i254.photobucket.com/albums/hh118/AntoineMuskat/ubuntugnome.jpg?t=1234190471[/IMG]

---

### Post by lovelyvik293 on 2009-02-09
The file is menu.lst not menu.list.

---

### Post by Ant01 on 2009-02-09
Thats what I got (as shown above), but there seems to be a problem and the file menu.list is empty, nothing to edit?

---

### Post by lovelyvik293 on 2009-02-09
there is no menu.list in the /boot/grub.And when you use the 
```
gedit menu.list 
```
It will open the new file menu.list

---

### Post by Ant01 on 2009-02-09
Sorry I am not following you properly, must I save the code you gave me earlier in the menu.list file

______________________________________________________________
# (4) Windows
title Windows XP Professional SP3
rootnoverify (hd0,0)
makeactive
chainloader +1
______________________________________________________________

---

### Post by Nepherte on 2009-02-09
No, I simply used an incorrect file name. It should be menu.lst as others have told:
```
gksudo gedit /boot/grub/menu.lst
```

---

