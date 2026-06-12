---
title: "Burning my back up avi files to DVD"
date: 2009-05-28
forum: New to Ubuntu
---

### Post by SodaAsh on 2009-05-28
First off i would like to say that im really enjoying Ubuntu its much better than the windows i was using before... i first loaded it on my laptop and liked it so much i put it on my main box. everything is working fine, however, my kids ruined this movie i wanted to watch but i did however make a back up of it before they got their hands on it.

Now i did do some reading on this before but i just cant get make the DVD with out getting an error. i convert the avi file to an iso or vob files(ive tried both) with DeVeDe program that everyone says should work. but when i go to burn the image to DVD it says there was a disc error. 

Im not sure what im doing wrong but any help with this would be great!

thanks

---

### Post by SunnyRabbiera on 2009-05-28
Well a burn error is probably related to your disk burning application, try burning at a lower speed.
There is a possibility of bad disks too, it happens.

---

### Post by halitech on 2009-05-28
How big was the resulting iso file? usually I only get errors if I try to burn something thats even just a little over the 4.4gig limit. Also, is the iso on an ext partition or ntfs?

---

### Post by blueridgedog on 2009-05-28
Try telling DeVeDe to make an ISO, then you can look at the resulting size and try and mount it to test.

If you have a directory called /mnt/disk and want to mount an iso file called myavis.iso, it would be:

```
mount -o loop myavis.iso /mnt/disk
```

You can also look at the log to see if there are more details about the error.

---

### Post by LowSky on 2009-05-28
burning AVI to a movie DVD isnt the best idea, your taking an AVI and re-encoding it to Mpeg2, kinda a backwords process, and you need a PC that can handle that much data that need to be cached and temporaritly stored.

 If you are going to rip movies and then re-burn them to other media, use mpg as the file container. its a much better idea. Or watch it on your laptop, or get a DVD player that can read Divx or Xvid, that way you dont have to make the file into an movie DVd, just a file dvd, which i faster and less prone to failing.

---

### Post by SodaAsh on 2009-05-28
[COLOR=Navy][COLOR=Black]Well you guys work fast thanks for all the replys.[/COLOR]


"Well a burn error is probably related to your disk burning application, try burning at a lower speed.
There is a possibility of bad disks too, it happens."[/COLOR]

[COLOR=Red]Well i did it a few times with different disk all coming up with error, but anything is possible.[/COLOR]

[COLOR=Navy]"How big was the resulting iso file? usually I only get errors if I try to burn something thats even just a little over the 4.4gig limit. Also, is the iso on an ext partition or ntfs?"

[COLOR=Red]well i tried it many different ways but the biggest the file ever got was 2.7GB so it[/COLOR]
[/COLOR][COLOR=Red]was never too big for the disk.
[COLOR=Navy]
[/COLOR][/COLOR][COLOR=Navy]"Try telling DeVeDe to make an ISO, then you can look at the resulting size and try and mount it to test.

If you have a directory called /mnt/disk and want to mount an iso file called myavis.iso, it would be:[/COLOR] " 

[COLOR=Red]ill give that a shot and tell you what happens[/COLOR].

[COLOR=Navy]burning AVI to a movie DVD isnt the best idea, your taking an AVI and re-encoding it to Mpeg2, kinda a backwords process, and you need a PC that can handle that much data that need to be cached and temporaritly stored.[/COLOR]

[COLOR=Red]Ya your prob. right but the thing is i have like over a hundred movies backed up already in avi format.[/COLOR]

 

thanks again

---

### Post by SodaAsh on 2009-05-29
Well i mounted it but it doesnt come up and play like a DVD should however i can go in and play the VOB files.


I went and d/l the 64bit version of ubuntu for my desktop and when i burned it... it came up with the same error but i was able to boot off of the disk so im not sure what that means.


Can it be that my DVD burners arent working with ubuntu or is it something im doing? Im leaning more towards the latter.

---

### Post by cjv8888 on 2009-05-29
Have you tried using vlc to play the iso file directly?  If it can play with vlc then the file is probably ok.

---

### Post by SodaAsh on 2009-05-29
okay i figured out how to do it.... for those of u having prob. burning avi to dvd.... i found this thread that shows you how to do it and it works so heres the link:

[URL="http://ubuntuforums.org/showthread.php?t=183936&highlight=avi+mpg"]
http://ubuntuforums.org/showthread.php?t=183936&highlight=avi+mpg[/URL]

i used the command line didnt try using GUI way.

i did one thing different than what he shows because i didn't want a menu so instead of using the command line:

makexml -menu *movie.mpg* -out *Mydisc*
I did:
makexml -dvd *movie.mpg* -out *Mydisc*

used:
[COLOR=Red]tovid[/COLOR]
[COLOR=Red]makexml
makedvd

[COLOR=Black]using these three scripts worked so thats how i will be burning my back-up avi files.

[/COLOR][/COLOR]

---

