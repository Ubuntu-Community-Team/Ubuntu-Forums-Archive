---
title: "No Sound on Asus W7J"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by Ads1969 on 2011-04-30
Have just installed Ubuntu 11.04 on an Asus W7J.

I have read  previous forum entries on this but am so new to Linux I just can't get  my head around what to do to fix the no sound issue. 

Im just not experienced enough to work out vi commands etc so will need a step by step "dummies guide"

I did find this:

 # Edit alsa config file 
   vi /etc/modprobe.d/alsa-base 
   # and add this line 
   options snd-hda-intel model=3stack


but have no idea on how to do this.:confused:

---

### Post by lidex on 2011-04-30
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Ads1969 on 2011-04-30
> **lidex said:**
> Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]


Thanks!

[http://www.alsa-project.org/db/?f=bdf24506189f53acf1daf5dd6dc5fa9057e09f7b](http://www.alsa-project.org/db/?f=bdf24506189f53acf1daf5dd6dc5fa9057e09f7b)

---

### Post by lidex on 2011-04-30
Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=3stack" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by Ads1969 on 2011-04-30
Thank you! Problem solved!

---

### Post by lidex on 2011-04-30
Sweet. Please mark the thread solved using 'Thread Tools' up top.

---

### Post by bcrawford on 2011-05-17
Having the same problem on a ASUS N53JF. Here is the output from the script if anyone is willing to take a look.

[http://www.alsa-project.org/db/?f=27938cda5da3d769a6d7401735bd3e1e0f57a608]("http://www.alsa-project.org/db/?f=27938cda5da3d769a6d7401735bd3e1e0f57a608")

Thanks!

SOLVED(Sorry I should have searched for my model number right off the bat)

**ASUS N53Jf**

> **wyotecher20 said:**
> Greetings,

I have got my speakers working as they should on my laptop. Hopefully this will work for other people as well.

I added this line to my /etc/modprobe.d/alsa-base.conf:

options snd-hda-intel model=auto index=-0

Also I had to do a complete shutdown before this worked. It did not work after a restart.

Hope this helps.

---

