---
title: "problems with opening file in homebanking"
date: 2010-08-08
forum: New to Ubuntu
---

### Post by thorbs on 2010-08-08
I am all of a sudden experience problems with opening my file in homebanking. Before one could easaly go in and find the key file now i cant direct the menu to the desktop where my key is. The open/find menu also looks different. I was working with the gnome keygen yesterday, can I have messed something up?

I have been checking if it could be something with Java, but from what I can see java 6.0 is installed on my firefox browser.


t.

---

### Post by lovinglinux on 2010-08-08
Please post screenshots.

---

### Post by thorbs on 2010-08-08
here is the screenshot

---

### Post by lovinglinux on 2010-08-08
Looks like a java file picker indeed. Have you tried to open a file on other sites to see if there is any difference?

Also check if **ui.allow_platform_file_picker** preference in **about[noparse]:[/noparse]config** is set to **true**.

BTW, you could type /home/thorbes/Desktop in the path.

---

### Post by thorbs on 2010-08-08
ahhh, I allready tried to type /home/thorbes/Desktop but the path seems completely unresponsive. I have also chosen desktop among the files and clicked ok, but again unresponsive. 

I am not sure how to "Also check if ui.allow_platform_file_picker preference in about:config is set to true."

btw. it seems that I do not have the "real" java 6 installed but an opensource alike, called icetea...


t.

---

### Post by lovinglinux on 2010-08-08
> **thorbs said:**
> ahhh, I allready tried to type /home/thorbes/Desktop but the path seems completely unresponsive. I have also chosen desktop among the files and clicked ok, but again unresponsive. 

I am not sure how to "Also check if ui.allow_platform_file_picker preference in about:config is set to true."

btw. it seems that I do not have the "real" java 6 installed but an opensource alike, called icetea...


t.

Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **ui.allow_platform_file_picker** in the filter, then double-click the same item in the results to make it **true/false**.

---

### Post by thorbs on 2010-08-11
Ok I found the solution to this one. Needed to put the key file in the my home directory to make it work.

---

