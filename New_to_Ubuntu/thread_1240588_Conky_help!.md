---
title: "Conky help!"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by amdemas on 2009-08-14
Im trying to configure conky and i just isnt working for me. If anyone can help me that would be great!

Im following this site [http://www.ubuntugeek.com/conky-a-light-weight-system-monitor-for-ubuntu-linux-systems.html](http://www.ubuntugeek.com/conky-a-light-weight-system-monitor-for-ubuntu-linux-systems.html)

---

### Post by credobyte on 2009-08-14
What's exactly not working ( conky, startup, etc. ) ?
[COLOR=DimGray]** Post your conky & the way you launch it ..[/COLOR]

---

### Post by amdemas on 2009-08-14
> **credobyte said:**
> What's exactly not working ( conky, startup, etc. ) ?
[COLOR=DimGray]** Post your conky & the way you launch it ..[/COLOR]

Well I have conky pull up when I log in but it shows up as a pop up window. I just need he'll customizing it to be integrated with my desktop. Sorry I didn't say that earlier.

---

### Post by credobyte on 2009-08-14
Add this line somewhere at the top of your conky file ( settings area ):
```
own_window_transparent yes
```

---

### Post by amdemas on 2009-08-14
> **credobyte said:**
> Add this line somewhere at the top of your conky file ( settings area ):
```
own_window_transparent yes
```

Thanks. This is silly I know but I found the file that's how I added it to my startup programs but is that the file I edit?  Or where would the file be located?

---

### Post by infernowolf36 on 2009-08-15
woo! i'm in the same boat. i just found conky and i don't know what is going on. i can only run it from the terminal and i can't customize it at all.. have no idea what's going on i just did 

sudo apt-get install conky

 and it installed it kinda.

---

### Post by infernowolf36 on 2009-08-15
i'm trying to get something similar to this 

[http://img152.imageshack.us/img152/1318/resizedmp9.png](http://img152.imageshack.us/img152/1318/resizedmp9.png)

---

### Post by infernowolf36 on 2009-08-15
how do you "Save and Exit" the editor? i have my terminal open and i don't know how to save the script i just made...

---

### Post by sideaway on 2009-08-15
Scripts for conky are saved in a text file: ~/.conkyrc

---

### Post by sideaway on 2009-08-15
Also, those look like Screenlets rather than conky. For a beginner you may wish to try screenlets first :)

sudo apt-get install screenlets

---

### Post by amdemas on 2009-08-15
> **sideaway said:**
> Scripts for conky are saved in a text file: ~/.conkyrc

Ok great but where would this file be located?

---

### Post by jrothwell97 on 2009-08-15
.conkyrc is saved in your home folder (the tilde, ~, is shorthand for this) but as it has a period at the beginning of its name it's hidden by default. The best way to edit it is to open a terminal and run

```
gedit .conkyrc
```

or, on Kubuntu,

```
kate .conkyrc
```

---

### Post by credobyte on 2009-08-15
[http://ubuntuforums.org/showthread.php?t=205865](http://ubuntuforums.org/showthread.php?t=205865)

---

### Post by infernowolf36 on 2009-08-15
> **amdemas said:**
> Ok great but where would this file be located?

you have to create it.. go to Places -> Home Folder then right click and click "create document -> empty file" and name it .conkyrc

then you click it and open it to edit it. copy paste the stuff in the guide and then save and exit.. and there ya have it..

---

### Post by infernowolf36 on 2009-08-15
> **sideaway said:**
> Also, those look like Screenlets rather than conky. For a beginner you may wish to try screenlets first :)

sudo apt-get install screenlets

tried screenlets.. it's ok.. kinda got what i wanted but not really. lol. you're definitely right though, it'd be for beginners but that's not the kind of data layout i want. thanks though.

---

### Post by amdemas on 2009-08-16
> **infernowolf36 said:**
> you have to create it.. go to Places -> Home Folder then right click and click "create document -> empty file" and name it .conkyrc

then you click it and open it to edit it. copy paste the stuff in the guide and then save and exit.. and there ya have it..

Yep that worked great for me. Thanks for the help.

---

### Post by amdemas on 2009-08-17
Well doing sudo gedit .conkyrc and editing it with the script on the listed web page at the beginning worked for me. The issue i am having now is that it is staying on top of all my open windows so if anything opens under it i can move it or even see it.

---

### Post by zerhacke on 2009-08-17
I wouldn't use sudo to gedit .conkyrc.  That will mess with your permissions later in life.  Just use gedit .conkyrc.

---

