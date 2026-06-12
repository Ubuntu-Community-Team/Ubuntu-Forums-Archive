---
title: "Just switched a few questions"
date: 2010-08-03
forum: New to Ubuntu
---

### Post by Aulex on 2010-08-03
As u can see by the title i just switched from win 7 pro x64 to ubuntu x64, well dual boot, and i ran into two problems, one is quite important grub, when i got ubuntu 10.04 i had many updates a few was about grub, when i did update ubuntu and restarted my computer i ran into an error where it said no devices where found xxxx-blah blah its just the udid, grub recovery >, and i also couldn't boot into an os because the error was before the grub selection menu so then i booted my comp from a live cd i played around with a few things updating grub and so on and this time i got a different error, file not found. At this point i gave up and reinstalled ubuntu. Now ubuntu keeps on telling me i have those same updates which i refuse to install, is there any solution to this problem so i can install the update

**Never mind about the one below the driver apparently got installed so now i have opengl**
My second problem includes the gl which i have no clue what it is. I have this thing called cairo dock, which you probably already know about that acts like a dock similar to mac os x's and a few of the options said that it needed opengl. Which i have no clue what it is, i googled it up and had something to do with graphics card capabilities, and nvidea (my graphics card is 8800 gts) said that my graphics card supports that, so i decided to download the driver even though i got this automatically when i first started up ubuntu and it installed it for me. When i tried to run the file, which has the extension .run, with sh, sudo, and chmod +x i ran into an error, which ill post later if requested cause im using windows so i can't simulate it. So my question here is how do i install the driver or is there another way to get opengl 

thanks for the help:D

---

### Post by ubunterooster on 2010-08-03
I say install those updates and if something goes wrong see this solution: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by sandyd on 2010-08-03
> **Aulex said:**
> As u can see by the title i just switched from win 7 pro x64 to ubuntu x64, well dual boot, and i ran into two problems, one is quite important grub, when i got ubuntu 10.04 i had many updates a few was about grub, when i did update ubuntu and restarted my computer i ran into an error where it said no devices where found xxxx-blah blah its just the udid, grub recovery >, and i also couldn't boot into an os because the error was before the grub selection menu so then i booted my comp from a live cd i played around with a few things updating grub and so on and this time i got a different error, file not found. At this point i gave up and reinstalled ubuntu. Now ubuntu keeps on telling me i have those same updates which i refuse to install, is there any solution to this problem so i can install the update
**<snip>**
thanks for the help:D
You didn't need to reinstall ubuntu.
You could have simply reinstalled grub.
post the output ot 
```

sudo fdisk -l
```
and ill give you some commands you can run after a grub update that will ensure that grub doesn't screw up.

---

### Post by low_rider on 2010-08-03
openGL is a graphics programming language which I think comes standard on ubuntu.  If you want to test to see if yours is working open up a terminal and type:
$ glxinfo | grep direct

if you see "direct rendering: Yes" then opengl should be working

(note you may need to install glxinfo with sudo apt-get install mesa-utils)

If you don't have openGL installed you'll need to find the appropriate driver for your graphics card.  I don't have an nvidia card so I'm not quite sure which driver that is, but if you could post the error you were getting that would help.

I just installed cairo and everything worked just fine for me. However I did notice that it had downloaded two versions, one with opengl and one without.


Hope this helps!

---

### Post by Aulex on 2010-08-04
@ubunterooster ok ill try that

@carlee i was looking all over trying to figure out how to do that, and ill post it in my edit, im in windows again if i get the error again :D

@low_rider its ok that problem is solved

---

### Post by mikewhatever on 2010-08-04
Sometimes, knowing what to search for is the question of life and death, if only you had asked.;)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by Aulex on 2010-08-06
ok im in the middile of the update and after i update everything grub gave me a bunch of choices ill list them here:

1.install the package maintainer's version
2.keep the local version currently installed
3.show the differences between the versions
4.show a side-by-side difference between the versions
5.show a 3-way difference between available versions
6.do a 3-way merge between available versions (experimental)
7.start a new shell to examine the situation

please respond quickly if u can cause im goanna turn off my computer very soon

**Edit: **srry im ignoring some of the others posts guys im just trying to take one suggestion at a time right now im trying ubunturooster next will be carlee if i run into problems

---

