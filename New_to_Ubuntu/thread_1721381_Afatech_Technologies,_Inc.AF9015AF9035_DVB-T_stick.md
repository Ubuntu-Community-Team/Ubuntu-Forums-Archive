---
title: "Afatech Technologies, Inc.AF9015/AF9035 DVB-T stick"
date: 2011-04-04
forum: New to Ubuntu
---

### Post by mark222 on 2011-04-04
AF9015/AF9035 DVB-T stick
Afatech Technologies, Inc.
AF0102020700001


Competent windows user but brand new linux user .Just installed Ubuntu desktop onto hard drive and  all well so far but i am haveing problems with my tv stick .
I have read some posts from way back in 2005 and just wondered if any one could treat me like a two year old and give me some direction as to how to install it  .

Finding Ubuntu desktop a real good system so far and have had to do very little to and during install .Hope i can get my tv stick to work and i will be a convert :-)

Thanks for any help offered

---

### Post by wolfen69 on 2011-04-04
> **mark222 said:**
> AHope i can get my tv stick to work and i will be a convert :-)


Years ago, that was the last thing I needed also before converting fully to ubuntu. Luckily my card worked with VLC. Have you installed TVTime and tried it? There is also XawTV. If it doesn't work with either of those, you'll have to do some research. It's usually just a firmware issue. I'll post back if I find any info.

---

### Post by wolfen69 on 2011-04-04
OK. According to [this]("http://www.linuxtv.org/wiki/index.php/Afatech_AF9015") page, it is supported natively in the kernel. Let us know about tvtime or xawtv.

---

### Post by mark222 on 2011-04-04
Yes i am fully taklen back how good Ubuntu is ....i did try it years ago but i have to say it has come on to be a serious challenger .I have it on a laptop also and i didnt have to do any thing ....every time i turned it on something else worked untill it was fully working ( toshiba laptop .
The one i want for the tv stick is a fujitsu siemens desk top i have in the kitchen so i can watch tv .
I have vlc and metv but not the ones you mention .The problem is it isnt being recognized for a driver but shows up in system device ok but with ????? for driver .

Thanks for looking into it for me


edit just saw your new post ...i will load the two programs yopu say and get back to you with the results .

---

### Post by mark222 on 2011-04-04
ok so i installed tv time and although it seemed to install ok .....no luck recognizing my stick .

Found this page that says it has firmware update but i havent a clue what to do with it ..........just a load of chinees writing when i click on it .

[http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/]("http://www.otit.fi/%7Ecrope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/")



can you help please


when i click on the tv viewer it just flashes a black box ...then nothing


edit right i have installed both the programs you suggested and neither program start up after installing .....any idea why .thanks

---

### Post by wolfen69 on 2011-04-04
Just download [this]("http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/4.95.0/dvb-usb-af9015.fw") firmware file and put it in your home folder. Then 
```
sudo cp dvb-usb-af9015.fw /lib/firmware 
```
then
```
sudo modprobe dvb-usb-af9015 
```

Btw, good eye for finding that firmware file. Let's hope it works.

---

### Post by mark222 on 2011-04-04
Right so i updated the fw ok ...( i'm learning :-)

Now i have no driver installed still but i have the driver on the cd that came with it but when i try to install ......it says 
" Archive:  /media/DVL USB DVB-T/Driver/DrvInstall/DrvInstall.exe
[/media/DVL USB DVB-T/Driver/DrvInstall/DrvInstall.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /media/DVL USB DVB-T/Driver/DrvInstall/DrvInstall.exe or
          /media/DVL USB DVB-T/Driver/DrvInstall/DrvInstall.exe.zip, and cannot find /media/DVL USB DVB-T/Driver/DrvInstall/DrvInstall.exe.ZIP, period.


Now i pressuming that its because it is an exe installer .

how to go about installing exe .............please please :-)


I have learned one thing today ....make it two and your on my buddy list :-)

---

### Post by wolfen69 on 2011-04-04
> **mark222 said:**
> 
I have learned one thing today ....make it two and your on my buddy list :-)

In that case, I'll give it my best. :)

The thing is, the driver on the cd is not going to work, as it's a windows only thing. Now the fun part begins. Unless someone else has any ideas, or I find something, it's pretty much between you and google.

But I'll keep my eyes peeled and let you know if I find anything. But I once heard someone say, "Are you going to let your hardware dictate what software you use, or are you going the OS dictate what hardware you use?" In other words, if using ubuntu is important enough, you would go out and buy a linux compatible tv tuner. And then you would be "free".

But first, let's see if we can get this one going. Cheers and good luck.

---

### Post by mark222 on 2011-04-04
I'm having fun :-) i like broken things so i can learn while fixing .....the truth is windows became boring and you do start to lose know how the more a system does for you .This is like starting over ....remember dial up and them funny noises lol 

Whats this Wine hq all about ....run windows platforms on ubuntu it says .........kinda like virtual drive i think .I wouldnt want to mix two systems realy but if i can get it loadedfor that one use i might try fiddling ( i'm a guitar player realy ....but a bit of fiddling good for the soul lol

Thanks wolf .......no doubt i'll be back with some questions tomorrow

---

### Post by wolfen69 on 2011-04-04
> **mark222 said:**
> 
Whats this Wine hq all about ....run windows platforms on ubuntu it says .........kinda like virtual drive i think .

Wine is a compatibility layer that allows you to run *some* windows apps as if they were native to linux. Here is some info, but I suggest downloading from the repos. Get winetricks afterwards also. [http://www.winehq.org/](http://www.winehq.org/)

---

### Post by wep940 on 2011-04-04
I'm not familiar with the device - is it internal or is it an external USB device?  If it's an external USB device, please do the following in a terminal window and post back the results:
 
(be sure the device is plugged, etc.)
 
lsusb 
 
That will list the USB devices that Ubuntu knows about, even if it has no driver for it.  Amongst the output on each device will be a xxxx:yyyy pair - that is the identifier for the product - xxxx being the manufacturer and yyyy being the device.  After getting that we can search the net with "linux xxxx:yyyy" and see what turns up.

---

