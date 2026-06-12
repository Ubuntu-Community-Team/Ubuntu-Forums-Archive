---
title: "Eclipse Applet Viewer Error"
date: 2009-10-20
forum: New to Ubuntu
---

### Post by Kchymet on 2009-10-20
Whenever I use the eclipse Java IDE (No matter which version I try), when I run an applet, there is only a 200x200 pixel area to work in, and no matter how I resize the applet or the window, the new space is never able to be occupied. I use Ubuntu 9.04 if that makes a difference. I can also assure you it is not a coding error, as I successfully run the code on my school computer (Ubuntu 8.something, but same eclipse version). Is it because of my version of Ubuntu? Is this a preference error, is my widescreen setting not supported? What is happening here?

I am open to try free new IDEs, but I am NOT a fan of NetBeans

---

### Post by Kchymet on 2009-10-25
does anyone have any advice or a solution?

---

### Post by raylinth on 2009-11-12
Go to: Run -> "Run Configurations"

Under the drop-down menu "Java Applet" select your source that runs the applet.

Select "Parameters" tab.

Width and Height are set to 200, 200. Change this to accommodate your applet's size in your code. 

Cheers!

---

