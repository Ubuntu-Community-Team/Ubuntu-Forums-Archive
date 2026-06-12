---
title: "Screen Brightness"
date: 2010-02-21
forum: New to Ubuntu
---

### Post by 289531.EXE on 2010-02-21
I have a Compaq Presario V4000 running 9.10. I try to add on the screen brightness control but its has the red crossed out circle over it and there isn't a button to dim the screen light.

The brightness is beginning to mess up  my eyes, is there anyway that I can dim the lights on this godawful bright screen?

---

### Post by spiderbatdad on 2010-02-21
have a look at the file /proc/acpi/video/OVGA/LCD/brightness

see the current value, if not 50, try setting to 50.
You will have to be root to edit the file...and probably a reboot or restart display.
First verify the path to the file with your browser, then edit the file with the command ```
gksu gedit /path/to/file
```
Also here is a link to a thread that might help if your problem persists: [http://ubuntuforums.org/showthread.php?p=5534813](http://ubuntuforums.org/showthread.php?p=5534813)

If you need more help please ask.

---

### Post by 289531.EXE on 2010-02-21
I ran the code. When the window opened there was nothing, its a blank text window.

---

### Post by spiderbatdad on 2010-02-22
blank file would indicate the file tree is slightly different...that's why I suggest using your file browser to first navigate there to find the actual path. Also remember file names are case sensitive.

---

### Post by 289531.EXE on 2010-02-22
Sorry, I don't understand what you mean.

---

### Post by spiderbatdad on 2010-02-22
ok. I'm currently on a netbook remix installation, but if I remember correctly...in your places menu you should see "file system" by clicking that start navigating through the folders...proc/acpi/video/VGA/LCD... and so on to find the file named "brightness." Be aware of uppercase file names like VGA, as you'll have to adjust the gedit command accordingly.

Also, for example opening your home folder, if your use browser windows, on the left side of the window you'll see "file system" in the the places menu.

---

### Post by 289531.EXE on 2010-02-22
I only seem to have GFX0 (no VGA) and folders DD01-DD05 in the: file system/proc/acpi/video,

I clicked on the "brightness" file but they say "<not supported>"

Does this mean I'm stuck with a fixed bright  screen?

---

### Post by spiderbatdad on 2010-02-22
> **289531.EXE said:**
> I only seem to have GFX0 (no VGA) and folders DD01-DD05 in the: file system/proc/acpi/video,

I clicked on the "brightness" file but they say "<not supported>"

Does this mean I'm stuck with a fixed bright  screen?

I don't believe you have to be stuck. The link here: [http://ubuntuforums.org/showthread.php?p=5534813](http://ubuntuforums.org/showthread.php?p=5534813)
provides information on a system similar to yours. The author had to try the brightness in various DD01-DD05 folders...settled on DD03 (yours may be different.) He then provides a script for getting fn keys to control brightness. Sorry this requires jumping through hoops on your system. There may be other solutions forth coming.

---

### Post by 289531.EXE on 2010-02-23
Hey, Thanks  for the link. I didn't put any code in but i pressed fn+f7 and the brightness went down!
Awesome, thank you.

---

### Post by tomjennings on 2010-05-20
> **spiderbatdad said:**
> I don't believe you have to be stuck. The link here: [http://ubuntuforums.org/showthread.php?p=5534813](http://ubuntuforums.org/showthread.php?p=5534813)
provides information on a system similar to yours. The author had to try the brightness in various DD01-DD05 folders...settled on DD03 (yours may be different.) He then provides a script for getting fn keys to control brightness. Sorry this requires jumping through hoops on your system. There may be other solutions forth coming.

I tried writing "90" to all of the brightness 'files' in all of the DD01..DD05 directories to no avail. I get write error for all values, but some I can write "20" without error (but not "21") etc. When I cat them they're all <not supported>. Nothing I've done so far has changed screen brightness.

This is a Samsung x460 with the Intel Mobile video (07) 10.04 LTS recent install. Mine's stuck at unusably dim. 

The brightness applet (pointless, as it must use the acpi stuff) doesn't work and acts oddly (likely inexpected values read).

---

