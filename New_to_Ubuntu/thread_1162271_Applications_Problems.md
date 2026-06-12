---
title: "Applications Problems"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by ian19jam on 2009-05-17
Please can somebody kindly help me with a Applications problem. Each time I place the cursor over Applications the scroll window does NOT scroll down and so I cannot access any of the programmes on Applications. Why is this happening and can anyone kindly solve this. I am a beginner so in simple computer language please. I use Ubuntu Intrepid Ibex version 8.10
Ian:

---

### Post by LeonBlade on 2009-05-17
Do you mind taking a screen shot so I can better understand what you are talking about?

---

### Post by ian19jam on 2009-05-18
Sorry for the delay in my reply but I am having difficulty with Mozilla Thunderbird and not easy to send emails at the moment. I don't understand what you mean by taking a screen shot? Sorry I am very amateur with the computer.

On my desk top screen on the top bar I have Applications Places and System set up. When I place my cursor on Applications it fails to download the box displaying all the programmes. When I do this for the other two it downloads normally, except that under Places it now no longer displays Documents. Why has this disappeared. So it looks as if I have two on going problems. 

Please can you kindly advise as to how I can solve this problem Many thanks Ian

---

### Post by Sef on 2009-05-18
So if you go to Applications on the top menu bar and click, then nothing happens.   If that is the case, have you upgraded recently or made any other changes to your desktop?

---

### Post by ian19jam on 2009-05-18
No I have not upgraded as I was not aware of it nor have i altered my desk top What is the answer to the problem please? Ian

---

### Post by mc4man on 2009-05-18
> am a beginner so in simple computer language please.
You need to delete or rename a certain file (applications.menu

Hold down the Alt button on your keyboard and then press the F2 button (Alt+F2

In the run box that pops up copy and paste this in, then press enter

```
gnome-terminal
```

In the new pop up (a teminal box) copy and paste this in and press enter
```
mv ~/.config/menus/applications.menu ~/.config/menus/applications.menu.bak
```

Try your Applications


To navigate to manually delete it'
Places -> Home folder -> press Ctrl+h (to show hidden files) -> .config -> menus

---

### Post by ian19jam on 2009-05-19
Thank you for that advice which I tried out but the terminal said that there was no such file or directory. I don't understand this as it was all there before. The incident happened after the telephone and adsl line went down for half an hour and after that the Applications did not work. What shall |I do next please? Ian

---

### Post by mc4man on 2009-05-19
Maybe try out what's in this thread
[http://ubuntuforums.org/showthread.php?t=1162022&highlight=no+applications+menu](http://ubuntuforums.org/showthread.php?t=1162022&highlight=no+applications+menu)

If you right click on Applications does anything drop down? (like edit menus, ect

---

### Post by ian19jam on 2009-05-19
Yes if you right click on Applicatoions down comes Edit menus, Remove from Panel, lock on Panel (the box beside that is NOT Ticked. I did not understand you new thread sorry. I am very amateur. What else can I do please?

---

