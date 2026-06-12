---
title: "Cant figure Xubuntu out!"
date: 2010-03-01
forum: New to Ubuntu
---

### Post by Tubbsmcfat on 2010-03-01
Hello, I am new to Xubuntu, and i am having troubles installing. I have an old spare Windows ME. I downloaded Kubuntu onto a CD-R. I put it in my drive (just normal CD-ROM). I restart the computer, the Kubuntu Menu comes up. I click Install Kubuntu, It goes to the mouse logo. Then the language select menu comes up. I select the language. Then the little spinnig mouse pointer comes up and the CD stops reading. Then Nothing.:cry:. Am I doing something wrong?
 
The Computers Specs are:
 
Compaq Armada 5000
800 MHZ Proccesor (or something between 800-900 MHZ)
128 MB RAM
Windows ME (millenium edition)
 
Thanks to any help!
:D

---

### Post by kerry_s on 2010-03-01
confusing you have xubuntu & kubuntu?

128mb is not enough to run kubuntu(kde) & xubuntu(xfce4) you need to use the text installer version cause the gui needs at least 256mb ram.

any which way, 128mb ram is not enough for a decent system.

you'll need to look at low raw distros like puppy linux.

[http://puppylinux.org/main/index.php?file=Overview%20and%20Getting%20Started.htm](http://puppylinux.org/main/index.php?file=Overview%20and%20Getting%20Started.htm)

---

### Post by Sir Jasper on 2010-03-01
Hi,

I am almost sure that you have no chance with 128 MB RAM. However, there are versions of Linux that will run well with that. 

I could recommend a couple of them, but since I have not used either I would await more knowledgeable advice.

My regards

---

### Post by Tubbsmcfat on 2010-03-01
Ok so im gonna download puppy linux  get to the page what am i supposed to do now?

---

### Post by Tubbsmcfat on 2010-03-01
Which one do i download?

---

### Post by MooPi on 2010-03-01
Ubuntu will work with those low specs but the internet will chew your PC up and spit it back at you. I'd suggest bumping up that ram regardless of what you attempt. When your better acquainted with Linux come back and give us a try. :p

Try this link: [http://distro.ibiblio.org/pub/linux/distributions/puppylinux/puppy-4.3.1/pup-431.iso](http://distro.ibiblio.org/pub/linux/distributions/puppylinux/puppy-4.3.1/pup-431.iso)

---

### Post by wojox on 2010-03-01
If you clicked kerry_s link select Download from the menu and where it says:

```
To download Puppy Linux, click on one of the following:
```

Click the blue hyper link below it.

---

### Post by Tubbsmcfat on 2010-03-01
Okay ill give puppy a try!

---

### Post by medicalystoned on 2010-03-01
Dude, puppy is great.... I had Puppy 4.20 on an old Dell 3800 Laptop and it was a screamer.....worked perfect, xine player on it plays movies as well as VLC any day.... try it... I would still have it if I wouldn't have dropped the machine and broke the fans....... have fun with all Linux ditros.....peace

---

### Post by Tubbsmcfat on 2010-03-01
Thanks everyone for ypur help, and medic "it was a screamer" haha

---

### Post by kerry_s on 2010-03-01
> **Tubbsmcfat said:**
> Thanks everyone for ypur help, and medic "it was a screamer" haha

:lolflag: it can be, i'm using debian lxde on 450mhz 256mb ram, not the fastest, but not slow. my niece does her homework on it when she's here. here's a pic of mine.

---

### Post by Tubbsmcfat on 2010-03-02
Alright!! It works with no lag, when i choose the screen options  what does it mean by 
 
Screen Ok, Maybe not for card;)

---

### Post by Tubbsmcfat on 2010-03-02
KErry is that Puppy Linux?

---

### Post by NightwishFan on 2010-03-02
When setting up xorg/xvesa, just choose safe defaults that you know works, such as 16-bit 1024x768. If you know your monitor supports better, use better.

---

### Post by kerry_s on 2010-03-02
> **Tubbsmcfat said:**
> KErry is that Puppy Linux?

debian lxde, i used the net installer advanced options> other desktops.

---

### Post by Tubbsmcfat on 2010-03-03
OK i go to click install, i go through all the steps, and a message says Ok Done! then when i restart the computer without the cd, it instantly goes to Windows ME, What should I do?

---

### Post by 4Orbs on 2010-03-03
Are you still using the Xubuntu live cd, or Puppy or Kubuntu?

---

### Post by Tubbsmcfat on 2010-03-03
I am using Puppy now (v4.10)

---

### Post by Tubbsmcfat on 2010-03-03
So what am i supposed to do?

---

### Post by 4Orbs on 2010-03-03
If you followed the steps to install Puppy, and it finished with no errors and gave you the "OK Done" message, then it's safe to assume that Puppy installed successfully.

But here's the problem, many old computers have the Master Boot Record permanently embedded in ROM instead of being in an accessible spot on the hard drive. So even though Puppy is installed, it was unable to overwrite the MBR... which leaves you with no option to boot into Puppy.

In order to boot into Puppy you will need to create a boot floppy disk, and have that disk inserted in the floppy drive when you turn on the computer. The instructions for creating the boot floppy can be found on Puppy's website.

---

### Post by Tubbsmcfat on 2010-03-03
couldnt i just enter the boot menu?

---

### Post by 4Orbs on 2010-03-03
Even if you put a new boot sector on the hard drive, it will not work. When the MBR is in ROM there is no way to access it to make any changes. A boot floppy is the only way to go. If you want to boot into Win ME, remove the floppy from the drive before turning on the computer. If you want to boot into Puppy, insert the floppy into the drive before turning on the computer.

It only takes a minute to create the boot floppy. Not very elegant, but probably the only way to boot into Puppy. Well... Maybe not the only way, but the easiest way by far.

---

### Post by Kixtosh on 2010-03-03
Tubbsmcfat, Puppy is meant to run from your CD drive only. It can be installed on the hard drive, but it's not what it was intended for. If you booted Puppy from the CD drive the first time, then you will have options to save certain small files almost anywhere on the hard drive (including Windows partitions) when you exit. That will make your next boot time faster, but you'll still need the CD to start up again. You have to ensure that your BIOS settings are set to boot from the CD before the HDD. When the Puppy CD is not present, your machine will automatically default back to the HDD and boot up Win ME. Also, you should defragment your Windows hard drive about three times over if you can, before you save the Puppy files on that partition.
 
Otherwise, Xubuntu will work on that machine IMO. I'm using it on two comput-o-saurs myself very successfully. If I were you, I'd search for an extra 128MB of RAM or more, depending on what is possible for your machine. It's probably very cheap at this point, but 256 is certainly a working solution for Xubuntu in my experience (I haven't tried anything less). In fact, once installed the O.S. will work, even with just 128MB, it just won't be optimal in terms of performance (slow start for Firefox etc.).
 
