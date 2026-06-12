---
title: "frequency out of range?"
date: 2009-05-29
forum: New to Ubuntu
---

### Post by milesorvana on 2009-05-29
(yes i misspelled frequency.... sorry... kinda rushed today XD)
Ok, i am rather new to Ubuntu and love it so far however i am having a slight issue. Any time i try to fire up my computer i keep getting a black screen that says frequency out of range. I hooked up my tower to an older computer and changed the settings to 60 mhz, and the resolution to 1024x768. Now i have an emachine flat screen monitor that can go up to 1024x768. Yet each time i turn on my computer i am getting that dreaded screen. Does anyone have any suggestions on why it doesn't like my newer screen but works perfectly on my older one? I have been fighting this problem for almost a week and would love some advice. my only ubuntu savy friend is out of the state right now.

---

### Post by overdrank on 2009-05-29
Hi and welcome, what is the model of the graphics card, version of Ubuntu?
Can you reach command line with the ctrl, alt, F1 keys and are you able to hear the login sounds?

---

### Post by milesorvana on 2009-05-29
Yes i can reach the command line, i am using 9.01 and i can still hear sounds. As to the graphic card i am not sure. It is still factory make, i have not added anything to it.

---

### Post by jmszr on 2009-05-29
milesorvana,

I had the same problem when I installed 8.04.2. I then connected a larger monitor on which the resolution worked, went to System > Preferences > Screen Resolution, switched the resolution to 800x600 (you might need to try another), reattached the original monitor (800x600 worked) and then went back to Screen Resolution and changed it to 1024x768 - worked.

You also might try Applications > Accessories > Terminal:```
xrandr -s 1024x768

```

Hope this helps.

---

### Post by milesorvana on 2009-05-29
Well i did something similar before, however it does work.  I am currently using the max resolution however when i turn off the computer  and try to turn it back on i keep getting the frequency out of range message.

---

### Post by milesorvana on 2009-05-29
Another weird thing that i noticed is that i set up the auto login. Now when i turn the computer off and back on. It will load the basic ubuntu but before the login screen comes up it says frequency out of range. Then about 10 seconds late it will log me in and i get to my desktop. It is like the only part that is having issues is that login screen.

---

### Post by lisati on 2009-05-29
I had a similar error message when I had 9.04 installed on one of my machines (mine showed "signal out of range"). It's likely to be a screen resolution issue, with more than one possible solution.

The workaround I used was to edit grub's menu.lst file and change the line that reads > # defoptions=quiet splash to read ```
# defoptions=quiet nosplash
```, save the file, and then use ```
sudo update-grub
```

---

### Post by milesorvana on 2009-05-29
o.0 well uh... i am still noobish to tech speak. any chance of an english translation?

---

