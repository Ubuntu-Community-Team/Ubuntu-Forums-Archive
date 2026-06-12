---
title: "running ubuntu on my laptop"
date: 2011-07-02
forum: New to Ubuntu
---

### Post by moonrays00 on 2011-07-02
im new here i want to run ubuntu on my acer 4750g 

will it work? :)
im using windows 7 64 bit.

can i dual boot with ubuntu?
how?

---

### Post by wildmanne39 on 2011-07-02
> **moonrays00 said:**
> im new here i want to run ubuntu on my acer 4750g 

will it work? :)
im using windows 7 64 bit.

can i dual boot with ubuntu?
how?Hi, you should be able too, I would like you to put this command in a terminal
```
sudo lshw
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets, that way I can make sure you have enough resources for ubuntu 11.04.

---

### Post by ClientAlive on 2011-07-02
Hi,

Welcome to Linux, to Ubuntu, and to the forums. You can dual boot. A lot of people do. I've never actually done it (I just switched completely when I went). I won't try to advise you on it but here's a link that may help.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Some people experience driver issues with certain acers. I'm not sure which ones but you might want to google around and see what others face who have acers. Linux is pretty darn good about driver support but there are a couple cards that are known problems (like the broadcom wireless card I have). There's usually always a way to work it out though. Just have to identify the solution and implement it.  :)

googlubuntu is google for ubuntu. It's a great way to find info.

[www.googlubuntu.com](www.googlubuntu.com)

here's a search on your computer on googlubuntu: [http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-8&q=acer+4750g&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-8&q=acer+4750g&as_qdr=all&sa=Google+Search&lang=en)

HTH
----------------

Edit:

Posting the output of what Wildemann asked for will also tell us what graphics card you have. Some nVida cards take a little tweak to get em' going with Ubuntu.

---

### Post by wolfen69 on 2011-07-02
> **moonrays00 said:**
> im new here i want to run ubuntu on my acer 4750g 

will it work? :)
im using windows 7 64 bit.

can i dual boot with ubuntu?
how?

You might want to read this [http://forums.opensuse.org/english/get-technical-help-here/64-bit/456838-acer-4750g.html](http://forums.opensuse.org/english/get-technical-help-here/64-bit/456838-acer-4750g.html)

I also saw other posts with people that had problems with that model. I wish you luck, but if worse comes to worse, you could install ubuntu via wubi. (which I normally don't advocate)

---

### Post by ClientAlive on 2011-07-02
well these guys here make it sound like there is no driver in existance for that card

[http://forums.nvidia.com/index.php?showtopic=191054](http://forums.nvidia.com/index.php?showtopic=191054)

if that's the case though, then what is it using for a driver when one pulls it off the shelf at the store? Doesn't make sense.

And here's an interesting link:  [http://ubuntuforums.org/archive/index.php/t-1657660.html](http://ubuntuforums.org/archive/index.php/t-1657660.html)

really we need to see the output of a couple things first though to be sure which cards you have and what kind of sys resources you have.

You'll have to run Ubuntu live on the thing in order to run these and get any information from them. Just choose "Try Ubuntu" when prompted at the first screen. It won't install and won't make any changes to your computer. Actually, doing that before installing is wise because it will show you exactly what things would be like/ would happen if you do install. If any issues come up you can find a fix for them and fix them running live first. If the fix works then you know you can install and just repeat what you did and you should be golden.

Actually theres a better one for the two cards that matter most when it comes to compatibility issues. Give us the lshw output first if you will. Then try these two so we see what graphics and what network card you have.

```
lspci | grep VGA
```

And

```
lspci | grep Network
```

If, for some reason, either of those don't give you any output then just run:

```
lspci
```

And paste the whole long list here. We'll sort it out

Thanks

---

### Post by moonrays00 on 2011-07-03
im confused 

its my first time :)

i never tried using ubuntu and installed one :)
can you simplify it for me?

i just want to dual boot :) ubuntu and windows 7 64 bit

---

### Post by waynefoutz on 2011-07-03
> **moonrays00 said:**
> im confused 

its my first time :)

i never tried using ubuntu and installed one :)
can you simplify it for me?

i just want to dual boot :) ubuntu and windows 7 64 bit


Youtube is your friend.

How to burn the disk:

[http://www.youtube.com/watch?v=F4quWYKejPk](http://www.youtube.com/watch?v=F4quWYKejPk)


You being a total newbie, and not even knowing if Ubuntu will work on your machine yet, since Windows is the only operating system on your computer, I'd recommend the "Wubi" install. It's installing Ubuntu under Windows. Basically, what goes on there, is instead of doing any major alterations to your hard drive, this method takes a chunk of hard drive space, makes one big file, and tricks Ubuntu into thinking that file is a hard drive. The advantage of this is, you can go into Add/Remove Programs in Windows, and get rid of Ubuntu any time you want. The disadvantage, if something happens to your Windows OS, in some cases, Ubuntu is killed off as well. Here's another How To:

[http://www.youtube.com/watch?v=iW1V6TuZZmc&feature=related](http://www.youtube.com/watch?v=iW1V6TuZZmc&feature=related)

The other way to install is to permanently install it on it's own physical partition. You do that by booting off the cd and clicking the install icon. You can dual boot this way as well, but it's a little  more involved if you choose to get rid of it, so the Wubi method is better for first timers, I think.

---

### Post by moonrays00 on 2011-07-03
> **waynefoutz said:**
> Youtube is your friend.

How to burn the disk:

[http://www.youtube.com/watch?v=F4quWYKejPk](http://www.youtube.com/watch?v=F4quWYKejPk)


You being a total newbie, and not even knowing if Ubuntu will work on your machine yet, since Windows is the only operating system on your computer, I'd recommend the "Wubi" install. It's installing Ubuntu under Windows. Basically, what goes on there, is instead of doing any major alterations to your hard drive, this method takes a chunk of hard drive space, makes one big file, and tricks Ubuntu into thinking that file is a hard drive. The advantage of this is, you can go into Add/Remove Programs in Windows, and get rid of Ubuntu any time you want. The disadvantage, if something happens to your Windows OS, in some cases, Ubuntu is killed off as well. Here's another How To:

[http://www.youtube.com/watch?v=iW1V6TuZZmc&feature=related](http://www.youtube.com/watch?v=iW1V6TuZZmc&feature=related)

The other way to install is to permanently install it on it's own physical partition. You do that by booting off the cd and clicking the install icon. You can dual boot this way as well, but it's a little  more involved if you choose to get rid of it, so the Wubi method is better for first timers, I think.

is this the wubi one? 

[http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)


so if i install this i could remove if i want to via add/remove programs.

in accessing ubuntu i will still choose the os via booting? :)

---

### Post by waynefoutz on 2011-07-03
> **moonrays00 said:**
> is this the wubi one? 

[http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)


so if i install this i could remove if i want to via add/remove programs.

in accessing ubuntu i will still choose the os via booting? :)

yes! that will work, you won't even have to burn a disk that way. so it's a lot easier that way. The downside to that, is you won't have a physical disk. 
You can also choose which version of Ubuntu with that method, for instance, Ubuntu, Kubuntu, or Xubuntu. They all have a different look and feel to them. I'd try Ubuntu first, although Kubuntu is my personal favorite.

---

### Post by moonrays00 on 2011-07-03
> **waynefoutz said:**
> yes! that will work, you won't even have to burn a disk that way. so it's a lot easier that way. The downside to that, is you won't have a physical disk. 
You can also choose which version of Ubuntu with that method, for instance, Ubuntu, Kubuntu, or Xubuntu. They all have a different look and feel to them. I'd try Ubuntu first, although Kubuntu is my personal favorite.

ah i see thats good :)

but i feel like when i install the OS i will encounter a problem like some people who posted above. problem is i am too noob to understand :(

physical disk? partition on my OS? so the disadvantage on not having a physical disk if my windows 7 doesn't works it will affect ubuntu as well thats fine by me xD is that the only disadvantage?

---

### Post by waynefoutz on 2011-07-03
> **moonrays00 said:**
> ah i see thats good :)

but i feel like when i install the OS i will encounter a problem like some people who posted above. problem is i am too noob to understand :(

physical disk? partition on my OS? so the disadvantage on not having a physical disk if my windows 7 doesn't works it will affect ubuntu as well thats fine by me xD is that the only disadvantage?

Yes. The Wubi installer is the way to go if you're new, or just want to test it out. I just wouldn't use it permanently or save any crucial data in Ubuntu installed that way, since it's not a real disk. Still a great way to try it out, get your feet wet. There is no partitioning. It's easily removed. Another disadvantage I just recalled is an Ubuntu Wubi install can't read or see  anything on the Windows drive, while a real install can. Still, this is the way I'd go for now.

---

### Post by ClientAlive on 2011-07-03
> **moonrays00 said:**
> ah i see thats good :)

but i feel like when i install the OS i will encounter a problem like some people who posted above. problem is i am too noob to understand :(


What some people do, and I think it's wise, is to run Ubuntu live first. Running it live is not the same as installing it on a partition of it's own or installing it via wubi. All it means is you are choosing to try it without it being put on your computer at all. The way this is done is simply to click the "try Ubuntu" button on the first screen you will see after you put the disc in the drive. The link to the youtube vid on how to burn a disc is a good start (the one in waynefoutz post). Then there's this:

[http://youtu.be/gIwPYy4Sigo](http://youtu.be/gIwPYy4Sigo)

(The guy in the vid is saying to have the disc in the drive. Then either power off the computer and push the power button again OR restart it. Right away, right when the computer is first first starting up (you have to get on it fast) there is one of the F# keys or the esc key that your computer uses to get into the "boot screen". You have to find out which key it is for your computer and use that one. The boot screen lets you choose which device on your computer to "boot from". In this case you would highlight and choose the cd/dvd drive and push enter. Once you do that Ubuntu will load up on your computer from that disc and there is an option in there to "try Ubuntu").

That being said, there are at least two good reasons to do this first:

(1) You can try it out without any affect to your computer and see if you like it. The next time you power the computer off, the disc will be ejected and you will be asked to take it out of the drive, shut the door and press enter to finish the shut down process. This will leave you in the same position you started. No changes to the computer whatsoever. One thing about "trying Ubuntu" is that any changes you make in Ubuntu while running it live will not be saved (so if you create a document or download a program or something it won't be there again after you shut down. There's a way to change that but let's not get into that now).

And (2): This one, in my opinion, is the more important reason. If there are going to be any compatibility issues with your computer they will show up when you run Ubuntu live (the "try Ubuntu" option) the same way they would if you installed (whether you do it wubi way or on it's own partition). What that means is that running it live (trying it) is a way to test drive what kind of problems might come up upon install before actually installing.

And there is a third thing (3) When you are running it live, if there are problems, you can fix the problems while running live the same way you would if you installed - except it still won't save those changes after you power off. This fact (not saving changes) is a pro and a con all in one. It is a pro because you get to figure out how to fix the problem without it being a critical situation where the problem knocks your computer out and you 'have to fix it' or the computer won't work. It is a con because, when you do install, you will have to do the fix all over again to make it permanent. Even the con part of it is mostly a pro anyway though because then you will have already learned what the problem is going to be and how to fix it and it will be easy to just go in and repeat the solution. EAsY PeASy!


> **moonrays00 said:**
> 
physical disk? partition on my OS? so the disadvantage on not having a physical disk if my windows 7 doesn't works it will affect ubuntu as well thats fine by me xD is that the only disadvantage?


In the most basic sense what a wubi install is, is almost like the way a virtual machine works. Instead of installing right onto the hard drive it makes a folder on the hard drive and then looks at that folder like it is a hard drive in and of itself. It then installs to the folder as though the folder were the hard drive. What is mean by losing Ubuntu if Windows messes up is that, with this way of doing it, Windows is still the base system and Ubuntu is just residing inside that folder. If something happens to Windows it could, possible knock that folder with Ubuntu in it out, as well. If you've invested a lot of time into making little tweaks and adding stuff to Ubuntu this might not make you feel very happy f it were to happen.

By contrast, creating a separate partition for Ubuntu makes a more permanent change to your hard drive than does a wubi install. I mean, it's not really "permanent," it can be changed as easily as it was created, but it is more so than a wubi install. This is an option better suited for a situation where you are certain you want that operating system on there for a while.

That being said, there are a lot of different Linux distributions out there and they are all pretty cool in their own right. Sometimes the differences are striking, sometimes they are not as much so. Ubuntu is a great first time Linux experience because it is easy to use for someone with little or no Linux experience. In general, though, navigating around the gui is not too much different than Windows. I mean, it's different, but it's not like an alien planet or something. You just have to see it to know what I'm talking about.

As an added bonus/ tip. Might I suggest that one good way to check out multiple distributions of Linux is to use something called virtualiztion. With virtualization you can install a program on your computer that will allow you to install multiple operating systems in it. You have to run them one at a time (there are exceptions to the one at a time thing but I won't get into them now) but you can have a whole list of installed operating systems in that program and just play with them and check them out. With virtualization the changes you make to that virtual operating system (called a guest) is permanent. (Not permanent like it can't be undone but permanent like it will still be there when you come back again).

Virtual Box is a free Virtualization software that a lot of people like. It's easy enough to learn and get started. Here's the link to their web site in case you'd like to check that out more.

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)  (by "host" what they mean is the operating system that it will be installed on)

If it was me *and this is just my personal opinion/ preference* I'd run Ubuntu live first ("try Ubuntu"), use that to figure out if there is going to be any problems and learn how to fix them, use that knowledge to install it but completely get rid of Windows in the process and just only have Linux on my machine, then install Virtual Box on that new operating system and put all kinds of different Linux distributions on it, to play with and check out. That's just me though. You do whatever suits you best brother.


Hope it helps. If you have any more questions, let us know. I'll be around and so will others.

Ubuntu is extremely cool, no, Linux is extremely cool - EXTREMELY! I just hope you get a chance to exper it my friend. I think you'll love it. You'll have to learn a little bit, but that isn't any different that when you started using Windows; and, I think, it's deff worth it.

:popcorn:

---

### Post by waynefoutz on 2011-07-03
> **ClientAlive said:**
> What some people do, and I think it's wise, is to run Ubuntu live first. Running it live is not the same as installing it on a partition of it's own or installing it via wubi. All it means is you are choosing to try it without it being put on your computer at all. The way this is done is simply to click the "try Ubuntu" button on the first screen you will see after you put the disc in the drive. The link to the youtube vid on how to burn a disc is a good start (the one in waynefoutz post). Then there's this:

[http://youtu.be/gIwPYy4Sigo](http://youtu.be/gIwPYy4Sigo)

(The guy in the vid is saying to have the disc in the drive. Then either power off the computer and push the power button again OR restart it. Right away, right when the computer is first first starting up (you have to get on it fast) there is one of the F# keys or the esc key that your computer uses to get into the "boot screen". You have to find out which key it is for your computer and use that one. The boot screen lets you choose which device on your computer to "boot from". In this case you would highlight and choose the cd/dvd drive and push enter. Once you do that Ubuntu will load up on your computer from that disc and there is an option in there to "try Ubuntu").

That being said, there are at least two good reasons to do this first:

(1) You can try it out without any affect to your computer and see if you like it. The next time you power the computer off, the disc will be ejected and you will be asked to take it out of the drive, shut the door and press enter to finish the shut down process. This will leave you in the same position you started. No changes to the computer whatsoever. One thing about "trying Ubuntu" is that any changes you make in Ubuntu while running it live will not be saved (so if you create a document or download a program or something it won't be there again after you shut down. There's a way to change that but let's not get into that now).

And (2): This one, in my opinion, is the more important reason. If there are going to be any compatibility issues with your computer they will show up when you run Ubuntu live (the "try Ubuntu" option) the same way they would if you installed (whether you do it wubi way or on it's own partition). What that means is that running it live (trying it) is a way to test drive what kind of problems might come up upon install before actually installing.

And there is a third thing (3) When you are running it live, if there are problems, you can fix the problems while running live the same way you would if you installed - except it still won't save those changes after you power off. This fact (not saving changes) is a pro and a con all in one. It is a pro because you get to figure out how to fix the problem without it being a critical situation where the problem knocks your computer out and you 'have to fix it' or the computer won't work. It is a con because, when you do install, you will have to do the fix all over again to make it permanent. Even the con part of it is mostly a pro anyway though because then you will have already learned what the problem is going to be and how to fix it and it will be easy to just go in and repeat the solution. EAsY PeASy!




In the most basic sense what a wubi install is, is almost like the way a virtual machine works. Instead of installing right onto the hard drive it makes a folder on the hard drive and then looks at that folder like it is a hard drive in and of itself. It then installs to the folder as though the folder were the hard drive. What is mean by losing Ubuntu if Windows messes up is that, with this way of doing it, Windows is still the base system and Ubuntu is just residing inside that folder. If something happens to Windows it could, possible knock that folder with Ubuntu in it out, as well. If you've invested a lot of time into making little tweaks and adding stuff to Ubuntu this might not make you feel very happy f it were to happen.

By contrast, creating a separate partition for Ubuntu makes a more permanent change to your hard drive than does a wubi install. I mean, it's not really "permanent," it can be changed as easily as it was created, but it is more so than a wubi install. This is an option better suited for a situation where you are certain you want that operating system on there for a while.

That being said, there are a lot of different Linux distributions out there and they are all pretty cool in their own right. Sometimes the differences are striking, sometimes they are not as much so. Ubuntu is a great first time Linux experience because it is easy to use for someone with little or no Linux experience. In general, though, navigating around the gui is not too much different than Windows. I mean, it's different, but it's not like an alien planet or something. You just have to see it to know what I'm talking about.

As an added bonus/ tip. Might I suggest that one good way to check out multiple distributions of Linux is to use something called virtualiztion. With virtualization you can install a program on your computer that will allow you to install multiple operating systems in it. You have to run them one at a time (there are exceptions to the one at a time thing but I won't get into them now) but you can have a whole list of installed operating systems in that program and just play with them and check them out. With virtualization the changes you make to that virtual operating system (called a guest) is permanent. (Not permanent like it can't be undone but permanent like it will still be there when you come back again).

Virtual Box is a free Virtualization software that a lot of people like. It's easy enough to learn and get started. Here's the link to their web site in case you'd like to check that out more.

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)  (by "host" what they mean is the operating system that it will be installed on)

If it was me *and this is just my personal opinion/ preference* I'd run Ubuntu live first ("try Ubuntu"), use that to figure out if there is going to be any problems and learn how to fix them, use that knowledge to install it but completely get rid of Windows in the process and just only have Linux on my machine, then install Virtual Box on that new operating system and put all kinds of different Linux distributions on it, to play with and check out. That's just me though. You do whatever suits you best brother.


Hope it helps. If you have any more questions, let us know. I'll be around and so will others.

Ubuntu is extremely cool, no, Linux is extremely cool - EXTREMELY! I just hope you get a chance to exper it my friend. I think you'll love it. You'll have to learn a little bit, but that isn't any different that when you started using Windows; and, I think, it's deff worth it.

:popcorn:


What you are saying is true, mostly. On my machine, the live environment works fine, but after the actual install, I have to do some wrestling to get my 3G modem working, even though it worked fine when running off the CD. 

That said, the OP is a beginner, that's the purpose of the thread, and he just wanted to try out Ubuntu the easiest way. I warned him that Wubi is not meant to be permanent. I could have thrown other methods like Virtualbox and the like, but after all, this is the "For Absolute Beginners" section of the message board. He even found the Wubi installer link on his own, I simply encouraged him along. In my opinion, a Wubi install is a far closer way to experience the real install, without actually installing it. Also deleting a real install, merging the partitions back into one, and restoring the Windows master boot record is something you and I can do in a couple of minutes, but for someone who has never done it before could very easily lose all their data.

---

### Post by moonrays00 on 2011-07-04
i understand a bit now :)

so you recommend to try ubuntu live to my laptop so that i will check which problem i will be able to face ? :) so that in the future you will help me how to find the solution or ill help myself :)

---

### Post by mastablasta on 2011-07-04
exactly. the live option will load everything to ram. so it might (especially if run from CD) be a bit slow as CD are slow to read. if computer supports USB bnooting it's better, safer and faster to do it form USB key. for that you can use LinuxLive USB creator found here: [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)
 
another option is uNetbootin found here: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
 
Anyway Live OS won't do any changes. since it's all in ram everything you download is lost after reboot (unless in case of USB where oyu can add persistance to it). but it gives the user an option to test the OS and desktop environment (Ubuntu has GNOME, Kubuntu - KDE, Xubuntu - XFCE and Lubuntu - LXDE). to see if all hardware is linux compatible. then if all works you can go onto next step - installation.
 
oh and if something doesn't work get here and ask why, how, why not. people here may be able to force it to work.  :-D

---

### Post by moonrays00 on 2011-07-04
> **mastablasta said:**
> exactly. the live option will load everything to ram. so it might (especially if run from CD) be a bit slow as CD are slow to read. if computer supports USB bnooting it's better, safer and faster to do it form USB key. for that you can use LinuxLive USB creator found here: [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)
 
another option is uNetbootin found here: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
 
Anyway Live OS won't do any changes. since it's all in ram everything you download is lost after reboot (unless in case of USB where oyu can add persistance to it). but it gives the user an option to test the OS and desktop environment (Ubuntu has GNOME, Kubuntu - KDE, Xubuntu - XFCE and Lubuntu - LXDE). to see if all hardware is linux compatible. then if all works you can go onto next step - installation.
 
oh and if something doesn't work get here and ask why, how, why not. people here may be able to force it to work.  :-D

thanks guys wow i was thinking if i could use usb for running live well you answered it in advance :)]


done downloading and installed the linux live usb creator
can someone give a tutorial about this.. I need a reliable one :)
that goes for you guys :)

---

### Post by ClientAlive on 2011-07-04
> **moonrays00 said:**
> thanks guys wow i was thinking if i could use usb for running live well you answered it in advance :)]


done downloading and installed the linux live usb creator
can someone give a tutorial about this.. I need a reliable one :)
that goes for you guys :)


There's one at their site brother. Check the tabs at the top on that site.

:)

---

### Post by moonrays00 on 2011-07-05
> **ClientAlive said:**
> There's one at their site brother. Check the tabs at the top on that site.

:)

why it says "I have the right ISO but is corrupted or was altered Please download it again.

but im downloading couple it times and still the same

---

### Post by wildmanne39 on 2011-07-05
> **moonrays00 said:**
> why it says "I have the right ISO but is corrupted or was altered Please download it again.

but im downloading couple it times and still the same
Hi, is that after you try to install from usb stick or livecd, or when you ran a checksum test on it, if it is when you run a checksum test try to download from another server.

---

### Post by moonrays00 on 2011-07-06
> **wildmanne39 said:**
> Hi, is that after you try to install from usb stick or livecd, or when you ran a checksum test on it, if it is when you run a checksum test try to download from another server.

im using ubuntu right now via usb flash drive (ubuntu live) i pressed try ubuntu..

in terms of internet connection it seems its good in connecting via WiFi

noob question: i want to run my video card?

and also is it possible to install my drivers? but its windows 7 compatible i think 

from here:
[http://support.acer.com/us/en/product/default.aspx?tab=1&modelId=3520](http://support.acer.com/us/en/product/default.aspx?tab=1&modelId=3520)

i want webcam application to be installed so that i can use the webcam
,turbo boost monitor,audio driver,intel rapid storage tech.

but in the website it says for windows 7 will it be compatible to linux? if not any solutions you could recommend

it says bluetooth is installed but when i turn it on its not highlighted is this normal?

---

### Post by wildmanne39 on 2011-07-06
> **moonrays00 said:**
> im using ubuntu right now via usb flash drive (ubuntu live) i pressed try ubuntu..

in terms of internet connection it seems its good in connecting via WiFi

noob question: i want to run my video card?

and also is it possible to install my drivers? but its windows 7 compatible i think 

from here:
[http://support.acer.com/us/en/product/default.aspx?tab=1&modelId=3520](http://support.acer.com/us/en/product/default.aspx?tab=1&modelId=3520)

i want webcam application to be installed so that i can use the webcam
,turbo boost monitor,audio driver,intel rapid storage tech.

but in the website it says for windows 7 will it be compatible to linux? if not any solutions you could recommend

it says bluetooth is installed but when i turn it on its not highlighted is this normal?
Hi, ok running usb live is just so you can try it and make sure everything works before you install ubuntu, you need to install ubuntu before you install video card drivers and wireless drivers, it looks like everything will work, but there maybe some manual setting up that will have to be done to get wireless and video card setup properly, we can help you with that after you install ubuntu. To install ubuntu you can use this guide.
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
This is basically how you will install ubuntu, some of the pictures will look different because this is for the previous version of ubuntu but the instrcutions are the same. Please follow the instructions carefully, also you can choose to let ubuntu install along side windows and it will split the drive in half that is the easy way.

---

### Post by moonrays00 on 2011-07-06
> **wildmanne39 said:**
> Hi, ok running usb live is just so you can try it and make sure everything works before you install ubuntu, you need to install ubuntu before you install video card drivers and wireless drivers, it looks like everything will work, but there maybe some manual setting up that will have to be done to get wireless and video card setup properly, we can help you with that after you install ubuntu. To install ubuntu you can use this guide.
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
This is basically how you will install ubuntu, some of the pictures will look different because this is for the previous version of ubuntu but the instrcutions are the same. Please follow the instructions carefully, also you can choose to let ubuntu install along side windows and it will split the drive in half that is the easy way.

last question in shrinking my HDD how much will i shrink?

i have 382 GB free in my hard drive

---

### Post by ClientAlive on 2011-07-06
A couple points here:

1) Make certain you have a good backup before installing or shrinking anything. There are a lot of ways and tools for making backups. One tool that I like is Clonezilla Live. (you can google "download clonzilla live"). It is text based so it may look a little scary but it's easy to follow if you just read the descriptions and menu items as you go along. Virtually all the selections you will make (at least the first 3 or 4) will be the default that is already highlighted for you. There are good tutorials available for this too if you google for them. Clonezilla will make an exact clone of your system (your Windoze system) before you make any changes by installing anything. You can save that image (the clone) to an external drive; and, if anything were to go sideways on you, you could use clonzilla again to restore the clone and get right back to where you started - no harm no foul.

2) It has been said; that, when making a dual boot (windoze/ linux) it's better to install Linux first as a fresh install then windows and not the other way round. There are some reasons they say that but I won't get into them here. If you were to do that. What you would do is use clonezilla (or something like it) to make your clone, then wipe the disk (optional), then install Linux directly (no dual anything at that point), then install windoze as the second o/s (here then would be where your dual boot comes in). A tip is that at that last part (where you install widows as the second o/s or dual o/s) you can use that clone you made to get the exact same widows you left off with (the one with all you personal little tweaks or whatnot in it).

Would be good for some of the other members to check me on this one though. I'm just repeating something I've heard about in a few places but I've never actually had the privilege of experiencing it myself.

HTH

---

### Post by wildmanne39 on 2011-07-06
Hi, you should resize your partition from windows but leave the space unallocated you want to create the partitions for ubuntu from the livecd, give as much space as you want to ubuntu,just do not make it to small, say 20 gigs for / which is root
2 gigs for swap
and what ever amount you want to for home or data, you can make this partition ntfs if you want so you can access your pictures movies from ubuntu and windows, but the files system needs to be ext3 or ext4. Also it is a lot easier to have windows installed then install ubuntu, otherwise when you install it windows it will overwrite the ubuntu boot loader and you will have to go through a lot of trouble reinstalling it.

---

### Post by ClientAlive on 2011-07-07
> **wildmanne39 said:**
> Also it is a lot easier to have windows installed then install ubuntu, otherwise when you install it windows it will overwrite the ubuntu boot loader and you will have to go through a lot of trouble reinstalling it.


Thanks for the clarification. Guess it's the other way round eh'?

---

### Post by moonrays00 on 2011-07-07
> **wildmanne39 said:**
> Hi, you should resize your partition from windows but leave the space unallocated you want to create the partitions for ubuntu from the livecd, give as much space as you want to ubuntu,just do not make it to small, say 20 gigs for / which is root
2 gigs for swap
and what ever amount you want to for home or data, you can make this partition ntfs if you want so you can access your pictures movies from ubuntu and windows, but the files system needs to be ext3 or ext4. Also it is a lot easier to have windows installed then install ubuntu, otherwise when you install it windows it will overwrite the ubuntu boot loader and you will have to go through a lot of trouble reinstalling it.


so ill install ubuntu via usb? using the live cd that was attached to my usb?  right? correct me if im wrong :)

---

### Post by Neoxhadowespio on 2011-07-07
A bit off-topic but I consider this fairly important.
And by no means do I attempt to (by my own will) to discurage you from using a Linux distobution. (a.k.a. Ubuntu, Kubuntu (as you heard before), and/or Debian (you will recognize if you did some WikiResearch). The only thing is, it appears that you will require a bit of knowledge before you truely get anywhere. Not that any of it is very tedious or difficult as many people may think initially. I myself am in Grade 7 and I know quite a bit. But much of this knowledge comes from experience. If you have some time in your hands, then go ahead! The route may be a little bumpy but rewarding. But if you intend to use it for work then proceed with caution. Its just that with little knowledge, a small error can lead to some bigger problems. Especially if you are unfamiliar with Linux. Also, some things unfortunatly cannot be replaced by Linux after Windows. Such is true for some software, hardware, etc. Its a fact of life. Windows, as terrible as it truely is (but one who has only used Windows his entire life will never realize this), is the most popular operating system in the world. And only god knows how it still exists. Sorry, this is a bit long but my point is, those unfamiliar with Linux who rely on their PCs for something as serious as your job may have trouble dealing with its occasional difficulties. If only we could get bigger with more support and make it easier to use. If we could surpass Windows and Macs in every way and truely become the most popular OS. Then we would be near flawless, perfect. Thats about all and welcome to the world of Linux! Where possibilities are (almost) endless ;)

---

### Post by wildmanne39 on 2011-07-07
> so ill install ubuntu via usb? using the live cd that was attached to my usb? right? correct me if im wrongHi, you can just use the usbdrive to install ubuntu, but please do what I mentioned in my last post for resizing and creating partitions.

---

### Post by moonrays00 on 2011-07-08
[IMG]http://i54.tinypic.com/34yuqrn.jpg[/IMG]

i cant shrink? O.o


i want to shrink it to 102400 MB or 100GB right?

---

### Post by ClientAlive on 2011-07-08
> **moonrays00 said:**
> [IMG]http://i54.tinypic.com/34yuqrn.jpg[/IMG]

i cant shrink? O.o


i want to shrink it to 102400 MB or 100GB right?


Did you defrag your hard drive before attempting this?

What is the used and available space (including the unit of measurement)?

What is the current partition scheme on that hard drive? Is there more than one partition? What are their sizes? What are they for within the overall system?

---

### Post by moonrays00 on 2011-07-08
> **ClientAlive said:**
> Did you defrag your hard drive before attempting this?

What is the used and available space (including the unit of measurement)?

What is the current partition scheme on that hard drive? Is there more than one partition? What are their sizes? What are they for within the overall system?

i defragged it but still nothing changed

[IMG]http://i52.tinypic.com/50mudc.jpg[/IMG]

there are 365 GB free of 596 GB

overall hdd is 640 i think the rest to system reserved

---

### Post by wildmanne39 on 2011-07-08
Hi, size of your drive does not change from running defrag, I think I gave you a link much earlier in this thread but I might not have so here is one with pictures for resizing partitions in windows with pictures, just scroll down the page until you see it.
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

---

### Post by ClientAlive on 2011-07-08
> **wildmanne39 said:**
> Hi, size of your drive does not change from running defrag, I think I gave you a link much earlier in this thread but I might not have so here is one with pictures for resizing partitions in windows with pictures, just scroll down the page until you see it.
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)


Not to get off track here or anything; but, do you think that using up all the possible primary partitions could be part of a Windows strategy to keep people from putting any other o/s on their machine? Or at least making it much more difficult for them to do?

Oh, sorry, that notion occurred to me when reading the thread at your link (above). I got as far as post #7 where it shows the layout of the drive partitions on that brand of machine - and it struck me! That would be a great way to discourage people from using any other o/s on the machine. Make it hard for them to install anything else by using up all the partitions they are able to have.

Just a though. Moonray has a different brand of machine so nothing to worry about there (no worries moonray, you got this man!).

---

### Post by wildmanne39 on 2011-07-09
> Not to get off track here or anything; but, do you think that using up all the possible primary partitions could be part of a Windows strategy to keep people from putting any other o/s on their machine? Or at least making it much more difficult for them to do?Hi, I have thought the same thing before, windows does make things as hard as possible for people to install another operating system I think, I never boot my windows, it makes me break out in a rash.

---

### Post by moonrays00 on 2011-07-09
and now im more confused ill just read the new thread..

the only problem im encountering now is shrinking the disk to make a partition then install the ubuntu from it :(


so when shrinking what will i use in windows or ubuntu?

---

### Post by ClientAlive on 2011-07-09
> **moonrays00 said:**
> and now im more confused ill just read the new thread..

the only problem im encountering now is shrinking the disk to make a partition then install the ubuntu from it :(


so when shrinking what will i use in windows or ubuntu?

Hi,

Yeah, I know. These things were confusing at first for all of us. Taking just a little time to learn about the basics is a great first step and you'll be surprised how quickly you can learn a whole lot! Computers are amazing. It's an appliance. It isn't magic. It can't think or do anything on it's own. It was engineered by another human being and is really more like an over grown toaster than anything. Just that you can do so much with this 'toaster' - lol. Seriously though, it's worth checking out.


So then, there's a difference between defragmenting your hard drive and resizing a partition on it.

Defragmeting needs to be done because, with a Windows file system, the files and other data that are on the drive end up getting spread around on the physical unit (the hard drive). As time goes on there ends up being stuff scattered all over the drive. (A hard drive is still a physical piece of equipment made up of real tangible materials, metals and plastics and whatnot).

Resizing has to do with changing the dimensions of the partitions. A partition is like having a wall on either side of a space that defines its boundaries. Resizing is like moving that wall over one way or another.

But what happens if you move the wall and it ends up getting parked right on top of something you need? Something important. Or, what happens if you intend to clear out or remodel the space on the other side of that wall after you've moved it; but when you move it there are still important things you need on the other side? The side you intended to remodel.

Those "important things" are the files and parts of files, data, etc that get spread around, scattered across the disk (disk is another way of saying "hard drive"). So this is why a person defragments the disk. One reason is to make sure all those important things are all in one place before they resize a partition. Kind of like making sure you move all your important furniture and belongings out of the room before you begin construction to remodel that room. You take those imprtant things and put them all toget in one safe place together so nothing happens to them when you do the construction.

There is also a second reason people defragment their disk and this one is not connected to resizing. The other reason is that, when those files and parts of files, data, etc - get spread around on the disk like that, it makes your computer run slower. When you tell the computer to do something by clicking some button or typing something in and hitting enter, it may have to access information stored on the hard drive (the disk). If that information is broken up and spread all around it will have to work harder to find all the relevant pieces it needs in order to do what you asked it to. This makes it take longer to complete the task. This is the other reason people defragment a Windows file system: once again, to move those files and pieces back to being all grouped up in one place (on the physical, tangible disk).

I say "a Windows file system" because the file system(s) Linux uses do not do that. It doesn't loose track of information and the stuff end up scattered all over the place like Windows does.

These are all foundational concepts (what a file system is, how a hard drive is constructed and how the space is divided up on the physical drive (hint: "platters, tracks, and sectors"). You would gain quite a bit of understanding if you look at some wikipedia articles on some of these subjects. Check out search terms in wikipedia on things like: Hard disk drive, partitioning, RAM, and any other terms you encounter that you wonder about. Here's one to get you started (if you want):

[http://en.wikipedia.org/wiki/Hard_disk_drive](http://en.wikipedia.org/wiki/Hard_disk_drive)


Reading about all those things will not specifically get you any closer to having Ubuntu installed on your machine but it will help you grasp many basic concepts of how a computer works. Those basic concepts (building a foundation) are things you can keep with you and apply in many many many situations as you continue to work with your computer. That's why those fundamental concepts are so important - because they do apply to so many specific things when they come up. It's up to you, but if it was me, I'd spend a couple hours reading a few wikipedia articles and work on the dual boot at the same time. In the end you'll have much more than just a computer with two operating systems on it. You'll have valuable knowledge - and that's something no one can take from you.

Hope it helps.

Peace out for now bruthah!

:)

---

### Post by ClientAlive on 2011-07-09
> **moonrays00 said:**
> and now im more confused ill just read the new thread..

the only problem im encountering now is shrinking the disk to make a partition then install the ubuntu from it :(


so when shrinking what will i use in windows or ubuntu?


I'm sorry, in all that I never really addressed this question.

Once you have 'resized' the partition you will then be left with 'space' on the other side of the 'wall' (so to speak). Then you can 'remodel' over there in that new space. In your case maybe your remodel is to build an "Ubuntu" over there (an analogy for saying 'install Ubuntu' over there).

Right?

:)
-------------------

Edit:

If we misunderstand your question or you have more questions, please let us know.
-------------------

Edit:

> **moonrays00 said:**
> 
the only problem im encountering now is shrinking the disk to make a partition then install the ubuntu from it :(


I'm not quite sure what the source of this problem is but I'm willing to help you figure it out. If all else fails, there are other programs that can do this besides the Windows one. We can look at those options if it comes to that. I want to be sure you have all your personal data backed up though before any kind of resizing or installing Ubuntu. Unless it's a brand new computer and you have made no changes to it, I don't think you would be very happy if any of your personal files got damaged or ruined. You would lose them, possibly forever. That's why it's important to back up everything before doing something like this.

> **moonrays00 said:**
> 
so when shrinking what will i use in windows or ubuntu?

Think of an operating system (whether its Windows or Ubuntu or whatever one) like a bunch of boxes full of books. Then think of a hard drive like a garage or a shed where you want to store those boxes of books. When you move them out to that shed for the first time, that is like "installing". After you have moved them out to that shed (the hard drive) you might need to get one of those books out every so often. That is like accessing the hard drive. Sometimes you just want the book to just be handy and in a convenient place where it doesn't take so much work to go digging through all those boxes, way out in the shed, to get to it. Then maybe you go find it in the shed and you set it on a shelf next where you sit. You don't want to read it right that minute, you just want it next to you so you can reach it easy when you do want it (that's like RAM - also known as Random Access Memory but most just call it 'memory').

> **moonrays00 said:**
> . . . ill just read the new thread..


It has good info too. I read most of it myself last night.
-------------

One last thing. The difference between 'resizing' and 'partitioning' is like the difference between moving a wall and building a new one from scratch. 'Formatting' is like tearing down the building so you can put up a new one after that (that's if you format the whole entire hard drive (or disk)). You can also 'format' just a part of a drive (one partition on it) and that is like tearing out all the fixtures and carpet and whatever else in one room of the house so you can remodel that one room later.

HTH

---

### Post by moonrays00 on 2011-07-09
> **ClientAlive said:**
> Hi,

Yeah, I know. These things were confusing at first for all of us. Taking just a little time to learn about the basics is a great first step and you'll be surprised how quickly you can learn a whole lot! Computers are amazing. It's an appliance. It isn't magic. It can't think or do anything on it's own. It was engineered by another human being and is really more like an over grown toaster than anything. Just that you can do so much with this 'toaster' - lol. Seriously though, it's worth checking out.


So then, there's a difference between defragmenting your hard drive and resizing a partition on it.

Defragmeting needs to be done because, with a Windows file system, the files and other data that are on the drive end up getting spread around on the physical unit (the hard drive). As time goes on there ends up being stuff scattered all over the drive. (A hard drive is still a physical piece of equipment made up of real tangible materials, metals and plastics and whatnot).

Resizing has to do with changing the dimensions of the partitions. A partition is like having a wall on either side of a space that defines its boundaries. Resizing is like moving that wall over one way or another.

But what happens if you move the wall and it ends up getting parked right on top of something you need? Something important. Or, what happens if you intend to clear out or remodel the space on the other side of that wall after you've moved it; but when you move it there are still important things you need on the other side? The side you intended to remodel.

Those "important things" are the files and parts of files, data, etc that get spread around, scattered across the disk (disk is another way of saying "hard drive"). So this is why a person defragments the disk. One reason is to make sure all those important things are all in one place before they resize a partition. Kind of like making sure you move all your important furniture and belongings out of the room before you begin construction to remodel that room. You take those imprtant things and put them all toget in one safe place together so nothing happens to them when you do the construction.

There is also a second reason people defragment their disk and this one is not connected to resizing. The other reason is that, when those files and parts of files, data, etc - get spread around on the disk like that, it makes your computer run slower. When you tell the computer to do something by clicking some button or typing something in and hitting enter, it may have to access information stored on the hard drive (the disk). If that information is broken up and spread all around it will have to work harder to find all the relevant pieces it needs in order to do what you asked it to. This makes it take longer to complete the task. This is the other reason people defragment a Windows file system: once again, to move those files and pieces back to being all grouped up in one place (on the physical, tangible disk).

I say "a Windows file system" because the file system(s) Linux uses do not do that. It doesn't loose track of information and the stuff end up scattered all over the place like Windows does.

These are all foundational concepts (what a file system is, how a hard drive is constructed and how the space is divided up on the physical drive (hint: "platters, tracks, and sectors"). You would gain quite a bit of understanding if you look at some wikipedia articles on some of these subjects. Check out search terms in wikipedia on things like: Hard disk drive, partitioning, RAM, and any other terms you encounter that you wonder about. Here's one to get you started (if you want):

[http://en.wikipedia.org/wiki/Hard_disk_drive](http://en.wikipedia.org/wiki/Hard_disk_drive)


Reading about all those things will not specifically get you any closer to having Ubuntu installed on your machine but it will help you grasp many basic concepts of how a computer works. Those basic concepts (building a foundation) are things you can keep with you and apply in many many many situations as you continue to work with your computer. That's why those fundamental concepts are so important - because they do apply to so many specific things when they come up. It's up to you, but if it was me, I'd spend a couple hours reading a few wikipedia articles and work on the dual boot at the same time. In the end you'll have much more than just a computer with two operating systems on it. You'll have valuable knowledge - and that's something no one can take from you.

Hope it helps.

Peace out for now bruthah!

:)

wow I did learn a lot thanks for explainin it all :)

so defragmenting my hdd couple of times is good?
i see now a change of available size to shrink when i degframent my hdd shall i continue? :)

---

### Post by wildmanne39 on 2011-07-09
Hi, yes go a head and resize your partition in windows with this link as your guide, just do not format it until you have booted with the ubuntu livecd or usd stick. If it asks you to make the disk dynamic do not let it that will cause all kinds of problems.
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

---

### Post by moonrays00 on 2011-07-10
> **wildmanne39 said:**
> Hi, yes go a head and resize your partition in windows with this link as your guide, just do not format it until you have booted with the ubuntu livecd or usd stick. If it asks you to make the disk dynamic do not let it that will cause all kinds of problems.
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

WTH it comes back to 0 :confused:

---

### Post by ClientAlive on 2011-07-10
> **moonrays00 said:**
> WTH it comes back to 0 :confused:


We can't see what you're seeing brother. Without sitting in from of your compuer there's no way to understand what you are seeing or what the problem is unless you post information about it - whether pictures, screenshots, copy and pasting the output, whatever.

---

### Post by wildmanne39 on 2011-07-10
Hi, exactly I have no idea what problem you experienced. I am not going to be on here for awhile today I am working on a guide for the cube and effects. I will leave you in the capable hands of clientalive and others.

---

### Post by moonrays00 on 2011-07-13
> **ClientAlive said:**
> We can't see what you're seeing brother. Without sitting in from of your compuer there's no way to understand what you are seeing or what the problem is unless you post information about it - whether pictures, screenshots, copy and pasting the output, whatever.

i have unallocated space now 97.66 GB what will i do next to install ubuntu?

---

### Post by ClientAlive on 2011-07-14
> **moonrays00 said:**
> i have unallocated space now 97.66 GB what will i do next to install ubuntu?


If what you are saying is that the resize worked and that is how you have this unallocated space - if that, then go for it. Install it.

Do you have the cd? You burn the image to a cd then start the computer and make it boot from the cd drive. When it starts, just follow the prompts/ instructions to install it. Make sure you install it in that unallocated space. You should be asked somewhere along the installation where you want to install to. See the links we gave you in this thread here. The one that shows you how to install. While you are following the instruction and installing, look for the step where it asks you where to install to and make sure you install it there.

Hope you enjoy it brother. We do.

---

### Post by moonrays00 on 2011-07-14
> **ClientAlive said:**
> If what you are saying is that the resize worked and that is how you have this unallocated space - if that, then go for it. Install it.

Do you have the cd? You burn the image to a cd then start the computer and make it boot from the cd drive. When it starts, just follow the prompts/ instructions to install it. Make sure you install it in that unallocated space. You should be asked somewhere along the installation where you want to install to. See the links we gave you in this thread here. The one that shows you how to install. While you are following the instruction and installing, look for the step where it asks you where to install to and make sure you install it there.

Hope you enjoy it brother. We do.


im using my usb flash disk to install it since i burned it down on my usb flash disk however it wont detect my partition. it wont even detect that i have currently using windows 7.

what can be the solution to this problem?
i use Gparted to see if it detected something or not.
it only views the whole size of HDD and recommended me to format the HDD.

if i will do i will lose the files :(

---

### Post by Swagman on 2011-07-14
Why is a n00b resizing his Hard drive when he should be trying it via wubi first ?

I can see this ending in tears !!

---

### Post by moonrays00 on 2011-07-14
> **Swagman said:**
> Why is a n00b resizing his Hard drive when he should be trying it via wubi first ?

I can see this ending in tears !!

sorry im not that good :(

im just followin the other threads

---

### Post by annu2127 on 2011-07-14
U can Install is very easily, once u have windows on ur machine, just start with ubuntu setup.....it will manage it all to make ur machine dual boot by default & believe me....installing ubuntu is far easier than installing windows.....u just need to know few very basic things. & just remember to switch on all ur hardwares (eg wireless & all) while installing ubuntu. Ubuntu is smart enough to detect them & install drivers for them (i learnt from experience). just go for it....

---

### Post by moonrays00 on 2011-07-14
> **annu2127 said:**
> U can Install is very easily, once u have windows on ur machine, just start with ubuntu setup.....it will manage it all to make ur machine dual boot by default & believe me....installing ubuntu is far easier than installing windows.....u just need to know few very basic things. & just remember to switch on all ur hardwares (eg wireless & all) while installing ubuntu. Ubuntu is smart enough to detect them & install drivers for them (i learnt from experience). just go for it....

do you in installing ubuntu while on windows 7? there are many disadvantage on doin that :)

---

### Post by ClientAlive on 2011-07-15
> **moonrays00 said:**
> do you in installing ubuntu while on windows 7? there are many disadvantage on doin that :)


When you install you don't want to be in Windows when you do it. You have to put the usb in the machine and then shut off the machine then turn it back on. When it starts to come on - very very early in the very beginning - you have to press the key that gives you the boot menu. Pressing that key makes you go into something called bios or setup. Different computers use a different key to make it go into this boot menu. My computer is the esc key. Some computers it is the F12 key - but your's may be different. You need to find out which key it is for your computer first, shut the computer off, turn it on again, press the key very early at the beginning of the start up, select the item in the menu to boot from usb and press enter. (read this whole thing before you start then go back and follow along if you want to).

After that, Ubuntu (from the usb) will come up on the computer and you will have a choice to "Install Ubuntu". Make that selection and follow the instructions very carefully (read everything). When you get a chance in the steps to choose what "partition" to install to, make sure you choose the one that _doesn't have Windows on it_ - the one you made space in it for Ubuntu.

Once you have chosen _the correct partition_ to install it to, move forward in the steps. In one of the steps it's going to give you a standard warning about "formatting" and tell you it is going to "format" the partition. If you chose the _right partition_ (the one that _does not_ have Windows on it) you will be fine and just tell it "ok" or whatever the button says to make it go ahead. It will ask you questions like what language and what time zone and what user name and computer name as you go along the steps to install it. Just answer them the way you want it to be and it will install it however you told it.

By the way . . . not every computer is able to boot into usb. I have a computer in my house that does not have the option for that. If that happens you may have to burn a cd and try it that way. If you do it from the cd you just go into the same boot menu/ setup menu and that option instead of the usb one.


There is one thing that has been mentioned several times and I don't think you have answered us about it. (If I'm wrong I'll apologize but I don't think you have). This thing is EXTREMELY important.

**Make sure you have a _backup_ of your personal files from Windows.**

If you _don't have_ a **backup** and something goes wrong you will lose everything and there will be little hope to get it back.

If you _do have_ a **backup** and something goes wrong, you will be able to reinstall Windows and you will have your personal stuff - to put back on there.

There is more than one way to make a backup. If it was me (and this is just me) I would _clone_ the entire Windows. A clone makes an exact copy of the entire thing. The Windows operating system, the personal stuff, any programs you added to it, any settings you made or changed - an exact copy of the entire thing. With a clone you can take the saved clone and restore it and make the computer exactly like it was before you did anything. If something goes wrong you will have the clone to put back on the computer and you won't lose anything.


All that being said, don't be scared. Doing all these things is pretty normal and anyone can learn them. The most important thing is to follow the steps and instructions in the program when you are using it for real, and to do what you are doing - asking questions to the people who have done it before and who are here to help you.

We want to see you succeed and to help you. We did the same things in the beginning that you are doing - we started out and didn't know how and then we learned. All we did was use the programs to try them out, hands on, and use them. We made mistakes sometimes and sometimes they were big ones that cost us a lot - but we kept going forward. We kept pressing on until we got it right. When we had problems we didn't understand we came here (or other forums or friends we knew) and asked them to help us understand. You are doing good; and, if you keep it up, I know you will have what you are looking for. I only hope that Ubuntu Linux makes you as happy as it has made me and has made many others.

Linux is sooo neat because you can learn sooo much about computers by using it. Once you get it up and running, one of the next things you might want to do is start studying how to use the command line. Everyone has a different opinion about the command line, about whether it's important or not. In my humble opinion - it is very important and powerful. You don't have to use it in order to use Ubuntu. You can do all the same things without it. But the command line is something that gives you more.

I hope this has helped you. I apologize if I have been a little hard to you. I just don't want to see you have any problems with this and I felt I needed to stress a couple point. Many blessings in getting this going on your computer my friend. We will still be here if you need us.

Please be sure and let us know how you like Ubuntu and how everything went for you. You can help other people the same way we help you by telling your experience here on this post. You never know how many other people are out there have the same problem or wonder what it's like and maybe they come and see what you wrote about it for us.

It is also important to "mark you thread as solved" once you do get the problem solved. Other people looking for help can see the "solved" label on it and then they know it is something that can help them. Without it they might pass it up and not look. Don't mark it solved until it really is though. This way the other people get good information for their help.

Thanks brother.


Sincerely,
Jake

---

### Post by ClientAlive on 2011-07-15
I also would like to explain another thing. I hope it helps you.

When you install a program on a computer it is being put on a real place. It is being put on a place on your hard drive on the real hard drive.

Also, when you are in a program you have already installed, you are in that place on your hard drive. The parts inside the hard drive are at the place where the program is at.

This means that if you are 'in Windows' when you install Ubuntu it would hurt Windows. It would be the same way as if you started building another house inside your house and you didn't care if you damage the house you already have.

I want to make it clear what I mean by being 'in Windows'. I don't think you can be logged into Windows and still install Ubuntu. I don't think it would work that way. What I mean is that the parts inside the hard drive put Ubuntu on the actual drive wherever you tell it to put it. If you tell it to put Ubuntu on the 'part' (as in 'partition') of the drive that already has Windows on it, it will be like that building a house inside the one you already have and it will destroy the first house (Windows). That is why it's important to tell the computer to put Ubuntu in the other place. The other place is more like an empty lot. The ground has been prepared and it is level and ready to build on. That's where new houses (Ubuntu) goes.

Many blessings. I'm cheering for you and I hope to see you mastering computers some day. You can do it.

;)

---

### Post by ClientAlive on 2011-07-15
> **moonrays00 said:**
> im using my usb flash disk to install it since i burned it down on my usb flash disk however it wont detect my partition. it wont even detect that i have currently using windows 7.

what can be the solution to this problem?
i use Gparted to see if it detected something or not.
it only views the whole size of HDD and recommended me to format the HDD.

if i will do i will lose the files :(


One of the steps asks you if you want to install it on the whole hard drive or if you want to install it (??) whatever other options it gives you. When you are at that step make sure you choose the right option or it will show you the whole hard drive like what you said.

---

### Post by moonrays00 on 2011-07-15
> **ClientAlive said:**
> When you install you don't want to be in Windows when you do it. You have to put the usb in the machine and then shut off the machine then turn it back on. When it starts to come on - very very early in the very beginning - you have to press the key that gives you the boot menu. Pressing that key makes you go into something called bios or setup. Different computers use a different key to make it go into this boot menu. My computer is the esc key. Some computers it is the F12 key - but your's may be different. You need to find out which key it is for your computer first, shut the computer off, turn it on again, press the key very early at the beginning of the start up, select the item in the menu to boot from usb and press enter. (read this whole thing before you start then go back and follow along if you want to).

After that, Ubuntu (from the usb) will come up on the computer and you will have a choice to "Install Ubuntu". Make that selection and follow the instructions very carefully (read everything). When you get a chance in the steps to choose what "partition" to install to, make sure you choose the one that _doesn't have Windows on it_ - the one you made space in it for Ubuntu.

Once you have chosen _the correct partition_ to install it to, move forward in the steps. In one of the steps it's going to give you a standard warning about "formatting" and tell you it is going to "format" the partition. If you chose the _right partition_ (the one that _does not_ have Windows on it) you will be fine and just tell it "ok" or whatever the button says to make it go ahead. It will ask you questions like what language and what time zone and what user name and computer name as you go along the steps to install it. Just answer them the way you want it to be and it will install it however you told it.

By the way . . . not every computer is able to boot into usb. I have a computer in my house that does not have the option for that. If that happens you may have to burn a cd and try it that way. If you do it from the cd you just go into the same boot menu/ setup menu and that option instead of the usb one.


There is one thing that has been mentioned several times and I don't think you have answered us about it. (If I'm wrong I'll apologize but I don't think you have). This thing is EXTREMELY important.

**Make sure you have a _backup_ of your personal files from Windows.**

If you _don't have_ a **backup** and something goes wrong you will lose everything and there will be little hope to get it back.

If you _do have_ a **backup** and something goes wrong, you will be able to reinstall Windows and you will have your personal stuff - to put back on there.

There is more than one way to make a backup. If it was me (and this is just me) I would _clone_ the entire Windows. A clone makes an exact copy of the entire thing. The Windows operating system, the personal stuff, any programs you added to it, any settings you made or changed - an exact copy of the entire thing. With a clone you can take the saved clone and restore it and make the computer exactly like it was before you did anything. If something goes wrong you will have the clone to put back on the computer and you won't lose anything.


All that being said, don't be scared. Doing all these things is pretty normal and anyone can learn them. The most important thing is to follow the steps and instructions in the program when you are using it for real, and to do what you are doing - asking questions to the people who have done it before and who are here to help you.

We want to see you succeed and to help you. We did the same things in the beginning that you are doing - we started out and didn't know how and then we learned. All we did was use the programs to try them out, hands on, and use them. We made mistakes sometimes and sometimes they were big ones that cost us a lot - but we kept going forward. We kept pressing on until we got it right. When we had problems we didn't understand we came here (or other forums or friends we knew) and asked them to help us understand. You are doing good; and, if you keep it up, I know you will have what you are looking for. I only hope that Ubuntu Linux makes you as happy as it has made me and has made many others.

Linux is sooo neat because you can learn sooo much about computers by using it. Once you get it up and running, one of the next things you might want to do is start studying how to use the command line. Everyone has a different opinion about the command line, about whether it's important or not. In my humble opinion - it is very important and powerful. You don't have to use it in order to use Ubuntu. You can do all the same things without it. But the command line is something that gives you more.

I hope this has helped you. I apologize if I have been a little hard to you. I just don't want to see you have any problems with this and I felt I needed to stress a couple point. Many blessings in getting this going on your computer my friend. We will still be here if you need us.

Please be sure and let us know how you like Ubuntu and how everything went for you. You can help other people the same way we help you by telling your experience here on this post. You never know how many other people are out there have the same problem or wonder what it's like and maybe they come and see what you wrote about it for us.

It is also important to "mark you thread as solved" once you do get the problem solved. Other people looking for help can see the "solved" label on it and then they know it is something that can help them. Without it they might pass it up and not look. Don't mark it solved until it really is though. This way the other people get good information for their help.

Thanks brother.


Sincerely,
Jake


i can boot out of the usb flash disk my problem is
ubuntu doesnt detect the new partition i made what will i do?

---

### Post by ClientAlive on 2011-07-16
> **moonrays00 said:**
> i can boot out of the usb flash disk my problem is
ubuntu doesnt detect the new partition i made what will i do?



We want to help you brother but you're going to have to do some learning about the basics of partitioning. If you know how to use google, use it. Find some tutorials and things that explain different types of hard drives (ie: sata, ide, scsi) and one about partitions and partitioning. Explore a little bit buy clicking any links inside those tutorials. I've tried to explain some of those basics the best I can but we aren't in front of your computer and we 'can't see' what you are looking at. At the very least you need to post pictures of the screens and of any error messages or other windows that pop up. There's more to this stuff than just saying ubuntu doesn't detact the new partition. Without seeing the technical details there is no way for any of us here to figure out why. At this point it is just guessing.

I'm willing to help you but I don't know everything. Maybe there are guys around here who can tell what the problem is without seeing what you're seeing but I can't do that. I don't have the experience some of these other guys have. If I was in front of that computer or if you posted pictures (of everything - everything) I could probably figure it out though.

---

### Post by ClientAlive on 2011-07-16
> **moonrays00 said:**
> sorry im not that good :(

im just followin the other threads

I think he was reprimanding us, not you. He was saying that we shouldn't be telling you to do something that's actaully a little complicated and that can possibly cause you to lose data. Personally, I think it can be done, even by a noobie, but it depends on the noobie. Depends on whether he's motivated to learn the things he needs to in order to understand what he's being told to do. Depends on whether he's willing to check what people tell him to do before just doing it - to try and understand what he's being asked to do so it makes sense to him. That's why I felt ok about it.


> **moonrays00 said:**
> i have unallocated space now 97.66 GB what will i do next to install ubuntu?

Are you reading the links people are giving you here?
-------------------------

Edit:

[http://www.google.com/search?client=opera&rls=en&q=what+is+the+difference+between+a+primary+and+extended+partition&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest](http://www.google.com/search?client=opera&rls=en&q=what+is+the+difference+between+a+primary+and+extended+partition&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest)


**Note: _If you play around with these things without having a backup you are playing with fire. You've been warned._**

---

### Post by moonrays00 on 2011-07-22
> **ClientAlive said:**
> I think he was reprimanding us, not you. He was saying that we shouldn't be telling you to do something that's actaully a little complicated and that can possibly cause you to lose data. Personally, I think it can be done, even by a noobie, but it depends on the noobie. Depends on whether he's motivated to learn the things he needs to in order to understand what he's being told to do. Depends on whether he's willing to check what people tell him to do before just doing it - to try and understand what he's being asked to do so it makes sense to him. That's why I felt ok about it.




Are you reading the links people are giving you here?
-------------------------

Edit:

[http://www.google.com/search?client=opera&rls=en&q=what+is+the+difference+between+a+primary+and+extended+partition&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest](http://www.google.com/search?client=opera&rls=en&q=what+is+the+difference+between+a+primary+and+extended+partition&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest)


**Note: _If you play around with these things without having a backup you are playing with fire. You've been warned._**

since i havent got a external hdd yet. ill just go try wubi then? will it be fine?

---

### Post by ClientAlive on 2011-07-22
> **moonrays00 said:**
> since i havent got a external hdd yet. ill just go try wubi then? will it be fine?

You can also back up your things to DVD/ DVDs or to online storage. They have free online storage you can use. Google has one (I think they give you 1 GB and there is Ubuntu One which gives you 2 GB but I'm not sure if Ubuntu One requires you to have Linux to access it). It is a good idea to keep a regular backup schedule anyway - just in case something happens, and it is a good idea to make a back up any time you are about to do any major change to the computer like this.

I wish I could be there where you are because I would surely help you. In the end you will have to be the one that does this. You're the one in control, the one in front of your computer making the choices.

I've never done the wubi route before but if I had to guess I would have to say its as big of a change as going any other route. Personally, I just switched completely over when I went. Don't give up. It's usually when things get most challenging that you are right on the verge of breakthrough. I know that has been the case for me many times in my life.

I do promise you though, that if you study up a little on the meaning and how these things work (partitioning and resizing and the concepts of the hard drive and how data is stored on it, etc, etc) - that if you spend some time to study it, you will come away with enough of an understanding to really make what you're trying to do work. Not only make what you're trying to do work but you'll have that knowledge forever. You'll be able to go back to it and use it whenever you need it in the future.

Stay encouraged brother. Go for wubi if you like. Go for install if you like. There is also running it as a virtual machine and Virtual Box is a free program for that (they make one for Windows and one for Linux). Or you can just totally switch. The choice is up to you my friend.

If you have any specific questions just let me know. I promise I will keep checking on you as long as you need. One thing I would like to see is some questions based on you reading about the principles behind all this. I would be more than happy to help you along in learning these things that will help you.

May blessing attend you and the ones you care about.


Sincerely,
Jake

---

### Post by moonrays00 on 2011-07-24
> **ClientAlive said:**
> You can also back up your things to DVD/ DVDs or to online storage. They have free online storage you can use. Google has one (I think they give you 1 GB and there is Ubuntu One which gives you 2 GB but I'm not sure if Ubuntu One requires you to have Linux to access it). It is a good idea to keep a regular backup schedule anyway - just in case something happens, and it is a good idea to make a back up any time you are about to do any major change to the computer like this.

I wish I could be there where you are because I would surely help you. In the end you will have to be the one that does this. You're the one in control, the one in front of your computer making the choices.

I've never done the wubi route before but if I had to guess I would have to say its as big of a change as going any other route. Personally, I just switched completely over when I went. Don't give up. It's usually when things get most challenging that you are right on the verge of breakthrough. I know that has been the case for me many times in my life.

I do promise you though, that if you study up a little on the meaning and how these things work (partitioning and resizing and the concepts of the hard drive and how data is stored on it, etc, etc) - that if you spend some time to study it, you will come away with enough of an understanding to really make what you're trying to do work. Not only make what you're trying to do work but you'll have that knowledge forever. You'll be able to go back to it and use it whenever you need it in the future.

Stay encouraged brother. Go for wubi if you like. Go for install if you like. There is also running it as a virtual machine and Virtual Box is a free program for that (they make one for Windows and one for Linux). Or you can just totally switch. The choice is up to you my friend.

If you have any specific questions just let me know. I promise I will keep checking on you as long as you need. One thing I would like to see is some questions based on you reading about the principles behind all this. I would be more than happy to help you along in learning these things that will help you.

May blessing attend you and the ones you care about.


Sincerely,
Jake

another question.

what does this mean?

No root file system is defined.
Please correct this from the partitioning menu?

---

### Post by ClientAlive on 2011-07-25
> **moonrays00 said:**
> another question.

what does this mean?

No root file system is defined.
Please correct this from the partitioning menu?


Sorry for the delay. It's super late where I am right now and I need to go to bed. I have some stuff to do tomorrow but I'll make sure and get back here for a proper answer tomorrow evening.

For now here's a couple links you can look at:

[http://www.neowin.net/forum/topic/594903-ubuntu-710-no-root-file-system-is-defined/](http://www.neowin.net/forum/topic/594903-ubuntu-710-no-root-file-system-is-defined/)

[http://www.linuxquestions.org/questions/linux-newbie-8/no-root-file-system-is-defined-during-installation-process-of-ubuntu-643386/](http://www.linuxquestions.org/questions/linux-newbie-8/no-root-file-system-is-defined-during-installation-process-of-ubuntu-643386/)

(post #6 in the above link sums up the process pretty well).


Basically, when you are in the manual partition, there is a drop down menu in the lower right hand corner (or somewhere in there). When you click on it you will see a bunch of things in the list. One of them is just the slash "/" which is root. You have to deliberately set it to that. You need to also make one for swap. I don't recall off the top of my head which selection is for swap in that drop down menu but I'll look it up and let you know tomorrow ok? Gotta get some sleep right now though. I'm beat.

Let me know if you get further along or if something else comes up. I'll see you in about 18 hrs.


Jake
-----------------

Can you tell me what version release of Ubuntu you are installing again? Is it 11.04? 10.10? 10.04? I have Virtual Box on my machine. I can install the same release on my machine in Virtual Box that way I can tell you for sure.

Just let me know if you want me to.

Peace out.

---

### Post by moonrays00 on 2011-07-25
> **ClientAlive said:**
> Sorry for the delay. It's super late where I am right now and I need to go to bed. I have some stuff to do tomorrow but I'll make sure and get back here for a proper answer tomorrow evening.

For now here's a couple links you can look at:

[http://www.neowin.net/forum/topic/594903-ubuntu-710-no-root-file-system-is-defined/](http://www.neowin.net/forum/topic/594903-ubuntu-710-no-root-file-system-is-defined/)

[http://www.linuxquestions.org/questions/linux-newbie-8/no-root-file-system-is-defined-during-installation-process-of-ubuntu-643386/](http://www.linuxquestions.org/questions/linux-newbie-8/no-root-file-system-is-defined-during-installation-process-of-ubuntu-643386/)

(post #6 in the above link sums up the process pretty well).


Basically, when you are in the manual partition, there is a drop down menu in the lower right hand corner (or somewhere in there). When you click on it you will see a bunch of things in the list. One of them is just the slash "/" which is root. You have to deliberately set it to that. You need to also make one for swap. I don't recall off the top of my head which selection is for swap in that drop down menu but I'll look it up and let you know tomorrow ok? Gotta get some sleep right now though. I'm beat.

Let me know if you get further along or if something else comes up. I'll see you in about 18 hrs.


Jake
-----------------

Can you tell me what version release of Ubuntu you are installing again? Is it 11.04? 10.10? 10.04? I have Virtual Box on my machine. I can install the same release on my machine in Virtual Box that way I can tell you for sure.

Just let me know if you want me to.

Peace out.

im trying to install 11.04

---

### Post by ClientAlive on 2011-07-25
Hi,

Sorry took me so long to get back to you. Today, I rode my bike places I needed to go. It's was a long trip but I didn't realize how long until I put it into mapquest to see the distance. I rode 22 miles today (a marathon is 26 miles). OMG I was tired when I got home! Still am, really.

Here is a link to a guide about manual partitioning.

[http://www.linuxbsdos.com/2011/05/04/manual-disk-partitioning-guide-for-ubuntu-11-04/](http://www.linuxbsdos.com/2011/05/04/manual-disk-partitioning-guide-for-ubuntu-11-04/)

It shows everything in detail and even what I was talking about with needing to set the mount point.

The image below is one of the images on that web page. It is the one that shows the thing to set the mount point. It is a good idea to go to that page and study the whole thing though.

[IMG]http://www.linuxbsdos.com/wp-content/uploads/2011/05/Uinstall4-600x296.png[/IMG]

Hope it helps. Let me know how it goes for you ok?
---------------------------

If you follow the guide at that web page exactly everything 'should' work out fine. Just make sure you have the right partition selected to begin with when you start the process. Ultimately you will be creating more partitions in the one you made when you resized before. You'll have to do a little math in order to have the right numbers for size for each partition.

> 
Dictionary
Search Results
kil·o·byte
noun&#8195;/&#712;kil&#601;&#716;b&#299;t/&#8195;
kilobytes, plural

1) A unit of memory or data equal to 1,024 (210) bytes


> 
Dictionary
Search Results
byte
noun&#8195;/b&#299;t/&#8195;
bytes, plural

1) A group of binary digits or bits (usually eight) operated on as a unit

2) Such a group as a unit of memory size


> 
1 megabyte = 1 048 576 bytes
1 megabyte = 1024 kilobytes
1 gigabyte = 1024 megabytes


---

### Post by moonrays00 on 2011-07-26
> **ClientAlive said:**
> Hi,

Sorry took me so long to get back to you. Today, I rode my bike places I needed to go. It's was a long trip but I didn't realize how long until I put it into mapquest to see the distance. I rode 22 miles today (a marathon is 26 miles). OMG I was tired when I got home! Still am, really.

Here is a link to a guide about manual partitioning.

[http://www.linuxbsdos.com/2011/05/04/manual-disk-partitioning-guide-for-ubuntu-11-04/](http://www.linuxbsdos.com/2011/05/04/manual-disk-partitioning-guide-for-ubuntu-11-04/)

It shows everything in detail and even what I was talking about with needing to set the mount point.

The image below is one of the images on that web page. It is the one that shows the thing to set the mount point. It is a good idea to go to that page and study the whole thing though.

[IMG]http://www.linuxbsdos.com/wp-content/uploads/2011/05/Uinstall4-600x296.png[/IMG]

Hope it helps. Let me know how it goes for you ok?
---------------------------

If you follow the guide at that web page exactly everything 'should' work out fine. Just make sure you have the right partition selected to begin with when you start the process. Ultimately you will be creating more partitions in the one you made when you resized before. You'll have to do a little math in order to have the right numbers for size for each partition.


how can i acess this through wubi?

---

### Post by ClientAlive on 2011-07-26
> **moonrays00 said:**
> how can i acess this through wubi?

I didn't realize you were going for a wubi install. Wubi is a totally different way of going about it. It isn't bad, it's just an option - a different way if you choose to go that route. Unfortunately I don't know anything about how wubi works. I mean, I understand the basic concept but that's all. I don't know how to use it.

You'd have to start a new thread asking about it and maybe do some googling on the topic while people are talking to you on that thread. If you start a new thread you should get more responses since this one seems pretty dead now (I'm the only one here for days now). Maybe one of them knows more about wubi.

With a forum like this you need to include pictures and/ or whatever text the computer spits out at you when you're doing things on it. That means extra work on your part but a lot of people on forums like this expect that. People want to help but it's frustrating when we can't see what you're talking about. After a while people just start to leave.

Just a little advice. Take it however you want.
--------------------------------

Edit:

If I were you I would put the new post in the forum called "Installation & Upgrades." It's just for these type of questions.

[http://ubuntuforums.org/forumdisplay.php?f=333](http://ubuntuforums.org/forumdisplay.php?f=333)

I would also make sure I don't use the same subject line. Be descriptive in your subject line so people know what your question is. If it's using wubi put 'trying to install using wubi' or 'problems using wubi' - something like that. Add "tags" to the thread when you create it. You find the place to put them below where you write the message.

Sorry I don't know more about wubi or can't help more with it. Good luck.

---

