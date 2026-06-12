---
title: "No splash screen"
date: 2010-11-13
forum: New to Ubuntu
---

### Post by Robert Buckmaster on 2010-11-13
My Ubuntu Maverick splash screen has disappeared. Instead I see a flashing "_", then a bad parody of the splash screen with clunky text and information about the system processes. I tried installing a splash screen in the program 'Splash Screen', but with no success.

---

### Post by coffeecat on 2010-11-13
Did you install a proprietary graphics driver?

---

### Post by Robert Buckmaster on 2010-11-13
Yes: nVidia. Is that the reason for the lack of splash screen?

---

### Post by coffeecat on 2010-11-13
It's certainly a known issue that the proprietary nvidia and fglrx (ATI) drivers mess up the Plymouth boot screen - giving you ugly text. I'm not sure about the information about system processes that you describe. If you occasionally get a message about a filesystem check, that's normal. But if you get a large amount of rapidly scrolling text, that means you've lost the Plymouth splash entirely. Can you elaborate?

---

### Post by Robert Buckmaster on 2010-11-13
There's not much to see. The plymouth screen has been transformed into a low-resolution one, with the purple Ubuntu background, and without the elegant graphics I had before I installed the nVidia graphics driver. And there is the flashing '_'. On shutting down, the screen gives text of incident processes, underneath the "Ubuntu" and the dots.

I had my heart set on this splash screen. [http://2.bp.blogspot.com/_VUfNF3TAmiU/TBU5BJ2O5HI/AAAAAAAACus/kndmq1v3RBA/s1600/Ubuntu2.png](http://2.bp.blogspot.com/_VUfNF3TAmiU/TBU5BJ2O5HI/AAAAAAAACus/kndmq1v3RBA/s1600/Ubuntu2.png)

Is there a hack that will restore plymouth?

---

### Post by Toxicbits on 2010-11-13
Yes there is:

[How-To: Fix Your Ubuntu Boot Screen | kyleabaker.com]("http://kyleabaker.com/2010/07/11/how-to-fix-your-ubuntu-boot-screen/") 

Good Luck

Toxicbits

---

### Post by Robert Buckmaster on 2010-11-13
I am sure that solution would have worked just fine, but I used [http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml).

But thank you for your help!

---

### Post by Robert Buckmaster on 2010-11-13
I found the solution here. [http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

But thank you both for your help!

---

