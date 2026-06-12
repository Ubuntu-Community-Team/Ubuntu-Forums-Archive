---
title: "Add/Remove Programs are not the same"
date: 2009-06-14
forum: New to Ubuntu
---

### Post by rosswmcgee on 2009-06-14
One of my 9.04 installs  has only Canonical maintained applications,third party and already installed. It is missing the 
All open source applications. When I opened it the first time it did do an update. How to fix?

Added note under applications there is no system tools.

---

### Post by gradinaruvasile on 2009-06-14
Did u check the software sources?

---

### Post by camper365 on 2009-06-14
Go to System -> Administration -> Software Sources
Make sure that Community Maintained Open Source Software (universe) is checked.
If you want the multiverse, check that too.

---

### Post by rosswmcgee on 2009-06-14
The only thing unchecked under Ubuntu Software is Source Code. Nothing is checked under the  third party software tab.

---

### Post by camper365 on 2009-06-14
try:
```
sudo aptitude update
```

---

### Post by rosswmcgee on 2009-06-14
I just did it, but it did not change anything.

---

### Post by Amilo1718 on 2009-06-14
can you provide us with a screenshot of your mainscreen where you 'add/remove programs' ?

---

### Post by rosswmcgee on 2009-06-14
Took screen shot how do I post it?

---

### Post by coffeecat on 2009-06-14
Open the Add/Remove application and at the top of that Windows, by "Show", choose "All Available Applications", "All Open Source Applications", or whatever you want from the drop-down list.

---

### Post by Therion on 2009-06-14
Make sure the dropdown menu/filter is showing "**All available applications**".  

The filter is at the top right of the Add/Remove window just to the left of the "Search" bar.

---

### Post by rosswmcgee on 2009-06-14
I know that but all the choices are not there.

---

### Post by Amilo1718 on 2009-06-14
> **rosswmcgee said:**
> Took screen shot how do I post it?

in your reply... you'll see a paperclip... put the image there, upload & we're ready to solve this
:)

---

### Post by rosswmcgee on 2009-06-14
I know all that stuff but the choices are not available as I first mentioned. All open sources is not there. With all high lighted there are only  three choices sas mentioned.

---

### Post by rosswmcgee on 2009-06-14
file:///home/rosswmcgee/Desktop/Screenshot-Add-Remove%20Applications.png

Hope this works.

---

### Post by Elfy on 2009-06-14
> **rosswmcgee said:**
> file:///home/rosswmcgee/Desktop/Screenshot-Add-Remove%20Applications.png

Hope this works.

Close :)

Have a look here - [http://ubuntuforums.org/showpost.php?p=4527031&postcount=4](http://ubuntuforums.org/showpost.php?p=4527031&postcount=4)

---

### Post by ajgreeny on 2009-06-14
Try ```
sudo apt-get install --reinstall gnome-app-install
```which may just do the trick for you.

---

### Post by rosswmcgee on 2009-06-14
Thanks tried it. Still the same thing. Must I do another clean install?

---

### Post by rosswmcgee on 2009-06-14
Found the fix: sudo

/usr/bin/gnome-app-install

this did it all is well that ends well.

---

