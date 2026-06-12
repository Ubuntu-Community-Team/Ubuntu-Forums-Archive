---
title: "Ubuntu freezes, image problem?"
date: 2010-01-04
forum: New to Ubuntu
---

### Post by | Gnome | on 2010-01-04
Ok, I torrented the Ubuntu 9.1 image, burnt to a CD (690 MB) and installed in my computer. Now, after installing when I run my new Ubuntu, the computer freezes after couple of minutes. I tried restarting several times, but it soon freezes in the same way; no cursor movement, nothing. 
Then, I booted from the live CD, and lo! same problem. Computer freezes even during live boot. The problem was right in that image, I guess! 
So, would you please suggest me a solution to this problem? Please don't tell me to re-download the image again. I have just downloaded that in one month time, because of slow net connection. 

Thanks in advance!

---

### Post by USB_NL on 2010-01-04
the slow download maby made the image file corrupt

maby you can order one cd if money is not the problem
or lend from schools, liberaries, etc
or get one from a frend with faster internet and a usb or a burner for the cd
if you have a new computer you can simply boot that image on a usb or sdcard and use that to install on computer harddrives instead of cd you can even save things in a live-session-user mode

is it an old pc or notebook?

---

### Post by USB_NL on 2010-01-04
maby downloading with a torrent would be more reliable

---

### Post by | Gnome | on 2010-01-05
By slower speed I meant around 10kbps, not so much slow speed. And I had torrented Ubuntu 9.04 on the same connection which is running absolutely fine.

^ USB_NL
I had torrented that image. And would you make it clear why are you suggesting to install via USB? BTW, my computer does support USB booting, not that old! :P 
And isn't there anyway to find out if my image is corrupted and if it is, any way to repair it?
Isn't there any solution except redownloading the image?

Thanks!

---

### Post by USB_NL on 2010-01-05
> make it clear why are you suggesting to install via USB? BTW, my computer does support USB bootingsome reasons for useing a liveCDimage on a USBstick or sdcard instead of burning a cd 

[LIST=1]
[*]a usb does not cost much and can be reused later
[*]some pc dont have a burner or cdrom drive (netbooks for instance)
[*]you can make them with MSwindows or linux
[*]it runs presistently so you can save settings, files, bookmarks, etc
[*]it does not use a lot of power
[*]you can run it on countless pc's and it looks like your on your own machine
[*]it's not mechanical
[*]you can boot multiple iso
[*]you dont have to make a dualboot or delete your other OS
[*]very easy to remake with other distro's so you can try more if you can download them
[*]cdrom is so 90ties
[/LIST]
:)


about your problem iso maby you can hash test it in your torrent program i belive that is to see if it is 100% complete

i dont know how you could repair your iso
i would need to do a google search on that

---

### Post by mastablasta on 2010-01-05
> **| Gnome | said:**
> By slower speed I meant around 10kbps, not so much slow speed. And I had torrented Ubuntu 9.04 on the same connection which is running absolutely fine.
 
^ USB_NL
I had torrented that image. And would you make it clear why are you suggesting to install via USB? BTW, my computer does support USB booting, not that old! :P 
And isn't there anyway to find out if my image is corrupted and if it is, any way to repair it?
Isn't there any solution except redownloading the image?
 
Thanks!
 
 
Also there is a bug that causes this. Search for thread about Compaq 615 (and apparently it affects some other computers as well). luckily there is a workarround for it. it had something to do with new Kernel i think.

---

### Post by USB_NL on 2010-01-05
> **mastablasta said:**
> Also there is a bug that causes this. Search for thread about Compaq 615 (and apparently it affects some other computers as well). luckily there is a workarround for it. it had something to do with new Kernel i think.

interresting i have an old compaq presario with ubuntu904 witch freezes especially with movies , livestreams

---

### Post by | Gnome | on 2010-01-05
Ok, here is a new development. I again booted via same 9.1 live CD and noticed an alternative startup option (Pressing F4 key) 'Safe graphics mode'. Then when I selected that and ran, voila!, it didn't freeze and worked perfectly.
Now, what should I do? Will booting from live CD first with safe graphics mode and then installing in my system work?
Does this mean that 9.1 is graphically incompatible with my system?
BTW, 9.04 is running damn well.

