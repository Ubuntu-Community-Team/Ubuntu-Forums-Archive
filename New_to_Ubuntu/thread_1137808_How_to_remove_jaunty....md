---
title: "How to remove jaunty..."
date: 2009-04-25
forum: New to Ubuntu
---

### Post by icivilion on 2009-04-25
Hi..... i am totally new for ubuntu.... i had ubuntu 8.10 on wiproz35fm laptop... i tried to upgrade from cd rom as i didnt had internet connection...... but unfortunately i installed fresh copy of jaunty.. now as a matter of space on my disk i want to remove the frest copy of juanty and want to upgrade the 8.10 to 9.04
my cd rom wont prompt for autorun option even though it does it gives an error message , even ii tried this command in terminal gksu “sh /cdrom/cdromupgrade” nothing happened.... now i want to remove 9.04 and want to upgrade 8.10 to 9.04,

out of 80gb, 60gb is ext3 and remaining is ntfs........ can any one help????? please.. and thank you in advance

---

### Post by SunnyRabbiera on 2009-04-25
Truth be told if Ibex works for you then the update to Jaunty is not needed.
Its not that much of an upgrade in my opinion.

---

### Post by icivilion on 2009-04-25
ok thans... but how to remove the fresh copy of jaunty i have installed .. any idea?

---

### Post by icivilion on 2009-04-26
hi thanks eventhoug i do it.. its on separte disk and  i want to merge that space into this existing.... is there any formal way to remove it other than formatiing.....

---

### Post by ashton88 on 2009-04-26
Preface: I am not an expert.  Just a newb who likes to read and play around.

So I think what you are saying is you installed 9.04, it resized your 8.10 partition down so you have 2 partitions - the second (hda2/sda2) being your 9.04 partition now.

If I'm reading you correctly I believe I would go about doing it like this:

1) Backup what I need to keep, for safety.
2) Load up gparted.
3) Make sure that I have an updated emergency GRUB boot disk.
3) Delete the 9.04 partition
4) Resize the 8.10 partition to occupy the entire drive.
5) Before rebooting update my /boot/grub/menu.lst
6) Boot into 8.10
7) Run the upgrade from the 8.10 command line. (instructions are here:[http://www.ubuntu.com/getubuntu/upgrading]("http://www.ubuntu.com/getubuntu/upgrading"))

There is the potential that you do some damage, so don't do any of this unless you are comfortable.  Make sure you have a backup.

Make sure you have a backup.

Also - I have never personally resized a partition with gparted, so if there is a flaw in my plan it is probably there.  But the option is in the gparted menu, and you can read more about the program and it's capabilities before doing it.  Be sure to choose the right partitions when hitting delete, and resize, and such.

Make sure you have a backup.

Hope this helps to steer you in the right direction.  If you get it done tell me how it worked out!

---

### Post by icivilion on 2009-04-27
hi ashton really thanks a ton for your time and suggestions.. the thing is that .. i am totally new to ubuntu.. so if you give a detailed command in each i would do it... what that my stands in my /boot/grub/menu.lst... how to do this bit more detail i need .. hope u wont mind..

---

### Post by trucker33377 on 2009-04-27
I would also google supergrub and make a copy of that program. its come in very handy for over the past few years. if you do delete your partition and find an eror in your grub this will allow you to find your linux or windows and boot it up.

---

### Post by ashton88 on 2009-04-28
> **icivilion said:**
> hi ashton really thanks a ton for your time and suggestions.. the thing is that .. i am totally new to ubuntu.. so if you give a detailed command in each i would do it... what that my stands in my /boot/grub/menu.lst... how to do this bit more detail i need .. hope u wont mind..

I'm not good enough to be able to give step-by-step for this.  The other problem is that there are going to be things that are particular to your machine that I can't anticipate.  But I will fill in a little more detail as I can:

Again - to reiterate - I'm just a newb who likes to read and tinker.  There are some real gurus on here so by all means wait for others to point out my stupid mistakes before doing any of this (read the comments below!)- and be sure to have backups.

*1) Backup what I need to keep, for safety.*
I would use K3b to burn any Documents/Pictures/... other data to CD.  I wouldn't worry about any operating system files, or configuration.  Sounds like you haven't got much of that anyways.

K3b can be installed by typing:
sudo apt-get install k3b

Then type "k3b" to start it.  From there it is a standard drag and drop application.

I would imagine most people use Braesro (spl?) but I tried it a long while back and got on the K3b train.  Braesro might be installed by default.

Check in the /home/yourusername directory for the subdirectories with your important data stuff to back up.

*2) Load up gparted.*

