---
title: "scheduling program and OS shutdown"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by kenmac2 on 2009-07-23
Hi folks,
 I've just joined this Forum, having decided to use Unbuntu for a specific project. (I'm normally an XP user)
 I am in the process of replacing an older PC running Win 98, serving as a continuous slideshow in a museum.
 It uses Open Office/Impress and is scheduled using  a program called Somnifero.
 The replacement PC is an IBM P4 and we have decided to try Ubuntu as the OS, mainly because it is free, and won't require any of the Museum's hard won funds.
 So, I'm on a steep learning curve here.
 I've downloaded V9.04 and installed it OK.
I also have the Pocketbook .pdf.

 

 The museum has mains power on for about 8 hours each day, so the program needs to scheduled on and off, and the OS shutdown before the power goes off.
 Somnifero normally handles this, but this is a Windows based program.
 My first question is: 



 Can Ubuntu be configured to automatically start up the slideshow after bootup, and then later close the program and shutdown the OS.
 If so, please point me in the right direction.
 

 

 

 kenmac2

---

### Post by kpkeerthi on 2009-07-23
[https://help.ubuntu.com/community/CronHowto]("https://help.ubuntu.com/community/CronHowto")

---

### Post by kenmac2 on 2009-07-23
Thanks for the link.
Cron seems fairly straight forward.
I had a play with the Editor and have some more questions:
How do you "save"  a Crontab entry - there doesn't seem to be an option for it.
Also, what commands would be used for:
1... to open OpenOfficePresentation?
2... close the program
3... shutdown the OS

kenmac2

---

### Post by kpkeerthi on 2009-07-23
1. Check 
```
soffice --help
```. Write the above command in a terminal window (command prompt)

2. killall <program> 
3. halt or shutdown -h now

Refer to manpage for more info
```
man killall
man halt
man shutdown

```

---

### Post by kenmac2 on 2009-07-23
Thanks for the prompt reply.
What about the action required to save the Crontab?

kenmac2

---

### Post by kpkeerthi on 2009-07-23
Refer to the [Tips]("https://help.ubuntu.com/community/CronHowto#Tips") where it explains how to change the editor used for crontab.

You could use nano or gedit for editing the crontab. Saving files with these editors is intuitive. nano lists the options at the bottom of the editor and gedit has GUI menu items.

---

### Post by kenmac2 on 2009-07-24
When I do a "crontab -l" it says there is no crontab for that username, which is to be expected as it is a new install.
When I save a script in the nano editor, it seems to save it to a temp file (shown at bottom of window.)
Does this file need to be saved to the Crontab folder in the root?
Or does another folder need to be created?
In other words, how do I initiate a  user Crontab system.
I tried to look in the root crontab folder, but it is locked out (no permission for user)
This operation is not as easy as I expected and is getting harder by the minute!
Confusing.

kenmac2

---

### Post by kenmac2 on 2009-07-24
OK, I've manged to work out how to generate the new crontab's and have managed to program the PC shutdown successfully.
I can call Soffice to open OpenOffice, but how (what command) do I open the Presentation (Impress) part of Oo automatically?
After that works, a slideshow file (.odp) needs to be started automatically with a "norestore" option - suggestions?

Ken Mac

---

