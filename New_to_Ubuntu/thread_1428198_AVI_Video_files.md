---
title: "AVI Video files"
date: 2010-03-12
forum: New to Ubuntu
---

### Post by mistypotato on 2010-03-12
Does anyone know a way to adjust the date/time stamp for Video files specifically, AVI files?

thx

---

### Post by HalfEmptyHero on 2010-03-12
I don't know if there is an easier way, but this terminal command should work if you want to change it to today's date.

```

[FONT=Tlwg Typist][SIZE=2]mencoder -ovc copy -oac copy -o outputfilename.avi inputfilename.avi
[/SIZE][/FONT]
 
```

---

### Post by andrew.46 on 2010-03-14
Hi mistypotato,

> **mistypotato said:**
> Does anyone know a way to adjust the date/time stamp for Video files specifically, AVI files?

To adjust the *timestamp* of the file you would use the utility touch, or do you mean the filename of your .avi files? You can incorporate the date and time into your filename by using something like:

```
my_filename_$(date +%Y%m%d_%H_%M).avi
```

or some variation of the date syntax.

All the best,

Andrew

---

### Post by mistypotato on 2010-03-15
Well,

I was actually looking for a GUI type utility that I could use to change the system details date of photos I took because the camera doesnt and the photos and videos are always dated Jan 1 1961.

Right now the only way is to use TOUCH or to use a hex editor.

I want them to have the date I took them as part of the system details.  Not the name necessarily.

---

### Post by mistypotato on 2010-03-15
The very best and easiest way I have found to do this is as follows....

1). Open a terminal window
2). Copy all the pictures or videos you took to a unique temporary folder on your PC
3). In the Terminal window, Navigate to the folder you created with the photos
4). issue the command below
[B][COLOR="Blue"]
touch *.*[/COLOR][/B]

This will change the modified date of all files in that folder to the current system date and time.

If you want to custom time-stamp each file, you'll need to read up on the Linux TOUCH command.

:KS:KS Sure does seem that someone could program a really nice GUI utility to do this :KS:KS

---

