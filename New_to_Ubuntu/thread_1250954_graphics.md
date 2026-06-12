---
title: "graphics"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by dzon65 on 2009-08-27
I was wondering if the problems with the graphics(9.04,no synchro video-audio,jerky flash and scrolling,zzzzzlowing down everything while f.e a youtube clip is playing on the background etc.....)would remain if a)installing from disc instead of wubi  b)installing 8.10 instead (since the difference in graphic use).As for the hardware,well it's all up to date,would like to do a system testing but it freezes all the time so...

---

### Post by SunnyRabbiera on 2009-08-27
actually the type of hardware does matter, any info on your graphics card?

---

### Post by dzon65 on 2009-08-27
operating system linux x86_64
nvidia driver version 180.44

---

### Post by dzon65 on 2009-08-27
Forgot: medion,2GB memory,120 disc.

---

### Post by SunnyRabbiera on 2009-08-27
> **dzon65 said:**
> operating system linux x86_64
nvidia driver version 180.44

Your issue might be your nvidia card, lucky you dont have an ATI.
I am unsure of any resolutions for you as I dont use nvidia but its possible to get you up to full speed.

---

### Post by dzon65 on 2009-08-27
I'm not quite sure what you mean.The graphic card is at his max.

---

### Post by Cresho on 2009-08-27
open up terminal and install these

#sudo apt-get install compizconfig-settings-manager nvidia-settings

now under
system->preferences->sessions add+ (sessions is changed in jaunty i think its startup)

name: Nvidia
command: nvidia-settings --load-config-only
comment: Nvidia settings loader



now go to system->preferences->advanced desktop effects->general options->display settings
Change the texture filter to "best" or good, untick "detect refresh rate""(this one was the one that made a difference and reboot the system between changes), bump to 200 "refresh rate", tick "Sync to vblank" value string 1920x1200+0+0 (keep the 640 one and put it under the 19200)

open up nvidia-settings in terminal with that name command and go through the list and tick all sync that it offers.  reboot and your good to go


after this, your desktop should be looking synced and running at 200 frames per second.  ( I said LOOK and not actually run).  It is silky smooth and you can gaze at it all day.

---

### Post by dzon65 on 2009-08-27
Cresho,I've installed it in start up.But then,the adjusting,well, I'm lost there.Where do I do the settings?Texture filter etc...?Forgive me but I'm totally knew and I'm used to dutch so..

---

### Post by dzon65 on 2009-08-27
Cresho.Did exactly what you proposed,but after reboot.....still the same.Youtube still very jerky,no synch and when in use (youtube)on background all other applications (scrolling,popup menus) veeery slow.

---

### Post by SunnyRabbiera on 2009-08-27
> **dzon65 said:**
> I'm not quite sure what you mean.The graphic card is at his max.

meaning making sure it runs smoothly.

---

### Post by NoaHall on 2009-08-27
Yes, if you install NOT using wubi, it will run better, but try using a older driver first.

System -> Admin -> Hardware Drivers

And select a older driver, restart, and test !

---

### Post by dzon65 on 2009-08-27
Well,tried about everything now.Still same problems.Last hope are the ubuntu guys at the local university.If they can't solve it I'm afraid ubuntu is a no-go.I could try to install 8.10 to see if the same problems occur,but if so...

---

### Post by Cresho on 2009-08-28
is your system 64bit os?

what graphics nvidia card are you using?

what is your pc spec?

are you running compiz fusion?

are you using firefox with native 32bit or 64bit flash?

how did you install flash?

Sorry for all these questions but honestly if your pc or laptop is slow, you will never get these running.  There are specific hardware and software in win or lin or mac that allowes you to enjoy HD content.  Hulu is HD content

---

### Post by dzon65 on 2009-08-28
No problemo for the questions.Really want this to be solved.
So here we go:Medion 32 bit,2gb ram,120hd,nvidia 6150(version 180),yes I'm running compiz fusion( yet,the only application is the ringswitcher,all others are turned off).As for the shockwave,while having 9.04 installed (wubi)and starting my personal touches,I wanted some music.So turned on youtube ,chose something and then I got the notice "you'll need shockwave to play this video---install?....",so I did.That's how I got this 9.0 r999 installed.

---

### Post by Cresho on 2009-08-28
is your os 64bit?  this is important. ohh wait a minute.  Your running jaunty!?  this is a sorry excuse for ubuntu.

I cant even get my games to run on this os.  even flash sucks,  I used the karmic koala ubuntu alpha version and flash works fine.  Flash works fine in hardy heron LTS.  Jaunty plain sucks.

Try another ubuntu version...seriously.

---

### Post by dzon65 on 2009-08-28
Cresho,are you sure about this?I was planning to do this in the first place cause if I remember well,didn't have this problem with 8.04 (a long while ago).I tried about everything to get this working but....Tell you what,I'll uninstall 9.04 and install 8.10 or something and I'll let you know.J.

---

### Post by dzon65 on 2009-08-28
Cresho.You were wright.Ditched the 9.04 and installed 8.10.No problems here with flash and jerky scrolling.Installed latest shockwave and works like a charm.That's one problem less.Unfortunately some others to come.(usual stuff,hybernate -issue and headphone-sound-problem).So....thanks for the advice,J.

---

### Post by Cresho on 2009-08-29
ya i used jaunty beta and full and determined this issue long ago.  koala works awsome.  in fact, looks super!  wait for that one and maybee it will fix your issues.

---

