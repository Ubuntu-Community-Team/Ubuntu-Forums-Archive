---
title: "Grub issues"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by Red_Safari on 2009-01-27
Hello all,
I have recently installed Ultimate on an external HD with my laptop. I am running Vista on the internal. The problem I'm having is that I cannot restart my computer without having the external HD plugged into the USB port. Otherwise I get an error during Grub. Can anyone direct me to fix this?

---

### Post by caljohnsmith on 2009-01-27
**Red_Safari**, does your BIOS support booting USB devices? If so, how about installing Grub to your USB drive with:
```
sudo grub
grub> find /boot/grub/stage1
```
The command above should return your main Ubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd1,0), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Reboot, set your BIOS to boot the USB drive, and you should at least get the Grub menu if all goes well. Let me know if you can get that far and we can work from there if you want.

---

### Post by Red_Safari on 2009-01-27
Okay, followed those directions.
Now when it tried to load Ubuntu I am getting 
"Error 17: Cannot mount selected partition

Press any key to continue..._

Am I on the right track?

---

### Post by caljohnsmith on 2009-01-27
Great, sounds like you are on the right track. How about when you get the Grub menu on start up, select the first Ubuntu entry, press "e" to edit it, select the line that says "root (hdX,Y)" where X and Y are numbers, press "e" to edit it, change it to "root (hd0,Y)", press return to save the change, then press "b" to boot. Based on the info you gave, I think that should be all it takes to boot Ubuntu. Note that the change is not permanent, so you'll need to modify your menu.lst to make it permanent.

So if it works, when you get into Ubuntu, just do:
```
gksudo gedit /boot/grub/menu.lst
```
And change the line that says "# groot=(hdX,Y)" to use the (hd0,Y) that worked to boot Ubuntu. Save, quit gedit, then run:
```
sudo update-grub
```
And you should be all set about booting Ubuntu directly from your USB drive. If all the steps above work OK, you can restore a Windows MBR to your Windows drive by doing:
```
sudo fdisk -lu
sudo apt-get install lilo
sudo lilo -M /dev/[COLOR="Blue"]sda[/COLOR] mbr
```
Use the output of the fdisk command to determine which is your Windows drive (probably "sda"), but replace "sda" in the lilo command with the Windows drive if it is different. Let me know how it goes or if you run into problems.

---

### Post by overdrank on 2009-01-27
Hi and I have moved Red_Safari post and caljohnsmith reply to a new thread to not cause confusion. Red_Safari please be considerate and not hijack other users threads. :)

---

### Post by Red_Safari on 2009-01-27
Sorry Overdrank,
I tried for quite a while to find a way to post a whole new topic and could not figure it out. I assumed that there may be a waiting period for new users and tried to find the closest thread to what I wanted.
Best,
Red_Safari

---

### Post by Red_Safari on 2009-01-27
CalJohnSmith,

Let me just say "Wow".
Your knowledge of Ubuntu is very impressive. Everything is working just the way I wanted it to. I can't thank you enough for walking me through all this. 
I installed Ubuntu last week in Computer Club with my Prof. and she didnt have enough time to help me fix the MBR. I was going to have to wait 2 more weeks till our next meeting and I've had to lug that 2nd HD around with me just to start up either OS.
Thanks for your expert help.

Best Regards,

Red_Safari

---

### Post by caljohnsmith on 2009-01-27
Glad to hear that worked OK, Red_Safari. Cheers and enjoy your new Ubuntu install. :)

---

### Post by overdrank on 2009-01-27
> **Red_Safari said:**
> Sorry Overdrank,
I tried for quite a while to find a way to post a whole new topic and could not figure it out. I assumed that there may be a waiting period for new users and tried to find the closest thread to what I wanted.
Best,
Red_Safari

No problem, you may look at the [forum features]("http://ubuntuforums.org/showthread.php?t=1006656")for some more hints.
The new thread button is in the top left corner right above the sticky threads of the forum that you enter like Absolute Beginner Talk. Good luck! :p

---

