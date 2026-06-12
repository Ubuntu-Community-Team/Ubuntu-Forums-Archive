---
title: "A Questions Three"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by aaronej on 2009-04-15
I consider my self a moderately knowledgeable computer user edging to the level of geekdum, however windows crashed and I finally got a good enough connection to install Ubuntu.  I'm new to Linux and therefore have some questions:

1. I installed Ubuntu on a 2gb flash drive because I didn't want to mess with the hard drive as it may be possible to restore functionality to windows at some later date.  However 2gb is not enough to install many more programs onto the main drive. How does one install/move program locations to other hard drives?  I read that it is not as easy as in windows, however I cannot believe that there is not a way.

2. I would like to update to Open Office 3 (and if at all possible install some components to another drive so that it does not eat up storage on my 2gb main flash.  I downloaded the compressed files but there does not seem to be anything to initiate the installation, just the various packages.

3. Is there any downloads to install USB internet support for the Huawei u120e internet phone?  The CD is only for windows.  Just for kicks I tried the workaround for the Huawei 220 modem but it didn't work (the 220 has the drivers built in and doesn't use any CD's).

Thanks

---

### Post by Jakey_TheSnake on 2009-04-15
My turn for a question: if you want more space but don't want to intrude on Windows, why not install Ubuntu on a separate partition of the same hard-drive?

What format are the compressed packages?

If you got them from here: [http://download.openoffice.org/](http://download.openoffice.org/)

You should be able to right click, press extract here to extract. Put them on your desktop, and open up a Terminal. 

Type in:

```
cd ~/Desktop/OO [press tab here so it automatically completes destination]
``` 
then press enter. 

Then: ```
 sudo dpkg -i *.deb
``` 

Then: ```
cd me [tab]
```
(this should take you into a menu integration folder - if it does not, delete the "me" and press tab twice to get a list of folders, then cd to the one that's closest to menu integration)

Then run: ```
sudo dpkg -i *.deb
``` again.

---

### Post by abn91c on 2009-04-15
unless you installed a mini-ubuntu distro, the "normal" Ubuntu requires minimum 4 Gig space to work normally.

---

### Post by jARLAXL on 2009-04-15
Things in linux are different than in windows. Well hardware is the same but the software requires different practices/anticipation. But it is not impossible to do what you want. You just have to find out as in window$.

1.I recommend  installing on hard disk if you need more space. I dont see why you would mess the hard drives. Otherwise this would require to move system directories such /var to another partition which for me sounds like a more mess with your system.

2. Installation on ubunutu/linux works differently than in windows but being an ex-window$ user myself (12 years) i think installations are more straight forward (and easier) in linux. Still i suggest you install in a disk partition the whole ubuntu (hint: wait for Jaunty in a few weeks as it will have the OO 3 built in); that is make a dual boot ubuntu/windows.
 Otherwise you d have to find a way to move your system directories (as indicated above) to a hard drive. A link for installation of OO 3 (not in a seperate media) is here: [http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

3. Dont know about it but a search in the forums would help as many people use the devices you mentioned.

In conclusion:
 Get knowledgable about linux if you like/can although you dont have to. Try a dual boot. Its the easiest thing to do in your case i believe. Reccomendation: Wait 2 weeks (if you can) and install Jaunty after it is released (see [www.ubuntu.com](www.ubuntu.com)) with OO 3 and new kernel but not only.

Update: Just checked ubuntu.com and its released in 8 days...

---

### Post by aaronej on 2009-04-15
I have about a GB of extra room on my actual hard drive so the only way I'm  installing to the hard drive is to wipe it clean.  

Oh two more things:
1. I see that there is a palm program, how do you use it to sync things like pdf files and contacts?
2. is there software for syncing a dell Pocket PC running Windows mobile 2003?

---

### Post by jARLAXL on 2009-04-15
> **aaronej said:**
> I have about a GB of extra room on my actual hard drive so the only way I'm  installing to the hard drive is to wipe it clean. 

The OO size is several hundreds Mbs. How do you expect to create a partition and install other programs too in that a Gb space (either in windows or linux)?

Try freeing some of your disk space or buy a new disk.

---

### Post by aaronej on 2009-04-15
Um, thats my whole problem, I *don't* want to do anything to my main hard drive or my the flash I have my OS on, I want to install the programs I use every once and a while on my external hard drive to save space... and that seems a real flaw with linux that programs are not self contained...

---

### Post by llamabr on 2009-04-15
> **aaronej said:**
> Um, thats my whole problem, I *don't* want to do anything to my main hard drive or my the flash I have my OS on, I want to install the programs I use every once and a while on my external hard drive to save space... and that seems a real flaw with linux that programs are not self contained...

I'm not sure I understand the flaw.  You want to put linux applications on your hard disk, but you don't want to make any space for it on your hard disk?  So you both want to write to your disk, and not write to your disk?

You can easily mount your disk, MS partition and all, while running your ubuntu os from usb.  You can write files to it.  You could probably even mount it as /usr/bin/, and install apps to it, but that sounds pretty complicated, and asking for trouble with your other os.

---

### Post by jARLAXL on 2009-04-15
> **aaronej said:**
> Um, thats my whole problem, I *don't* want to do anything to my main hard drive or my the flash I have my OS on, I want to install the programs I use every once and a while on my external hard drive to save space... and that seems a real flaw with linux that programs are not self contained...

If you dont mention the spaces you have available in your hard drives and your hard drives that you have available, it is hard that someone can solve your problem be it in linux or window$. obviously you need somewhere a disk space to install anything in any OS. well if that is a flaw with linux why dont you try windoze to solve your problem which i seem to dont get. I diont know if it si possible for windoze but why dont you try installing windows on the usb and linux on the hard disk? It may make the things easier for you.

---

