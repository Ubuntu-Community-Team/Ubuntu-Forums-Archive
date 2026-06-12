---
title: "Installing fonts in ubuntu."
date: 2009-09-04
forum: New to Ubuntu
---

### Post by karthick87 on 2009-09-04
I cannot visit any tamil websites,and i have downloaded suitable font which is in ttf extension.How to install it in ubuntu?

---

### Post by Hospadar on 2009-09-04
[http://www.detector-pro.com/2009/04/how-to-install-fonts-on-ubuntu-904.html](http://www.detector-pro.com/2009/04/how-to-install-fonts-on-ubuntu-904.html)

---

### Post by Finalfantasykid on 2009-09-04
Since you have already downloaded the font.  You should be able to drop it into this folder

/usr/share/fonts

which should allow other programs to see that font and use it.

---

### Post by zerhacke on 2009-09-04
You can't just drop it in the /usr/share/fonts folder because of permissions.  If you go to a terminal and type in 

sudo nautilus

and press enter, this will start up nautilus with root permissions and THEN you can drag and drop or cut and paste or what have you.

If you drop it in there with root nautilus, go back to your terminal and type

sudo fc-cache -f -v

and press enter, which will rebuild your font cache without having to reboot the computer as so many people seem to be fond of doing these days.

---

### Post by halitech on 2009-09-04
it should actually be 
```
gksudo nautilus
``` and not just sudo

personally, I like creating a .fonts folder in my /home folder and putting them there. As I am the only user and I have a seperate /home partition, this allows me to have all my fonts saved in the case of something happening and needing to reinstall without hunting down all the fonts again. I know some prefer to put them in /usr/share/fonts which might be better for multi-user machines but the choice is yours.

---

### Post by blackened on 2009-09-04
How bout
```
sudo apt-get install language-support-fonts-ta ttf-tamil-fonts
```

---

### Post by zerhacke on 2009-09-04
> **halitech said:**
> it should actually be 
```
gksudo nautilus
``` and not just sudo

The only difference between gksudo and plain Jane sudo is that gksudo allows for GTK2 themes on the window.  sudo is fine if you don't care that the root window isn't themed.  gksudo is NOT the only way to do it and sudo does it just fine with no serious consequences.

---

### Post by halitech on 2009-09-04
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by zerhacke on 2009-09-04
I stand corrected.  Thank you for enlightening me.

---

### Post by halitech on 2009-09-04
not a problem. I got blasted the first time I suggested it and it wasn't pretty so I try to let others know as nicely as I can and that link is nicer put then I could ever be :)

---

### Post by karthick87 on 2009-09-05
Thank you all,i have installed the font..

---

### Post by longtom on 2009-09-05
Just as an AddOn:

What about creating a .font directory in your homefolder and dropping the ttf file in there?  Would that work?

---

### Post by | Gnome | on 2009-09-05
> **longtom said:**
> Just as an AddOn:

What about creating a .font directory in your homefolder and dropping the ttf file in there?  Would that work?

I would like to add one question here. I had created a ".font" folder inside my home folder. But now, when I go to home folder I can't see it. But it is there, may be hidden. I know that because when I save some files, the program asks for destination and when I browse the destination inside the home folder, it shows that ".font" folder. Does that mean, it is hidden??

And would you please tell me the difference between a folder named "xxx" and ".xxx".

---

### Post by halitech on 2009-09-05
the . in front of the folder name makes it hidden as they are usually used for system config files and folders that you normally don't want to mess with.

---

### Post by longtom on 2009-09-05
> **halitech said:**
> the . in front of the folder name makes it hidden as they are usually used for system config files and folders that you normally don't want to mess with.

but if you have to - want to - see it, press Ctrl + H in Nautilus.

---

### Post by karthick87 on 2009-09-05
creating a .font directory in your homefolder and dropping the ttf file didn' work for me..

The following method works for me,

[LIST]
[*]     [FONT=Verdana][SIZE=2]Make a root directory[/SIZE][/FONT] 
[/LIST]
 [FONT=Verdana]                [/FONT][FONT=Verdana][SIZE=2]**mkdir /usr/share/fonts/truetype/myfonts**[/SIZE][/FONT]
 
[LIST]
[*][FONT=Verdana] Copy the font(s) into the newly created directory[/FONT]
[/LIST]
 [FONT=Verdana]                 **[SIZE=2]cp [fonts] /usr/share/fonts/truetype/myfonts[/SIZE]**[/FONT]
 
[LIST]
[*]     [FONT=Verdana][SIZE=2]To Run[/SIZE][/FONT]
[/LIST]
 [FONT=Verdana][SIZE=2]        **fc-cache -f -v**[/SIZE][/FONT]

---

### Post by | Gnome | on 2009-09-05
> **getyourkarthick said:**
> creating a .font directory in your homefolder and dropping the ttf file didn' work for me..



Is it so?? But it worked on me!!

---

### Post by longtom on 2009-09-05
> **getyourkarthick said:**
> creating a .font directory in your homefolder and dropping the ttf file didn' work for me..


Good to know.  It worked for me to have all my Windows fonts available in OO.  So I thought it was worth a shot...

 Glad you got it going so.

---

