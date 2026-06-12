---
title: "Host drive not seen by ubuntu"
date: 2011-05-29
forum: New to Ubuntu
---

### Post by r2d211 on 2011-05-29
Hello, I installed Natty as a windows application in one of my two HDs. 

Now, when I go Places and Computer, it shows only the second HD and the ubuntu File system (or something like that) which is the virtual loop partition where Natty was installed on my first HD. But the remaining windows partition on the same disk is not seen. 

However, I can see this HD named Host by the system manager and am able to surf it there.

Is there any way to make it visible in Places or Computer?

Thank you.

---

### Post by wildmanne39 on 2011-05-29
> **r2d211 said:**
> Hello, I installed Natty as a windows application in one of my two HDs. 

Now, when I go Places and Computer, it shows only the second HD and the ubuntu File system (or something like that) which is the virtual loop partition where Natty was installed on my first HD. But the remaining windows partition on the same disk is not seen. 

However, I can see this HD named Host by the system manager and am able to surf it there.

Is there any way to make it visible in Places or Computer?

Thank you.
HI, I have not used wubi but you should see it in the files manager, if not open disk utility and see if it is there if so see if it will let you mount it.

---

### Post by r2d211 on 2011-05-29
No, the files manager doesn't show it but only the System Manager where I am even able to surf it (in Sys. Man. is called Host).

And how to mount it or transfer ot from SysMan to FileMan? I tried by dragging but at no avail.

---

### Post by wildmanne39 on 2011-05-29
> **r2d211 said:**
> No, the files manager doesn't show it but only the System Manager where I am even able to surf it (in Sys. Man. is called Host).

And how to mount it or transfer ot from SysMan to FileMan? I tried by dragging but at no avail.Hi this is all the information I have on wubi installs.
[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Differences+between+Wubi+vs+dual-booting&as_qdr=all&sa=Google+Search&lang=en#911](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Differences+between+Wubi+vs+dual-booting&as_qdr=all&sa=Google+Search&lang=en#911)
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20access%20the%20Windows%20drives?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20access%20the%20Windows%20drives?)
did you open disk utility and see if it is in there?if so you can mount it from the utility.

---

### Post by coffeecat on 2011-05-29
You've discovered how to find the "host" folder. Simply open it and then (from the nautilus menu) Bookmarks > Add Bookmark. It will now appear in the left Places pane of a nautilus window. If you don't like the name "host", simply right-click on it and rename it.

---

### Post by r2d211 on 2011-05-29
Kitty, I think this is the best solution so far (for a wubi installation). Yes, I will bookmark it and have it at hand. Tomorrow morning I'll try your idea and then I think I can mark the thread as Solved.

Thank you all!

---

### Post by athenroy on 2011-05-29
On mine, it's Places, Computer, File System, Host, Users to access your files from Windows.  That's with a Wubi install of 11.04 and win 7.  I use Copy and Paste to transfer files.  It's worked so far.

---

### Post by r2d211 on 2011-05-30
Maybe yours is a double install with wubi, not an install inside windows. What can I say?

---

### Post by coffeecat on 2011-05-30
> **r2d211 said:**
> Kitty

That's the first time I've been called that, but I think I like it. :-k

:wink:

---

### Post by r2d211 on 2011-05-30
Kitty, Athenroy, Wildy, thank you so much for your help. The trick with the bookmark worked perfectly.

Have a blessed day!

---

