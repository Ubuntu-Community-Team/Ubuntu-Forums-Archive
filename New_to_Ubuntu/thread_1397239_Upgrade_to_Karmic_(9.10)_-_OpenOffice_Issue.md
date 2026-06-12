---
title: "Upgrade to Karmic (9.10) - OpenOffice Issue"
date: 2010-02-03
forum: New to Ubuntu
---

### Post by Vinnie V on 2010-02-03
Hello,

I am having a display issue with Open Office 3.1, and my recently upgraded 9.10 (Karmic). I noticed that in Open Office many of the menu titles are not showing up as actual text. They are all black rectangular boxes, or horizontal lines. When I right click for a menu, there appear to be the correct number of options, however once again horizontal lines. Everything seems to be OK in Firefox (which I am using to post this message). And for some reason, the screensaver does not seem to work correctly...

My issue seems to be confined to:
* OO title menus
* OOright click menus
* Main screensaver (multicolor horizonal and vertical lines [almost like flannel?])

Thank you for any suggestions.

---

### Post by nhasian on 2010-02-03
sounds like a video driver issue.  first in a terminal type:

```
sudo apt-get update && sudo apt-get upgrade
```

after that is done, go to System->Administration->Hardware Drivers

are there any drivers for your video card you could enable?  Does that resolve the issue?

alternatively you can try going to System->Preferences->Appearance->Visual Effects and changing the radio button from None to Normal or Extra.  Or if they are already on, change it back to None to see if it fixes your display problem.

please let me know if that resolves your problem.

---

### Post by Vinnie V on 2010-02-03
> **nhasian said:**
> sounds like a video driver issue.  first in a terminal type:

```
sudo apt-get update && sudo apt-get upgrade
```after that is done, go to System->Administration->Hardware Drivers

are there any drivers for your video card you could enable?  Does that resolve the issue?

alternatively you can try going to System->Preferences->Appearance->Visual Effects and changing the radio button from None to Normal or Extra.  Or if they are already on, change it back to None to see if it fixes your display problem.

please let me know if that resolves your problem.

OK. So, I updated and upgraded, there were no video drivers that I could enable. I then went to ...->Visual Effects and changed the radio button from None to Normal. That caused my system to act weirdly, and the screen wouldn't refresh properly or display any window in it's entirety.

---

### Post by nhasian on 2010-02-03
well it seems like we're on the right track and that its a video problem.  can you give us the output of the terminal command:

```
lshw -C display
```

---

### Post by Vinnie V on 2010-02-03
> **nhasian said:**
> well it seems like we're on the right track and that its a video problem.  can you give us the output of the terminal command:

```
lshw -C display
```
*-display UNCLAIMED     
       description: VGA compatible controller
       product: Radeon Mobility M6 LY
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master vga_palette cap_list
       configuration: latency=32 mingnt=8
       resources: memory:e0000000-e7ffffff(prefetchable) ioport:c000(size=256) memory:fcff0000-fcffffff memory:fc000000-fc01ffff(prefetchable)

---

### Post by nhasian on 2010-02-03
give this a try:

[http://ubuntuforums.org/showthread.php?t=899178](http://ubuntuforums.org/showthread.php?t=899178)

---

### Post by Vinnie V on 2010-02-05
It worked! Thank you so much! I saw that someone else who had replied to that thread also had a Dell C610, and only needed to do up to step 8. I am curious, what is compiz, and will I need to configure it to avoid future issues?

---

### Post by Vinnie V on 2010-02-25
Hello again. The issue reoccurred, and I used the info from the thread referenced:

[http://ubuntuforums.org/showthread.php?t=899178]("http://http://ubuntuforums.org/showthread.php?t=899178")

When I got back to step # 5,  instead of the expected output:

server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc.

I received: 

server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Mesa Project

I do not understand enough to know if I can proceed from this step or if I will break my system. Can someone please help? Thank you.

---

### Post by ndefontenay on 2010-02-25
Hi.

It seems your screen is a different one. 
I would say go ahead with the tutorial.
Worst case you have to re-install linux again but it's pretty fast and in the learning curve it happens.

If you are scared to do anything because you don't want to loose some data, back it up. You will feel more free to screw up!

Nico

---

### Post by Vinnie V on 2010-02-25
It doesn't look like it matters anyway... none of the steps past 8 would return a valid response. I keep getting error messages that the files are unsupported or unauthorized. Starting over...

This time, I was able to get it to work when I stopped at step 8. Starting to wonder if my system is unstable, or if I am :)

---

### Post by Vinnie V on 2010-03-04
I noticed something interesting when the issue reoccurred. It has been happening a lot more lately, and until recently, the steps up to 8 would restore the display that I wanted. Now I noticed that when it happens, the appearance settings are set to none. I can change them, and get the results that I want but then the computer runs sloooowly. In addition, I noticed that when I use my laptop for a certain period of time then the issue reoccurs. 

I am curious, is there a test that can be done to verify that my video card is still functional? My thinking is that the vid card is getting overheated? Is that a logical hypotheses?

Otherwise why would I have to keep doing the same process in order to try to "fix" the problem?

---

### Post by Hagar Delest on 2010-03-06
See that one perhaps (several fixes, read until the end): [[Solved] No text in OpenOffice.org menus]("http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=10183").

---

