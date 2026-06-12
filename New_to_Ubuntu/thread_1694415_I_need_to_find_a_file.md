---
title: "I need to find a file"
date: 2011-02-24
forum: New to Ubuntu
---

### Post by Miss. Dobson on 2011-02-24
Hello all,

Sorry if this is very vague but I'm hoping someone can help me.

I recently did a clean install on my laptop.  I did 32 bit 10.10 Ubuntu and 32 bit Win 7.  I installed Ubuntu first and everything was good to go.  Then I did Win 7.  To get to Ubuntu I used EasyBCD to dual boot.  Then when I went to log in it wasn't taking my pass.  So I got it changed.  So then when I logged in I got a bunch of errors.

 could not update ICEauthority file /home/linux/.ICEauthority


  There is a problem with the configuration server.  (/user/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)


  Nautilus could not create the following folders: /home/linux/Desktop,/home/linux/.nautilus.  before running Nautilus, please create these folders, or set permissions such that Nautilus can create them.
  
I'm ok with having to reinstall Ubuntu but there's an issue.  There is a VERY important file I moved over to it.  I should have just copied but this was the only file I needed from my backup on ubuntu so I just moved it.  I'm pretty sure it's in the doc. folder on the linux drive.  But since I can't access anything on Ubuntu (all I see is the wallpaper I can do terminal) I'm having a hard time finding where that folder is in the file system.

I have a way to look at the ext4 file system on 7 but I just don't know where the folders are.

If there is a way to help me either find the folder/file or fix these errors I would be forever grateful.

---

### Post by TeoBigusGeekus on 2011-02-24
Boot up with a live cd, open terminal and give
```
find / -name "nameoffile.ext" 2>/dev/null
```

---

### Post by Old *ix Geek on 2011-02-24
Finding the file is simple--but there's NO NEED to reinstall the OS. This isn't Windows, and you need to get out of the "reinstalling the OS every few months is part of computing" mindset. The problems you're having are easily solved.

You said you can get to a terminal, right? Okay!

>  could not update ICEauthority file /home/linux/.ICEauthorityType this:
```
rm /home/linux/.ICEauthority
```> There is a problem with the configuration server.  (/user/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)

Nautilus could not create the following folders: /home/linux/Desktop,/home/linux/.nautilus.  before running Nautilus, please create these folders, or set permissions such that Nautilus can create them.Now type this:
```
mkdir /home/linux/Desktop
touch /home/linux/.nautilus
```and then:
```
chmod 666 /home/linux/Desktop /home/linux/.nautilus
```Finally:
```
sudo shutdown -r 0
```When the computer comes back up, is it back to normal?

---

### Post by Miss. Dobson on 2011-02-24
> **TeoBigusGeekus said:**
> Boot up with a live cd, open terminal and give
```
find / -name "nameoffile.ext" 2>/dev/null
```
 
Anyway to wildcard it?

---

### Post by Miss. Dobson on 2011-02-24
I can get into the root shell in recovery.

```
rm /home/linux/.ICEauthority
```

rm: cannot remove '/home/linux/.ICEauthority': No such file or directory

```
mkdir /home/linux/Desktop
touch /home/linux/Desktop/home/linux/.nautilus
```

touch: cannot touch '/home/linux/Desktop/home/linux/.nautilus' : no such file or directory

```
chmod 666 /home/linux/Desktop /home/linux/Desktop/home/linux/.nautilus
```

Same thing as the above ones.

---

### Post by Old *ix Geek on 2011-02-24
Please see my edited post above. I didn't notice the comma in the OP and that changed things!

---

### Post by Miss. Dobson on 2011-02-24
Sorry, no change.  Still get the same thing for the first.  Everything seemed to go well for the rest but the errors still come.

---

### Post by Old *ix Geek on 2011-02-24
> **Miss. Dobson said:**
> Sorry, no change.  Still get the same thing for the first.  Everything seemed to go well for the rest but the errors still come.

Do you mean for removing the file?: rm /home/linux/.ICEauthority

That's okay, the error message is just telling you it doesn't exist, which is fine.

When you reboot now, what happens?

---

### Post by TeoBigusGeekus on 2011-02-24
> **Miss. Dobson said:**
> Anyway to wildcard it?

Of course, you can use any regular expression for nameoffile.ext.

---

### Post by Miss. Dobson on 2011-02-24
> **Old *ix Geek said:**
> Do you mean for removing the file?: rm /home/linux/.ICEauthority

That's okay, the error message is just telling you it doesn't exist, which is fine.

When you reboot now, what happens?

The errors keep coming.

---

### Post by Old *ix Geek on 2011-02-24
> **Miss. Dobson said:**
> The errors keep coming.

The SAME errors?

---

### Post by Miss. Dobson on 2011-02-24
> **Old *ix Geek said:**
> The SAME errors?

Yes.

---

### Post by Miss. Dobson on 2011-02-24
I forgot about this.  But I did encrypt my home folder.  Which is most likely why I can't find the file.  

So I'm guessing I'll have to get into my account to get past it.

---

