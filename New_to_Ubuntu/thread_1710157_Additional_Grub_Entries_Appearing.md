---
title: "Additional Grub Entries Appearing"
date: 2011-03-19
forum: New to Ubuntu
---

### Post by tybrownintn on 2011-03-19
I have a rather strange problem.  Every so often the number of Grub entries for ubuntu increases.  Originally I had one entry for windows and two for Ubuntu, with one being the "safe mode".  Then two additional entries got added and then today I see there are three sets of ubuntu entries.  What could be causing this and should I worry about grub getting messed up?

---

### Post by cbowman57 on 2011-03-19
If you have been adding periodic updates there will be additional entries every time a new kernel is added.

Are the entries identical or do they reflect different kernels?  If so everything is fine.

---

### Post by ChuckyDuckster on 2011-03-19
Hello,

The new entries you are seeing are different Linux Kernels installed on your system.
If you are looking to get rid of the old ones, check out this thread: [http://ubuntuforums.org/showthread.php?t=1454122](http://ubuntuforums.org/showthread.php?t=1454122)

Cheers

---

### Post by PPPilot on 2011-03-19
The easiest way to keep your GRUB cleaned up would be to install Ubuntu Tweak. This little program will allow you to a lot of other valuable things without having to go into Terminal and type a bunch of arcane code. Here is the link: [HTML]http://ubuntu-tweak.com/[/HTML]Download and Run the .deb file to install. Then open the program. On the left under Applications>Package Cleaner select Clean Kernals. The list of installed kernals will come up. The kernal you are currently using will not be on the list. You always want to keep the newest kernal on the list as a backup so hit unlock, enter your password. Then check all the entries except the newest three (3). Note: There are three (3) entries for each kernal version. Select the Cleanup button. This will erase all selected your old kernals and update your grub.cfg file.

Then check out all the other features of Ubuntu Tweak.

Next time you restart your GRUB menu will show the current kernal and the previous version for backup. Hope this helps....

---

### Post by tybrownintn on 2011-03-19
Thanks and that explains things.  I was thinking perhaps this issue was why I get a black screen and blinking cursor for so long between when I choose what to boot into and the login screen.  Unusually long wait for Ubuntu.  However, I don't think having different linux images would cause that problem.

I did not follow the instructions in the link above because I think I will adopt the practice of keeping the newest kernel and the one just before that, to be safe.  However, synaptic only lists the latest kernel image.  How can I remove the oldest one?

---

### Post by gofurygo on 2011-03-20
Do you really want to remove the oldest ones or just keep them from showing in the grub selection menu?

If you want to remove them, get ubuntu-tweak. It has a cleaning option which allows you to remove the unwanted "old" packages.

I for myself keep those packages. But I prevented grub from showing them in the selection screen. I only keep the latest and the kernel before that for selection. I used a program called "Grub customizer" (its in the reps) to uncheck the unwanted entries in the selction menu... hope that helps

---

### Post by tybrownintn on 2011-03-20
Yes, Ubuntu Tweaks, I saw that in the linked thread and am just now playing with it.  I would like to know how to do a lot of the things it does myself, but it is a very handy application.

---

### Post by Dutch70 on 2011-03-20
> **tybrownintn said:**
> Yes, Ubuntu Tweaks, I saw that in the linked thread and am just now playing with it.  I would like to know how to do a lot of the things it does myself, but it is a very handy application.

The only problem with using Ubuntu Tweak to delete old kernels, is that it deletes all of them except the latest one. When you get a kernel update that your system doesn't like, you'll be sorry you deleted ALL of the old kernels. It is recommended to keep at least 2 kernels.
(4 entries if you're counting recovery mode)

Edit: After a 2nd thought on this, you'll be able to test your newest kernel update before deciding to remove the older one. Just be sure to do that. I still prefer the option listed below.

The best way to delete old kernels is to go to Synaptic package manager and search for "linux-image-2" or just "image-2" this will show all the ones you have installed. Just tick the ones you don't want & mark them for removal & click Apply. Make sure you don't remove the wrong one.

---

### Post by tybrownintn on 2011-03-20
Yes, I did keep the second to latest kernel as well as the latest.  Ubuntu tweaks allowed me to select which ones I wanted to remove.  I had tried in synaptic but when I searched under "linux-image" it only showed the latest kernel for some reason.

---

### Post by Dutch70 on 2011-03-20
> **tybrownintn said:**
> Yes, I did keep the second to latest kernel as well as the latest.  Ubuntu tweaks allowed me to select which ones I wanted to remove.  I had tried in synaptic but when I searched under "linux-image" it only showed the latest kernel for some reason.

Good, we both learned something. Not sure why synaptic would only show the latest kernel. 

So are you satisfied that this thread is "Solved"?

---

### Post by tybrownintn on 2011-03-20
> **Dutch70 said:**
> 

So are you satisfied that this thread is "Solved"?

Yes and marked as such.  Thanks again to all.

---

