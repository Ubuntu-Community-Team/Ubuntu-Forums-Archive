---
title: "Epson Avasys Image Scan! - change defaults?"
date: 2011-04-19
forum: New to Ubuntu
---

### Post by 2CV67 on 2011-04-19
I know there are both simpler & more comprehensive scanning applications available, but on balance I generally prefer using Avasys Image Scan! for Linux.

One minor irritation is that there does not seem to be any way of changing the default settings (300dpi - Color Photo - png - save to home - etc).
I usually want: 150dpi - Color Document - jpg - save to desktop, so this means resetting all of them every time...

Has anybody found a way of changing the default settings?

I imagine it is all in a simple text file somewhere, but I have not found it yet.

Thanks for any help!

---

### Post by ajgreeny on 2011-04-19
Why do you prefer it if it does not do what you want?  If you used xsane, assuming it will see your scanner, of course, it will allow you to change all those preferences that at the moment you can't change.

Try using the command ```
locate -i avasys
``` which will find all the files and folders that contain the string *avasys* in both upper and lower case.  That may tell you where any config files are located.

I am still interested in the reason for using this program and why it is so great, when it can't do what xsane can do, and do it so easily.

---

### Post by 2CV67 on 2011-04-20
> **ajgreeny said:**
> I am still interested in the reason for using this program and why it is so great, when it can't do what xsane can do, and do it so easily.
Thanks for your reply.

I did say I knew of simpler & more comprehensive applications...

I think "Simple Scan" is great for users who don't want to get too technical & I have a launcher for it on all my family & guest desktops.
I particularly like the fact that it can print easily, even to pdf.

Avasys Image Scan does everything I want (except keeping favorite default settings) & still has a clean, user-friendly GUI.
Specifically, it allows me to choose my dpi settings from 50/72/96/150/240/300/360/400/600/720/800/1200/1600/2400/3200/4800/6400/9600 (overkill!).
For everyday use, I rarely exceed 150dpi, to keep file size down, though for serious photo, negative & slide scanning I obviously use much higher settings.

Maybe XSane can do a whole lot more (I am sure it can, in the right hands) but for me the GUI is cluttered & incomprehensible.
Starting with the fact that when you open it, it doesn't open the preview window automatically.
One specific problem is that there are separate controls for x & y dpi but they don't have the same values.
For x dpi, the choice is 75/300/600/1200/2400/4800 but for y dpi it is 100/200/300/400/600 etc etc.
That means the smallest undeformed image I can get is 300dpi & the next choice is 600dpi.
Maybe this makes sense, but not to me at the moment.
That in itself is enough to exclude it.
Many other options are totally bewildering, but I didn't find a direct print control yet. 
Maybe I just need to spend a lot more time reading the manual?

My object was not to attack XSane, but to improve my Iscan.

---

### Post by 2CV67 on 2011-04-24
As an alternative approach, is there any way I can get XSane to give me matching x & y dpi's?
> **2CV67 said:**
> 
One specific problem is that there are separate controls for x & y dpi but they don't have the same values.
For x dpi, the choice is 75/300/600/1200/2400/4800 but for y dpi it is 100/200/300/400/600 etc etc.
That means the smallest undeformed image I can get is 300dpi & the next choice is 600dpi.

---

