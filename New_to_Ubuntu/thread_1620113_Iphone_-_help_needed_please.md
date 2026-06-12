---
title: "Iphone - help needed please"
date: 2010-11-12
forum: New to Ubuntu
---

### Post by nicho J on 2010-11-12
Hello,

I am a very recent convert to ubuntu and am still trying to get my head round things and I have been trying to get my iphone to sync with little luck.

I can sync the iphone (its a 3GS if that makes a difference) and have managed to get some songs transferred to it, but when I come to play them on the iphone they refuse to start. I can see them but they just won't play.

Please can you help and let me know what I need to do. 

Thanks

Nicho

---

### Post by Cowboybebop79 on 2010-11-12
First thing would be to check they are the correct format for your iphone. Other thing to check is whether anything actually got transferred I have seen some 0 byte files in my time which look like a file but there is nothing in it so its not going to work.

I assume that you can check the size of files on your iphone and the type of the file. If you can post with your results then I can advice the next step.

---

### Post by nicho J on 2010-11-12
The files are MP3 which the internet says are supported on Iphone. I can play the songs through rythum box once they are there I just can't play them through the iphone itself.

---

### Post by Jetso on 2010-11-12
I have the same problem with my Ipod Nano. The only solution I found was to import the files into iTunes and put them on there manually.

---

### Post by Cowboybebop79 on 2010-11-13
OK done a bit of searching and found that there is a problem with Iphone4 and transferring music. There is one package which does all the magic called "libimobiledevice" at the moment the standard installed version is 1.0.1-1 they are now at 1.0.3 which has support for Iphone4 the solution is to add the ppa of libmobile device so you can get the most upto date version.

to do this open terminal "accessories > terminal and paste the line below
 
```
sudo add-apt-repository ppa:pmcenery/ppa
```

you will need to confirm your password once the ppa has been added you can close the terminal and open update manager from the admin menu and do a manual update.

Hope this helps.

---

### Post by nicho J on 2010-11-13
I have uploaded libimobile device and the songs are still not being played on the iphone. It is not an iphone 4 only 3gs.

The iphone is mounting and files are uploading to it I believe but still cannot be played on the phone.

---

### Post by Cowboybebop79 on 2010-11-13
Hi, Nicho

Did a bit of googleing on the subject as I'm not the best when it comes to Iphone or anything beginning with an I. I managed to track down a how to here which expands on the tip I mentioned about adding the ppa from p mcenery.

you can find the how to here

[http://www.taranfx.com/sync-iphone-linux]("http://www.taranfx.com/sync-iphone-linux")

I have have checked it and there aren't any harmful commands in it so it looks safe to use if you are successful update the thread as solved for others with the same problem.

---

### Post by nicho J on 2010-11-13
I have tried following the instructions on the link but when I restarted my system would not load and I now need to reinstall.

I have had a look round the iphone that is mounted on the desktop and I cannot actually see any mp3 files located. Could it be that somehow the mp3 files are not there?

---

### Post by CBR_Rob on 2010-11-13
I've been using Ubuntu for about a year now and only 2 things I can't get working are AutoCAD and moving music onto my iPod.

Rythembox has been the most consistent at actually getting the files on there. Not sure if the iPhone will show up the same as the iPod though but worth a try.

Once I get a bigger SD card for my Evo my iPod syncing problem will be solved.

I know the iPod will play MP3 and m4a (iTunes calls these ACC files). I would assume the iPhone would take the same files.

---

