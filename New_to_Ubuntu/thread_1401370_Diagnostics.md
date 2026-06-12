---
title: "Diagnostics ?"
date: 2010-02-08
forum: New to Ubuntu
---

### Post by Innernet on 2010-02-08
Hi.
Is there any way to look for a log of events that will keep the reason why at any random time some applications... Open office, Totem, Firefox just grey-out, or quit, or freeze ?

Transcribing such log here for the experts to discern what is wrong, wouldn't that be a dream ?

Firefox > Tools > Error console contents ; is it informative enough ?  Or is it strictly for Firefox and will not tell hardware hiccups, Open Office  crashes... ?

With the system monitor on screen; when such grey-outs happen, what processes to look at or capture the information from ?... That is IF can be looked at in such freeze status.

There is plenty of knowledgeable collaborators here; is there any solid known fixes by checking records of failures ?

---

### Post by Cheezespread on 2010-02-08
Almost all logfiles are located under /var/log directory.
```
tail -f /var/log/messages
``` should give you a nice idea of whats happening at  the moment.I am not sure if it includes the application crashes. Hope some one clarifies that one.

I don't think I would fit the bill to answer the rest . Sorry. Some one else would be answering them shortly.

---

### Post by Innernet on 2010-02-08
Thanks.  
Checked such on the console, and it may tell something to some expert; not to one coming to the "Absolute Beginners Talk"

The warning contents on Firefox > tools > error console seem more scary; but again, how can a novice discern the hieroglyphics ?

And is very rare to see a response from the experts here telling

...go to such and such location and copy and paste the contents to your next reply to examine what is wrong and be able to suggest a fix... 

If it is not happening that way on these trouble-dealing forums, is it because is not helpful to expose such files or too few discern their meaning ?

---

### Post by nhasian on 2010-02-08
when my firefox greys out, its because my cpu is working hard doing something else like unpacking rars in the background or transcoding a video file or similar the crunches a lot of numbers.  to see what is eating up your CPU cycles, open a terminal and use the command:

```
top
```

you and quit by pressing the letter 'q' or press the letter 'k' to kill a process.

---

### Post by Innernet on 2010-02-08
Oh boy!  So yours does it too!  And you know your stuff being a developer.

Tried the "top' command;  neat.

But in order to kill a process, I would have to highlight the cpu eating process first in order to select such?  The thingy is constantly changing, when I try to highlight something it changes before hitting 'k'    ¿?

Any way to freeze the window to capture it and post for evaluation ?

Edited:   OK, found it.  after hitting K asks for the process ID to kill.

---

### Post by lovinglinux on 2010-02-08
> **Innernet said:**
> Thanks.  
Checked such on the console, and it may tell something to some expert; not to one coming to the "Absolute Beginners Talk"

The warning contents on Firefox > tools > error console seem more scary; but again, how can a novice discern the hieroglyphics ?

And is very rare to see a response from the experts here telling

...go to such and such location and copy and paste the contents to your next reply to examine what is wrong and be able to suggest a fix... 

If it is not happening that way on these trouble-dealing forums, is it because is not helpful to expose such files or too few discern their meaning ?

Firefox error console is for identifying errors in web pages, in Firefox extensions and the browser itself. That tool is mostly useful for web developers, extension developers and beta testers. You need some knowledge of xul, javascript, html, xml or css to understand some of the error reports. I wouldn't bother with it if I were you. Besides, the problems you are facing will probably not show up in that console, since is not only Firefox that is graying out.

Do you experience the same problem on other applications while Firefox is closed? It could be Firefox causing the system to become too busy and then other applications becomes grayed out.

I recommend disabling Firefox [blocking system for attack sites and web forgeries](http://lovinglinux.megabyet.net/?page_id=220#Firefox-becomes-unresponsive-%28grey%29-frequently-2), performing [database optimization](http://lovinglinux.megabyet.net/?page_id=220#Database--Optimization-1) and installing [NoScript](https://addons.mozilla.org/en-US/firefox/addon/722) and [Adblock Plus](https://addons.mozilla.org/en-US/firefox/addon/1865), to control which content is displayed. Flash content and some javascript code can cause extremely high CPU usage, so is better to avoid them when you don't need them (ads for example).

More info on the [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).
 
> **Innernet said:**
> Oh boy!  So yours does it too!  And you know your stuff being a developer.

Tried the "top' command;  neat.

But in order to kill a process, I would have to highlight the cpu eating process first in order to select such?  The thingy is constantly changing, when I try to highlight something it changes before hitting 'k'    ¿?

Any way to freeze the window to capture it and post for evaluation ?

Edited:   OK, found it.  after hitting K asks for the process ID to kill.

Open "System >> Administration >> System Monitor", then click on the CPU column header so it will sort the applications based on CPU consumption. If you have a rogue application, it will be showed at the top and will stay there as long is it using too much CPU. You can also sort by name, so they won't switch positions.

If you are unable to find an application using too much CPU, try to disable vino-server. Go to "System >> Preferences >> Startup Applications (aka Session)" and disable "Remote Desktop" then reboot.

---

### Post by oshunluvr on 2010-02-08
dmesg

---

