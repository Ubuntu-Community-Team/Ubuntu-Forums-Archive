---
title: "Starting up boot message. Please help!"
date: 2010-09-02
forum: New to Ubuntu
---

### Post by Swami_Sez on 2010-09-02
I'm sure this is a common problem which has already been posted but I couldn't find it in the search bar. Here's my problem
 
When I power up my laptop I get the message:
 
Starting up...
usplash: Setting mode 1024x768 failed
usplash: Using mode 800x600
 
Ubuntu 8.04.1 antione tty1
 
antione login:
 
 
All help would be greatly appreciated. Thanks.

---

### Post by dash86no on 2010-09-03
> **Swami_Sez said:**
> I'm sure this is a common problem which has already been posted but I couldn't find it in the search bar. Here's my problem
 
When I power up my laptop I get the message:
 
Starting up...
usplash: Setting mode 1024x768 failed
usplash: Using mode 800x600
 
Ubuntu 8.04.1 antione tty1
 
antione login:
 
 
All help would be greatly appreciated. Thanks.

Sounds like X is failing to start on your machine. Are you using 8.04 desktop version of Ubuntu? Have you considered using the latest 10.04 release?

---

### Post by Swami_Sez on 2010-09-03
> **dash86no said:**
> Sounds like X is failing to start on your machine. Are you using 8.04 desktop version of Ubuntu? Have you considered using the latest 10.04 release?
 
