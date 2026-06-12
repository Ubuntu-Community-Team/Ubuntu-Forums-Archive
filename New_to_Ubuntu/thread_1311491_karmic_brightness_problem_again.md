---
title: "karmic brightness problem again"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by jarongg on 2009-11-02
last night, before i installed karmic, i was researching it a bit and found that a bunch of people were having problems with the brightness adjusting itself and generally freaking out. now, as i am experiencing this, i can't seem to find the fix for it. can anybody link me to a thread where this is resolved? thanks.

---

### Post by ximatz on 2009-11-03
Yup. I must sadly confirm this, as I have been affected too. I have just installed Karmic on my Esprimo Mobile U9200. Before I installed Karmic, I was using Jaunty on my laptop. I found on the web a very usefull site on the Kubuntu wiki, wich had instructions to solve this problem (and may others also): [https://wiki.kubuntu.org/LaptopTestingTeam/FujitsuEsprimoU9200](https://wiki.kubuntu.org/LaptopTestingTeam/FujitsuEsprimoU9200)

All solutions worked fine for me on Jaunty, but they seen to have no effect on Karmic. Bleading edge technology has its price, as too many changes are required...

I am also looking for a solution, but until now: NADA :(

---

### Post by ximatz on 2009-11-21
Brothers, I am a believer: Trust the community!  :wink:

I received a message from chessnerd, who kindly shared a working solution for this problem with me. You can find chessnerd's original post here:
[http://ubuntuforums.org/showthread.php?t=1331709](http://ubuntuforums.org/showthread.php?t=1331709)

A resume of chessnerd's solution, which by the way worked for me:

1) Open Grub2 file.
```
  
 sudo gedit /etc/default/grub 
```

2) Add line on Grub2 file.
```
  
 GRUB_CMDLINE_LINUX="nomodeset acpi_backlight=vendor" 
```

3) Update Grub2.
```
  
 sudo update-grub 
```

4) Reboot your computer.

5) Now brightness should work as expected.

I must admit, I was tempted to try another disto because of not only this problem, but also of other two problems I was having with ad-hoc wireless connections and inverted touch pad two-finger-gestures, which I have more or less resolved by now.

My findings: if it does not work in Ubuntu, it does also not work anywhere else. :neutral:

I think the problem lies actually on GNOME's brightness manager, which does not allow users to adjust the brightness and sets instead a default value every time the user tries to set the brightness up or down. It is just a feeling...

I hope this helps others further!

---

### Post by cybil on 2009-11-25
Did it make anyone's video sluggish?

---

### Post by tayran on 2009-11-26
I have tried the solution above. I am using Karmic on a MSI Wind re-branded netbook with same hardware. Now brightness is fixed at full. Brightness shortcuts do not work and i don't experience any sluggish video. That is ok for me for now until finding a better solution.

---

### Post by cybil on 2009-11-26
Yeah, my brightness shortcuts don't work either.  It is a shame, because they worked previously.

---

### Post by SirLagz on 2010-02-07
I have the issues on my Lenovo laptop as well, and when I disabled power saving the brightness stopped changing itself, however the brightness FN keys do not work.

---

