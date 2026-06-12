---
title: "Mouse click just stops working"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by pachiko-ichiro on 2009-05-26
I re-installed Ubuntu on my labtop. Fresh install, using the whole hard drive. After a few minutes the mouse click both right and left stop working. This error means that I can't just click on things to fix it. 

I'm using a USB type mouse as well, but no luck

---

### Post by spartan_87 on 2009-05-27
I saw a workaround for this problem a long time ago, here is the old post: [http://ubuntuforums.org/archive/index.php/t-421581.html](http://ubuntuforums.org/archive/index.php/t-421581.html) , it seemed to work for most people.

Lisati wrote:
"In a terminal, type:

sudo gedit /boot/grub/menu.lst

Then scroll down to the line that begins "# defoptions=quiet splash "

add the following to the end of the line:

acpi=force irqpoll

Save and exit the editor, then type in the terminal,

sudo update-grub

Reboot, and things should be fine."

---

### Post by pachiko-ichiro on 2009-05-27
I tried the following, however it did not work for me. I'm still having the mouse clicking problem.
 
On a secondard note: 
pressing Alt+F2 opens a terminal but it isn't normal. 
 
What can I press to just open a normal terminal window?

---

### Post by raymondh on 2009-05-27
> **pachiko-ichiro said:**
>  
What can I press to just open a normal terminal window?

Hello Pachiko-ichiro,

To open a terminal, try xterm.

Alt+F2 and type xterm

Hope that helps.

Best,

---

### Post by rachelgoodpeople on 2009-05-27
Hi, I have installed Ubuntu remix 9.04 on my acer aspire one about 2 months ago, and have had no problems 
Today however, the mouse click left and right have stopped working as well. I am not familiar with linux enough to know what y'all mean about the terminal.  Can someone walk me through it? Rachel

---

### Post by raymondh on 2009-05-27
> **rachelgoodpeople said:**
> Hi, I have installed Ubuntu remix 9.04 on my acer aspire one about 2 months ago, and have had no problems 
Today however, the mouse click left and right have stopped working as well. I am not familiar with linux enough to know what y'all mean about the terminal.  Can someone walk me through it? Rachel

Hello Rachel,

Think of the terminal as another way to communicate with your machine and vice-versa.  It requires typing as opposed to a mouse/mice which is just point and click. Please see  this link.

[https://help.ubuntu.com/community/UsingTheTerminal#Why?](https://help.ubuntu.com/community/UsingTheTerminal#Why?)

As for the acer, does it have a function key to enable/disable the trackpad?  If so, try toggling it on/off and see what happens.  Also, can you hook-up an external USB mice and see if that works?

Best,

---

### Post by rachelgoodpeople on 2009-05-27
Thank you Raymond, 
Where would the enable/disable button be on the acer for the trackpad?

---

### Post by raymondh on 2009-05-27
> **rachelgoodpeople said:**
> Thank you Raymond, 
Where would the enable/disable button be on the acer for the trackpad?

I'm sorry, I am not familiar with the acer. It may be a function key.  On my MSIwind (as an example only), pressing Fn + F3 will toggle the touchpad/bar on and off.  Again, as an example, the icon drawn on the F-key looks like a screen with a slash mark on it.  Yours' may vary.  

Best,

---

### Post by rachelgoodpeople on 2009-05-27
Oh and Raymond an external mouse doesn't work any different. Thanks

---

### Post by rachelgoodpeople on 2009-05-27
I tried all the FN combinations, I can get the mouse pointer to start and stop working, but the click buttons still don't work. Mostly the left one. and a weird thing happens when I hover over the icon another version of the icon will follow with the pointer.  This just started happening today. When I do a right click the shadow version goes back to the original. Help!

---

### Post by rachelgoodpeople on 2009-05-27
How can I save it if the left click button is not working?

---

### Post by raymondh on 2009-05-27
Hello Rachel,

Do you still have XP installed in the acer?  If so, can you boot into XP and test if both trackpad and external mouse works?

Also, have you  updated recently?  What actions have you been doing with regards to the system?  (Update,upgrade, install drivers, those kinds of system maintenance)

In the meantime, I am searching launchpad to see if it is a Ubuntu bug and hopefully, the solutions.

Best,

---

### Post by raymondh on 2009-05-27
Just to clarify,

Pressing Fn key + F7 (together) does not work?

Ok, let's continue basic troubleshooting.

Go to system > preferences > mouse and see if the trackpad and mouse clicks are enabled.  I don't know how the layout is in UNR but the actions should be the same (it being ubuntu based)

Best,

---

### Post by pachiko-ichiro on 2009-05-27
Was that last response for both or just rachel?

---

### Post by spartan_87 on 2009-05-27
Here's another workaround similar to the other one that worked for some people, I found this today. [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/41301](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/41301)

John wrote:
"The workaround is to edit the /boot/grub/menu.lst file. Add "noapic acpi=off" to the end of the root line. You can do this while booting just by hitting e when the boot menu appears. Then select the root line and hit e again. Go to the end of the line and add the command. Hit return to save the edit and then b to continue the boot process.

Editing it during boot makes the command happen on booting, but only for that session. If it solves the problem you can add it to the end of the line by editing the /boot/grub/menu.lst file. From a command line enter "sudo gedit /boot/grub/menu.lst." When Gedit comes up add the command to the end of the line and save the file. Now it will be permanent."

---

### Post by raymondh on 2009-05-27
> **pachiko-ichiro said:**
> Was that last response for both or just rachel?

My apologies, Panchiko-ichiro.  This is, after all, your thread.

Any luck on your mouse-click issue?

Again, my apologies.

Regards,

---

### Post by pachiko-ichiro on 2009-05-27
Looks like the first suggestion worked... I'll give it a couple days. But so far so good. Thank You

---

### Post by pachiko-ichiro on 2009-05-27
well as soon as I type my last msg it stops working so I'm trying the other one now

---

### Post by pachiko-ichiro on 2009-05-27
I'm still having the problem with the mouse. Now I'm still able to right click but no left click. This is fustrating, I know the mouse is good because I use them on another computer. I've also used multiple mice, still same problem.

---

### Post by spartan_87 on 2009-05-27
Sorry those didn't work. Iv read on some other bug posts that some people updated their bios, it seems a lot of people have this problem on older computers and a bios update helped. Other then that I don't know what else to try. Anyone else have any suggestions?

---

### Post by pachiko-ichiro on 2009-05-27
well I have tried something that is working out so far. I changed my mouse to left hand input, and the mouse is still working both sides, but it is backwards so it is strange

---

### Post by pachiko-ichiro on 2009-05-28
Does anyone have any ideas, for getting past this. I have the most updated version for my BIOS. I'm using a T43 IBM ThinkPad. Any other ideas would greatly be appreciated.

---

### Post by The Shaolin on 2009-06-12
I had the same problem in Jaunty.

The mouse click would fail when the update manager opened.  After that, it would work very sporadically.  Using the keyboard, I tried to update, but it kept "flashing" to the enter password screen and then "crashing" and then I was getting errors that Ubuntu couldn't grab my mouse.

Out of ideas, I hit ALT+F2 to run application, and just typed in mouse, and "mousetweaks" auto completed.  I tried to run it, and a message popped up that something or other wasn't enabled.  I clicked "Enable and Reboot" and it's been working like a charm ever since.

Not entirely sure what I did (HAHA), but hope this helps someone else with this super frustrating problem!

---

### Post by knownhuman on 2010-04-25
Son of a... that seems to have worked for me.

---

