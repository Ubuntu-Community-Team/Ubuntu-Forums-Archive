---
title: "ATI Screen Tearing"
date: 2010-12-27
forum: New to Ubuntu
---

### Post by maryalesia on 2010-12-27
Hello again! 

I just got my friends computer running on a dual boot. After we installed the proprietary graphics drivers, there was some pretty bad horizontal screen tearing.

I've only ever used a computer with nvidia cards, so I don't know any easy fixes (like sync to v-blank in compiz and nvidia settings + adding nvidia settings to startup apps) for ATI tearing issues.

I think his card is, like, a 4000 650 ATI HD card or something. Emphasis on the "or something". My friend had to go home with his computer; I wont be able to test any potential fixes until wednesday. 

I've been googling "ATI Ubuntu screen tearing" to no avail. Does anyone know the fix to this problem?

Thankyou all for reading! :D

---

### Post by sandyd on 2010-12-27
> **maryalesia said:**
> Hello again! 

I just got my friends computer running on a dual boot. After we installed the proprietary graphics drivers, there was some pretty bad horizontal screen tearing.

I've only ever used a computer with nvidia cards, so I don't know any easy fixes (like sync to v-blank in compiz and nvidia settings + adding nvidia settings to startup apps) for ATI tearing issues.

I think his card is, like, a 4000 650 ATI HD card or something. Emphasis on the "or something". My friend had to go home with his computer; I wont be able to test any potential fixes until wednesday. 

I've been googling "ATI Ubuntu screen tearing" to no avail. Does anyone know the fix to this problem?

Thankyou all for reading! :D
ati propriety drivers have always been a hit/miss affair. For some releases, it works, for some it doesnt, and on other releases, it works kinda fine.

Check out [http://ubuntuforums.org/showthread.php?t=1238129](http://ubuntuforums.org/showthread.php?t=1238129)
for some good fun stuff that will not create screen tearing.

---

### Post by Mr James on 2010-12-27
Use the Catalyst 10.10 from the ATI site (not jockey) and bump VSync in the Catalyst Control Center all the way. In Compiz set Sync to V Blank and Undirect Full Screen (General section).

---

### Post by no2498 on 2010-12-27
if theres does not help you can try this right down the settings you are going to change so you can set them back after a restart they work for me

click system, preferences
go down the list to multimedia systems selector, start it click video
set the plugin to no xv or what ever works for you

this comes from the cheese help faq's

hope it helps you

---

### Post by maryalesia on 2010-12-27
Thanks for all the replies! I'll be sure to try each on wednesday and get back to you on what works / doesnt work. :)

---

### Post by maryalesia on 2010-12-29
> **Mr James said:**
> Use the Catalyst 10.10 from the ATI site (not jockey) and bump VSync in the Catalyst Control Center all the way. In Compiz set Sync to V Blank and Undirect Full Screen (General section).


I can't find the syn to v-blank setting in catalyst control center.

---

### Post by maryalesia on 2010-12-29
> **Mr James said:**
> Use the Catalyst 10.10 from the ATI site (not jockey) and bump VSync in the Catalyst Control Center all the way. In Compiz set Sync to V Blank and Undirect Full Screen (General section).


when you say "catalyst 10.10", do you mean a driver? I'm not sure how to download a proprietary driver and get it to work. I set sync to v blank to always on in catalyst control and clicked both sync to v blank and undirect full screen in compiz and the screen still tears.

Any ideas?

---

### Post by maryalesia on 2010-12-29
It doesn't tear when turning the compiz cube, tho. Only when moving around windows and playing videos in hulu.

---

### Post by Mr James on 2011-01-02
Go to AMD's website. In there somewhere (google the link) are the drivers. Select the one for your CPU (x86/amd64) and download it. It is a .run file. Open a terminal and

sudo sh xxxx-driver-file-name-xxxx.sh

And follow the directions. After, do 

sudo aticonfig --initial -f

to create the configuration file (/etc/X11/xorg.conf)

reboot.

Note: Plymouth (the purple boot splash screen) will look horrible. This is unfortunately unavoidable with proprietary drivers yet workaroundable.

---

