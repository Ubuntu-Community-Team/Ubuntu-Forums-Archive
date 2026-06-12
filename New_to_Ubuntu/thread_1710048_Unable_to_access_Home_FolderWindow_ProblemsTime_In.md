---
title: "Unable to access Home Folder/Window Problems/Time Incorrect"
date: 2011-03-19
forum: New to Ubuntu
---

### Post by tapplewhack on 2011-03-19
Hello, I am fairly new to Ubuntu and I have to say I enjoy it a lot. I've just had a few (maybe just bugs) issues with it. For starters, I cannot access my Home folder from "Places" (it's not just the home folder, it's everything except for "Computer"). Also, something is wrong with the size of my screen. It is possible for me to drag a window past the point that I can click the top bar to close it or to drag it back. Lastly, every time I restart or log back in after suspending the time is always an hour ahead.

I think some more description is needed for the first one. Though many people have had this problem, I think that my situation has a different cause. I have tried all of the solutions suggested to other people that worked for them and none of them work for me. Typing "sudo apt-get install nautilus" simply says that nautilus is already the newest version. It goes on to say that there are two linux headers that are no longer required and that I can type "apt-get autoremove" can remove them. If I type it, however, it gives me two errors and then asks me "are you root?" If I type root, it says "The program root is currently not installed. You can install it by typing sudo apt-get install root-system-bin." (I don't know if this last part means anything, but I have seen root-system-bin mentioned in other solutions.) Also, if it helps at all in finding a solution, I can access everything (Home, Documents, etc.) by going to Places>Computer, which then opens up the normal explorer window. I can click on home, documents, etc. in this window and access them just fine.

I am running on a Gateway NV78. I have Windows 7 and Ubuntu on my computer, and I switch back and forth regularly to watch Netflix and manage my iPod. I just updated Ubuntu, so it should be up to date.

Also, just a quick question: Is it normal for it to ask me to unlock my "default" keyring 3 times every time I log on?

---

### Post by fabricator4 on 2011-03-19
> **tapplewhack said:**
> Hello, I am fairly new to Ubuntu and I have to say I enjoy it a lot. I've just had a few (maybe just bugs) issues with it. For starters, I cannot access my Home folder from "Places" (it's not just the home folder, it's everything except for "Computer").


Go to a folder on your desktop (make one if you don't have one already), right click on the folder and select "open with other application".  Make sure the box for "Remember this application for folder files" is checked, then select "file browser" in the list.  This should fix it - you've just lost the default association for opening folders is all...

> 
 Also, something is wrong with the size of my screen. It is possible for me to drag a window past the point that I can click the top bar to close it or to drag it back.


That's a feature, not a bug.  To drag it back hold down the <alt> while clicking (anywhere) and dragging the window back.


> 
 Lastly, every time I restart or log back in after suspending the time is always an hour ahead.


There's something wrong with your time/date settings. Either your timezone (location) is set to an hour later than your local time, or it's set to add daylight saving that is not used in your area.

> 
Also, just a quick question: Is it normal for it to ask me to unlock my "default" keyring 3 times every time I log on?

Only if you type it wrong the first two times. :-)

Chris.

---

### Post by tapplewhack on 2011-03-19
> **fabricator4 said:**
> Go to a folder on your desktop (make one if you don't have one already), right click on the folder and select "open with other application".  Make sure the box for "Remember this application for folder files" is checked, then select "file browser" in the list.  This should fix it - you've just lost the default association for opening folders is all...



That's a feature, not a bug.  To drag it back hold down the <alt> while clicking (anywhere) and dragging the window back.




There's something wrong with your time/date settings. Either your timezone (location) is set to an hour later than your local time, or it's set to add daylight saving that is not used in your area.



Only if you type it wrong the first two times. :-)

Chris.

That solved the first and second problems. =D There's still a problem with the time, though. Every time I log on I set it to the right time in preferences, but when I log off and then log back on it switches back. It stays set for my timezone, but it still says the time is an hour ahead.

---