If increasing RAM is not an option, and you don't want to just use the CD method for Puppy, then read up on how to install it to the hard drive.
 
One other thing: why are you using Puppy V4.10? The current version is 431 (or 4.3.1).

---

### Post by Tubbsmcfat on 2010-03-03
Well when i save something, can i save it to the desktop? cause when i save it goes somewhere i dont where it is. And every time i start it off the cd, i need to go throught all the settins like the language and time, is there any way to set that so i dont have to keep doing it?

---

### Post by Kixtosh on 2010-03-03
> **Tubbsmcfat said:**
> ... And every time i start it off the cd, i need to go throught all the settins like the language and time, is there any way to set that so i dont have to keep doing it?If you saved the necessary files when you first shut down, you shouldn't have to enter the settings again each time you boot. From the F.A.Q. section here: [http://puppylinux.com/faq.htm](http://puppylinux.com/faq.htm)
 
> **Q: **How do I save my personal files and settings?
 
**A: **The very first time that you boot Puppy from live-CD, all of the Puppy files will load off the CD into RAM and Puppy will run totally in RAM. When you shutdown for the first time (see Menu -> Shutdown), Puppy will ask you where you want to save your personal files and settings. Puppy will see what is available and will display a menu and you just choose what you want. It's pretty simple. You can choose to save to the hard drive, or a plug-in USB drive -- in some cases even a floppy disk.
 
