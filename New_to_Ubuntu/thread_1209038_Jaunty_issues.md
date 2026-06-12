---
title: "Jaunty issues"
date: 2009-07-09
forum: New to Ubuntu
---

### Post by wo1fe on 2009-07-09
OK the computer i am running is geared towards 64 bit. see specs below

Nvidia 9600gt
AMD dual core 6000+ (3.1 Ghtz)
8 GB ram
ASUS M2A-VM


the issues that i am having is i do some decently intensive gaming with this machine. (games such as crysis running full bore, source games ect ect....) i recently switched from windows because i was having the issue that the explorer.exe would crash randomly and force me to loose everything on desktop. this continue after a reformat and a clean install of windows. 

now the issues that i am having with "Jaunty" is that it seems rather quite slow compared to what i was running at. just at an idle trying to bring up the mozilla application it probably takes around 5-6 second to actually load it. this shouldnt be happening.

not only that i installed one of the lowest requirment games i have (Day of Defeat) and installed the recommended graphics driver (see above for card). yet when actually in the game it became nearly impossible to play because something was bogging it down. i know its not my internet because i checked it while in game and the latency was staying around 25-30. i checked the fps and where i should have been getting around 80-100 i was only hitting 35 at the most and when something went on it dropped to something horrible.

any ideas on this will be greatly appreciated. i apologize for using all varients didnt know exactly what it should be. also as of right now i have gone to the 8.04..2 ubuntu 64 bit LTS should i stay with this for now?

---

### Post by cariboo on 2009-07-09
I would suggest you have an application running that is using a lot of cpu cycles. Check to see if tracker is running, becuase if the database is corrupted, it will use a lot of cycles. Have a look at this bug #[lpbug]148520[/lpbug], if that doesn't help and you don't need tracker remove it completely. Open an Applications-->Accessories-->Termianl and type:

```
sudo apt-get purge tracker
```

---

### Post by wo1fe on 2009-07-09
> **cariboo907 said:**
> I would suggest you have an application running that is using a lot of cpu cycles. Check to see if tracker is running, becuase if the database is corrupted, it will use a lot of cycles. Have a look at this bug #[lpbug]148520[/lpbug], if that doesn't help and you don't need tracker remove it completely. Open an Applications-->Accessories-->Termianl and type:

```
sudo apt-get purge tracker
```


it purged something that did not need to be there. ended up being 3 files that were installed and no longer needed

actually at this point with the older version it seems to be running much faster. there is something new no. i just tried installing the nvidia driver that is for my computer and this is what i get after typing what you see below into console like it tells you to.

wolfe@wolfe-desktop:~$ sh NVIDIA-Linux-x86_64-185.18.14-pkg2.run
sh: Can't open NVIDIA-Linux-x86_64-185.18.14-pkg2.run

i have no idea why this isnt working considering that the primary video adapter that the computer is running off of right now is my nvidia 9600 gt 512. i also tried signing in as root figuring that i needed to be signed in as admin but still same message.

---

### Post by zerhacke on 2009-07-09
Try not to use the nVidia drivers found on the nVidia website.  You should be able to find drivers for your machine automagically by System -> Administration -> Hardware Drivers.  Using drivers from the repositories does not break Xorg on an update of Xorg.

---

### Post by Crunchy the Headcrab on 2009-07-09
> **zerhacke said:**
> Try not to use the nVidia drivers found on the nVidia website.  You should be able to find drivers for your machine automagically by System -> Administration -> Hardware Drivers.  Using drivers from the repositories does not break Xorg on an update of Xorg.
Yeah but the drivers from NVIDIA.com are far and away better than what is in the repos.  Plus he is using them for gaming.

Make sure you don't have any other drivers installed before you initialize this process! The easiest way to run the installation is to right click the driver and in properties choose make executable.

Then log out of ubuntu and hit CTRL-ALT-F1.  This will bring up a command prompt.  Log in.  

Type:>  sudo /etc/init.d/gdm stopThen navigate to the folder that the driver is in and type: > sudo ./sh NVIDIA-Linux-x86_64-185.18.14-pkg2.runFinish the process, then type:
> sudo /etc/init.d/gdm startWalla.  You may want to restart just for the heck of it.

---

### Post by wo1fe on 2009-07-09
I think ill try it your way crunchy. only because while i was using jaunty there were no drivers found when gone to that specific directory. ty very much trying it now will let you know

---

### Post by wo1fe on 2009-07-09
> **wo1fe said:**
> I think ill try it your way crunchy. only because while i was using jaunty there were no drivers found when gone to that specific directory. ty very much trying it now will let you know

well just got done trying it. and its telling me that ./sh does not exist. 

below is exactly what i tpyed.

logged out

signed in

sudo /etc/init.d/gdm stop
stopping gnome blah blah (forget exact words)
sudo ./sh NVIDIA-Linux-x86_64-185.18.14.pkg2.run
(something) ./sh does not exist.

something else interesting just happened.

wnt to get the downloadable pdf noob guide and tried installing the Gnash plugin  for mozilla that allows the flash videos to play and what not and i got an error message about something called nvidia-glx-new bot able to uninstall. i can get it to happen everytime. i will post the exact error when i have time right now need to go get old lady.

---

