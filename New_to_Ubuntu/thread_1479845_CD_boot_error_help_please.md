---
title: "CD boot error help please"
date: 2010-05-11
forum: New to Ubuntu
---

### Post by ozstar on 2010-05-11
HI,
I have just dloaded 10+ created a CD at 4x so it would burn okay, but when I try to boot, I get 'Boot Error, try again.

Bios is fine, other boot okay.

Any advise please?

Thanks

oz  :-)

---

### Post by s.fox on 2010-05-11
Hello,

Did you do a md5sum check before burning?  [Here]("https://help.ubuntu.com/community/HowToMD5SUM") is a guide on how to do so.

-Silver Fox

---

### Post by anand_30 on 2010-05-11
I am also new to this os but may be your downloaded image is not correct.Have you checked md5sum of your image?.Check md5sum if it is not same then download image another time and give it another try,but i will advice you to install from usb(2 gb for desktop edition).If you are using windows then download universal usb creater its free and follow instructions on screen if u r using ubuntu then there is statup disk creator in system>administrator.

hope this may help.

---

### Post by ozstar on 2010-05-11
Thank guys..

I have the winMd5sum program and it shows the iso I down,oaded frokm the ubunu download page as..

d044a2a0c8103fc3e5b7e18b0f7de1c8

But as much as I searched, I cannot find the number it is supposed to be.

Where would I find it?

Thanks

oz


PS  Yes I am also going to try the usb way

---

### Post by bananas4370 on 2010-05-11
> **ozstar said:**
> Thank guys..

I have the winMd5sum program and it shows the iso I down,oaded frokm the ubunu download page as..

d044a2a0c8103fc3e5b7e18b0f7de1c8

But as much as I searched, I cannot find the number it is supposed to be.

Where would I find it?

Thanks

oz


PS  Yes I am also going to try the usb way

You can find the MD5 values [here]("http://releases.ubuntu.com/10.04/"). Near the bottom of the page is a file tree, view the file called MD5SUMS.

---

### Post by ozstar on 2010-05-11
Thanks again.

Well than goodness the md5sum is the same so my trouble is obviously elsewhere.

Other CDs boot okay except I changed the primary drive to a larger one and maybe this is the problem as it is not formatted to XP pr Linux.

I will go back to the previous drive that worked and try again.

Apprecate the help.

oz  :-)

---

### Post by ozstar on 2010-05-11
No go ! ..  Same 'Boot Error'.

I burnt it with Magic ISO at only 4 but I will try again with a faster burn.

oz

---

### Post by cap10Ibraim on 2010-05-11
Maybe you are booting the wrong drive (not the one with the Ubuntu cd)

---

### Post by narendraD on 2010-05-11
I think Anand above gave you the best advice. Dont keep trying to burn CD's if they are not working. Just use Unetbootin or Startup Disk creator to write the iso to a USB then use that to install. I too went thru a similar issue before i used a USB to install the OS.

---

### Post by ozstar on 2010-05-11
Thanks again guys..

I did try another CD but it too gave the same message.  Really weird ad I tried the MEPIS Boot CD again and it works okay.

Anyway did the usb stick using the universal usb thingo however my box is from antiquity and there is nothing in the bios to suggest a boot from a usb.  USB is enabled okay but no boot option.

There was SCSI and Network and neither boot went to the usb.

So here I am wanting to dance with Ubuntu and she's playing hard get.

Any ideas?

Thanks again,

oz

---

### Post by anand_30 on 2010-05-11
> **ozstar said:**
> Thanks again guys..

I did try another CD but it too gave the same message.  Really weird ad I tried the MEPIS Boot CD again and it works okay.

Anyway did the usb stick using the universal usb thingo however my box is from antiquity and there is nothing in the bios to suggest a boot from a usb.  USB is enabled okay but no boot option.

There was SCSI and Network and neither boot went to the usb.

So here I am wanting to dance with Ubuntu and she's playing hard get.

Any ideas?

Thanks again,

oz

Now if you really want to give it a try there is an option of installing it inside windows.I have done this thing.As your CDs are not working just download Deamon tools Lite.

[http://www.disk-tools.com/download/daemon](http://www.disk-tools.com/download/daemon)

Now mount ubuntu image using this software  and do wubi installation.Its very simple type of installation just provide some HD space your login name and password and you are ready to go.

But before doing this i will advice you to really look carefully in your boot options(but dont try to change other things except your usb boot).There should be usb boot option.(My antique comp has that option how you dont have?)

---

### Post by ozstar on 2010-05-11
Yes I guess I will give that a try.

My mobo is an old Asus TULSI-M with the bios Award Medallion V6

I hope I can get it to work.. 

oz  :-)

---

### Post by spydeyrch on 2010-05-11
I have a few suggestions...... (coming in following post)

-Spydey :guitar:

---

### Post by KinKiac on 2010-05-11
You may have to enable the USB boot option by digging a bit deeper in your BIOS and adding USB to the list of available drives for booting.  Ive yet to find a PC that doesnt allow for booting to a thumb drive as if it were a HDD

---

### Post by spydeyrch on 2010-05-11
> **spydeyrch said:**
> I have a few suggestions...... (coming in following post)

-Spydey :guitar:
Sorry guys, my work machine just crashed, windoze.  :lolflag:

So a few days ago, I ran into an issue where the x32 flavor wouldn't burn correctly to the CD, I tried several different things. My out come can be found in these two threads:

[thread #1]("http://ubuntuforums.org/showthread.php?t=1479071")
[URL="http://ubuntuforums.org/showthread.php?t=1479197"]
thread #2[/URL]

Any who, I had to use a live usb pen drive or the x64 flavor to get around the issue.

Also, there is a program, that you can either boot off of a cd or floppy, that will allow legacy computers to boot from usb drives. It can be found here:

[Boot from usb drive if your computer won't let you]("http://www.howtogeek.com/howto/16822/boot-from-a-usb-drive-even-if-your-bios-wont-let-you/")

Hopefully those will help you. So then you could boot off of the usb pen drive via that program linked above and hopefully get the issue fixed.

-Spydey :lolflag:

---

### Post by ozstar on 2010-05-12
Hey this is great.. many thanks.

I have upgraded the Bios as well so will look forward to getting time to try these things out.

I'll post as soon as I know in case someone in  the future has the same probs and this thread may save them hours of time.

oz :-)

---

