---
title: "Wacom Bamboo Fun"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by Sedative on 2009-06-08
I did this:

[Click](http://ubuntuforums.org/showthread.php?t=765915)

But got a lot of errors in the terminal while doing it, so obviously, it didn't work. I think it was because it's for an older version of Ubuntu. What else can I do to make my Wacom Bamboo Fun to work?

---

### Post by Favux on 2009-06-08
Hi Sedative,

I'm going to guess you are using Jaunty.  If so see post #176 here:  [http://ubuntuforums.org/showthread.php?t=967147&page=18](http://ubuntuforums.org/showthread.php?t=967147&page=18)  Then go on to post #188 where shatterblast shows how he configured his Bamboo.

Good luck!

---

### Post by thepiratefish on 2009-06-08
what is this Wacom Bamboo fun?

---

### Post by Sedative on 2009-06-08
I don't know what Jaunty is. x.x;

And a Wacom Bamboo fun is a graphics tablet.

---

### Post by Favux on 2009-06-08
Hi Sedative,

Jaunty Jackalope (9.04) is the latest release of Ubuntu.  Before that was Intrepid (8.10) and Hardy (8.04).

Notice the release number is the year and month.  So 9.04 is 2009 April.

---

### Post by Sedative on 2009-06-08
Oh, yes, I have that. Thank you!

---

### Post by Sedative on 2009-06-08
The link you showed me, when I type one of the commands into the terminal, it doesn't work.

Still looking for help. :)

---

### Post by Favux on 2009-06-08
Could you tell me which command?

---

### Post by Sedative on 2009-06-08
```
sudo cp /usr/share/hal/fdi/policy/20thirdparty/10-wacom.fdi /home/yourusername/Desktop/10-wacom.bak
```


I replaced yourusername.

---

### Post by Favux on 2009-06-08
Hi Sedative,

Sorry if I get too basic.

sudo:  makes you root

cp:  is the copy command

/usr/share/hal/fdi/policy/20thirdparty/10-wacom.fdi:  is the location of the default Jaunty 10-wacom.fdi

/home/yourusername/Desktop/10-wacom.bak:  is the location we want to copy the 10-wacom.fdi to, renaming it 10-wacom.bak

So your user name is what you would see if you click on Places (Nautilus) and then Home Folder.

Assuming you are using Gnome and not KDE.

---

### Post by Sedative on 2009-06-08
I know, I replaced  it with my username.

---

### Post by Favux on 2009-06-08
OK, but you haven't told me what goes wrong.  What happens when you use it?  Did you check with Places (Nautilus) that the 10-wacom.fdi is in the location specified?

---

### Post by Sedative on 2009-06-08
I get this:


```
cp: cannot stat `/usr/share/hal/fdi/policy/20thirdparty/10-wacom.fdi': No such file or directory
```

---

### Post by Favux on 2009-06-08
OK, check with Places that you have a 10-wacom.fdi.  Open your home folder and then below Desktop click on File System and then navigate to it following the path description.  If it isn't there check in Synaptic Package Manager to see if wacom-tools is installed.  Search wacom.  If it isn't install it.

---

### Post by Sedative on 2009-06-08
I have:

Favux_Jaunty ext graphics_test 2_10-wacom.fdi.txt

And I downloaded wacom-tools.

---

### Post by Favux on 2009-06-09
Hi Sedative,

Alright, is that something you did earlier or did you mistype the command?  Normally when it says type you actually copy and paste.  And when you have to edit a command you can copy it into a text file and edit it there.  Editing it in a terminal can be a little tricky at first.

If Favux_Jaunty ext graphics_test 2_10-wacom.fdi.txt is really in /20thirdparty/ you need to change it's name to 10-wacom.fdi.

So close everything and in a terminal:
```
gksudo nautilus
```
Use nautilus to navigate to it and then right click on it and rename it 10-wacom.fdi.  Close nautilus and then use a regular Places to check on it and see what's in it.  The Jaunty wacom.fdi or the new one in post #176.

---

### Post by Sedative on 2009-06-09
Thanks! I renamed it and the command worked!

After I do what #176 says, then what?

---

### Post by Favux on 2009-06-09
Hi Sedative,

If you install the new .fdi correctly you will then be able to use wacomcpl.  See Section 3 here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  You can calibrate and configure your tablet.  Then you can manipulate the .xinitrc, which is a Hidden File in your Home Folder.  So in View you need to click on Show Hidden Files.  And shatterblast on post #188 shows you how to do that.

---

### Post by Sedative on 2009-06-09
I am so confused. :( I wish I was better at this stuff. Thanks for your time! I'll figure it out eventually.

---

### Post by Favux on 2009-06-09
Good luck!

It's just new.  Take your time and read things over a few times.

---

