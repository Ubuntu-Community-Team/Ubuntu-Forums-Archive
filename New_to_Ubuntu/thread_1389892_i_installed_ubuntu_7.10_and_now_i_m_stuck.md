---
title: "i installed ubuntu 7.10 and now i m stuck"
date: 2010-01-25
forum: New to Ubuntu
---

### Post by sashi on 2010-01-25
help please, i installed ubuntu 7.10 gutsy and now i m stuck literally, i can download driver s i can t install software i can do any thing. heck i can t even install a flash player for the browser. please please help me.

---

### Post by Merk42 on 2010-01-25
[Ubuntu 7.10 is no longer supported](http://www.ubuntu.com/products/ubuntu/release-cycle)

I would recommend either getting the Long Term Support Hardy Heron 8.04 from April 2008 or the more recent Karmic Koala 9.10 from October 2009. Both can be downloaded from [Ubuntu's Website](http://www.ubuntu.com)

---

### Post by yeats on 2010-01-25
Unfortunately, Gutsy has not been supported or maintained for some time.  You'll want to upgrade to 8.04 (at least), which will be supported through next year.  Are you able to download and install a newer version?

---

### Post by zipperback on 2010-01-25
To install software you can use synaptic.

Click System -> Administration -> Synaptic Package Manager

Select the packages that you would like to install, and click "Apply".

When the system asks you for the password, it is YOUR password.

- zipperback
:popcorn:

---

### Post by zipperback on 2010-01-25
You should really consider downloading the most recent version of Ubuntu available.

Here is the download page.
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

- zipperback
:popcorn:

---

### Post by sashi on 2010-01-25
i can download the new version but i have no software to burn the iso into a cd.

---

### Post by Merk42 on 2010-01-25
It's been so long, there's nothing under Accessories? CD/DVD creator?

Do you have a USB drive? You can put the iso on that with [UNetbootin](http://unetbootin.sourceforge.net/).

---

### Post by infinitejones on 2010-01-25
> **sashi said:**
> i can download the new version but i have no software to burn the iso into a cd.

You could download it!

Here's [some options for Windows]("http://mp3.about.com/od/essentialsoftware/tp/Best_Free_Burning_software.htm") if that's what you're using, or if you've got Ubuntu running, install Brasero (either via Synaptic or by typing ```
sudo apt-get install brasero
``` at the command line).

Or you could transfer the ISO to a USB drive - [here are the instructions]("https://help.ubuntu.com/community/Installation/FromUSBStick"). Where I live, I can get 2GB USB drives for $8 from the office supply store, so hopefully that's an easy option for you too.

If none of that works, tell us exactly what problems you're having when you try to install stuff and we'll help you try and fix it.

Just saying "it doesn't work" isn't going to help us or you very much at all!

---

### Post by sashi on 2010-01-25
i ve started downloading 9.10 it take me an hour to complete. i ve already installed and am running 7.10 right now. my computer dates back to the stone age and i have no idea what motherboard it uses. but when i installed xp in it last time i did t even need any drivers to make all the hardware work(sound graphic card). i ve got plenty of thumbdrives so i think i ll go with that option. all i want is to be able to hear some music and watch video and also use flash player based websites.

some bacis specs of my comp,
amd duron 900mhz
10 gb harddisk
256 mb ram
64 bit tnt nvidia gpu

thank you so so so much to everyone who is trying to help me. i really appreciate the help, been having a totally bad day, my proper computer died and i had am forced to use this comp till i manage to get some money to redo my original.and it been hell trying to get this old computer to run n again and when i finally did i m stuck with the OS.

---

### Post by Merk42 on 2010-01-25
If your computer "Dates back to the stone age" it may not support booting from USB, so just keep that in mind.

If it does, you have to make sure you set it to check your USB drive before your harddrive in your BIOS.

---

### Post by oldos2er on 2010-01-25
With those specs you should grab the alternate CD: [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

---

### Post by infinitejones on 2010-01-25
According to [this page]("https://help.ubuntu.com/community/Installation/SystemRequirements"):

Ubuntu should run reasonably well on a computer with the following minimum hardware specification. However, features such as visual effects may not run smoothly.

    * 700 MHz x86 processor
    * 384 MB of system memory (RAM)
    * 8 GB of disk space
    * Graphics card capable of 1024x768 resolution

So unfortunately you're going to be pushing it a bit. Just don't try activating the graphics effects or anything like that. Also you'll only have about 2GB of hard disk left, but that's where those thumb drives will come in handy!

Depending on how much you've downloaded so far (and therefore whether you want to abort!), you could try installing Xubuntu instead - all the software you need is still there (browser, email, media player etc) but much better for lower-spec machines like yours.

---

### Post by sashi on 2010-01-25
i ve considered all your opinions and my options. i have a windows me cd which is not bootable. can you guys tell me how to run the setup.exe file? when i click it it says no program found to run it.

---

### Post by Merk42 on 2010-01-25
> **sashi said:**
> i ve considered all your opinions and my options. i have a windows me cd which is not bootable. can you guys tell me how to run the setup.exe file? when i click it it says no program found to run it.

If it's not bootable you're not going to be installing it.

I'm guessing the setup.exe would be if you put it in a computer running Windows 98 or so.

Also Windows Me, is also unsupported and even older than Ubuntu 7.10 so you'd be going backwards

---

### Post by sashi on 2010-01-25
ok. i guess i m @#$%ed. i guess i ll just go soundless and videoless till i get my computer fixed.i just checked i can t boot from the usd drive either, usb 1.1 and the bios does t have a option to chose the boot propriety.anyway i appreciate all your help guys thanks anyway.

---

### Post by Merk42 on 2010-01-25
Sorry it didn't work out for you. Maybe you could get someone else to burn the installation CD for you?

---

### Post by oldefoxx on 2010-01-25
Linux distros will run in 256 MB, but it might limit you,  Might want to check into whether you can use a thumb drive to extend virtual memorym as would be much haster than a hard drive.  Actuallym that just means making the thumb drive a swap partition.  Some prefer to install Linux to the thumb drive and carry it around for use on other PCs,  Linux much better for older machines than Windows, so you should see some improvement in performance

---

### Post by markbuntu on 2010-01-25
For old machines like that you might want to use xubuntu or puppy linux or something like them which is aimed at old machines with slow processors and limited ram.

---

