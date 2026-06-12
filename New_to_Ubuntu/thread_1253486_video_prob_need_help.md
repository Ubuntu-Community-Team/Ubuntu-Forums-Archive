---
title: "video prob need help"
date: 2009-08-30
forum: New to Ubuntu
---

### Post by Mtrboat on 2009-08-30
I haven't done this much at all . I had to sudo killall gdm . uninstall tne invideo driver and reinstall it .after i did that it looks like it wants to start but i get a dark screen . i just know i forgot something can anyone help ?
OK let me see first i hit ctrl alt f1 put in the user name then password . at the prompt i typed in sudo killall gdm .
i uninstalled the nvivia-linux-x86-177.82-pkg1.run driver then reinstalled it .the reason i did this is when this computer gets a kernel update it kick the screen to a 600x800 view . i want it to be 1280x768 70 hz .At first it looks like the computer is ok and going to dtart up and let you see the log in and password then there is a second  then the screen goes dark and then you are done .anyone out there have this trouble before and have a answer as to how do i get this back up and running ?

---

### Post by PorkyPie on 2009-08-30
Could you provide more detail? Like what you are trying to do? I'm sorry, but I don't seem to understand you.

---

### Post by Mtrboat on 2009-08-30
thank you for looking . I hope i can tell you what is going on with this . when i get a kernel update the video card i have is not suported i guess so i have to uninstall the driver and reinstall it . the file name is NVIDIA-Linux-x86-177.82-pkg1.run . i had to get help from a family member before but they walked me through it on the phone . i havent had to do an update for a while or i had thought .(my wifes computer) she dosent do updates for some reason . so i am left with the task of trying to fix it . i hope you can help .

---

### Post by PorkyPie on 2009-08-30
> **Mtrboat said:**
> thank you for looking . I hope i can tell you what is going on with this . when i get a kernel update the video card i have is not suported i guess so i have to uninstall the driver and reinstall it . the file name is NVIDIA-Linux-x86-177.82-pkg1.run . i had to get help from a family member before but they walked me through it on the phone . i havent had to do an update for a while or i had thought .(my wifes computer) she dosent do updates for some reason . so i am left with the task of trying to fix it . i hope you can help .

Did you try the open source drivers? Are you currently using the official Nvidia drivers?

---

### Post by NoaHall on 2009-08-30
Do not use the ones from the nvidia site! They are currently poorly supported, and do more harm than good when you don't know what you are doing. Instead, uninstall EVERYTHING to do with nvidia from your system, and then go to System -> Admin -> Hardware Drivers and select the right one.

---

