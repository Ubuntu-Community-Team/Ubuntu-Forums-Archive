---
title: "Need help getting Ubuntu installed"
date: 2010-09-23
forum: New to Ubuntu
---

### Post by mjneid on 2010-09-23
I have an older dell insprion 1150 computer. It does not have any sort of Windows, or Linux programming on the computer. Strictly a bare naked computer for lack of better terms. I have tried creating a CD-ROM, DVD-ROM, and a USB stick to install Ubuntu 10.04 on to the computer. I've got into the BIOS screen and had it load the USB-Stick or CD-ROM before attempting to load information from Hard drive. I can get to the Ubuntu screen and i do select "install Ubuntu" when i do this the screen goes black and i get a flashing underscore for about 20 mins, then i'll get the Ubuntu logo with the progress. And it will remain on that screen for approximately 30 mins, then the screen goes dark for about 5 then shuts off. 

I know i have to be doing something wrong, but i cannot figure it out. I am doing everything on their page [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) and have crossed the T's and dotted the I's.



anyone out there have a clue as what to i am doing wrong?

---

### Post by spiky001 on 2010-09-23
I think the cd/usb might not be good did yo check the md5sum?

---

### Post by mjneid on 2010-09-23
> **spiky001 said:**
> I think the cd/usb might not be good did yo check the md5sum?

I have not checked it out yet. I did see a page about that.. .. but i didn't do it. I guess i should do that and report.

---

### Post by sikander3786 on 2010-09-23
First of all check the MD5SUM as **spiky** suggested of the downloaded image. See here.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by spiky001 on 2010-09-23
It is best that will check that integrity of the iso

---

### Post by mjneid on 2010-09-23
> **sikander3786 said:**
> First of all check the MD5SUM as **spiky** suggested of the downloaded image. See here.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Okay i've checked the MD5SUM of the program i am using [ubuntu-10.04.1-desktop-i386.iso ] and according to the winMd5Sum by Nullriver they are the same as what i have downloaded.

---

### Post by spiky001 on 2010-09-23
Ok thats a good start, I would burn it to a cd BURN AT SLOWEST SPEED it might be worth checking md5 of burnt cd as well at least then yo know you have a good cd

---

### Post by mjneid on 2010-09-23
> **spiky001 said:**
> Ok thats a good start, I would burn it to a cd BURN AT SLOWEST SPEED it might be worth checking md5 of burnt cd as well at least then yo know you have a good cd

Okay, i am burning the image at the slowest speed possible, by InfraRecorder, which is a 4x..

How would i check the MD5SUM of the CD, is this what i should do?
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck)

since it puts everything in files on the disc?

---

### Post by spiky001 on 2010-09-23
have a look down the end of page
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) if your using windows

---

### Post by mjneid on 2010-09-23
> **spiky001 said:**
> have a look down the end of page
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) if your using windows

Okay, that was the same thing i was point to. Glad we are on the same page.

When i insert the CD-ROM and it boots from the CD i get the purple screen with the two icons at the bottom. i cliked on "check disc for errors" and all i am getting is the flashing underscore.

---

### Post by spiky001 on 2010-09-23
it,s been awhile since i installed
[http://news.softpedia.com/news/Installing-Ubuntu-10-04-LTS-141550.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-04-LTS-141550.shtml)
so maybe this will help cant remember the 2 icons, I think I just put cd in let it run,

---

### Post by mjneid on 2010-09-23
> **spiky001 said:**
> it,s been awhile since i installed
[http://news.softpedia.com/news/Installing-Ubuntu-10-04-LTS-141550.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-04-LTS-141550.shtml)
so maybe this will help cant remember the 2 icons, I think I just put cd in let it run,

I'm beginning to think it might be something with the computer. I just installed ran the Netbook Version on my Asus w/o a problem. 

i'll give that page a look over when i get home, i get off in a few. 

And last night i put the disc in and had it install, and when i woke up about 7 hours later it was just a blinking underscore still.

---

### Post by Lateralis on 2010-09-23
I'm shooting from the hip here, so forgive me if I'm way off the mark and totally wrong...! 

[This Ubuntu link]("https://help.ubuntu.com/community/Installation/SystemRequirements") describes the minimal system requirements that you need.  The Dell specifications listed in [this PDF]("http://www.google.com/url?sa=t&source=web&cd=5&ved=0CDkQFjAE&url=http%3A%2F%2Fsupport.dell.com%2Fsupport%2Fedocs%2FSYSTEMS%2Fins1150%2Fen%2FF7573a01.pdf&rct=j&q=dell%20insprion%201150%20hardware&ei=PrWbTPDvAujO4wavs_Bu&usg=AFQjCNHNN7-Nw2Fy6ztHsJDVyXVsA6dO4g&sig2=jEubhZLN_UnXTYnu1Yew7Q&cad=rja") seem to suggest that you may not have enough RAM to meet the minimum specifications.  So my question: how much RAM have you got?  How old is the computer and what are the other specs of your system?

---

### Post by scrooge_74 on 2010-09-23
there are a couple of options you can try, some laptops have a harder time installing than others.

at boot option for the Live CD you should find at the bottom of page some options. Try them dont remember them by name but there should be things like noacpi.

---

### Post by mjneid on 2010-09-23
> **Lateralis said:**
> I'm shooting from the hip here, so forgive me if I'm way off the mark and totally wrong...! 

[This Ubuntu link]("https://help.ubuntu.com/community/Installation/SystemRequirements") describes the minimal system requirements that you need.  The Dell specifications listed in [this PDF]("http://www.google.com/url?sa=t&source=web&cd=5&ved=0CDkQFjAE&url=http%3A%2F%2Fsupport.dell.com%2Fsupport%2Fedocs%2FSYSTEMS%2Fins1150%2Fen%2FF7573a01.pdf&rct=j&q=dell%20insprion%201150%20hardware&ei=PrWbTPDvAujO4wavs_Bu&usg=AFQjCNHNN7-Nw2Fy6ztHsJDVyXVsA6dO4g&sig2=jEubhZLN_UnXTYnu1Yew7Q&cad=rja") seem to suggest that you may not have enough RAM to meet the minimum specifications.  So my question: how much RAM have you got?  How old is the computer and what are the other specs of your system?

more than likely that is my problem. The RAM, my wife got this computer around 4 or 5 years ago, and it's been setting downstairs in it's bag and hasn't been touched. I'm sure it doesn't have 1G of RAM.... that's most likely it.

---

### Post by Lateralis on 2010-09-23
In principle, you probably don't need that much RAM to get Ubuntu working.  I've got an exceptionally old and creaking laptop that I installed Xubuntu to (I thnk 9.04 but more likely 8.10) which I keep lying around at my mother's in case her PC encounters problems.  I believe that only has 512 MBs of RAM and runs fine.  But I would hazard the guess that anything less might be too little, and probably too little to run the graphical LiveCD.

Still, you could try using the [Ubuntu alternative install CD]("http://www.ubuntu.com/desktop/get-ubuntu/alternative-download").  You will install through a command line and will not boot to a live Gnome desktop but might be a possible way forward.

---

