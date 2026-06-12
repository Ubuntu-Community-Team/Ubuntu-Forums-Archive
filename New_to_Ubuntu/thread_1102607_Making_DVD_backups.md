---
title: "Making DVD backups"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by servicetech on 2009-03-21
Is there an easy way to do this with Linux?
I've tried K9copy and DVD9to5 in combination with K3b and can't get either to work. I've tried some tutorials I've found online and haven't had any luck.

---

### Post by theozzlives on 2009-03-21
remastersys

---

### Post by servicetech on 2009-03-21
> **theozzlives said:**
> remastersys

How/where do I get this?

---

### Post by binbash on 2009-03-21
What kind of backups are you talking about?Dvd Movies, live ubuntu system etc?

---

### Post by benerivo on 2009-03-21
Try dvdbackup

---

### Post by servicetech on 2009-03-21
> **binbash said:**
> What kind of backups are you talking about?Dvd Movies, live ubuntu system etc?

DVD movies. I'd also like to take the avi/mpeg/flv files and make them into DVD's if that's possible.

---

### Post by servicetech on 2009-03-21
> **benerivo said:**
> Try dvdbackup

DVDbackup doesn't compress, 1:1 only. I think K3b will do that.

---

### Post by halitech on 2009-03-21
K9copy and K3b work great for me for backing up dvd movies. I use Devede to create my own dvds from avi files.

what happens when you try to use K9copy?

---

### Post by binbash on 2009-03-21
I am using dvd:rip .Latest version is not at the repos (Last time i checked ), which supports 2 pass x264 encoding.

---

### Post by Dr Small on 2009-03-21
k9copy should work; I don't know why it wouldn't. That's the only thing I use (on my sister's computer) for copying DVDs.

---

### Post by benerivo on 2009-03-21
For dvd backups it's worth looking at [dvdshrink]("https://help.ubuntu.com/community/DVDShrink"). For conversion of video files for dvd playback use ffmpeg to convert to mpeg format. I think most dvd players will play a dvd disk that has a mpeg file on it.

---

### Post by servicetech on 2009-03-21
When I try K9 copy it copies the vob files to the hard drive w/o compressing. It doesn't create an ISO or burn the DVD.

---

### Post by halitech on 2009-03-21
sounds like K9 just isn't set up correctly. Go into Settings - Configure K9copy then go to the DVD section. Set the dvd size to 4400 and check burn with K3B. You can also check auto burn if you want. This should work properly for you.

---

### Post by servicetech on 2009-03-21
> **halitech said:**
> sounds like K9 just isn't set up correctly. Go into Settings - Configure K9copy then go to the DVD section. Set the dvd size to 4400 and check burn with K3B. You can also check auto burn if you want. This should work properly for you.

I tried that, it still just dumps the vob files into the home folder.

---

### Post by dwasifar on 2009-03-21
I regret to say that the best programs for this, in my experience, are both Windows apps: DVDFab HD Decrypter and DVDShrink.  You get better control of compression and an easier interface than any of the available native Linux tools.  They both run fine under Wine.

[http://www.dvdfab.com/free.htm]("http://www.dvdfab.com/free.htm")

[http://www.softpedia.com/get/CD-DVD-Tools/CD-DVD-Rip-Other-Tools/DVD-Shrink.shtml]("http://www.softpedia.com/get/CD-DVD-Tools/CD-DVD-Rip-Other-Tools/DVD-Shrink.shtml")

---

### Post by halitech on 2009-03-21
> **servicetech said:**
> I tried that, it still just dumps the vob files into the home folder.

for the output device, is it on ISO or folder?

---

### Post by servicetech on 2009-03-21
> **halitech said:**
> for the output device, is it on ISO or folder?

Set to ISO

---

### Post by halitech on 2009-03-21
just out of curiousity, is genisoimage or mkisofs installed? Also, make sure dvd+rw-tools is installed.

---

### Post by fenian on 2009-03-21
You can find a good [tutorial for k9copy here]("http://www.dvd-guides.com/content/view/213/59/").

---

### Post by Alex82 on 2009-03-22
I am also having a similar problem, but when I try to back up a dvd it takes ages and get to 99% and fails or gets to 100% and does not attempt to burn and then I cant find any ISO files on my system?

---

### Post by halitech on 2009-03-22
Alex, where do you have the output directory set to?

---

### Post by Alex82 on 2009-03-22
halitech, as a default../tmp/kde-alex/k9copy/

but i have also tried to save in home and dektop

---

