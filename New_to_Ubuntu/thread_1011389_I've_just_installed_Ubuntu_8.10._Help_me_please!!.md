---
title: "I've just installed Ubuntu 8.10. Help me please!!"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by and0001 on 2008-12-14
Hi folks and thanks for having me here. I have just installed Ubuntu 8.10 on a Compaq Evo N610c laptop from the December 2008 issue coverdisc of Computer Active Magazine. It looks really impressive, I have to say, but, being a complete newbie to anything Linux, and also being trained in the ways of all things Windows, I'm feeling really useless here. The thing is, I want to take things a little at a time and I don't want to go online with it just yet, but it wont let me play dvds, avis or pretty much any other movie-type files unless I do (I normally use my laptop a lot for music, movies and writing). As I'm sure most of you know, if such a situation arose with Windows, I would just go online, download a particular codec with a .exe suffix and save it to a flash drive or a cd and then install it from there. So why is it not giving me the option to do so with 8.10? And why can't I find anything online that would appear to be a downloadable, install-from-a-flash-drive-or-cd-type codec anyway? There is a lot of info in the magazine, but none of seems to apply to offline users. Someone please help (preferably with idiot-proof instructions). Thanks, Andy

---

### Post by karlr42 on 2008-12-14
You can install them with the command
```
sudo apt-get install ubuntu-restricted-extras
```
in a terminal(in the Applications menu somewhere), but that won't work offline.
Also, Linux is NOT Windows! You install software from repositories. in that above command, your system downloads the necessary codecs automatically from the net, and installs them for you. You don't need to find a .exe file and run it- that command does it all for you.

---

### Post by GMachine_24 on 2008-12-14
It sounds as if you are running Ubuntu "live", i.e. from the CD and that you have not installed the OS onto your computer. If this is true, you will not be able to download the codecs you need as there is nowhere to install them on your computer since you haven't loaded the Ubuntu software.

If this is incorrect, i.e. if you have installed Ubuntu, then do as the previous post suggest and you should be able to view DVDs and MP4 movies, etc.

---

### Post by dwasifar on 2008-12-14
+1 on what Karl says.  If you find you still don't have the codecs you need after installing ubuntu-restricted-extras, you could also try installing a couple of things from the medibuntu repositories.  The instructions to add those repositories are at [https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu").  Once you add them, you can install libdvdcss2 and w32codecs (or w64codecs if you are using 64-bit Ubuntu):

```
sudo apt-get install libdvdcss2 w32codecs
```

---

### Post by WinterWeaver on 2008-12-14
> **and0001 said:**
> There is a lot of info in the magazine, but none of seems to apply to offline users.

go to:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

and search for the packages mentioned above. Make sure to choose the right one for your version of ubuntu.

They should be .deb files. You dowload them and then just run them on your ubuntu, and it installs. (I'm not so sure though if it installs any dependancies, can anyone confirm that?)

hope it helps,

BTW, Welcome to Ubuntu :)

WW

---

### Post by dwasifar on 2008-12-14
> **WinterWeaver said:**
> go to:
[URL]They should be .deb files. You dowload them and then just run them on your ubuntu, and it installs. (I'm not so sure though if it installs any dependancies, can anyone confirm that?)

Installing by double-clicking a .deb does not automatically install dependencies, but it will tell you what's missing so you can find and install it yourself.

---

