---
title: "print output needs adjustment"
date: 2010-09-27
forum: New to Ubuntu
---

### Post by Schwoggel on 2010-09-27
Hello,
The problem _*[occured to somebody else already]("http://ubuntuforums.org/showpost.php?p=3851371&postcount=8")*_, but I couldn't find a solution to this:

I'm trying to set-up a Lexmark X74 (ubuntu 10.04) for someone and got the driver to work as *_[described in this thread]("http://ubuntuforums.org/showthread.php?p=3589880#poststop")._* The result is nice, but the beginning of the page starts in the middle.

Something that's supposed to look like:

```
|01234 56789|
|ABCDE FGHIJ|
```looks like

 ```
56789| |01234
FGHIJ| |ABCDE
 
```So, it's not just a few millimeters, it's half of the page. 

I did try the perl script _*[alignmargins]("http://www.openprinting.org/download/printing/alignmargins")*_, but with no success. I only gave the x-value to  the script since that's the only thing I want to be adjusted. The script went through without complaining. I restarted cups, but don't see any effect.

I appreciate any ideas on this.

Greetings,

Schwoggel

---

