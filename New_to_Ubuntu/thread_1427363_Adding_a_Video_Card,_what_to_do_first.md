---
title: "Adding a Video Card, what to do first?"
date: 2010-03-11
forum: New to Ubuntu
---

### Post by hondajt on 2010-03-11
Do I download the drivers first? Then turn off, install card and restart?

That's my guess, but I wasn't sure.

---

### Post by stoneage on 2010-03-11
If you install the card first, Administration -> Hardware Drivers will autodetect, search and make a recommendation.

Post the make and model of the card, probably someone is already running it and will suggest which drivers are available to use.

---

### Post by hondajt on 2010-03-11
thanks. It's a MSI N9800GT. 1GB Overclocked edition. Great card.

---

### Post by Mark Phelps on 2010-03-12
If you have proprietry drivers in place when you boot, and they're the wrong drivers, it's likely you won't get a display.  In which case, you'll need to boot into a console and reconfigure your display.

So, I'd check first to see if you have proprietary drivers installed.  If so, I'd remove them and replace them with the open source drivers.

---

### Post by markbuntu on 2010-03-12
The safest way to do this is to first remove any proprietary driver and reboot into the recovery kernel and choose the fix x or fix broken packages option. This will get the generic VESA driver loaded. Shutdown the machine and unplug it.

Install the new card, check in the bios to make sure that it is the default graphics and disable the on board if you do not intend to use it. Continue the boot and do the fix x thing again. Once you are sure the new card is working properly you can install the new proprietary driver if you need/want to.

I do this a lot and I have found this to be the best method for painless gpu replacement.

---

### Post by de Bacon on 2010-03-12
First time using the forum EEK!
Since this issue is on topic, sort of, I thought it would fit here at least.
I have a new video card on the way. So I was looking over how to install it, having no experience with this after leaving the windowz world.  
I am just kind of wondering about the instructions above "reboot to a console", not sure what a console is?  sorry I am ignorant.  I have an old nvidia card now that has no real comparability with ubuntu, though it works, sort of, and has caused me difficulty over time.  Last week after an old HDD failure I decided to get some new ones and a new video card.  So I found one that research showed me is compatible. (hopefully they will all arrive later today?)  
I am thinking from what is in this thread, that I having what I think are generic drivers running the current video card, I should be able to simply replace the old card, reboot and it might work well enough to get a display at least.  
Thus, when you say boot to a console, is that saying boot to a terminal, and if so, being ignorant, I wouldn't know what to do there as far as commands etc.  I feel quite comfortable using terminal though don't really know commands well enough to do much other than change permissions. 
Any assistance would be appreciated.  

Tom

---

### Post by markbuntu on 2010-03-13
The console is also called Terminal. You can find it in the Applications/Accessories menu. If you are very new to linux you should read the tutorials in the stickies at the top of the Absolute Beginners forum. There are also many tutorials for specific tasks and to overcome specific issues in the Tutorials and Tips forum here.The Ubuntu Wiki pages are also a good resource.

---

