---
title: "Stuck in Virtualbox. Can't exit capture mode."
date: 2009-08-10
forum: New to Ubuntu
---

### Post by gfunkera on 2009-08-10
okay now im stuck in windows 7 using virtualbox and the "Right Ctrl" button is not deactivating the capture mode in virtualbox! lol its kind of funny i feel like a prisoner on my own computer!! 
 
when i hit either ctrl button it shows the true position of the mouse on the screen but i cant seem to get control back to linux... the arrow in virtualbox is green... 
 
i desperately await your help while i am held prisoner in my own realm!!!
 
also how do you change the escape button from "Right Ctrl" to something else? i cant seem to find the options dialogue for this...

---

### Post by Dark Aspect on 2009-08-10
> **gfunkera said:**
> also how do you change the escape button from "Right Ctrl" to something else? i cant seem to find the options dialogue for this...

VirtualBox --> File --> Preferences --> Input

---

### Post by philcamlin on 2009-08-10
right ctrl + F to exit full screen then follow the above osters directions :)

---

### Post by gfunkera on 2009-08-10
IM NOT STUCK IN FULLSCREEN MODE
 
my mouse and keyboard input is being taken by virtualbox.. the little downwards pointing arrow at the bottom right is green... next to it, it says "Right Ctrl"...
 
when i push Right Ctrl on the keyboard, i cant make my mouse and keyboard work normally in linux...
 
does that make more sense? fullscreen is not the problem, it seems that the program isnt recognizing the key to make it so that i can toggle mouse and keyboard control between linux and virtualbox...
 
i hop someone out there can help..

---

### Post by Dark Aspect on 2009-08-10
Ignore philcamlin's post, than go to

VirtualBox --> File --> Preferences --> Input

That has what your after, CTRL+F is unrelated if your not running the vm.

---

### Post by mrgreggie on 2009-08-10
Not sure if there is a potential conflict with right ctrl on your system, but changing it might be something to try.  To get out of Windows in the meantime, select shutdown from the start menu.  Once it gets done shutting down the VM, you should be able to get back to Ubuntu.  Again, i'm not sure why the right ctrl key isn't working, but changing it to see whether it makes a difference would be a start.

---

### Post by Wharf Rat on 2009-08-10
gfunkera,
I hope find a solution and post it.
I have had the same problem since upgrading to 9.04.    I am using a Lenovo T61.   
I have to kill VB in order to escape.

---

### Post by mrgreggie on 2009-08-10
> **Wharf Rat said:**
> gfunkera,
I hope find a solution and post it.
I have had the same problem since upgrading to 9.04.    I am using a Lenovo T61.   
I have to kill VB in order to escape.

Shutting down Windows in VirtualBox should have the same result as killing the process without the risk of corrupting the virtual hard drive.

---

### Post by Wharf Rat on 2009-08-11
Yes it does.
However, the point of having VB is not only to run Windows applications but be able to utilize Linux apps at the same time.   If you need to switch back to Ubuntu, you MUST exit VB dumping anything you have set up.

---

### Post by gfunkera on 2009-08-27
I FOUND A SOLUTION TO THE PROBLEM:

my right ctrl wasnt working, for unknown reasons (only thing that i can think of is that its occuring cause its jaunty. when i migrated to jaunty from intrepid i have been having TONS of problems..)

anyway, i managed to change it to the super key (windows key) and now it works fine

---

### Post by Shazaam on 2009-08-27
Have you installed Guest Additions on the guest?

---

### Post by gfunkera on 2009-08-28
what is guest additions?

---

### Post by win_soft2005 on 2009-08-28
on the virtualbox menu go to:
Devices --> Install Guest Additions...
If your guest system is Windows, you will see the guest additions installation utility(if autorun is enable).

And do try this:
[http://www.virtualbox.org/manual/UserManual.html#id2507347](http://www.virtualbox.org/manual/UserManual.html#id2507347)
If you don't know what are guest additions.

---

### Post by howefield on 2009-08-28
> **gfunkera said:**
> what is guest additions?

The point being that with the installation of guest additions your mouse won't be "captured" ie, you will be able to move the mouse seamlessly from virtual guest to host without the use of a release key, there are other significant benefits of using guest additions.

---

### Post by gfunkera on 2009-08-28
please guide me through this amazing feature you have brought to my intrigued attention :)

---

### Post by howefield on 2009-08-28
> **gfunkera said:**
> please guide me through this amazing feature you have brought to my intrigued attention :)

[http://www.virtualbox.org/wiki/VirtualBoxTV](http://www.virtualbox.org/wiki/VirtualBoxTV)

Second video down the page,..

"Creating your first Guest Virtual Machine (Windows 7)

Fatbloke creates a Windows 7 virtual machine and installs the Guest Additions into it."

---

### Post by markackerman8@gmail.com on 2010-04-18
I had the same problem and changing to the super key worked for me too thanks.

---

### Post by bzhao on 2010-11-07
yes, I met the same problem.
swithing to win key(super key) has solved the problem.

---

### Post by diablo75 on 2010-11-08
> **win_soft2005 said:**
> on the virtualbox menu go to:
Devices --> Install Guest Additions...
If your guest system is Windows, you will see the guest additions installation utility(if autorun is enable).

And do try this:
[http://www.virtualbox.org/manual/UserManual.html#id2507347](http://www.virtualbox.org/manual/UserManual.html#id2507347)
If you don't know what are guest additions.

> **gfunkera said:**
> please guide me through this amazing feature you have brought to my intrigued attention :)

I just wanted to add a little explaination about what happens when you do this.

When you click "Install Guest Additions", Virtualbox virtually "plugs in" a fake CD-ROM drive with a bootable CD volume that contains the guest additions software.  Just like you would expect on Windows after inserting a software installation CD, it will instantly ask you if you want to run it.  Then you just follow the onscreen instructions to install it within Windows.  Once finished, reboot your VM.  Guest additions will enable features like the ability for the mouse to travel seemlessly between linux and your VM, with no need to use that stupid Superkey.  There are other performance enhancements and cool stuff that happen but just follow that link above to learn more.

---

### Post by tmpanon on 2011-10-29
I had to solve it in a slightly different way as changing the key used didn't have an effect while running the current VM in which just the mouse was trapped. I'm assuming changing the key will work later after I shutdown and then retry the VM, but for now it doesn't; and I can't shut it down currently as it is restoring a large disc image.
 
My solution was to simple unplug my usb mouse from the pc for 5 seconds, put it back in and problem solved. Hope it helps someone.

---

### Post by oldos2er on 2011-10-29
Closed for necromancy.

---

