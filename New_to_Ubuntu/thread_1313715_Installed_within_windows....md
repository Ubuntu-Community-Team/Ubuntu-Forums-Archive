---
title: "Installed within windows..."
date: 2009-11-04
forum: New to Ubuntu
---

### Post by Robert98374 on 2009-11-04
Basicly i am trying to find a good program to either partition my hard drive, either to have a majority of the hard drive as a place that windows xp and what ever Ubuntu flavor. What would be a good program that i would have to run from windows to do that?

---

### Post by garvinrick4 on 2009-11-04
Use WUBI is my choice for you. It will let you get to know Ubuntu with little trouble as possible. 
You do not have to fool around with grub. It uses windows grubdos4.
It will be a folder inside of windows in C: right next to Users.

You just pick out size you want up to 30 gig. Put in your password.
and install. It will do it by itself.
When you reboot it will stop at Windows version and give you 10 seconds to
arrow down to Ubuntu press enter and will boot to login screen.
Put in your password and off you go. 

Download an .iso image to your desktop. Burn image to a CD disc. 
Put CD disk in and it will say do you want to use WUBI say yes. 

Wubi installer will be on ubuntu site also [http://releases.ubuntu.com/karmic/](http://releases.ubuntu.com/karmic/)

---

### Post by N4zgu1 on 2009-11-04
I would boot from the livecd and use gparted, but if you want to do it from windows I recomend you partition manager

---

### Post by Robert98374 on 2009-11-04
whats throwing me off is that i used the install within windows but i have no idea why i am not able to see any type of partition. when i was trying to install the normal way it would only allow me to reformat the entire hard drive. i would assume that would be the Wubi installation?

---

### Post by Trav1s on 2009-11-04
> **garvinrick4 said:**
> Use WUBI is my choice for you. It will let you get to know Ubuntu with little trouble as possible. 
You do not have to fool around with grub. It uses windows grubdos4.
It will be a folder inside of windows in C: right next to Users.

You just pick out size you want up to 30 gig. Put in your password.
and install. It will do it by itself.
When you reboot it will stop at Windows version and give you 10 seconds to
arrow down to Ubuntu press enter and will boot to login screen.
Put in your password and off you go. 

Download an .iso image to your desktop. Burn image to a CD disc. 
Put CD disk in and it will say do you want to use WUBI say yes. 

Wubi installer will be on ubuntu site also [http://releases.ubuntu.com/karmic/](http://releases.ubuntu.com/karmic/)

I second that.  As a seasoned computer builder this suggestion is the easiest way to learn Ubuntu.  Even with my experience and knowledge of computers it is easy to wipe a drive clean and not realize what happened.

---

### Post by Robert98374 on 2009-11-04
Double post

---

### Post by Trav1s on 2009-11-04
Wubi will install Ubuntu as a giant file in the Windows drive and you will not see a dedicated partition.

---

### Post by Robert98374 on 2009-11-04
then thats how it did it. Anyway i can turn that into a full ubuntu wtih a partition?

basicly i want to not have to completely reformat my computer because i have tons of music/games etc. 

at the same time i want to be able to access those files from either side.

---

### Post by la3875 on 2009-11-04
From what you describe you may be better served dual booting or running as a virtual machine if your computer has enough horsepower? See these sites if you haven't already. I find myself referring to them on occasion and they have not let me down yet. Cheers!

[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)
[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

---

### Post by lrcaballero on 2009-11-04
Welcome to Linux world,

I would first play with as many flavors you can get your hands on, one's you know what you want, run the live cd and run the installation from the live cd, in my case every flavor I have tried it walked me through the partion by default, and there I allocate the memory i want to give to Windows and Linux. Linux will automatically install the GRUB that will allow you to either boot-up to Windows or to linux. I personally run Ubuntu 9.04 (100%) don't care for Windows and don't need it! Also, I personally think that it is always better just to run ONE OS on one machine. But if you are not ready!! you can also try virtual machines; such as VMWare, Virtual PC, etc....

Good Luck with Linux

Luis

---

### Post by Robert98374 on 2009-11-04
The biggest thing that prevents me from going full to Ubuntu is my games, i am a huge gamer. On my hard drive its about 160gigs worth of games and music xD. With Virtual box am i able to access all the files on the windows side?

---

### Post by Robert98374 on 2009-11-04
> **lrcaballero said:**
> Welcome to Linux world,

I would first play with as many flavors you can get your hands on, one's you know what you want, run the live cd and run the installation from the live cd, in my case every flavor I have tried it walked me through the partion by default, and there I allocate the memory i want to give to Windows and Linux. Linux will automatically install the GRUB that will allow you to either boot-up to Windows or to linux. I personally run Ubuntu 9.04 (100%) don't care for Windows and don't need it! Also, I personally think that it is always better just to run ONE OS on one machine. But if you are not ready!! you can also try virtual machines; such as VMWare, Virtual PC, etc....

Good Luck with Linux

Luis

I dont have Ubuntu and Kubuntu installed as separate OSs i have the Kubuntu desktop installed with Ubuntu.

---

### Post by garvinrick4 on 2009-11-04
You can access all Windows files within the WUBI install.
Computer/filesystem/host/users/ (your files)
drag and drop them to Ubuntu file system.
And now you have everything in windows now in Ubuntu.
To get your Linux to Windows-put onto external drive and when in windows copy.
Cannot copy Linux directly to Windows as you can Windows to Linux.

Remember [host] in linux is always your C: drive in windows  for WUBI

Because your Ubuntu is inside of Windows in a folder named Ubuntu.

If you have 32 bit Windows you can still use 64 bit Ubuntu if machine is 64 bit capable.
Works just fine.

While you are learning Linux and all of its Terminal and GUI and nautilus file system it
is nice to know if you trash you can just uninstall in Windows and stick CD in and 12 minutes you can be in a new fresh Ubuntu install. Without harm to Drive. 
 When you get more accomplished do a dual boot with partitions with seperate Grubs.
 Have fun with Linux and have a good day.

---

### Post by Robert98374 on 2009-11-05
Hmm...i dont see that folder in windows...

---

### Post by garvinrick4 on 2009-11-05
The folder will be there when you install WUBI. It is not there before you install.

Google   ubuntu pocket guide and download. It will give you info on using Ubuntu.

There is also   Ubuntu reference guide    Google that also    It is one page Terminal
commands that will get you started.

When you have problem first Google problem and study.
Read the forums when possible you never know when you will learn something new.
Learn one thing a day that is 365 a year. I do it everyday and always glad to learn something new. And I am know Genius believe me but willing to learn.

To reboot from Terminal:   code:   sudo shutdown -r now

To shutdown from Terminal  code:  sudo shutdown -h now

That is two things today.   Have fun with Ubuntu 

Do not type code in, start with sudo.

sudo means you are super user and gives you permission to use terminal for certain things. You can read about that.

---

### Post by Robert98374 on 2009-11-07
The weird thing is tho that i have ubuntu installed right now, it gives me the option to boot into ubuntu without any issues. I am able to keep my settings and everything...thats whats so confusing, its acts like a wubi install but the folder that your talking about isnt there.

---

### Post by LewRockwell on 2009-11-07
> **LewRockwell said:**
> Multi-booting...Partitioning Screenshots Provided

Acer Aspire One Multi-Boot Machine(daily use=ten hours plus)

[http://ubuntuforums.org/showthread.php?t=1222961](http://ubuntuforums.org/showthread.php?t=1222961)


Toshiba Satellite Multi-Boot Machine(daily use=four to six hours plus)

[http://ubuntuforums.org/showthread.php?t=1252042](http://ubuntuforums.org/showthread.php?t=1252042)


Other:

[http://www.justlinux.com/forum/showthread.php?t=147959](http://www.justlinux.com/forum/showthread.php?t=147959)

.

might help you visualize some different partitioning schemes

enjoy!

.

---

### Post by garvinrick4 on 2009-11-07
Check in Windows add-Remove programs. Ubuntu should be in
there. Ubuntu folder has got to be in Windows somewhere.
You used WUBI or you would have had to make a partition. 
 Have a nice time with Linux.

---

