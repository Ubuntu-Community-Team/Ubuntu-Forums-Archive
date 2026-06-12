---
title: "panel (not responding)"
date: 2010-03-07
forum: New to Ubuntu
---

### Post by pidu87 on 2010-03-07
OK so I was moving the postion of the bar that shows opened programs, when I accidently held down the power button on my laptop.

Now whenever I start _UBUNTU 9.10_ 75% of the time it freezes at the ubuntu splash loading bar. The other 25% of the time it will load but the two bars don't work(maybe because they are on top of each other.....)

*How do I close "PANEL"?

*How do I find the folder that has terminal because i can't use the the menus to open it because the bars donts work.

also I tryed alt+F2 and that does nothing.


PLEASE HELP ME!!!! 

P.S. I LOVE YOU UBUNTU lol

---

### Post by Barriehie on 2010-03-07
> **pidu87 said:**
> OK so I was moving the postion of the bar that shows opened programs, when I accidently held down the power button on my laptop.

Now whenever I start _UBUNTU 9.10_ 75% of the time it freezes at the ubuntu splash loading bar. The other 25% of the time it will load but the two bars don't work(maybe because they are on top of each other.....)

*How do I close "PANEL"?

*How do I find the folder that has terminal because i can't use the the menus to open it because the bars donts work.

also I tryed alt+F2 and that does nothing.

PLEASE HELP ME!!!! 

P.S. I LOVE YOU UBUNTU lol

When you get to the desktop press ALT and F2 at the same time.  You'll get a box pop open and enter **gnome-terminal** to run the terminal.
when in the terminal try this:
```

sudo aptitude reinstall gnome-panel
```

HTH

---

### Post by pidu87 on 2010-03-08
Alt+F2 doesn't do anthing....... 


Is there something I cant type into recovery mode to fix this?

---

### Post by Robster2 on 2010-03-08
First thing I would do is do a recovery boot.  

Hold down the shift key when you are booting.

Select recovery boot from the grub menu.

When you get to the repair menu select the fix broken packages.

Then follow the other advise you are given here.

---

### Post by pidu87 on 2010-03-08
tryed that didn't help at all.........


So there is no folder that terminal is sitting in......


I guess I'll just download the Ubuntu 9.10 cd and try to reinstall it.... Which sucks cuz i'll prob loose all my data

---

### Post by Barriehie on 2010-03-08
> **pidu87 said:**
> tryed that didn't help at all.........


So there is no folder that terminal is sitting in......


I guess I'll just download the Ubuntu 9.10 cd and try to reinstall it.... Which sucks cuz i'll prob loose all my data

I know this is like closing the gate after the horse got out but if you have to reinstall then put /home on a different partition.  If you don't have to reinstall I'ld still recommend a diff. partition for /home.  Do you have any type of thumb drive to store on???  If you can get to a terminal we can in all likelihood save your data.

---

### Post by koleoptero on 2010-03-08
When you manage to start ubuntu hit ctrl+alt+f4 to go to a shell. Login using your details, and then to delete the panel configurations:

```
cd ~/.gnome2
rm -fr panel2.d
cd ~/.gconf/apps
rm -fr panel
```

then to restart the system:
```
sudo shutdown -r now
```

and I believe you'll be OK when you log back in.

---

### Post by pidu87 on 2010-03-08
> **koleoptero said:**
> When you manage to start ubuntu hit ctrl+alt+f4 to go to a shell. Login using your details, and then to delete the panel configurations:

```
cd ~/.gnome2
rm -fr panel2.d
cd ~/.gconf/apps
rm -fr panel
```

then to restart the system:
```
sudo shutdown -r now
```

and I believe you'll be OK when you log back in.


BINGO, you are the MAN!!!!!! THAT WORKED!!!!!

Thank you so MUCH!

---