### Post by lavinog on 2009-07-09
it should read
```

sudo sh ./NVIDIA-Linux-x86_64-185.18.14.pkg2.run

```
move the './' to the nvidia file. 
It is assuming that it is in the current folder. if you get a file not found error, type ls to see if you are in the right place.
if you cant find it, type:
```
 find /home/ -name 'NVIDIA-Linux-x86_64-185.18.14.pkg2.run'
```


generally I use bash instead of sh but sh should still work

---

### Post by wo1fe on 2009-07-10
ok i will check it out right now. ty all in advance for all the help you are posting to this "noob" it is very much appreciated.

---

### Post by wo1fe on 2009-07-10
> **lavinog said:**
> it should read
```

sudo sh ./NVIDIA-Linux-x86_64-185.18.14.pkg2.run

```move the './' to the nvidia file. 
It is assuming that it is in the current folder. if you get a file not found error, type ls to see if you are in the right place.
if you cant find it, type:
```
 find /home/ -name 'NVIDIA-Linux-x86_64-185.18.14.pkg2.run'
```generally I use bash instead of sh but sh should still work

ok i have just tried this way of doing it with the same resluts

"sh: can't open 'NVIDIA-Linux-x86_64-185.18.14.-pkg2.run"

it gives no reason as to why it is unable to open the file. i have made sure that it is the correct one for the system that i am running. the file is located at usr/home./desktop which is where i am putting the cmds in from after disabling GUI by typing 
sudo /etc/init.d/gdm stop"
at this point i am at a loss as to what to do. ive looked and almost all places recommend installing it the way stated above in post #5. i do not believe that i am typing anything the wrong way as i wrote it down in a notebook copying direct from what was typed on the screen.

ok i just tried removing nvidia-glx-new as it is causing problems with installing a swf player for viewing online videos. this is the error i was speaking of last night.
"E: nvidia-glx-new: subprocess post-removal script returned error exit
status 2"

could this be the cause of why it will not install  the actual driver? i know it is why the copmuter will not install a swf player.

---

### Post by zerhacke on 2009-07-11
Assming you have no other .run files on the desktop, you could substitute the code for 

sudo sh ./*.run

It'd run any file found in the desktop folder with the .run extension.  I have a feeling your problem is that you don't have the same filename as what lavinog stated.

---

### Post by wo1fe on 2009-07-11
> **zerhacke said:**
> Assming you have no other .run files on the desktop, you could substitute the code for 

sudo sh ./*.run

It'd run any file found in the desktop folder with the .run extension.  I have a feeling your problem is that you don't have the same filename as what lavinog stated.

this is the response i get when i try running it like that
sh: Can't open ./*.run

---

### Post by Crunchy the Headcrab on 2009-07-11
Upgrading my driver right now.  I'll go through the process and then upload what I did here.

---

### Post by Crunchy the Headcrab on 2009-07-11
Okay.

1- Download driver
2- Right Click driver > permissions > allow to be executed
3- Logout
4- Alt-Ctrl-F1
5- Sudo /etc/init.d/gdm stop
6- cd (navigate to directory that driver is installed in)
7- sudo ./insertdriverfilenamehere                  <!---- if you don't remember it exactly type ls after you get to the directory your driver is in and it will list all the files in that directory so you can easily see the driver name you need to enter.
8- Follow Nvidia's prompts, at the end you want it to automatically configure your Xorg when it asks
9- sudo /etc/init.d/gdm start

PS: I messed up on my earlier post.  If you did step 2, all you need to type at step 7 is sudo ./ and directly following the ./ type the filename of the Nvidia installer.

PPS: If you are already using the NVIDIA Drivers from the Restricted Hardware list, you need to remove them first.  Not sure what all that entails, you might search the forums for deleting nvidia drivers.

---

### Post by wo1fe on 2009-07-11
> **Crunchy the Headcrab said:**
> Okay.

1- Download driver
2- Right Click driver > permissions > allow to be executed
3- Logout
4- Alt-Ctrl-F1
5- Sudo /etc/init.d/gdm stop
6- cd (navigate to directory that driver is installed in)
7- sudo ./insertdriverfilenamehere                  <!---- if you don't remember it exactly type ls after you get to the directory your driver is in and it will list all the files in that directory so you can easily see the driver name you need to enter.
8- Follow Nvidia's prompts, at the end you want it to automatically configure your Xorg when it asks
9- sudo /etc/init.d/gdm start

PS: I messed up on my earlier post.  If you did step 2, all you need to type at step 7 is sudo ./ and directly following the ./ type the filename of the Nvidia installer.

PPS: If you are already using the NVIDIA Drivers from the Restricted Hardware list, you need to remove them first.  Not sure what all that entails, you might search the forums for deleting nvidia drivers.


ok i will give this a shot. there have been so many things that i have tried and it has not worked. i will post back here and let you know if it works.

---

### Post by wo1fe on 2009-07-11
ok tried it and still the same thing. i tried changing the directory to home/usr/desktop to see if it would be able to open it that way but still nothing.

---

### Post by Crunchy the Headcrab on 2009-07-11
Stumped.

---

### Post by zerhacke on 2009-07-12
> **wo1fe said:**
> ok tried it and still the same thing. i tried changing the directory to home/usr/desktop to see if it would be able to open it that way but still nothing.

Try /home/username/Desktop  It is case specific.  Change username to your user name.

---

