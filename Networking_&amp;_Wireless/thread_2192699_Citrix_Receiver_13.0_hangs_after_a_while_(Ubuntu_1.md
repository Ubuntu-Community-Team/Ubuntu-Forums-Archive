---
title: "Citrix Receiver 13.0 hangs after a while (Ubuntu 13.10 x86_64)"
date: 2013-12-09
forum: Networking &amp; Wireless
---

### Post by Zeppe on 2013-12-09
Hi all, I have upgraded Citrix Receiver to version 13 and it seems to work fine, except that after like 5 minutes the whole session hangs. Sometimes neither mouse nor keyboard work, sometimes it is as if the CTRL key was constantly pressed (mouse works). I cannot find any diagnostic. I have installed the deb package using the suggestions in [https://help.ubuntu.com/community/CitrixICAClientHowTo]("https://help.ubuntu.com/community/CitrixICAClientHowTo"). 

Since then, reverting to version 12.1 (both 32 and 64 bits) has changed nothing. I therefore suspect that it issomething to do with what I did upgrading.

If anybody has similar experiences, can you please share? thanks.

---

### Post by daniel-matthis on 2014-01-08
I have run into a similar issue. I can generally get it to happen any time I press CTRL + ALT. After that things git strange. My mouse keeps working and the issue will persist even after I disconnect and reconnect with Citrix on a windows system. However at least then I can press CTRL a couple of times and it generally will return to working normally. However it seems to cause some instability issues with Windows 7 that is loaded on my Citrix VM as the VM will be come entirely unresponsive and have to be restarted.

If i just connect from a Windows system, it just works and doesn't have any issue. My two Ubuntu 13.10 systems have the issue.

I have been able to get back to the session if I lock ubuntu and then authenticate back into the systems and press CTRL+ALT again. Then I can start typing again.

Still I didn't have this issue with Ubuntu 13.04.

PS: If I hit CTRL + ALT + DEL and cancel out I can usually regain my keys.

PSS: If I hit CTRL + ALT + RETURN I can get it to cause the problem every time.

---

### Post by daniel-matthis on 2014-01-23
I have discovered some more information. 

"super key" will essentially lock an never release thus messing up all keys after that. Only way I have found to correct it is to either reboot the VM or load it on a windows system.

---

### Post by hyrschall on 2014-01-31
I'm having a very similar issue too, n looking as well for an answer. Citrix will be running fine, then it will start acting like ALT is being held down, and respond as such in no matter what application I try to type in. I'm going to try some of the things you did Daniel, and see if I can get some of the same responses. I'm just starting to dig into it and see what could be causing it. I'll be following this thread to see if there's an answer and if I find a solution or additional information, like your follow up post on super key, I'll be sure to post it here.

---

### Post by hyrschall on 2014-01-31
> **Zeppe said:**
> Hi all, I have upgraded Citrix Receiver to version 13 and it seems to work fine, except that after like 5 minutes the whole session hangs. Sometimes neither mouse nor keyboard work, sometimes it is as if the CTRL key was constantly pressed (mouse works). I cannot find any diagnostic. I have installed the deb package using the suggestions in [https://help.ubuntu.com/community/CitrixICAClientHowTo](https://help.ubuntu.com/community/CitrixICAClientHowTo). 

Since then, reverting to version 12.1 (both 32 and 64 bits) has changed nothing. I therefore suspect that it issomething to do with what I did upgrading.

If anybody has similar experiences, can you please share? thanks.

I had pretty much the same issue. What I realized is, that with my situation anyways, the Citrix Receiver was running in the browser when I first signed in and started and it would initiate the Citrix Receiver. However the Citrix Receiver was not continuing to run, it was crashing, and only running off the in browser Citrix Receiver and once the in browser session timed out, which is about 5 min the whole thing would lock up and crash. I ended up fixing my issue by recompiling the Citrix Receiver and discovered some simple mistakes I made which was causing it to fail. Specifically for me I had tried to install and compile using libxm12:i386 and it is libxml2:i386 and the other one I messed up was libcur13:i386 and it's actually libcurl3:i386. So double check the changes made to the deb package, cause it doesn't sound like the Citrix Receiver is continuing to run after you log on.

---

### Post by hyrschall on 2014-01-31
> **daniel-matthis said:**
> I have discovered some more information. 

"super key" will essentially lock an never release thus messing up all keys after that. Only way I have found to correct it is to either reboot the VM or load it on a windows system.

Not sure how much this will help, but I found this on how to turn off the super key, [http://askubuntu.com/questions/105558/how-do-i-disable-the-super-key](http://askubuntu.com/questions/105558/how-do-i-disable-the-super-key). I don't know enough about the tool to use it effectively though.

---

### Post by tpdene on 2014-02-16
I've got exactly the same issue. Are there any solutions to solve the problem?

EDIT: Now it's working. I tried this [http://askubuntu.com/questions/264361/where-is-show-position-of-the-mouse-when-the-control-key-is-pressed](http://askubuntu.com/questions/264361/where-is-show-position-of-the-mouse-when-the-control-key-is-pressed) (the answer with dconfig) and set the value to "GERMAN" at "KeyboardLayout" in the wfclient.ini file. Finally I restarted my computer and now it works all fine. Unfortunately I don't know the responsible change that solve the problem ...

EDIT: Unfortunately it doesn't work anymore. Strange behaviour ... :-(

---

