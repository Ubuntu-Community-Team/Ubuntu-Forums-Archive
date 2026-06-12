---
title: "How do I uninstall BlueFish?"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by bilbo.san on 2009-11-15
Hello!

I recently installed Aptana Studio, and works nice, and decided to also install BlueFish, but apparently, Aptana is not actually installed on the system, it is just un-packed... so when I try to open a .PHP file on Aptana, it opens BlueFish instead, even using the 'open file' dialogue in Aptana... 

So perhaps I should un-install Blue Fish... any suggestions please.

Many thanks

---

### Post by AndyCooll on 2009-11-15
```
sudo apt-get remove bluefish
```
That should do the trick.

However rather than uninstalling Bluefish, are you not able to get .php files to be associated with Aptana by right-clicking on a file, selecting "properties", then selecting "open with" and navigating to Aptana?

:cool:

---

### Post by bilbo.san on 2009-11-15
> **AndyCooll said:**
> 

However rather than uninstalling Bluefish, are you not able to get .php files to be associated with Aptana by right-clicking on a file, selecting "properties", then selecting "open with" and navigating to Aptana?

:cool:

Thanks AndyCool,
I actually tried that, but I couldnt find Aptana in the programs list, I even tried that on the 'preference' settings in Aptana... and didnt work.
Maybe I could just get use to it... apparently, CSS and JS files do open in Aptana, everything else goes to BlueFish

---

### Post by halitech on 2009-11-15
If Aptana is not in the list, you should have an option of "Other". If you select that you can browse to where the file is actually located. If you aren't sure, you can use
```
locate aptana
``` to find where the executable file is (probably /usr/bin)

---

### Post by bilbo.san on 2009-11-15
> **halitech said:**
> If Aptana is not in the list, you should have an option of "Other". If you select that you can browse to where the file is actually located. If you aren't sure, you can use
```
locate aptana
``` to find where the executable file is (probably /usr/bin)

Thanks!
That actually worked, but... for some reason, it loads some in BlueFish and other in Aptana... anyway. Will try to work this way.

---

### Post by Sef on 2009-11-15
How did you install Bluefish?

---

### Post by halitech on 2009-11-15
> **bilbo.san said:**
> Thanks!
That actually worked, but... for some reason, it loads some in BlueFish and other in Aptana... anyway. Will try to work this way.

you may need to do it for each file type you want to open with Aptana

---

### Post by bilbo.san on 2009-11-22
> **Sef said:**
> How did you install Bluefish?

I did what AndyCooll suggested:
sudo apt-get remove bluefish
But since BlueFish is recognized in the list of installed programs in Ubuntu, you could just to to 'ubuntu software center' under the Applications menu, search for BlueFish and then uninstall it.

---

### Post by bilbo.san on 2009-11-22
> **halitech said:**
> you may need to do it for each file type you want to open with Aptana

Thanks,
I was able to keep both at the end... still, I do not like BlueFish, but apparently Aptana will not edit PHP files as good as it does HTML.

Will see if I can install DreamWeaver with Wine...

e.

---

