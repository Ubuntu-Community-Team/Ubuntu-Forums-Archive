---
title: "Ubuntu not installing"
date: 2011-02-12
forum: New to Ubuntu
---

### Post by oberliner on 2011-02-12
Hello there everyone,

I'm very new to ubuntu (I just downloaded it yesterday), and I'm hoping that one of you might be able to answer my question. I've been trying to install Ubuntu 10.10 on an old laptop I have (about 4 years old).

The trouble is it seems to get stuck on the "loading screen." (I'm not sure what to call it; it says "ubuntu" and has little white dots that blink to red one after another.) It won't ever move on to where I can actually install Ubuntu. It just sits on that screen for hours.

I've tried burning a new cd, restarting the computer, letting it sit overnight, installing the netbook version (instead of the desktop version). I also tried checking the boot options; it says that it can boot from a CD, so I don't think that's the issue.

Anyway, I'd really like to get this sorted out, and any help you have would be much appreciated!

Thanks!

---

### Post by dalekirkwood on 2011-02-12
Whats the spec of your laptop? Are you using the correct version (64bit or i386 or mac)? Whats the make of the laptop?

---

### Post by jerrrys on 2011-02-12
be nice to know how much ram you have

---

### Post by oberliner on 2011-02-12
Wow, you all rock! I totally didn't think people would get back as fast as you all did!

It's an HP pavillion currently running Windows XP. It's got 1.50GHz Intel processor, and it's got 480 MB of RAM.

As for the version of Ubuntu that I'm trying to install, I've been trying the 32-bit version.

I'm not quite sure if that's all the information you all were asking for. Frankly, I'm not super computer literate (though, downloading linux is part of my plan to become more so)

Thanks again for all your help!

---

### Post by jerrrys on 2011-02-12
you got enough ram and computer to run ubuntu.  have you first just tried running the live cd?

---

### Post by dalekirkwood on 2011-02-12
Your getting stuck on the boot screen which is where Ubuntu loads all the files for a live boot. Personally I would try an older version of Ubuntu, maybe 10.04 LTS (Long Term Support) just to see if you can get it to load the GUI install otherwise you may wish to try this - [http://www.ubuntu.com/desktop/get-ubuntu/alternative-download]("http://www.ubuntu.com/desktop/get-ubuntu/alternative-download") - a text based install. Your laptop sounds like it is an ok spec. Please let us know if you get any luck.

---

### Post by Hippytaff on 2011-02-12
What graphics card do you have? is it nvidia?

---

### Post by oberliner on 2011-02-12
I'm not sure. What is running the live CD? Putting it in after the computer has rebooted? I haven't done that. Should I try it?

---

### Post by dalekirkwood on 2011-02-12
No a live CD is when the OS is run off the CD, Standard Ubuntu Install CD's are now Live CD's as standard so it is already trying a live boot.

---

### Post by Hippytaff on 2011-02-12
try the live environment - put the cd in, reboot and it should just boot from live cd, else you might have to change the boot sequence in your bios, but I doubt that needs to happen - if you can run that you can choose to install ubuntu

---

### Post by hansolo4949 on 2011-02-12
Boy, that sure is cutting it close! The MINIMUM requirements for a normal (gui) install is as follows: 

1 GHz x86 processor
512MB of system memory (RAM)
5GB of disk space (for OS files; consideration should be given to the (often very large) size of user files that will occupy the /home directory)
Graphics card and monitor capable of 1024x768
Cd/Dvd-drive
Sound support, if you need sound.
Internet access is helpful


From what you are saying, it may be your ram is preventing you from installing. Try running a lighter version, [Xubuntu]("http://www.xubuntu.org/") and see if it works. If it does, that means that your system us probably too lightweight for Ubuntu. Xubuntu works just as well, and when you get advanced enough, it is pretty easy to install a gui that looks like Ubuntu.

Hope that helps!

---

### Post by jerrrys on 2011-02-12
you have the option at the beginning to install ubuntu or try it.  just try it and see what results you get

---

### Post by oberliner on 2011-02-12
I'll try to use the slightly older version, and I'll post if that works. Thanks for the tip!

Also, it's an intel 82852/82855 GM/GME Graphics Controller.

---

### Post by oberliner on 2011-02-12
Cool. I'll try it and let ya know.

---

### Post by dalekirkwood on 2011-02-12
> **Hippytaff said:**
> try the live environment - put the cd in, reboot and it should just boot from live cd, else you might have to change the boot sequence in your bios, but I doubt that needs to happen - if you can run that you can choose to install ubuntu

That is what is he is doing I believe. Am I correct saying this is the screen its stuck on?[IMG]http://www.indygeek.net/wp-content/uploads/2010/05/ubuntu-load-screen1.jpg[/IMG]

The Ubuntu install disc loads a live install then you install from the desktop.

---

### Post by Hippytaff on 2011-02-12
> **oberliner said:**
> I'll try to use the slightly older version, and I'll post if that works. Thanks for the tip!

Also, it's an intel 82852/82855 GM/GME Graphics Controller.

then you shouldn't get graphics issues, as already suggested Lubuntu or Xubuntu might be a better option given your specs :-)

---

### Post by jerrrys on 2011-02-12
> **oberliner said:**
> I'll try to use the slightly older version, and I'll post if that works. Thanks for the tip!

Also, it's an intel 82852/82855 GM/GME Graphics Controller.

its not slightly older, its ubuntu LTS (long term support)

---

### Post by Hippytaff on 2011-02-12
> **dalekirkwood said:**
> That is what is he is doing I believe. Am I correct saying this is the screen its stuck on?[IMG]http://www.indygeek.net/wp-content/uploads/2010/05/ubuntu-load-screen1.jpg[/IMG]

The Ubuntu install disc loads a live install then you install from the desktop.

Yeah...I think it's lack of ram. Gnome is greedy :-)

---

### Post by hansolo4949 on 2011-02-12
Yep, please try that and tell us what happened. Glad that everyone agrees with me! But anyway, you will need a fair amount of ram to run Ubuntu even if you can run the installer in sub 512 Meg conditions. Ubuntu recommends at least 1 gig to run properly. So I would just stick with Xubuntu, if it works.

---

### Post by oberliner on 2011-02-12
Hey everyone,

Okay, so I tried it by putting the CD in after it had already started up. I followed the directions, but, alas, no joy.

I'm starting the download of xubuntu now, it'll take about a half an hour, but I'll try that next.

Also, the screen of which you posted the image is indeed the screen it's getting stuck on.

Thanks again for all of your help!

---

### Post by dalekirkwood on 2011-02-12
My apologies I overlooked the 512mb RAM. On boot Ubuntu eats up 800MB of RAM. Hope you get some luck from it.

---

### Post by jerrrys on 2011-02-12
> **hansolo4949 said:**
> Yep, please try that and tell us what happened. Glad that everyone agrees with me! But anyway, you will need a fair amount of ram to run Ubuntu even if you can run the installer in sub 512 Meg conditions. Ubuntu recommends at least 1 gig to run properly. So I would just stick with Xubuntu, if it works.

not that this is a perfect world, but i got ubuntu on a box with 512M ram and dual boot.  it will work

---

### Post by hansolo4949 on 2011-02-12
Hope it works! I have subscribed to the thread, so I'll be sticking around. Now, whether you think that is good or not......


My fingers are crossed for you!

---

### Post by hansolo4949 on 2011-02-12
Yes, I know it will probably work on that much ram, jerrrys, but I am sure you are only running one program at a time, and have disabled several features to be able to do that with that much ram comfortably.

---

### Post by jerrrys on 2011-02-12
> **hansolo4949 said:**
> Yes, I know it will probably work on that much ram, jerrrys, but I am sure you are only running one program at a time, and have disabled several features to be able to do that with that much ram comfortably.

no, haven't disabled anything, work out of the box (10o4)

i should add that gimp runs acceptable on it, but im not using it as my primary box

---

### Post by oberliner on 2011-02-12
Hey everyone,

So, I tried to install xubuntu 10.10, but that didn't work either. This time, I was able to get to a screen that asked for a language selection and another that asked if I wanted to install. When I said yes (in all the different forms, i.e. try without installation, install, etc.), it went to a screen that only said xubuntu and say there. It seems content to sit there for hours.

I also tried installing it by putting the CD after I'd started the computer up. When I asked it to help me install, it would start, but then display an error message: "An error has occurred. Permission Denied." It directed me to another file, but I couldn't find that anywhere.

Thanks again for your help.

---

### Post by Hippytaff on 2011-02-13
The iso might be corrupt or has been corrupted via the burn process you can [check the md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") to verify that. You might be more successful [booting from usb]("http://unetbootin.sourceforge.net/")

Failing that it might be a hardware issue, however if none of the above works try the [minimal install]("https://help.ubuntu.com/community/Installation/LowMemorySystems") and installing [fluxbox]("https://help.ubuntu.com/community/Installation/LowMemorySystems#Fluxbox") or one of the other light windows managers.

---

### Post by The Cog on 2011-02-13
It coul dstill be running out of RAM during the install. I would suggest that you try the "alternate" install CD. This is a text-mode installer so it's much less memory hungry than the GUI based ones although the questions are the same.

You could go for the Ubuntu destop version. The advantages are that this is the "standard" version and you will get more help from the forums than with the less well known desktops. The possible disadvantage might be slowness due to lots of disk swapping.

Xubuntu is said to be lighter and faster although I just prefer it for its look and feel. So it might be faster on your laptop, but fewer people here will be able to help with GUI questions.

Tough choice, but I think since you are a complete newcomer, I think you should go with Ubuntu first and later Xubuntu if performance really sucks.

---

### Post by hansolo4949 on 2011-02-13
@the cog,


IF he/she can get Ubuntu to install, that is what they should go with.


@Jerrrys,

I am happy Ubuntu works just fine with that much ram. Do you have any limitations when you run it on that much? I have been lucky enough to install it in systems that have plenty if ram, so I would not know (they also all happen to be laptops). I am interested to know!


@oberliner, I wish you the best of luck, and Ubuntu is not normally this frustrating! I promise you will like it after all this grief is over.

---

### Post by jerrrys on 2011-02-13
the biggest limitation it has is its 100MHz front side bus, but its surprising how it will hobble along.  i got it because it came with a 19" monitor i wanted.  so im thinking if this old thing can do it, just about anything else can.  its a dell 240

---

### Post by hansolo4949 on 2011-02-13
Ouch, that sounds pretty slow! I guess, in conclusion, that as long as you have enough ram to run the GUI installer, you probably can run Ubuntu/Xubuntu/Lubuntu on just about anything. Happy hobbling!;)

---

### Post by jerrrys on 2011-02-13
and like the cog said, theres always the alternate install.

---

