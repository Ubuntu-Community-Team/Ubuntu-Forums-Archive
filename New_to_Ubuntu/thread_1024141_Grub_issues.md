---
title: "Grub issues"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by Chaosis on 2008-12-28
I have been having tons of trouble getting grub to work the past couple of days! I have been trying to install Kubuntu 8.10 on my 320 GB WD external USB drive. When I try to install Kubuntu on the computer I want to run it on, the computer doesn't show the external drive because I have two internal drives (which I don't want to disconnect). I installed it from a computer with only one hard drive, but it will only run on that computer. When I edited grub to run on the other it runs on neither.

So how do I edit grub to work on my other computer (which I didn't install Kubuntu on)?
And is there a way to make grub load Kubuntu on all computers I plug my drive into (I installed grub to the external drive)?
And in menu.lst it used some wired locations, and it said UUID instead of root, whats with that?

If it helps... My knowledge of Linux intermediate. I have used many live CD's, know enough commands, and I am a master *windows* programmer.

---

### Post by caljohnsmith on 2008-12-28
How about first ensuring that Grub is installed to the MBR of your Kubuntu drive by doing the following:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Kubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd1,0), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Please post the output of all the above commands. If the commands complete successfully, you should be able to boot the Kubuntu drive without any Grub problems. If you run into problems, how about doing:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by louieb on 2008-12-28
The two main grub programs are stage1 and stage2.

Stage1 by default is  installed in the MBR of the 1st drive in the boot order.  By pressing the advanced button on the install summary page you can change the stage1 install location to the MBR of another drive  (like the MBR of an external drive)  or alternately in the boot sector of a partition.    you can find a copy of the stage 1 program in /boot/grub.

Stage1 is quite small in fact its just loads the stage2 program.

Stage2 is the main program it displays the menu and does all the stuff a good boot loader/manager does.  By default stage2 is installed in /boot/grub.

To make the external drive boot-able you need to install stage1 in the MBR of the external. By pressing the advanced button on the install summary page you can change the stage1 install location to the MBR of another drive  (like the MBR of an external drive) .

Then you tell the computer to boot the USB drive and you should be all set.

UUID is just a way of identifying a particular partition.

Just like Linux is not windows. GRUB is not Linux, its a boot loader. Heres a good place to learn more.    [IDBS GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm")

---

### Post by Chaosis on 2008-12-28
I reverted back to the original and did those commands and everything worked, unlike before...
I then booted from the external drive, but I got grub error 2.

EDIT:
And all of my grub errors have been at stage 1.5.
I also installed stage 1 to the external, I already knew to do that...
So any other ideas? And how do I find the UUID (grub>UUID doesn't work)?

EDIT 2:
How can I rebuild the menu.lst (I deleted it, and for some reason my backup us missing it)?

---