I was using this layout version of 8.04 Ubuntu [http://www.automaticable.com/wp-content/uploads/2009/03/dell-ubuntu-desktop.png](http://www.automaticable.com/wp-content/uploads/2009/03/dell-ubuntu-desktop.png)  I dont think it was the desktop version. 
 
And I tired to update to 10.04 but during the update, something got deleted that shouldn't have, and it went from me having a blank desktop with only the background showing to the startup boot message I posted above. And I would just be happy to simply have my 8.04 version back since I cant even get to the desktop screen now.

---

### Post by Swami_Sez on 2010-09-13
bump* Still need help. Thanks ppl

---

### Post by amjjawad on 2010-09-13
It could be a problem with your Video Card's Driver. Have you tried to update it?

Could you boot from Ubuntu 10.04 Live CD? try that and see if you get the same problem. Don't install it, just choose TRY and see what you get.

---

### Post by Swami_Sez on 2010-09-13
> **amjjawad said:**
> It could be a problem with your Video Card's Driver. Have you tried to update it?
 
Could you boot from Ubuntu 10.04 Live CD? try that and see if you get the same problem. Don't install it, just choose TRY and see what you get.
 
 
if thats the case then Ill have to go out and buy an external cd drive since mine doesnt have one? or is there a site that has the Ubuntu 10.04 Live on it I can transfer to my laptop through USB? (If that makes sense) Sorry Im not much of a wiz on these kind of things :???:

---

### Post by amjjawad on 2010-09-13
> **Swami_Sez said:**
> if thats the case then Ill have to go out and buy an external cd drive since mine doesnt have one? or is there a site that has the Ubuntu 10.04 Live on it I can transfer to my laptop through USB? (If that makes sense) Sorry Im not much of a wiz on these kind of things :???:

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

then: Burn your CD or create a USB drive
Click on USB stick then show me how.

This will be very helpful so you don't have to buy anything :)

---

### Post by Swami_Sez on 2010-09-13
> **amjjawad said:**
> [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
 
then: Burn your CD or create a USB drive
Click on USB stick then show me how.
 
This will be very helpful so you don't have to buy anything :)
 
This is why I love this community! Im downloading it right now to my USB, I'll keep you updated. Thx

---

### Post by amjjawad on 2010-09-13
> **Swami_Sez said:**
> This is why I love this community! Im downloading it right now to my USB, I'll keep you updated. Thx

Trust me, this is why I'm using Ubuntu because I adore this forum ;)

Let me know what will happen and good luck!

---

### Post by tarps87 on 2010-09-13
Have you tried starting x yet?
```
startx
```

---

### Post by Swami_Sez on 2010-09-13
Thanks for the StartX command:p Now I got to the desktop page but my icons are gone from this shortcut panel [[COLOR=#000000]http://www.automaticable.com/wp-cont...tu-desktop.png[/COLOR]]("http://www.automaticable.com/wp-content/uploads/2009/03/dell-ubuntu-desktop.png") and top panel is gone as well.
 
However when I popped in the USB with Ubuntu 10.04 on it, it opened up and I have it open in Archive Manager but am unsure where to go from there, since I dont want to mess things up further.

---

### Post by amjjawad on 2010-09-13
> **Swami_Sez said:**
> Thanks for the StartX command:p Now I got to the desktop page but my icons are gone from this shortcut panel [[COLOR=#000000]http://www.automaticable.com/wp-cont...tu-desktop.png[/COLOR]]("http://www.automaticable.com/wp-content/uploads/2009/03/dell-ubuntu-desktop.png") and top panel is gone as well.
 
However when I popped in the USB with Ubuntu 10.04 on it, it opened up and I have it open in Archive Manager but am unsure where to go from there, since I dont want to mess things up further.


You need to BOOT from your USB ;)

---

### Post by Swami_Sez on 2010-09-13
Instead of getting the Welcome Screen like the Show Me How says I should see, I still am getting taken, not to the usplash failed screen, but the 
"Ubuntu 8.04 antione tty1
antione login:" screen
 
I just got this as a gift for school and already am messing it up, so I apologize for my lack of knowledge please bear with me :)

---

### Post by amjjawad on 2010-09-13
> **Swami_Sez said:**
> Instead of getting the Welcome Screen like the Show Me How says I should see, I still am getting taken, not to the usplash failed screen, but the 
"Ubuntu 8.04 antione tty1
antione login:" screen
 
I just got this as a gift for school and already am messing it up, so I apologize for my lack of knowledge please bear with me :)

No worries.
Do you know how to boot from your USB? how to change your BIOS settings so that you can boot directly from your USB instead of your Hard Disk?

---

### Post by Swami_Sez on 2010-09-13
> **amjjawad said:**
> No worries.
Do you know how to boot from your USB? how to change your BIOS settings so that you can boot directly from your USB instead of your Hard Disk?
 
No and no

---

### Post by Swami_Sez on 2010-09-13
> **amjjawad said:**
> No worries.
Do you know how to boot from your USB? how to change your BIOS settings so that you can boot directly from your USB instead of your Hard Disk?
 
Creating a Bootable Ubuntu USB by following this [http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/](http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/)
 
In progress of creating one right now...

---

### Post by amjjawad on 2010-09-13
> **Swami_Sez said:**
> No and no

I think there are 2 options
A- you need to choose which device you want to boot from (CD, HDD, FLOPPY, etc)
B- then there is another option to set the priority of HDD booting just like this on: [http://i53.tinypic.com/2lcfns.jpg](http://i53.tinypic.com/2lcfns.jpg)

You need to choose USB as your bootable device then change the HDD priority.

I guess you know who to get inside BIOS and how to change these options? It depends on your MB and your PC/Laptop but usually it's "Del" key that will get you into BIOS. As for changing the boot devices, I think it's the 2nd option in the BIOS menu.

---

### Post by Swami_Sez on 2010-09-13
> **amjjawad said:**
> I think there are 2 options
A- you need to choose which device you want to boot from (CD, HDD, FLOPPY, etc)
B- then there is another option to set the priority of HDD booting just like this on: [http://i53.tinypic.com/2lcfns.jpg](http://i53.tinypic.com/2lcfns.jpg)
 
You need to choose USB as your bootable device then change the HDD priority.
 
I guess you know who to get inside BIOS and how to change these options? It depends on your MB and your PC/Laptop but usually it's "Del" key that will get you into BIOS. As for changing the boot devices, I think it's the 2nd option in the BIOS menu.
 
Thank you, I'll work on this a bit more then I have to get ready for work, but I will be on later with updates. Thanks again!

---

### Post by amjjawad on 2010-09-13
> **Swami_Sez said:**
> Thank you, I'll work on this a bit more then I have to get ready for work, but I will be on later with updates. Thanks again!

You most welcome :)

Take your time and I'll be around if you need anything ;)

---

### Post by amjjawad on 2010-09-14
Hey,

Did you fix it? :)

---

