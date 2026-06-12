---
title: "shut laptop brightness led completely"
date: 2011-06-28
forum: New to Ubuntu
---

### Post by begin on 2011-06-28
I am using ubuntu 10.10 and I want to shut the brightness led completely or down to level not available when use the function key

---

### Post by amjjawad on 2011-06-28
> **begin said:**
> I am using ubuntu 10.10 and I want to shut the brightness led completely or down to level not available when use the function key

Hello and Welcome,

What's the name/brand of your machine?

---

### Post by begin on 2011-06-28
Thanks
I am using lg x140 netbook

---

### Post by amjjawad on 2011-06-28
> **begin said:**
> Thanks
I am using lg x140 netbook

Was that function working before and it stopped working suddenly?
What happens when you try to do that from the keyboard?

---

### Post by begin on 2011-06-28
The function key works fine but I just want to down the level of the brightness  more than that

---

### Post by amjjawad on 2011-06-28
> **begin said:**
> The function key works fine but I just want to down the level of the brightness  more than that

If the Fn key is working just fine, then I guess the minimum brightness that you can get is what you already have.

---

### Post by Maheriano on 2011-06-28
There's a separate Fn key for turning the LCD on/off, try that. Brightness only goes down so far.

---

### Post by tgalati4 on 2011-06-28
Brightness is typically controlled by a value that you echo to a file.  On my ibm thinkpad my LCD brightness is controlled by:

tgalati4@tpad-Gloria7 /proc/acpi/video/VID/LCD0 $ ls
brightness  EDID  info  state

Try poking different values into your brightness file.

Since you have a different machine, your actual file name and location may be different.

---

### Post by JC Cheloven on 2011-08-05
I realize this thread is a month old, but I'll post a solution, thinking in someone else looking for that in the future.

If lowering brightness by usual means don't get your screen dark enough for you, you can lower it much more using the xrandr command. Fisrt run it without arguments (once in life) to find out the name of your output. For me this shows ```
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 4096 x 4096
VGA-1 disconnected (normal left inverted right x axis y axis)
DVI-I-1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0*+   75.0  
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
TV-1 disconnected (normal left inverted right x axis y axis)

```
From this I see that my output in use is DVI-I-1. Then I run at a terminal ```
xrandr --output DVI-I-1 --brightness 0.6
```
This puts the brightness to 60%. Change the "0.6" for a number between 0.1 (barely lighting screen) to 1 (same brightness level as formerly) depending on your needs. 
A command like this is the only one to execute in future adjustements. Of course it can be saved over there (in a shell script...) for future use.

---

### Post by KBD47 on 2011-11-07
Thanks for this! 
 My brightness control on my laptop works, but it jumps from too dark to too bright, using the above code for my video adjust the brightness well.
Thanks again!
KBD47

---

