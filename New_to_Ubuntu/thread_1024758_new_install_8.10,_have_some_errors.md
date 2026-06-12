---
title: "new install 8.10, have some errors"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by quadcam on 2008-12-29
I installed Ubuntu on my xp media center machine last night and I'm running into some errors. I had about 50 gigs of space left on my drive and gave ubuntu a 35gig partition. no issues with the install but I did make the mistake of importing my media files from xp (20 gigs?). I only did that because I didnt think I could access my windows partition from linux, I tried from the live cd before install and couldnt mount the drive because I got a "volume in use" error. 

So I finally got everything installed and took it for a test run.
My first issue is that ubuntu only fills about 1/3 of my screen and it's shifted to the left, looks like widescreen format only off center.  I am running an Nvidia GeForce6600 video card so I installed the Nvidia drivers and rebooted. when Xserver came up all I had a was a blank screen with a thin yellow line across the top. I went back rebooted to the recovery console and fixed xserver. Obviously Ubuntu doesnt like Nvidia drivers very much. 

Next error, I tried to open firefox and I get an error about the security component in firefox and about 3 seconds later firefox shuts down. 

the other issue is, I still cant access my windows partition. I can see the disk but when i try to mount it says "volume in use" I want to delete all of the files I imported to ubuntu and use them from my xp partition since they take up most of my linux partition. 

I'm not 100% new to linux, I have very very limited experience though.  I had RH 8.0 installed on another machine awhile back but I had problems with drivers and hardware compatibility so I got annoyed and removed it. I'm going to go back to school for networking/network security and i'm going to have to learn open source/linux OS anyway, figured I would get a jump start.

edit: for some reason I can now access my xp partition and I went into my ubuntu docs and deleted all of the media files I had imported so now i have 29 gigs of free space but when I tried to download firefox from mozilla i get an error telling me my temp folder is full...so i check and it's filled with a bunch of files but i'm not sure what they are so i dont want to delete them. meanwhile i cant download anything because there no room in my temp folder

---

### Post by oldos2er on 2008-12-29
"I didnt think I could access my windows partition from linux, I tried from the live cd before install and couldnt mount the drive because I got a "volume in use" error."

 This could be caused by the Win* partition not being shutdown properly; just so you know in case it happens again.

 How did you install the Nvidia drivers?

 Rebooting should clear out /tmp.

---

### Post by quadcam on 2008-12-29
I installed the Nvidia drivers when I was prompted with "restricted drivers available" from the hardware icon at the top left of the screen. I think it installed Nvidia driver 177.XX. not sure though, i'm still pretty lost in this system. 

I'll try rebooting to see how that affects the /tmp folder

thanks

---

### Post by BDNiner on 2008-12-29
Since you have a Nvidia card i would recommed install nvidia-settings program and setting the resolution there instead of the regular ubuntu resolution tool. In my experience the built in tool does not work and i now just go to the nvidia settings tool to setup the display.

---

### Post by wmoore on 2008-12-29
> **quadcam said:**
> 
Next error, I tried to open firefox and I get an error about the security component in firefox and about 3 seconds later firefox shuts down. Are you logged in as root? It is a security risk running your browser with elevated privileges.

---

### Post by LowSky on 2008-12-29
How did you install Ubuntu? from LiveCD? Wubi?
Did you  defrag your Windows drive before creating a new partition for it?
Nvidia grahics actually work great on Linux. ATI onthe other hand...

run firefox from a terminal window
type the command: firefox


your /tmp folder shouldn't fill up like that..

Its sounds like you have a bad install, usually caused by a bad dwnload or buring the CD at too high a speed.
post what errors its says before it shuts down

---

### Post by quadcam on 2008-12-29
> **BDNiner said:**
> Since you have a Nvidia card i would recommed install nvidia-settings program and setting the resolution there instead of the regular ubuntu resolution tool. In my experience the built in tool does not work and i now just go to the nvidia settings tool to setup the display.

ok where would I find that? 

> **wmoore said:**
> Are you logged in as root? It is a security risk running your browser with elevated privileges.

well, yeh actually I am. I forgot to make another account after creating my main account. 

> **LowSky said:**
> How did you install Ubuntu? from LiveCD? Wubi?
Did you  defrag your Windows drive before creating a new partition for it?
Nvidia grahics actually work great on Linux. ATI onthe other hand...

run firefox from a terminal window
type the command: firefox


your /tmp folder shouldn't fill up like that..

Its sounds like you have a bad install, usually caused by a bad dwnload or buring the CD at too high a speed.
post what errors its says before it shuts down

I installed ubuntu from a live cd, downloaded the 8.10 iso and burned it with infrarecorder at 16x.
No I didnt defrag XP before the install and yeh xp was not too happy about it and ran the disk checker when i booted back into windows. next time i log in i'll see if I can cut and paste the errors. I'm just getting really frustrated with it already, especially when I dont know the commands to use the terminal

---

### Post by wmoore on 2008-12-29
> **quadcam said:**
> ok where would I find that? Fire up a terminal and type:```
sudo apt-get install nvidia-settings
```

---

### Post by quadcam on 2008-12-29
thanks...sorry for the stupid Q's, been using WinBlows since 3.1 
so this is going to take awhile to get used too. I am going to burn 
another 8.10 iso at a really low speed and try to do a fresh install. hopefully that will help some.

---

