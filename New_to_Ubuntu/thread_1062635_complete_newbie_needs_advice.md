---
title: "complete newbie needs advice"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by rick fowler on 2009-02-07
hi all i hope there is someone here kind enough to help a newbie out,i am coverting from vista 64bit to ubuntu 64bit os.
my specs are
q6600 overclocked to 3.5ghz
ati radion 4850
asus p5q pro mobo
4gig dominator ram
500gig digital westen hard drive

ok the plan is this downloading os,then i burn using infrarecorder,i want to get rid off vista and put ubuntu on as sole os,whats the best method for that,also im a bit confused on how much drive space to give os need help here.


secondly wanted to know will i be able to run zbrush 3.1(3d program) and paintshop cs3 with this os,if so how do i get them running,i heard about wine but im not sure as im a complete newbie to this os,so if someone can give me a step guide to installing these apps that would be great.

lastly drivers for my grapics card ect how do i go about getting and installing these,will i still get the ati program which controls my card settings ect,i hope someone can help me here as really hoping this os will make me more happy,i have read some treads on here but would like a bit more help or rather a laymans way of doing it lol,sorry if i have asked loads just wanted to do a smooth change over many thanks in advance.

---

### Post by nj96 on 2009-02-07
hi.

Yes, installing ubuntu is easy except there is are a few tricky parts. You should make sure you don't use up your whole disk partitions or windows will vanish.(*if you want windows.*)then itll be a piece of cake.

---

### Post by nj96 on 2009-02-07
oh.. and to install your hardware mostly the graphics card, you should go to the settings on ubuntu and click hardware. It will then search for hardware on your os. You then need to just enable the driver and restart ubuntu.
voila!

---

### Post by konqueror7 on 2009-02-07
about whats the best way to install ubuntu is by using the manual partition method in my opinion, lets you customize your partitions...you could use this as a [guide]("http://http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm")

about your applications, you could first check it out if running it under wine is acceptable, [AppDB]("http://appdb.winehq.org/")...if it doesn't support it yet, you could try some alternatives for your 3d program like blender (but i know you would prefer you application;))

as for you video card drivers, usually most of them are automatically installed by ubuntu, but for some proprietary drivers like nvidia, you could install it through "System>Administration>Hardware Drivers", or using Envy for installing you ati/nvidia drivers (this is what i use), [here]("http://albertomilone.com/nvidia_scripts1.html")..

hope i helped you somehow...

---

### Post by theinnercityhippy on 2009-02-07
It's worth pointing out that a good first step in the direction of Linux would be to first download a live install cd such as those found at 

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Then, when you have burned this iso image to a cd/dvd using whatever disk burning application you have with windows (or order a copy from the website if you don't have any), check your bios settings (if you've overclocked I'm assuming you know how to do this) to make the cd/dvd your first boot device. 

Boot the computer with the disk in the drive and run the distro as a live system. This means that you can have a poke around with settings/software etc to your hearts content without committing the system to disk at this stage or overwriting any existing files.

When you are sure Ubuntu is right for you, you have the choice of either dual booting with windows, choosing which you would like to use at boot time, or installing over the whole drive.

Due to your exacting requirements of software etc, I would probably recommend dual booting at first which will allow you to continue being productive whilst you look for open source equivalents to your software (eg replacing photoshop with the GIMP).

Check the forums out for some great advice on how to do this. I'm deliberately not posting a link as learning to search the forums successfully is a vital part of the linux experience, and can be one of the most enjoyable as you are welcomed into the community.

Good Luck, any problems at all then reply to this thread and I will try to help you.

-JimDog*-

---

### Post by johnjohn2 on 2009-02-07
> **theinnercityhippy said:**
> It's worth pointing out that a good first step in the direction of Linux would be to first download a live install cd such as those found at 

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Then, when you have burned this iso image to a cd/dvd using whatever disk burning application you have with windows (or order a copy from the website if you don't have any), check your bios settings (if you've overclocked I'm assuming you know how to do this) to make the cd/dvd your first boot device. 

Boot the computer with the disk in the drive and run the distro as a live system. This means that you can have a poke around with settings/software etc to your hearts content without committing the system to disk at this stage or overwriting any existing files.

When you are sure Ubuntu is right for you, you have the choice of either dual booting with windows, choosing which you would like to use at boot time, or installing over the whole drive.

Due to your exacting requirements of software etc, I would probably recommend dual booting at first which will allow you to continue being productive whilst you look for open source equivalents to your software (eg replacing photoshop with the GIMP).

Check the forums out for some great advice on how to do this. I'm deliberately not posting a link as learning to search the forums successfully is a vital part of the linux experience, and can be one of the most enjoyable as you are welcomed into the community.

Good Luck, any problems at all then reply to this thread and I will try to help you.

-JimDog*-

[www.winehq.com](www.winehq.com) is a god place to start with CS3 issues, i have the game Audiosurf working perfectly on 8.10.

It also depends what your flavour is i.e. Studio, Kubuntu, Ubuntu to name but a few.

For media creation you could do alot worse than use Studio.

Regards John

---

### Post by Sidewinder1 on 2009-02-07
Welcome Rick! :-)
I agree with all stated above. Since you have to maintain productivity with specified windose apps. run from "Live cd" first; then run "dual boot installation" while tweeking the various linux apps. that meet your needs. No sense burning any bridges behind you when you don't have to.
Good luck; and search these forums when you're looking for answers, as they are invaluable.

---

### Post by Sidewinder1 on 2009-02-07
Oh, I forgot. If you do decide to dual boot make sure that you defragment your windose partition prior to repartitioning the drive to accept ubuntu.

---

### Post by rick fowler on 2009-02-07
well i got it ubuntu installed updated ect i got wine installed,wanted to install zbrush 3.1 installed it on c drive ok there went to apps wine programs and there it was so clicked on my zbrush but nothing not a dickie bird does that mean i cant use it,shame really but if thats the case what else is as good to use,i really dont want to go back to vista but i need my programs like zbrush cs3,so fair it looks ok a bit plain lookin anyone got a place i can get some good looking wallpapers themes from.anyway if you have any ideas on gettin this zbrush to work let me know,but bear in mind im a newbie to this so commands ect are new to me.cheers

---

### Post by Muffinabus on 2009-02-07
I found a howto on getting Zbrush 3.1 installed via Wine here: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=12004](http://appdb.winehq.org/objectManager.php?sClass=version&iId=12004)

Not sure if it helps you at all.

> 1. in order to install the full version of zbrush 3.1 you need to install the demo version first.

2. you need a working zbrush installation in windows to grab a file named vcomp.dll search it under windows folder on your windows installation copy and paste it under /windows/system32 wine folder.

3. back to your ubuntu and go to applications > wine > browse c:\ drive and delete the folder /winsxs under windows folder then copy the folder with the same name you can find inside working windows installation. you will notice the name is capitalized and different from the one you just deleted, ignore the difference.

4. go to applications > wine > configure wine and on the application tab change the windows version to windows 98.

5. install dcom98 using this command on terminal
wget [www.kegel.com/wine/winetricks](www.kegel.com/wine/winetricks) && sh winetricks dcom98

6. run zbrush and use the key like you do it in windows installation.

---