My config is

MSI 945GCM7
1 GB DDR2 RAM
Intel Celeron 2.53 GHz

Now please someone suggest me some solution.

---

### Post by mastablasta on 2010-01-06
As i know that was also one workaround for Compaq 615 (where also 9.04 ran nicely & practically everyhting worked out of the box, but 9.10 could not be installed). I htink just the instalation is then done in compatibility mode and then it would work normally.
 
EDIT: Here is the link to the thread: [http://ubuntuforums.org/showthread.php?t=1327853&highlight=mastablasta](http://ubuntuforums.org/showthread.php?t=1327853&highlight=mastablasta)
 
Note, i am not experienced Linux user, but i did read about this error that seems very similar to yurs in the mentioned thread.

---

### Post by | Gnome | on 2010-01-10
Here is what I did recently after all this!

1. I tried the same CD (live boot and not in safe graphics mode) in two other systems. In one, it worked without any problem. But in another it did same as in mine. After some seconds, it freezed. FYI: the system in which Ubuntu freezed and mine are little newer than the system in which Ubuntu 9.1 ran well. By system, I meant the mobo.

2. With no solutions, I downloaded 9.1 again from another torrent provider. But to my utter dismay, the problem was same. It freezes after reaching the desktop.

Anyways, since I have downloaded twice already, I installed that in safe graphics mode. Now followings are my new problems.

1. When I access Display (System>Preferences>Display), it doesn't detect my monitor. 9.04 had detected it. My monitor is Samsung 14". Neither can I change the refresh rate nor rotation. Refresh rate is 0 Hz and I can't change it.

2. It doesn't allow visual effects. I mean there are three options in Visual effects. It works only in 'NONE'. When I try other options 'Normal' and 'Extra', it searches for drivers and says "Desktop effects could not be enabled". What does it mean. The newer version of each OS SHOULD support newer hardwares, isn't it? Or is it the other way round? Now, there are no visual effects and my Ubuntu feels like Windows 98. Yet I am running it, in hope of getting some solutions. 9.04 worked like a charm and 9.1 is showing so much problems.

Any solutions guys??
Thanks in advance.

---

### Post by massasauga on 2010-01-10
Go to the Burning How to page, and then the Ubuntu Hashes page and look at the md5 sum for the file you downloaded (e.g., the md5sum for 9.10 i386 desktop is 8790491bfa9d00f283ed9dd2d77b3906). Open a terminal window on your desktop, path to the directory where you have downloaded the iso file and then enter the command: md5sum <filename> (where <filename> is the exact name of the iso file). After a few minutes, the md5 sum will be displayed on your terminal window. It should match the md5 sum shown on the Ubuntu Hashes page. If it does match, your iso file is good. After you build your CD, try running the option to check the CD instead of the option to run or install it. If the CD checks out bad, you can reburn one from the same good iso file, but try burning it at a slower speed.
Good luck.  

> **| Gnome | said:**
> Ok, I torrented the Ubuntu 9.1 image, burnt to a CD (690 MB) and installed in my computer. Now, after installing when I run my new Ubuntu, the computer freezes after couple of minutes. I tried restarting several times, but it soon freezes in the same way; no cursor movement, nothing. 
Then, I booted from the live CD, and lo! same problem. Computer freezes even during live boot. The problem was right in that image, I guess! 
So, would you please suggest me a solution to this problem? Please don't tell me to re-download the image again. I have just downloaded that in one month time, because of slow net connection. 

Thanks in advance!

---

### Post by | Gnome | on 2010-01-10
What the heck happened?
I was using the same 9.1 today. Later when I again turned on the computer, the same ubuntu now behaves weird. I cant access any applications, nothing. When i click something it shows no response. It behaves as being freezed but the pointer moves. I had windows in another partition. Now it doesnt even boot. If I boot to windows, computer restarts without booting.
Conclusion is now I have nothing, neither ubuntu nor windows. I had important files in the home folder of ubuntu. I tried to access it via live cd boot. But it says i have no permission.
Whatever happened to my windows and ubuntu, let it be. But i must get back those files. Please help. How can i get permission of that folder? Now I am seriously messed up.

---

