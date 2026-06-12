---
title: "help me speedup my boottime"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by anantshri on 2010-05-26
Hi All,

I was having a preety stable system till 9.10 and then i did an autoupgrade to 10.04 and no i am having startup time in the range of 2 minutes.

attaching the bootchart png file can any good soul help me in understanding the chart and how can i use it to optimize my installation.

boot chart link : [http://anantshri.info/ubuntu/bootchart.png](http://anantshri.info/ubuntu/bootchart.png)

attachment is not working.

---

### Post by anewguy on 2010-05-26
You may need to re-do your image.  I clicked on it, and even when I use Firebirds' ctrl+ to enlarge the image as much as possible, it is completely unreadable.

Dave ;)

---

### Post by -humanaut- on 2010-05-26
I can't read your boot chart. It might be because you upgrade from 9.10--10.04 there has seemed to be a excess of problems dist-upgrading this time around.

---

### Post by philinux on 2010-05-26
@anantshri, see the forum sticky in General Help.

---

### Post by anantshri on 2010-05-26
thanks for the quick replies.


PNG file in full glory at this link

[http://anantshri.info/ubuntu/bootchart.png](http://anantshri.info/ubuntu/bootchart.png)

@philinux : checked the sticky and that's something i already checked but nothing in common to my configuration.

floppy drive not enabled in bios.


the main problamatic area is the time since plymouth stops display and autologin takes place and i get my desktop the time taken is in somewhere around 1 min 30 seconds per my stop clock.

will boot chart be of any help in this case.

i tried stopping most of the background processes as well as startup applications too. but nothing helps much.

note : my gnome session has following addon's 
Dockbarx and USP. do they make a difference.

and ya i am using x64 version.

---

### Post by migs73 on 2010-05-26
I upgraded from 9.10 to 10.04 and had a near 2 minute boot. Did a clean install instead and boot time dropped to 45secs. It is worth trying.

---

### Post by anewguy on 2010-05-26
+1 on the clean install.  I never did the upgrade, just saved what I wanted and did a complete clean install - it always seems to work out better that way.  My boot time is about 35 seconds.


dave ;)

---

### Post by laidback on 2010-05-26
Clean install here too, boot time of 58+ secs, not a lot better than 9.04 for me.

---

### Post by oldsoundguy on 2010-05-26
Remember boot time is actually TWO segments .. POST (Power On Self Test) which is bios chip related and then the operating system loads.  The more hardware plugged (especially USB items that have to be sorted out) into the computer, the longer the POST portion of boot up as all of that has to be recognized and set up.  
After a relative long POST on the computer that has all the crud plugged into it .. it takes about 10 to 20 SECONDS for the OS to load to the password screen for me.

---

### Post by anewguy on 2010-05-26
Hummmm...I was talking about the actual boot time of Ubuntu AFTER the POST and the grub menu selection is made.  For me, that's about 35 seconds.  I only have an AMD64 3200+ and it's on a MSI neo board that takes a long time to go through the POST before it gets to the grub menu.


Dave ;)

---

### Post by anantshri on 2010-05-27
I am having the max delay from plymouth disappearing to desktop appearing time.


going for a clean install but this should be something that needs to be taken up.

---

### Post by nhasian on 2010-05-27
on a fresh installation of Ubuntu 10.04 on my 2.5 year old notebook without any tweaking gets me to the desktop in 9.5 seconds.  I have a Corsair P128 SSD so that helps :)  I imagine it will boot even faster with Ubuntu 10.10

---

### Post by anantshri on 2010-05-28
i am averaging at around 30-35 seconds boot time from grub entry to workable desktop.


has anybody ever been able to find out the reason of this behaviour. fresh install always faster then upgrade.

---

### Post by oldsoundguy on 2010-05-28
> **anantshri said:**
> i am averaging at around 30-35 seconds boot time from grub entry to workable desktop.


has anybody ever been able to find out the reason of this behaviour. fresh install always faster then upgrade.

Not always .. this time I upgraded on line .. 3 boxes.  (DESKTOPS NOT LAPTOPS)  Had minor issue on the 8.04 to 10.04 with the display  ..seems the upgrade hauls the OLD xorg in and just adds to it .. confusing the video card.  Quickly solved by doing a sudo rm xorg and re-booting.  And I lost Skype.. it won't turn the camera or audio ON (works fine in cheese) 

Boot time .. amazingly fast .. MUCH faster than the previous builds.  

But again, none of these are proprietary laptops.

---

### Post by migs73 on 2010-06-11
My previous post saying my boot was 45s was from pressing the on button. The BIOS screen is up for about 17s of this. After that a blinking cursor for about 10s then the purple ubuntu background, then into my desktop.
I think that means an ubuntu boot time of 25-30s?

---

