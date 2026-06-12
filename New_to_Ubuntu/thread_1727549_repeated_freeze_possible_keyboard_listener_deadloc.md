---
title: "repeated freeze: possible keyboard listener deadlock with evolution mail client?"
date: 2011-04-12
forum: New to Ubuntu
---

### Post by SandalNYC on 2011-04-12
Hi All -  
 

 I am a new Ubuntu user (about 4 months) and am have a bizarre problem I could really use some insight into.  My hardware is an Acer Aspire X3950 desktop.
 

 Some user programs which require keyboard inputs (all web browsers, open office, gedit, and probably others) spontaneously cause the keyboard and operating system to freeze.  The symptoms are that I can not type anything (although I can use the mouse).  I also cannot access any drop down lists in the control panel at the top of the desktop, and so cannot open Applications, Places, System, or the power off/user toggle.  I can still navigate the file system, access widgets and all user programs, and interact with them using the mouse.
 

 If I unplug my keyboard from the USB port, the system frees up again.  But when I do this, the Ubuntu Evolution mail client gets opened (this does not happen if I unplug the keyboard before the deadlock occurs).  If Evolution is already open, its window simply becomes active.  If Evolution is uninstalled, I get an error box saying &#8220;Couldn't execute command:evolution.  Verify that this is a valid command.&#8221;
 

 Is unplugging the keyboard somehow making a call to Evolution, or is this call being generated elsewhere and deadlocking the keyboard?
 

 The deadlock happens spontaneously; sometimes I get 10 mins of active use and sometimes only 30 seconds.  But I am always typing when it happens.

 

 I have been using this computer with this os for 4 months without any such problem.  I never use Evolution and didn't even have it configured until I began trouble shooting this problem.  Yesterday afternoon it came out of nowhere.  I have tried reinstalling Ubuntu 10.04 from the disk, and also upgrading to 10.10, still the problem persists.
 

 Please help!

---

### Post by jtarin on 2011-04-12
> I have tried reinstalling Ubuntu 10.04 from the disk, and also upgrading to 10.10, still the problem persists.Have you tried another keyboard or USB port? Makes me believe its a hardware problem.
Depending on how your menu is setup under "Administration" there is an item for "Keyboard". Bring that up and check to see that under the "typing break tab" that the box is unchecked.(see attachment)

---

### Post by SandalNYC on 2011-04-12
I have tried plugging into a different USB port, still the same problem.  I can try getting my hands on a different keyboard - but I've been using this keyboard without problems since January so why now?

That box is unchecked, but thank you for the suggestion.

This thing where it prompts the Evolution mail client must be clue, right?  Still very perplexed...

---

### Post by jtarin on 2011-04-12
> **SandalNYC said:**
> I have tried plugging into a different USB port, still the same problem.  I can try getting my hands on a different keyboard - but I've been using this keyboard without problems since January so why now?

That box is unchecked, but thank you for the suggestion.

This thing where it prompts the Evolution mail client must be clue, right?  Still very perplexed...
New keyboard in January? What happened to the old one? I can't begin to answer the why of hardware failure.
As to Evolution the only association I know of with keyboard on the matter of launching is the e-mail key.....which is not present on all keyboards.Let's try to rule out a hardware problem before we proceed. What are the specs on the computer you are using and age?

---

### Post by jtarin on 2011-04-12
Do you have a USB to PS2 adapter to try?

---

### Post by jtarin on 2011-04-12
Here's a [link]("http://www.ubuntugeek.com/how-to-fix-usb-stops-working-problem-in-ubuntu.html") which some found to solve their problems. Read the "comments" section for additional advice and methods.

---

