---
title: "Usplash theme?"
date: 2010-01-04
forum: New to Ubuntu
---

### Post by allmightymoo on 2010-01-04
What is a usplash theme and how can i use one? i ahve startup manager and one of the options is changingthe usplash theme. I thought i downloaded one but nothing changed. Is a usplash theme change the theme of the boot menu? or just the log in screen for ubuntu?

Thanks.

---

### Post by Groucho Marxist on 2010-01-04
> **allmightymoo said:**
> What is a usplash theme and how can i use one? i ahve startup manager and one of the options is changingthe usplash theme. I thought i downloaded one but nothing changed. Is a usplash theme change the theme of the boot menu? or just the log in screen for ubuntu?

Thanks.

If I remember correctly, usplash changes the boot menu theme. 
In regards to the latter pertaining to custom log-ins, I'm posting an example of my custom log-in screen on my laptop :)

---

### Post by allmightymoo on 2010-01-04
That awesome...could you explain how to change either the log in screen or boot menu?

---

### Post by Groucho Marxist on 2010-01-04
> **allmightymoo said:**
> That awesome...could you explain how to change either the log in screen or boot menu?


Absolutely :) Although, I will only go into editing the log in screen for now, as I am also discovering how to alter my boot menu or "bootsplash" theme.

1.) I found my original Ubuntu login screen image in the following location: 
/usr/share/images/xsplash

2.) You are going to be looking for a file with the following name: bg_2560x1600.jpg
Make a back up of the file (such as copying the exact image into your Pictures folder just in case something does not work). 

3.) Take any desired jpg image (in my case, Gotham City) from your images folder and
open up GIMP to resize it to the original bg_2560x1600.jpg image size.

4.) Save your new image to the desktop (or any where else that is memorable) with the name bg_2560x1600.jpg
Do NOT save this new image in the same area that you placed the back up to the original.

4.) Place your newly re-named image into the following location:  /usr/share/images/xsplash

5.) It will say that you cannot place the image, as you do not have permission to alter the folder's content.
Open up Terminal and type the following command without brackets around your name:     sudo chown [YOUR NAME]:[YOUR NAME] /usr/share/images/xsplash/bg_2560x1600.jpg

6.) You now have permission to change the file. Paste your new image in the folder. It will ask if you would like to replace the older image with your new one; select yes.

7.) You will now have a custom log in screen :)

---

### Post by allmightymoo on 2010-01-04
i'm lost...i have the 2560x1600 .jpg image named correctly and it is saved to my desktop. So i tried to put it in the xsplash folder but it didnt work cuz i need permission, like you said. So after that i'm back to my new image on the desktop and the old one in xsplash. Right so far? after that i go into the terminal and type what u said nothing happens but it says there is a 'missing operand after...' (how do i know what my name is? haha i used the name thats on my task bar...is this correct?)

---

### Post by allmightymoo on 2010-01-04
Ok so now i think i do have the correct name but when i type it in nothing happens at all...it just goes to the next line...

---

### Post by the8thstar on 2010-01-04
Check your destination folder at /usr/share/images/xsplash to see if your custom picture is there. If it is indeed the change will be visible the next time you reboot.

BTW, you have only changed xsplash so far. To change usplash, which comes before xsplash, you can install different themes with Synaptic (just look for usplash keyword) and administer your different themes with Startup Manager (again, found in Synaptic).

---

