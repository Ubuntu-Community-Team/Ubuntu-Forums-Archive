---
title: "Computer Won't Load on Start Up After 10.04 Updated, No Partition"
date: 2010-10-27
forum: New to Ubuntu
---

### Post by mvblair on 2010-10-27
My "computer speak" is pretty poor, so the only way I can describe my problem is with a narrative. Sorry about that, but I just don't have the vocabulary or know-how to explain what happened. 

I have an MPC Transport T1200 with an Intel Celeron M. 

I have always had problems in Windows with viruses and I like the idea of the open source movement, so I decided to give Ubuntu a try. I ordered an Ubuntu disc, ran it from the CD drive and love it. I decided to install Ubuntu 9.04 permanently on my computer. I selected an option to simply delete Windows instead of making a partition. Everything was going great. I was using Open Office and Firefox, the only things I want on my computer, for several days. 

I tried to install the Sun Java program from the "install programs" menu at the top. I tried to load a webpage that had a Java game. It didn't work. I searched the 'net and this forum for a reason why it might not work, but I couldn't find an answer that I could understand. I saw an option to update Ubuntu from that top menu, and I thought maybe the problem was that I didn't have Ubuntu 10.04. 

I downloaded Ubuntu 10.04 and I thought everything was fine. When it finished, I think a pop-up window came up that said I needed to restart the computer, and I allowed it to restart. 

When the computer restarted, I saw the MPC (my computer brand) logo, a few lines of text (some technical things that I don't understand) and then a few colored lines flickered before the Ubuntu logo on a black screen popped up. The Ubuntu logo stayed for a second or two, then disappeared to a completely black screen. The computer was still on but I don't think anything was going inside it because the hard drive light never flashed. I let this sit overnight and through the rest of the day. 

When I got home from work, I pressed the power button for a few seconds to turn the computer off. I turned it on again, but got the same deal (MPC logo, colored lines, Ubuntu logo, black screen). I tried it a couple of times and noticed that before the colored lines and Ubuntu logo comes up, there is a cursor at the top left of the screen that I can write into, but it doesn't seem to do anything. 

I tried turning off the computer and turning it on with the Ubuntu CD 9.04 in the drive, but I get the same thing. 

I do not want to go back to Windows. I really liked the feel of Ubuntu for those few days, but I'm afraid I don't have many options. Can somebody please recommend a course of action for me? I'd appreciate any help that you can give.

---

### Post by terdon on 2010-10-27
Hi, have a look at [http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/]("http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/")

---

### Post by mvblair on 2010-10-27
> **terdon said:**
> Hi, have a look at [http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/) Thanks for the reply, Terdon. 

The page that you suggested talks about booting from a CD. I have a 9.04 CD, but I have 10.04 installed on my computer (I think). Will the advice on this page still apply to me? 

> 
There have been a number of reports regarding blank screens at startup pre and post installation on the new Ubuntu 10.04 “Lucid” release. It seems there are some incompatibilities with some video drivers, particularly (not surprising) some ATI and nVidia. Also in the mix are some older Intel cards. This post outlines a workaround you can try in order to get your video working properly again.
**Booting from CD**
This section outlines how to workaround the video issue while booting from the CD. Your mileage may vary, depending on your video card, but hopefully this steers you in the right direction:

[LIST=1]
[*]At the install screen press ‘*F6*‘ and insert one of the options below, depending on your hardware.
[*]On first boot after install, press *e* to edit the GRUB menu.
[*]Using the arrow keys to navigate, delete **quiet** and **splash** and again insert one of the options below.
[*]Press **Ctrl** and **X** to boot.
[/LIST]
The suggested options that I have found are hardware specific. Here is a list:

[LIST]
[*]Older Intel video card: *i915.modeset=1* or i915.modeset=0
[*]nVidia: *nomodeset*
[*]Generic: *xforcevesa*
[/LIST]
Hopefully one of these options will get you up and running. Keep reading now to make these changes persistent!
**GRUB**
You’ll want to change these settings in GRUB so they’ll automatically be applied on each reboot. To do so, follow the steps below:

[LIST=1]
[*]Edit the */etc/default/grub* file. You will need Admin privileges to do so (sudo)
[*]Find this line: GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash”
[*]Replace with: GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash <option>”
[/LIST]
For example, if I had an older Intel model, my GRUB configuration would read:
[INDENT]GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash i915.modeset=1&#8243;
[/INDENT]Save your changes and you should get proper graphics on each reboot.
*UPDATE: Based on a lot of user feedback I am reminded that you need to run ‘update-grub’ after you make changes.*

---

### Post by terdon on 2010-10-27
Yes, that should be no problem. Once you have managed to boot, find the partition your actual system is installed in and edit /partition_linux_is_installed_on/etc/default/grub file as described in the link.

Let me know if you need more help.

---

### Post by Mark Phelps on 2010-10-27
It also might be something completely different ...

I upgraded 10.10 this weekend, and for the first time in YEARS, I was presented with a blank, black screen.

My solution was to boot into the GRUB menu, select the recovery option for Ubuntu (second one down), run that.  That put me into a command line, where I enter "startx" and got a desktop.  I shutdown normally, restarted and this time, when I selected the first kernel option, the desktop loaded just fine.

Something in the latest round of updates broke my display capability and it took a recovery to fix it.

---

### Post by mvblair on 2010-10-27
Thanks so much for the advice, gang. I'm going to go home and try this in the evening. I'll report back tomorrow morning. Thanks!

---

### Post by mvblair on 2010-10-27
Perhaps I have another problem. I tried to use the advice from the page Terdon gave. I put in my Ubuntu CD and I get the same result. I try to enter the GRUB menu (as Mark suggested and as suggested on the page) by pressing ESC and E and SHIFT+ESC, but it doesn't work. I still get to the black screen. It's the same when I take the Ubuntu CD out of the drive. 
 
I suppose that getting to the GRUB menu is my big job now. I'm frustrated now because I don't know much about this GRUB thing, but once I get there, perhaps I can "fool around" and find the solution. 
 
Any suggestions for getting to this GRUB menu?

---

### Post by mvblair on 2010-10-27
Thanks for the quick responses, Terdon and Mark. I decided to try reinstalling Ubuntu. I will look for more information about how to upgrade to 10.10 before I do it again. I really want to give it another try (mostly for political reasons I don't want to use MS), so I hope these work-arounds that Terdon suggested are easy to do!! 

Thanks again!

---

### Post by beew on 2010-10-29
> I tried to install the Sun Java program from the "install programs" menu at the topHuh? At the top of what?

Here is the easiest way to install java in Ubuntu.

Add the Canonical Partner repository to your sources list 
(Open Synaptic, go to Settings> Repository> Other software and add the apt-line 
> deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick partnerclose the dialogue box and reload Synaptic.)

After adding the Canonical partner source you would be able to install sun-java from Synaptic. 
The packages you need are sun-java.bin, sun-java-jre, sun-java-jdk and sun-java plugin.

Ubuntu uses the open version of java as its default. You can either remove the open java packages or change the default to sun-java to make sure that Sun's version is used. To change the default to sun-java, open a terminal and type

```
sudo update-java-alternatives -s java-6-sun
```That's it.

---

