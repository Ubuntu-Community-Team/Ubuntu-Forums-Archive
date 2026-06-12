---
title: "How do I get Ubuntu to automatically recognize a printer?"
date: 2010-06-18
forum: New to Ubuntu
---

### Post by Keith Myers on 2010-06-18
New user to Linux. Is there a way to get Ubuntu 10.04 LTS to automatically recognize a Brother HL-1440 laser printer hooked up via USB?  I always have to physically unplug the USB cable and replug it to get Ubuntu to recognize that it is there.  It could be something to do with the printer I suppose since I have to do the same thing whenever I boot into my main OS, eComStation 1.05. I was just wondering if there was some Linux utility to automatically probe and tickle the printer so that Ubuntu automatically recognizes it when I boot into Linux.  Thanks in advance for any suggestions.

Keith

---

### Post by cariboo on 2010-06-18
Do you have it properly setup through System->Administration->Printing? I have a HL-5250DN that is auto detected on the network and the drivers are automagically downloaded and installed.

---

### Post by BandD on 2010-06-18
I have the same printer and (as cariboo907 suggested) after going to System --> Administration --> Printing.  Then clicking on "add"  and adding the Brother, it is always good to go whenever I need it.

---

### Post by Keith Myers on 2010-06-20
Hi All, yes the printer is setup in System/Administration/Printing.  It was discovered the first time I installed the OS and unplugged and plugged in the printer.  The problem is that until I physically unplug and plug in the USB cable each time I boot the OS fresh, the printer is not seen.  I always forget to do this and wonder why my first print job is taking so long to spit out.  Once the printer is discovered by unplugging and replugging the USB cable, the printer is always available and shows up as a system resource.  It's invisible otherwise.

Keith:confused:

---

### Post by Georgia boy on 2010-06-20
Check out this thread and see if it is something that will help you. Mine kept disappearing all the time and this helped me to always show upon start up. Hasn't disappeared since doing this so far. Knock on hard head.

[http://ubuntuforums.org/showthread.php?t=1500806](http://ubuntuforums.org/showthread.php?t=1500806)

Hopefully it contains what you're looking for.

Tom

---

### Post by Keith Myers on 2010-06-21
Thanks for the thread. Wow!  I won't do that again.  I tried the last suggestion about editing  the rc.local file to add starting the cups service and all subsequent  reboots left me at the command line and no way to start the graphical  gnome system.  After I figured out how to edit the file again from the  command line and remove the service cups restart line I was able to get back to a graphical boot.  Anyways, it didn't help, I still don't get the printer started until I physically unplug an replug the USB cable.  Any other suggestions?

Keith

---

### Post by Georgia boy on 2010-06-21
I followed Morbius1's suggestion. I didn't try the last one. So far my HP has been showing each time when I want to use it or even if I just go to the systems printing and look. No complaints on that yet. I too had to physically disconnect/reconnect a few times,didn't stay. Then got tired of doing the sudo cups thing each time I wanted to print. When I followed the suggestion by Morbius1 I had no further problems knock on wood. 
Sorry that the thread didn't help.Maybe someone else has something that will help you. Keep at it, something will show up to help.

Tom

---

### Post by Keith Myers on 2010-06-24
Thanks GeorgiaBoy for your last post.  With your reported success, I went back to the thread and looked at the posted technique you were successful with and I tried that.  I was successful too just now with CUPS being active when I rebooted.  I was real scared since the last try left me with a system state that I couldn't deal with and I was real panicked since I don't have any knowledge of how to get out of that predicament since I am so new to Linux.  Wouldn't have fazed me over in eComStation since I am so familiar with that OS.  The method I tried in the thread seemed the most logical to me since that is how I would have accomplished the task over in eCS.  I am closing this problem as solved now.

Thanks, Keith

---

### Post by Keith Myers on 2010-06-29
Well, I guess that the problem was not really solved.  It seemed to work the first time I rebooted after making the if-up.d/cups file.  Now it's back to not starting CUPS as a service again and the printer not being seen.  I still have to unplug the USB cable to get the printer working again.  I want to know if replacing the stock Ubuntu LTS 10.04 kernel with the latest mainline kernel 2.6.34-020634-generic causes the fix to not work?

Keith:confused:

---