Hit Alt-F2 to bring up the "run" window.  Type in "gksudo gparted" ... it will prompt you for your password - type it in.  You need to put the "gksudo" in front of it to run "gparted" with elevated privledges - or else you get an error.  Be careful in this program because it is a powerful one that can damage your system.  If you only have 1 harddrive with 2 partitions (1 your old ubuntu 8.10 and one is your ubuntu 9.04) like I described above you should see them there.

*3) Make sure that I have an updated emergency GRUB boot disk.*

Don't bother closing gparted.  Just open a terminal window.  You can do this by typing Alt-F2 again, and then typing in "gnome-terminal".  When you are there type in "grub".

The prompt will change to a grub type prompt.

What we want to do is make it so that if we screw up our Master Boot Record (MBR) we can still boot into ubuntu to fix it.

So put a new floppy disk in the drive and type in:
root (fd0)
setup (fd0,0)

Grub will spit some stuff at you and then it should say complete.

If you are feeling ambitious try rebooting your computer from the floppy disk now by leaving that in the drive.  You may have to go into your BIOS (usually by hitting "DELETE" while your computer is starting) to make sure your floppy drive is first in the boot order.

Having a grub boot floppy has saved my hide plenty of times.  Once you get more familiar with all this ubuntu/linux stuff you will see how easy it is to use grub, keep it up to date, and how powerful it is.  Right now I remember well how daunting it is.

*3) Delete the 9.04 partition*

Looking back at your gparted window, highlight the second (right-most of the 2) parition and delete it.  BE CAREFUL!  I have made a lot of assumptions in my posts which all culminate in me believing that your second partition on your primary drive is your new install of ubuntu 9.04.  If anything doesnt add up, or there are more partitions, or more hard drives (check the drop down box in the top right corner) then my assumptions are wrong.  If my assumptions are wrong go to a terminal window and type:
df -h
There will be a lot of output. Post that output here to give a clearer picture as to what is going on.

*4) Resize the 8.10 partition to occupy the entire drive.*

Assuming all is as it should be, after the second partition is deleted then resize the first partition.  I have never done this myself sing gparted, but given it is a GUI program it is fairly intuitive.  Expect this to take a long time (Hours).  Don't do it in a situation where you are likely to lose power during the process.  (You know, like a lightning storm, or if a herd of cats is chewing on your power cables).

Once you have dont that you need to hit the apply button.  Only then will all the changes in gparted be started.  Again, it will probably take hours (depending on the size of your drive).

*5) Before rebooting update my /boot/grub/menu.lst*

This is optional.  Type in:
sudo gedit /boot/grub/menu.lst
Scroll Down... way down... to the section that has "ubuntu 9.04" in the title.  Comment that section out by putting 2 # in front of each line underneath it until there is a blank line.  Here is an example of what it will look like after the edit.  Yours will look different:
## Title Ubuntu 9.04 some other words here
## root (0,1)
## kernel blah blah blah 
## initd blah blah 
## quiet
## make active

*6) Boot into 8.10*

Moment of truth, restart.  If your computer catches fire then I would like to point out again that I am a lowly newb who is just learning these things myself, so don't do anything you aren't comfortable with!

[I]7) Run the upgrade from the 8.10 command line. (instructions are here:[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading))
[/I]And follow the upgrade this time instead of the vanilla install!

Cheers.

---

### Post by icivilion on 2009-04-29
> **ashton88 said:**
> I'm not good enough to be able to give step-by-step for this.  The other problem is that there are going to be things that are particular to your machine that I can't anticipate.  But I will fill in a little more detail as I can:

Again - to reiterate - I'm just a newb who likes to read and tinker.  There are some real gurus on here so by all means wait for others to point out my stupid mistakes before doing any of this (read the comments below!)- and be sure to have backups.

*1) Backup what I need to keep, for safety.*
I would use K3b to burn any Documents/Pictures/... other data to CD.  I wouldn't worry about any operating system files, or configuration.  Sounds like you haven't got much of that anyways.