Puppy will create a single file, named *pup_save.3fs*, in which to save your personal data. If this file is created on a hard drive partition, it does not interfere in any way with whatever is already on the hard drive. So, if you have Windows installed on your C: drive, no problem, Puppy can create his pup_save.3fs file on your C: drive and when you run Windows it will just be an ordinary file. In other words, it should not upset the Windows installation at all.

---

### Post by Tubbsmcfat on 2010-03-03
Alright thanks guys for all your help!):P\\:D/

---

### Post by egalvan on 2010-03-03
> **4Orbs said:**
> 
But here's the problem,** many old computers have the Master Boot Record permanently embedded in ROM **instead of being in an accessible spot on the hard drive. So even though Puppy is installed, it was unable to overwrite the MBR... which leaves you with no option to boot into Puppy.

Wow, the last time I saw an MBR on a ROM was in late 1977...
a **TRS-80 4K cassette-based model** it was...
and even then, you could chainload the floppy (as we quickly found out)...

He says it's an WindowsME machine... not that old :)

No, it's *far* more likely that the BIOS is not being changed correctly.
Wrong options being taken, options not being saved,
battery flaky (causing CMOS resets), etc.



> In order to boot into Puppy you will need to create a boot floppy disk, and have that disk inserted in the floppy drive when you turn on the computer.
 The instructions for creating the boot floppy can be found on Puppy's website.

Floppy-based boots are one option, but I still think the problem lies elsewhere.

---

### Post by Tubbsmcfat on 2010-03-04
Ok no when i save something, where is the my documents folder located in Puppy?

---

### Post by Tubbsmcfat on 2010-03-04
I cant seem to be able to find the my documents folder when i save something](*,)

---

### Post by Tubbsmcfat on 2010-03-04
Okay i want internet now, i have a Belkin Wireless Usb adapter, i plug it in, i go to the wireless scanner... and nothing. Im sumped](*,)

---

### Post by NightwishFan on 2010-03-04
What is the output of this?
```
sudo lshw -C network
```

---

### Post by Tubbsmcfat on 2010-03-04
What do you mean? I just try to set it up using the connect icon, but i cant find the right driver for it, do you know what it might be called?:?:

---

### Post by NightwishFan on 2010-03-04
Perhaps if you would run the specified command in the terminal and post the output here, I could tell you. ;)

---

### Post by 4Orbs on 2010-03-04
Tubbsmcfat: you should seriously consider asking for help on the Puppy Linux forums rather than here... since you are now using Puppy. This thread's title indicates that you are using Xubuntu, and the answers you receive here will pertain to Xubuntu instead of Puppy (unless the person responding happens to read all the posts on this thread). I think you can probably see the potential for serious consequences because of any misinformation you might get from an answer regarding Xubuntu that you attempt to apply to your installed Puppy. We love you here, but to get the appropriate help you should be visiting the right forum (Puppy forums). Just a suggestion.

---

### Post by Rex Bouwense on 2010-03-04
> **4Orbs said:**
> Tubbsmcfat: you should seriously consider asking for help on the Puppy Linux forums rather than here... since you are now using Puppy. This thread's title indicates that you are using Xubuntu, and the answers you receive here will pertain to Xubuntu instead of Puppy (unless the person responding happens to read all the posts on this thread). I think you can probably see the potential for serious consequences because of any misinformation you might get from an answer regarding Xubuntu that you attempt to apply to your installed Puppy. We love you here, but to get the appropriate help you should be visiting the right forum (Puppy forums). Just a suggestion.
Good point.  If you need the site it is [http://www.murga-linux.com/puppy/](http://www.murga-linux.com/puppy/).  Enjoy.

---

