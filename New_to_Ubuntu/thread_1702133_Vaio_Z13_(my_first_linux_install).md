---
title: "Vaio Z13 (my first linux install)"
date: 2011-03-07
forum: New to Ubuntu
---

### Post by stygilation on 2011-03-07
Hello Guys;
I have found two guide and don't exactly know which one to choose.
My Vaio Z model is the VPC-Z13M9E/B. 

the lowl guide I have problem kernel 2.6.35-rc5 sources don't even know what to do with it...

The adhocism guide I have problem with installing the upstart-vaioz-gfx script (how do I even do that?) edit the gdm.conf (don't know what to edit...)

[http://lowl.net/en/linux-on-vaio-vpc-z.html#bios](http://lowl.net/en/linux-on-vaio-vpc-z.html#bios)

[http://www.adhocism.net/2010/11/installing-ubuntu-10-10-on-sony-vaio-vpc-z13m9eb/](http://www.adhocism.net/2010/11/installing-ubuntu-10-10-on-sony-vaio-vpc-z13m9eb/)

---

### Post by maqtanim on 2011-03-07
Hey... Welcome to the Community! :D

Forget about all the geeky things written on those links. Just forget those. Now start from the very beginning. First, Download the Ubuntu ISO from [here]("http://www.ubuntu.com/desktop/get-ubuntu/download"). Once you download it, you need to burn it into a CD/DVD or USB. Now follow the instructions written in that same link about how to burn or how to make an USB drive bootable. Ubuntu has a fantastic option of "TRYING". That means to test Ubuntu you do not need to install it! As you are not installing, so you donot have to worry about your existing settings of Windows. Now put the CD into the CDROM Drive and boot the computer from your CD. You'll find an option to "TRY UBUNTU" or "INSTALL UBUNTU". Just click the "try Ubuntu".

Let us know, if you face any problem with this procedure.

---

### Post by Lead_Rover on 2011-03-07
G'day mate,

I've tried the adhocism method with minor success. I haven't yet tried the lowl method. 

I have a VPCZ138GG, 64bit Ubuntu 10.10. After my first attempt (following procedures found on forums) I only had the vesa drivers working, second attempt I had a weird tiled effect happening...no idea why. I'm hoping to have some time soon to sit down and nut it out once and for all. 

I can't remember exactly how to do everything that you needed to do for the adhocism method. If you read the README.txt and search through the ubuntu forums you'll find other people who have done it and gotten various results. Some were quite well detailed.

Once I get some free time I'll try the lowl method and see if I can get anything working. When I do I'll let you know what I did and how I did it. 

Please post any progress you make too. 

In response to Maqtanim's message, most of the time the install cd will let you trial ubuntu with no errors, but occasionaly I've noticed it just doesn't want to work. I found that if you stay in speed mode you tend to get a higher success rate though.

best of luck!

---

### Post by stygilation on 2011-03-08
Hey again, I have tried the Adhocism method and Lowl method and have done a bit resource:
 
Lowl Result 1: 
-------------------------------------------------------------------------------------------------
I'm stuck right here. I just dont know what to do with it:
22/10/2010 update : Download these modified[ kernel 2.6.35-rc5 sources]("http://lowl.net/wp-content/uploads/drm-intel-edp-fixes-54d0229.tar.gz") (edp-fixes branch from jbarnes drm-intel git repository), untar it and go into his directory. 
**Does anyone know how to install the kernel?**
 
This guide seems to be very succesful with vaio z13 after all the comment I have observed on his blog. People in the comment have claimed to have everything even the graphic switching working except hibernate and suspend. Though I do not know if we still have to boot on a kernel to activate the card then restart and then log into Ubuntu
--------------------------------------------------------------------------------------------------
 
Adchocism Result 2:
--------------------------------------------------------------------------------------------------
I am stuck at this:
Installing the upstart-vaioz-gfx script
Editing the gdm.conf
 
Though everything worked in speed mode after the update manager, the intel card doesn't work and I have to boot and choose a kernel to activate the Nividia card speed mode everytime to use ubuntu.
 
---------------------------------------------------------------------------------------------------
 
Though what I want the most help with is the Lowl guide:
Adhocism is based on Fredricks guide: 
[http://questier.com/2010/04/26/ubuntu-10-4-lucid-lynx-on-sony-vaio-vpcz11x9e/](http://questier.com/2010/04/26/ubuntu-10-4-lucid-lynx-on-sony-vaio-vpcz11x9e/)
It's seem far more complicated to follow him but the blogs comment seems to be usefull, Hawk have claimed to have the suspend working in the Z13 series: [http://hawkcode.blogspot.com/2010/06/vpcz11z9e-on-ubuntu-lucid-lynx-9.html](http://hawkcode.blogspot.com/2010/06/vpcz11z9e-on-ubuntu-lucid-lynx-9.html)
If I could combine the Lowl guide with hawks guide, I think I would have a perfect Vaio Z13. + the newest Nvidia driver just came out 2011.03.07: [http://www.nvidia.com/object/linux-display-amd64-260.19.44-driver.html](http://www.nvidia.com/object/linux-display-amd64-260.19.44-driver.html)
Any of you know if it's give the Vaio Z some more problem?
 
So I need a bit help for the Lowl guide please:) and of course the Adhocism guide on how to edit and install the script

---

### Post by Lead_Rover on 2011-03-08
Thanks for the update. I'll see if I can work on the lowl method this weekend.

As I'm not sure if you're having problems untar'ing the file or building the kernel please forgive me for posting about both. 
To untar the sources create a directory using **mkdir** 
Then cd to that directory and type **tar -zxvf yourfile.tar** command to extract the file to the current directory. 
Then try to follow the steps in here to build the kernel [https://help.ubuntu.com/community/Kernel/Compile]("https://help.ubuntu.com/community/Kernel/Compile")

Alternatively use this guide [http://blog.avirtualhome.com/2010/11/06/how-to-compile-a-ubuntu-10-10-maverick-kernel/]("http://blog.avirtualhome.com/2010/11/06/how-to-compile-a-ubuntu-10-10-maverick-kernel/")
Its pretty detailed and I'm sure you shouldn't have too many issues. 

let me know if you do. I'm keen to hear how your integration of both the hawk and lowl methods go. Maybe when you're done you'll have a package you can release to help everyone else run linux on their vaio. All the best mate!

---

### Post by maqtanim on 2011-03-08
Having no prior experience with VAIO, I thought it would be a piece of cake! (Actually it is a piece of cake for my Dell Inspiron!) :P

Well.. it seems you are confused where to put the kernel files and how to access it, right? To do that, just copy the archives from that link to your home direectory. Then right click on that archive and extract that. Rename the extracted folder as **kernel**. Now open the terminal from **Applications > Accessories > Terminal** from the top panel and write the following command:
```
cd kernel
``` So now you're inside the kernel directory. That is what is mentioned by " *22/10/2010 update : Download these modified[ kernel 2.6.35-rc5 sources]("http://lowl.net/wp-content/uploads/drm-intel-edp-fixes-54d0229.tar.gz") (edp-fixes branch from jbarnes drm-intel git repository), untar it and go into his directory. *"

From now on just follow the instructions of Lowl or Lead_Rover.

---

### Post by stygilation on 2011-03-12
Update...
I haven't got time to do the guide, but I have unlocked the bios at least. By only unlocking the bios in the vaio z and switching the graphic policy to statistic, means that every time I boot my vaio the speed mode is on. using the update manager and Nvidia driver (System->Administration->additional drivers), means that everything work in speed just by pressing the power button, except the brightness key (no need to choose a kernel and reboot). 

This is so far what I have done-> unlock bios->updated Ubuntu and driver. 

I will still have to install the  kernel 2.6.35-rc5 sources to test the Intel-card.

I couldn't done this without low's guide. He also answered me after 3-5 minutes in the morning after I commented on his blog for help so lead_rover you could ask him for help. And of course thanks a lot for the kernel guide Maqtanim and lead_rover it helped a lot though I had to reinstall Ubuntu because I panicked and wrote a bad command.
---------------------------------------------------------------------------------------------------------------------------------
Additional information:
The Vaio Z last 3 hour in speed  mode might be lower or higher I don't remember in windows 7 though.

---

### Post by Lead_Rover on 2011-03-13
Thanks for the update mate. Really appreciate it. I'm trying to build the latest stable kernel at present and see if that fixes everything(lowl suggested it on his site). I'll let you know if that works too.

---

### Post by karel_buls on 2011-03-14
Lead_Rover, are things working now? I'm considering buying the same laptop but would be good to have some decent information regarding Linux support. How is the battery life by the way? Thanks!

---

### Post by stygilation on 2011-03-14
Karel_buls 

For my Vaio Z it's approximately 3 hours with speed mode I haven't had time to build the stable kernel yet though. It should be a lot lower in stamina mode.

---

