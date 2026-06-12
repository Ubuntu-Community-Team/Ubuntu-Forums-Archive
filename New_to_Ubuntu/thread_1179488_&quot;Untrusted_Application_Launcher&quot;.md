---
title: "&quot;Untrusted Application Launcher&quot;"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by sanderella on 2009-06-05
I have on my desktop the folder /home/sandra/Desktop/jws_app_shortcut_1239651540065.desktop. This is the file for launching the St Pixel's icon to get straight into St Pixel's Live Online Church.

When I try to open it, I get the message "**Untrusted Application Launcher** The application launcher "jws_app_shortcut_1239651540065.desktop has not been marked as trusted. If you do not know the source of this file, launching it may be unsafe." So I click on the box "Mark as Trusted." Then I click on the box "Launch Anyway.

The result is this message "**There was an error launching the application**. Details: Failed to execute child process "/usr/lib/jvm/java-6-sun-1.6.0.10/jre/bin/javaws" (No such file or directory).

I would like some help to getting my icon back and working. Thank you.

---

### Post by jonobr on 2009-06-05
Forgive my ignorance here.

Could you not just open it in a web browser and if you need to get to it pronto, set that up as your homepage?

Again, maybe Im missing something here, but this sounds like a labor saving mechanism that doesnt save much labor?

Cheers

---

### Post by sanderella on 2009-06-06
**SOLVED**

I had some advice from the St Pixel's website, and this is what I did. I just pasted "javaws -viewer" into the Terminal, the java box came up, I right-clicked it and it put icon back on my desktop. And it works to get me into Live.:p

---

### Post by haha.ysj on 2010-08-29
The .desktop file needs to be executable. You should add executable permission to it :

    chmod +x *.desktop

---

### Post by adrian_nye on 2011-03-14
The komodo application launcher does the same thing, even with
execute permissions:

-rwxr-xr-x

---

### Post by Randymanme on 2011-05-07
> **sanderella said:**
> When I try to open it, I get the message "**Untrusted Application Launcher** The application launcher "jws_app_shortcut_1239651540065.desktop has not been marked as trusted. If you do not know the source of this file, launching it may be unsafe." So I click on the box "Mark as Trusted." 

What box?
________________________
Okay.  After more googling, I've seen a screenshot of the complete box.  But the box that I get with the " . . . has not been marked as trusted. If you do not know the source of this file, launching it may be unsafe." does not have the three options at the bottom. There's no place to select anything.

---

### Post by ccben on 2011-08-08
The box is in right click of .desktop file and go to Permissions. You will find the Allow executing file as program tickbox there. I'm using 11.04

---

### Post by darreno1 on 2012-02-27
> **haha.ysj said:**
> The .desktop file needs to be executable. You should add executable permission to it :

    chmod +x *.desktop

Hate to bring back an old thread but I had to give thanks to haha,ysj for his/her help. I had a similar issue launching an icon from the desktop and the above command worked.

---

### Post by BlinkinCat on 2012-02-27
> **darreno1 said:**
> Hate to bring back an old thread but I had to give thanks to haha,ysj for his/her help. I had a similar issue launching an icon from the desktop and the above command worked.

Hi, 
As this thread is marked solved, it may have been best to create another one - You could have included a link back to this one.

Cheers - :p

---

### Post by jorcarras on 2012-04-17
> **haha.ysj said:**
> The .desktop file needs to be executable. You should add executable permission to it :

    chmod +x *.desktop

It worked perfectly for me. Thanks

---

### Post by oldos2er on 2012-04-17
Snooze time. Closed.

---

