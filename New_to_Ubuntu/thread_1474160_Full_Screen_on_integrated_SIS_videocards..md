---
title: "Full Screen on integrated SIS videocards."
date: 2010-05-05
forum: New to Ubuntu
---

### Post by Karmic Alice on 2010-05-05
Hello everybody! 

 I am a newbie @ linux and I LOVE IT. I love Ubuntu and I love to love it. Everything works well with my P4@2.40Ghz and Ati Raden HD 3650 AGP. 

 But as I got so in love with ubuntu I try all the peps around to use it. The most receptive till now was my almost 5 years old nephew. (Of course, with Qimo installed in LYNX to catch him:P). The problem is the other machine is also P4 but 1.60 with 512 RAM and a da*n SIS board. With a SIS onboard video card. I didn't knew the issue about SIS not supporting at all LINUX. Ubuntu 10.04 works pretty good on kid's pc. But He uses it most of the times for videos. And even if videos in firefox are ok while small, as soon as full screened everything freezes for ages. And if is not, is just soooo9 damn slow. maximum 2 frames/second. Is more like a slideshow. A bad one...

The thing is I don't want to invest in a video card now. And still want to keep ubuntu on it. And install windows 2000 as alternative OS only for when he wants online TV or downloaded movies. I run out of CD's (but mostly is a challenge, 'cos tomorrow I can have CD's anyway...) and I want to install winddows 2000 next to ubuntu FROM .ISO that is already saved in that PC.

What I did: 
With the live cd, I resized the space. The hdd is a 20 gb old one. Now I kept 9 Gb for ubuntu and the rest I formated it with NTFS and the same live CD and GParted.

Now I am stuck and would appreciate your help in this. Can I install windows in that system from the .iso file downloaded today? Without CD?

I do have several USB thumbs. But the BIOS can't see them. Because is 2002 and it seems I can't upgrade it. 

Thanks so much for your patience reading my "story" and thanks for your help. (Pleaseee?:P):KS

---

### Post by ubunterooster on 2010-05-05
[http://www.sis.com/download/agreement.php?url=/download/](http://www.sis.com/download/agreement.php?url=/download/)
I linked from
[http://www.linuxbasis.com/drivers.html#grap](http://www.linuxbasis.com/drivers.html#grap)

I'm not sure what card you use but the fact that linuxbasis linked to it means it is likely useful for you.

---

### Post by Karmic Alice on 2010-05-05
> **ubunterooster said:**
> [http://www.sis.com/download/agreement.php?url=/download/](http://www.sis.com/download/agreement.php?url=/download/)
I linked from
[http://www.linuxbasis.com/drivers.html#grap](http://www.linuxbasis.com/drivers.html#grap)

I'm not sure what card you use but the fact that linuxbasis linked to it means it is likely useful for you.


Been there much before asking. THANKS, but is just for redhat and I am a newbie and have no idea how to compile or make it work for ubuntu. I even bet 80% of ubuntu users neither:). If you suggest I should install redhat I also thought of it, but then it won't be attractive to the kid. See? Must be for ubuntu or foresight. (or any other distro for small children)

> 
I'm not sure what card you use
 SiS650 & SiS740 series

---

### Post by Karmic Alice on 2010-05-05
Anybody? Pretty please? Win2000 from iso directly from ubuntu? in a different partition? ](*,)

---

### Post by Karmic Alice on 2010-05-06
bump

---

### Post by shebaw on 2010-05-06
I dont think you can install windows from the disk image without burning it on a cd or using USB thumb drives(which your motherboard doesn't support). Anyways, why don't you try to install windows on a virtual machine. You can download and use VirtualBox for free and you can use windows from a virtual machine whenever you want to download/watch videos in your case. Hope this helps.

---

### Post by Karmic Alice on 2010-05-06
> **shebaw said:**
> I dont think you can install windows from the disk image without burning it on a cd or using USB thumb drives(which your motherboard doesn't support). Anyways, why don't you try to install windows on a virtual machine. You can download and use VirtualBox for free and you can use windows from a virtual machine whenever you want to download/watch videos in your case. Hope this helps.


Hello! Thank you! Can you tell me please if my drivers would be recognized in a virtual machine? I never used a virtual machine. I am not even sure what to search for. I checked vmware and was not for free... Of course I would prefer NOT to install from disk. Just to have an alternative for the videos.

I will take virtualbox:) Thanks again!

---

### Post by shebaw on 2010-05-06
Download virtualbox and install windows 2000 from the disk image, it will be faster. Virtualbox comes with guest addons cd that installs the necessary drivers and extras on the virtual machine, it takes care of the drivers so just install windows 2000 on the virtual machine.

---

### Post by Karmic Alice on 2010-05-07
> **shebaw said:**
> Download virtualbox and install windows 2000 from the disk image, it will be faster. Virtualbox comes with guest addons cd that installs the necessary drivers and extras on the virtual machine, it takes care of the drivers so just install windows 2000 on the virtual machine.
  Thanks so much! I will try it now (yesterday no time) and keep u updated. Thank you

---

### Post by Karmic Alice on 2010-05-07
OK. Sorry for double post, but the latest virtualbox is for Karmic. And I have 10.04. I will try anyways but if there are no packages I dont know how it will work. They ask me to edit sources.list. :(

---

### Post by sandyd on 2010-05-07
```

gksudo gedit /etc/apt/sources.list

```

add this on a new line at the bottom of the file.
```

deb http://download.virtualbox.org/virtualbox/debian karmic non-free

```
```

wget -q http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install virtualbox-3.1

```

done.

im using the karmic virtualbox on lucid w/o problems

---

### Post by Karmic Alice on 2010-05-07
> **carlee said:**
> ```

gksudo gedit /etc/apt/sources.list

```add this on a new line at the bottom of the file.
```

deb http://download.virtualbox.org/virtualbox/debian karmic non-free

``````

wget -q http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install virtualbox-3.1

```done.

im using the karmic virtualbox on lucid w/o problems
  Hey! Thanks for your reply. What I did was install the virtualbox beta for lucid. And is ok. The problem is i can't manage to give me more than 800x600. So no full screen really. Besides SIS gives me a really hard time with the drivers. I took them and the message is no videocard was found on my system. 

I thank you all for your help. I will install a fresh 10.04 and XP from cd.

I also want to mark this thread as solved. Because at least I know virtualbox is working and is just  question of setting it correctly so it can display 1280x1024.

Thank you again.;)

---

