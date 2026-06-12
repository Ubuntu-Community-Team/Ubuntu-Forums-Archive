---
title: "IDE Execution Problem, &quot;Permission Denied&quot;. (Natty)"
date: 2011-06-17
forum: New to Ubuntu
---

### Post by Smilee Face on 2011-06-17
Howdy,

Well, just installed Natty few days ago and thanks to this forum I was able to fix my wireless dilema.

Now I've run into another sticky situation. I downloaded Geany (worked fine), wrote a "Hello World!" in C++. Compile and build were successful, but when I execute the terminal displays the following:

sh: /media/*location*/*myFile*/bin/Debug/*myFile*: Permission denied

(Also whomever responds, it would be wonderful if you could show me how to paste the contents of the terminal onto here.)

I read that I had to delete -Wall from build settings at compile and build, but the terminal showed the same message. I went to the .exe in the debug folder and that told be me that the application cannot be found (or something similar to that). I checked the permissions and it did have the .exe as program checked.


I removed Geany and tried it with Code::Blocks and same deal.


If this problem has been encountered before then please don't go through the trouble of retyping the whole mess, just link me the website and I will figure it out from there.

Thanks very much! Cheers

---

### Post by FormatSeize on 2011-06-17
You probably have to run it as root, since it seems like it is trying to do something that requires root permissions.
 
To output code properly: Highlight what you want to put in the output, push the "#" button in the formatting bar
```
and it will look like this.
```

---

### Post by wildmanne39 on 2011-06-17
> **Smilee Face said:**
> Howdy,

Well, just installed Natty few days ago and thanks to this forum I was able to fix my wireless dilema.

Now I've run into another sticky situation. I downloaded Geany (worked fine), wrote a "Hello World!" in C++. Compile and build were successful, but when I execute the terminal displays the following:

sh: /media/*location*/*myFile*/bin/Debug/*myFile*: Permission denied

(Also whomever responds, it would be wonderful if you could show me how to paste the contents of the terminal onto here.)

I read that I had to delete -Wall from build settings at compile and build, but the terminal showed the same message. I went to the .exe in the debug folder and that told be me that the application cannot be found (or something similar to that). I checked the permissions and it did have the .exe as program checked.


I removed Geany and tried it with Code::Blocks and same deal.


If this problem has been encountered before then please don't go through the trouble of retyping the whole mess, just link me the website and I will figure it out from there.

Thanks very much! Cheers
Hi, try this to get ownership of the file.
```
sudo chown -R username:username /media/file 
```
the /media/file is the name of your file and the path where your program is that you need to access.

---

### Post by Smilee Face on 2011-06-17
Thanks to both!

I always forget to listen to my professors and apply the "simple solutions first" concept.

Basically I was saving the project to a USB. When I made a new project and saved it to the Desktop it worked fine.

I still would like to know if it is possible to run a project from a USB in Ubuntu. I do it for all my programming classes in Windows OS for both Visual studio and Code::Blocks and it works fine. Couldn't see why not?

I did do the permissions command and I'm pretty sure it did something because it paused after I entered it. But still no success.

```
And thanks for the pointer on how to properly display code.
```

---

### Post by wildmanne39 on 2011-06-18
> **Smilee Face said:**
> Thanks to both!

I always forget to listen to my professors and apply the "simple solutions first" concept.

Basically I was saving the project to a USB. When I made a new project and saved it to the Desktop it worked fine.

I still would like to know if it is possible to run a project from a USB in Ubuntu. I do it for all my programming classes in Windows OS for both Visual studio and Code::Blocks and it works fine. Couldn't see why not?

I did do the permissions command and I'm pretty sure it did something because it paused after I entered it. But still no success.

```
And thanks for the pointer on how to properly display code.
```
Hi, with the correct path it would give you ownership of that entire usb drive, and yes you can use usb for your work, you can even make a bootable usb and boot from it if you system allows booting from usb devices. Would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

