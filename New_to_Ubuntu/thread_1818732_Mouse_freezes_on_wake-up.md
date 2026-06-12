---
title: "Mouse freezes on wake-up"
date: 2011-08-05
forum: New to Ubuntu
---

### Post by toomanymatts on 2011-08-05
I am using 11.04 on a Dell Vostro V13, and find that any time my laptop goes to sleep, when it wakes back up, the mouse pointer is frozen.  Previously had the same issue with 10.10...any help greatly appreciated

- Matt

---

### Post by scruffyeagle on 2011-08-05
I don't know the fix, but I can suggest that you're more likely to get useful advice if you be more specific in your query. When you say "sleep", are you referring to use of "Suspend" or "Hibernate"? The difference is that one stores operational data in RAM while inactive, whereas the other stores all operational data on disk.

---

### Post by toomanymatts on 2011-08-05
according to my power management settings, the answer to that is 'suspend'. 

If I close the laptop, reopen it, ill get a login screen with a frozen mouse pointer (doesnt matter, I can type to login, the cursor is in the box) and the pointer remains frozen when the machine wakes up, and all i can do is press the power button and use the arrow keys to restart the machine.

edit - just did some testing - manually selected hibernate from the menu.  Takes a lot longer to wake up of course, but mouse was fine once it did - so it's a problem with suspend only.

---

### Post by mikejonesey on 2011-08-05
as a quick patch you can create a script to run on resume; the script can setprop with lspci to enable the device again...

---

### Post by scruffyeagle on 2011-08-06
> **mikejonesey said:**
> as a quick patch you can create a script to run on resume; the script can setprop with lspci to enable the device again...

That sounds like a great idea, but if you'd suggested that to me I wouldn't have a clue how to do it. Why don't you provide an example script, with instructions for how to apply it?

---

### Post by toomanymatts on 2011-08-08
As wonderful as that sounds, I have no idea what it means...how would I do something like that?

---

### Post by rausch74 on 2011-08-19
I'm running 10.10 on a Vostro V13 with the same issue.  My workaround currently is after resume to press FN-F6 to disable the trackpad.  Then press it again to re-enable, then it starts working properly.  Kind of a pain, but it beats a reboot.

---

