---
title: "Headphone jack/laptop speaker only"
date: 2011-04-27
forum: New to Ubuntu
---

### Post by mward69 on 2011-04-27
Hey good folks, having the same issue others are having, except I do NOT have a headphone selection in the output area
 The 2 it shows are 
*Internal stero speakers 
*HDMI digital output.

  If I open Alsa Everything is UNmuted.....
Card reads
 CONEXANT CX20561 {Hermoa}  and  ATI RS690/780 HDMI

 If I plug in the headphones, I get no sound and music still plays in the laptop speaker....

  My built is Ubu 10.10
  On a dual boot Gateway MD 2614U {crap} laptop

---

### Post by lidex on 2011-04-27
What profile is selected on the hardware tab?
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by mward69 on 2011-04-27
> **lidex said:**
> What profile is selected on the hardware tab?
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]


Sorry, still a little green with this, I ran the command.....what was I supp. to do after?  :p

Scratch that....here is the link

--------->> [http://www.alsa-project.org/db/?f=a3fed9d24100c013ce0d11ec77bdfdb8566e6885](http://www.alsa-project.org/db/?f=a3fed9d24100c013ce0d11ec77bdfdb8566e6885)

---

### Post by lidex on 2011-04-27
Good job, now try this. Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=laptop position_fix=1 enable=yes" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by mward69 on 2011-04-27
> **lidex said:**
> Good job, now try this. Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=laptop position_fix=1 enable=yes" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**


K...back in a sec...thx   :)


SOLVED!!!!!!   Whoo-hooooo    you rock bro!!!!!

---

### Post by lidex on 2011-04-27
Nice. Please mark the thread solved using 'Thread Tools' up top.

---

### Post by mward69 on 2011-04-27
> **lidex said:**
> Nice. Please mark the thread solved using 'Thread Tools' up top.

Done...thank you again for the quick help!!!!!

---

### Post by raphsabb on 2011-06-07
Had to do this on 11.04 also(if anyone has the problem)

---

