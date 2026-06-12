---
title: "iTunes &amp; Ubuntu"
date: 2010-07-12
forum: New to Ubuntu
---

### Post by OldGoat58 on 2010-07-12
I am so totally hooked on Ubuntu Linux that I really want to get my family onboard.  I can fairly easily get 3 out of the 4 people switched over from Windows but I have one with a valid concern.

Is there a way to use iTunes with Ubuntu 10.04 LTS?  I know Ubuntu will recognize the iPod and that Rhythmbox can add and delete tracks, but my 17 year old has an extensive library on iTunes and he tells me that he can't copy them from iTunes to an external HD only an iPod.  Any help or suggestions will be greatly appreciated.

Thanks!
Mike
Fairless Hills, PA

---

### Post by JustinR on 2010-07-12
Google is your friend! :p

I found a few links that may help.

[http://www.tuaw.com/2006/09/19/how-to-keep-your-itunes-library-on-an-external-hard-drive/](http://www.tuaw.com/2006/09/19/how-to-keep-your-itunes-library-on-an-external-hard-drive/)

This one will let you move the itunes library over. Copy over your music folder and import it into Rhythmbox.

---

### Post by Darkness Des on 2010-07-12
1. He isn't supposed to use iTunes to drag and drop tracks to the external hard drive. He's supposed to use Windows Explorer to copy your Music folder to the external hard drive.
2. There is a way to run it. Wine (free) and Cedega (expensive) can run Windows programs, although Cedega generally gives better results. These are both not very good and don't offer the full features of most programs as they can't completely emulate Windows. They both are rather slow on most things also. Most recent versions of iTunes aren't supported.

---

### Post by waynefoutz on 2010-07-12
> **Darkness Des said:**
> 1. He isn't supposed to use iTunes to drag and drop tracks to the external hard drive. He's supposed to use Windows Explorer to copy your Music folder to the external hard drive.
2. There is a way to run it. Wine (free) and Cedega (expensive) can run Windows programs, although Cedega generally gives better results. These are both not very good and don't offer the full features of most programs as they can't completely emulate Windows. They both are rather slow on most things also. Most recent versions of iTunes aren't supported.

PlayonLinux installs a working version of Itunes, but I've found it to be kind of buggy and unresponsive. There are plenty of alternatives that run better, Rhythembox or Amerok both do a better job. I prefer Amerok myself.

---

### Post by DeadSpace on 2010-07-13
As Darkness said, he can actually copy them over from within 'My Music' in Windows. As far as I'm aware the heavy DRM restrictions from iTunes only apply to video, so music should work fine.

By the way, I **strongly** recommend Banshee as the primary media player - comes with an equaliser by DEFAULT (Amarok's is coming but still not here yet) and it has a very clean interface. Rhythmbox I also found to be quite good.

EDIT: I just checked, I don't how this would work (never used this option before) but Banshee has an option to import media from iTunes Media Player. Just in case that helps you at all. I think iTunes has certain files that Banshee is probably compatible with?

---

### Post by k3lt01 on 2010-07-13
> **DeadSpace said:**
> EDIT: I just checked, I don't how this would work (never used this option before) but Banshee has an option to import media from iTunes Media Player. Just in case that helps you at all. I think iTunes has certain files that Banshee is probably compatible with?You need to install Banshee on the Windows partition so you can import the iTunes media over. Then you just copy it to the appropriate Ubuntu folder and us it to your hearts content.

I have found with my 6th Gen iPod 120gb Classic that nothing but GtkPod will load music/video files onto it. All other programs will do up to 5.5th Gen.

---

### Post by bytescribe on 2010-07-13
While this isn't the topic I was looking for at all, I had to sit up and take notice of the helpful suggestions! I am SO subscribing to this thread because of the useful info.

I want to use iTunes for one reason only: my fave musician has some stuff on there that I haven't listened to yet 'cause I haven't jumped on board the iTunes wagon (worries about expenses and compatibility with Linux).

Thank you to the one who posted the original question!

BB,
Kat ^.^

---

### Post by Zzl1xndd on 2010-07-13
As some said iTunes will not work natively but might with Wine (Or Cedega, Crossover or Play on Linux). I say might because I find all of these methods to be hit and miss. 

I would test their iPod to ensure it syncs with a program on Linux and ensure their music does not have any DRM on it. If it works then I would show them the Ubuntu Music store through Rythmbox and see if that fits their needs. (With a little luck Rythmbox will be able to sync to their ipod).

---

### Post by TBABill on 2010-07-13
Why not have the best of both worlds? Keep Windows running in a virtual machine or on a separate partition so you can use the program itself? There's no reason to dump Windows if you have it on the machine already. I lost Windows over a hard drive failure and did not ever create a backup copy so I was stuck with one OS. Now that I have a new machine and backup copies of Windows, I will keep both so for those rare times I need something in one or the other, both are available. 
 
There's nothing wrong with being a Windows user. I use it because I have to at work, but I use it at home because I need it sometimes. I get very aggravated with Windows sometimes, but not enough to just stop using it out of spite...although I won't buy a copy off of a shelf! Since it came on my machine I'll sure get my money out of it though.

---

### Post by mebomechanicno1 on 2010-07-14
Cucusoft [http://www.cucusoft.com/](http://www.cucusoft.com/) sell* a Windows based app for transferring data from an ipod to a pc or mac, and it need not be saved in iTunes.  I realise this doesn't help to get it into Ubuntu but at least it gets it out of iTunes (by transferring it to the iPod then into whichever other location you want).
 
*I bought it some time ago, but you may be able to download a test version.
 
If anyone can suggest how to read video from my Classic using Ubuntu I will be grateful.

---

### Post by nmaster on 2010-07-14
why not just install windows in virtualbox? you can share a directory with ubuntu.  that way you can listen to the music in ubuntu with rhythmbox/banshee/other and just pop over into windows to sync with the ipod.

---

### Post by mebomechanicno1 on 2010-07-15
I have just come across this link [http://www.pendriveapps.com/copytrans-free-ipod-manager/](http://www.pendriveapps.com/copytrans-free-ipod-manager/) which describes itself as
 
"CopyTrans Manager is a Free iPod Manager or *Alternative iTunes Manager* created by WindSolutions LLC. CopyTrans can be used as an iTunes replacement for the iPhone, iPod, and iPod Touch. Use CopyTrans Manager to add or remove music and videos, edit song tags and artwork, create and organize iPhone playlists, or preview tracks with it's integrated player. The coolest feature is that "unlike iTunes", it can be taken with you (requires no installation)."
 
I have not tried it so make no claims for it, but I will be trying it out as soon as I get some other issues resolved.  If you try it before I do, perhaps you will leave a note here?

---

### Post by k3lt01 on 2010-07-15
> **mebomechanicno1 said:**
> I have just come across this link [http://www.pendriveapps.com/copytrans-free-ipod-manager/](http://www.pendriveapps.com/copytrans-free-ipod-manager/) which describes itself as
 
"CopyTrans Manager is a Free iPod Manager or *Alternative iTunes Manager* created by WindSolutions LLC. CopyTrans can be used as an iTunes replacement for the iPhone, iPod, and iPod Touch. Use CopyTrans Manager to add or remove music and videos, edit song tags and artwork, create and organize iPhone playlists, or preview tracks with it's integrated player. The coolest feature is that "unlike iTunes", it can be taken with you (requires no installation)."
 
I have not tried it so make no claims for it, but I will be trying it out as soon as I get some other issues resolved.  If you try it before I do, perhaps you will leave a note here?
From their webpage
>  System requirements

    * Min. 128 MB of RAM
    * Designed for Windows XP, Vista & Windows 7
    * iPhone/iPod Touch: iPhone drivers must be installed
There is nothing there about its suitability for Linux OSs.

---

### Post by mebomechanicno1 on 2010-07-19
> **k3lt01 said:**
> From their webpage
 
There is nothing there about its suitability for Linux OSs.
 
I didn't say there was but the original question was 
 
"my 17 year old has an extensive library on iTunes and he tells me that he can't copy them from iTunes to an external HD only an iPod. Any help or suggestions will be greatly appreciated".

---

