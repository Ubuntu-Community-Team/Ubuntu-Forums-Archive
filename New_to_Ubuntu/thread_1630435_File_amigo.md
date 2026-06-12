---
title: "File amigo"
date: 2010-11-25
forum: New to Ubuntu
---

### Post by johnnie1uk on 2010-11-25
I have just started useing Ubuntu 10.10 full time.  I want to Install Fileamigo how do i go about doing this, please

---

### Post by pawhtiobo on 2010-11-25
Hi :)

I think its not possible to have it working correctly in Ubuntu, has i can see there Homepage:

FileAmigo Specifications:
        

Hardware
        

• Pentium 133 MHz +
• 72 MB memory +
• VGA 256 colors
• Mouse

Operating System
        

Windows 9x, ME, NT4, 2000, XP, Vista *
(FileAmigo Web requires IIS 4.0+)

Disk Space
        

60 MB +

Limitations
        

• Max File Size: 2 GB
• Data and SubData Designs: ~32 KB
• Files: No Limit Set
• Records: No Limit Set
• Record Size: ~2 KB
• Reports: No Limit Set
• Concurrent Users: 255 

You can try to use WINE and see if it works :)

[http://www.winehq.org/](http://www.winehq.org/)

See ya...

---

### Post by johnnie1uk on 2010-11-25
Thanks i will try to work out wine

---

### Post by johnnie1uk on 2010-11-26
Tried with wine but i get a message saying the Fileamigo program is not certified - like it might not be safe. 
is there anyway i can get it?

---

### Post by 3rdalbum on 2010-11-26
> **johnnie1uk said:**
> Tried with wine but i get a message saying the Fileamigo program is not certified - like it might not be safe. 
is there anyway i can get it?

The program hasn't been marked with the "executable" flag. You can either right-click it, go to Properties, then Permissions and make it executable, or run the program with Wine in the terminal:

```
wine <drag the file into the terminal>
```

---

### Post by johnnie1uk on 2010-11-26
Thanks, i got it installed but it wouldnt work as there was a error with a jet file.

---

