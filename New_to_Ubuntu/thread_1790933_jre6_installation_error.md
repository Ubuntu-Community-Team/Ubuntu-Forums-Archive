---
title: "jre6 installation error"
date: 2011-06-25
forum: New to Ubuntu
---

### Post by kangaroo3000 on 2011-06-25
So, first of all, I apologize if this is the wrong section... :(

Anyways, I tried downloading jre6 from here: [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java), but it didn't work. Another site then said to try this command in the terminal: sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts. I did this, and got this error:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Package sun-java6-fonts is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'sun-java6-jre' has no installation candidate
E: Package 'sun-java6-plugin' has no installation candidate
E: Package 'sun-java6-fonts' has no installation candidate
jim@jim-HP-Compaq-6910p-FL694UC-ABA:~$ sudo apt-get install sun-java6-jre sun java6-plugin sun-java6-fonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Package sun-java6-fonts is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'sun-java6-jre' has no installation candidate
E: Unable to locate package sun
E: Unable to locate package java6-plugin
E: Package 'sun-java6-fonts' has no installation candidate

Anyone know of a way to fix this and successfully install java plugin for firefox?

---

### Post by jtarin on 2011-06-25
There was another post on Java earlier today marked as solved that might be beneficial to look at......[Here.]("http://ubuntuforums.org/showthread.php?t=1790359")

---

### Post by kangaroo3000 on 2011-06-25
I tried that, but the files still aren't appearing when I search in the synaptics thing.

---

### Post by jtarin on 2011-06-25
After you add the repository you must update to see them.

---

### Post by kangaroo3000 on 2011-06-25
how might i update it?

---

### Post by dFlyer on 2011-06-25
from a terminal enter

sudo apt-get update

---

### Post by kangaroo3000 on 2011-06-25
did that, got this: E: The method driver /usr/lib/apt/methods/htto could not be found.

---

### Post by dFlyer on 2011-06-25
I'm not sure what htto is, are you sure it didn't say http?

---

### Post by kangaroo3000 on 2011-06-25
it said htto. I copied it directly from the terminal

---

### Post by dFlyer on 2011-06-25
Have you added any ppa's to your source file recently, if so you have you may have entered htto instead of http.

---

### Post by kangaroo3000 on 2011-06-25
I didn't add anything, only uncommented the stuff that was said too in jtarin's link. I checked, and these 3 had htto: deb-src htto://archive.canonical.com/ lucid partner
deb htto://archive.canonical.com/ lucid partner
deb-src htto://archive.canonical.com/ lucid partner

should I change it to http and maybe it'll work?

---

### Post by dFlyer on 2011-06-25
They need to read http not htto. Do you know how to edit them if not ask and I'll let you know.

---

### Post by kangaroo3000 on 2011-06-25
I edited them to http, saved it, then tried to update again, got the same error.

---

### Post by dFlyer on 2011-06-25
Can you post your source list.

---

### Post by kangaroo3000 on 2011-06-25
Turns out one of them wasn't changed... I re-changed it, the update worked, but I got: W: You may want to run apt-get update to correct these problems 
This worries me...

---

### Post by jtarin on 2011-06-25
Issue the command in a terminal ```
cat /etc/apt/sources.list
``` and copy and post results.

---

### Post by dFlyer on 2011-06-25
Run:

sudo apt-get update

This will fix you problem and you should be able to install jre6

---

### Post by jtarin on 2011-06-25
> **kangaroo3000 said:**
> Turns out one of them wasn't changed... I re-changed it, the update worked, but I got: W: You may want to run apt-get update to correct these problems 
This worries me...
It worries me that you didn't post the complete error dialog......there was some error before this that resulted in this....just try running update again and if it errors post the complete error message.

---

### Post by kangaroo3000 on 2011-06-25
ok, it worked this time through. The other error said something about duplicated resources, now that I bother to read the rest of it.

---

### Post by jtarin on 2011-06-25
If you would open your /etc/apt/sources.list you would probably see the duplication....edit only as root.

---

### Post by dFlyer on 2011-06-25
You can put a ## sign in front of the duplicate source file so you will not get that error. You should be able to update to jre6 since there are no more type-o. Let us know how it goes.

---

### Post by kangaroo3000 on 2011-06-25
Oh hooray :) finally worked, I have java installed succesfully :) thanks for the help :)

---

### Post by dFlyer on 2011-06-25
Please mark the thread as SOLVED.

---

