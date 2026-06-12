---
title: "Messed up with my theme - Can't see my Desktop now"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by suncoolsu on 2008-12-27
Hi,
I installed a theme yesterday. After installing and selecting the theme I thought I was done with the tar.gz file. So I deleted the files (which were used for the theme). Now when I login - I can only see a Orange screen with a black box in the top left corner. I can't see any icons as well. 

what can I do now? can some one help me? 
-Do i need to install ubuntu again?
-Or is there a way to set the Theme to the default theme?

Thx

---

### Post by Bucky Ball on 2008-12-27
System->Preferences->Appearance

---

### Post by suncoolsu on 2008-12-27
This is the problem - I cant see anything on my desktop - No Application, No Places, No System .. Nothing

Its just a blank orange screen with a black square on the top left corner

---

### Post by Nepherte on 2008-12-27
Switch to a virtual terminal (ctrl + alt + F1), login and try to remove the theme. The theme should be somewhere in ~/.themes. Go to the directory with this command:
```
cd ~/.themes/
```
See what files and directories are in it:
```
ls -la
```
and remove the appropriate theme:
```
rm -r themename
```
You can then switch back with ctrl + alt + F7

---

### Post by suncoolsu on 2008-12-27
Hi Nepherte,
Thanks for the quick reply

I did everything what you have told but - I still get the same blank orange desktop and nothing changed. 

Is there a way to select a theme? in .themes? I think that could help me :confused:
The best way would be - iif there was an option to set everything to default in gdm?

Thx

---

### Post by suncoolsu on 2008-12-27
anyone?

---