K3b can be installed by typing:
sudo apt-get install k3b

Then type "k3b" to start it.  From there it is a standard drag and drop application.

I would imagine most people use Braesro (spl?) but I tried it a long while back and got on the K3b train.  Braesro might be installed by default.

Check in the /home/yourusername directory for the subdirectories with your important data stuff to back up.

*2) Load up gparted.*

Hit Alt-F2 to bring up the "run" window.  Type in "gksudo gparted" ... it will prompt you for your password - type it in.  You need to put the "gksudo" in front of it to run "gparted" with elevated privledges - or else you get an error.  Be careful in this program because it is a powerful one that can damage your system.  If you only have 1 harddrive with 2 partitions (1 your old ubuntu 8.10 and one is your ubuntu 9.04) like I described above you should see them there.

*3) Make sure that I have an updated emergency GRUB boot disk.*

Don't bother closing gparted.  Just open a terminal window.  You can do this by typing Alt-F2 again, and then typing in "gnome-terminal".  When you are there type in "grub".

The prompt will change to a grub type prompt.

What we want to do is make it so that if we screw up our Master Boot Record (MBR) we can still boot into ubuntu to fix it.

So put a new floppy disk in the drive and type in:
root (fd0)
setup (fd0,0)

Grub will spit some stuff at you and then it should say complete.

If you are feeling ambitious try rebooting your computer from the floppy disk now by leaving that in the drive.  You may have to go into your BIOS (usually by hitting "DELETE" while your computer is starting) to make sure your floppy drive is first in the boot order.

Having a grub boot floppy has saved my hide plenty of times.  Once you get more familiar with all this ubuntu/linux stuff you will see how easy it is to use grub, keep it up to date, and how powerful it is.  Right now I remember well how daunting it is.

*3) Delete the 9.04 partition*

Looking back at your gparted window, highlight the second (right-most of the 2) parition and delete it.  BE CAREFUL!  I have made a lot of assumptions in my posts which all culminate in me believing that your second partition on your primary drive is your new install of ubuntu 9.04.  If anything doesnt add up, or there are more partitions, or more hard drives (check the drop down box in the top right corner) then my assumptions are wrong.  If my assumptions are wrong go to a terminal window and type:
df -h
There will be a lot of output. Post that output here to give a clearer picture as to what is going on.

*4) Resize the 8.10 partition to occupy the entire drive.*

Assuming all is as it should be, after the second partition is deleted then resize the first partition.  I have never done this myself sing gparted, but given it is a GUI program it is fairly intuitive.  Expect this to take a long time (Hours).  Don't do it in a situation where you are likely to lose power during the process.  (You know, like a lightning storm, or if a herd of cats is chewing on your power cables).

Once you have dont that you need to hit the apply button.  Only then will all the changes in gparted be started.  Again, it will probably take hours (depending on the size of your drive).

*5) Before rebooting update my /boot/grub/menu.lst*

This is optional.  Type in:
sudo gedit /boot/grub/menu.lst
Scroll Down... way down... to the section that has "ubuntu 9.04" in the title.  Comment that section out by putting 2 # in front of each line underneath it until there is a blank line.  Here is an example of what it will look like after the edit.  Yours will look different:
## Title Ubuntu 9.04 some other words here
## root (0,1)
## kernel blah blah blah 
## initd blah blah 
## quiet
## make active

*6) Boot into 8.10*

Moment of truth, restart.  If your computer catches fire then I would like to point out again that I am a lowly newb who is just learning these things myself, so don't do anything you aren't comfortable with!

[I]7) Run the upgrade from the 8.10 command line. (instructions are here:[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading))
[/I]And follow the upgrade this time instead of the vanilla install!

Cheers.


This is really a step by step guide..you tell even how and why thats good for me to understand the operating system... once again thanks for your valuable time... will come back with the results... thanks again

---

### Post by icivilion on 2009-04-29
This is really a step by step guide and you are more good enough...you tell even how and why thats good for me to understand the operating system...you say that for grub i need to install floppy but i am using laptop:).. can i use pendrive do that work?.. i will give first boot option from pendrive and wil try it, that will work i think... once again thanks for your valuable time... will come back with the results... thanks again

---

### Post by icivilion on 2009-05-07
thanks a lot a lot ashton i did it,,,,, thanks again..... hey how to close this thread..!!!!!

---

