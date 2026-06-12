---
title: "Why wont any games work with WINE and the Intel chipset?"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by 11010110 on 2009-03-25
Hi everyone,

I was just wondering why it is that very few good games (the ones I want to use lol) will not work with wine and my Intel chipset. Shouldn't there be a workaround for this? Also if they work with my windows and my Intel chipset so why dont they work with Ununtu? I was just wondering out of curiosity and also to see if there was any way I could get it to work lol.

Thanks a lot in advance everyone!

---

### Post by pbpersson on 2009-03-25
Wine is a Windows emulator, it is attempting to pretend it is a Windows machine running inside Linux.  It has come a long way but it will not run everything.

Let's pretend that Windows is the United States of America and Linux is Japan.  If you travel over to Japan you will be a stranger in a strange land - you will not understand anything that is said to you and no one will understand you.

You take an interpreter with you - but SOME things said in Japanese do not quite translate correctly into English and vice versa.

Does that make sense?  Your Windows programs are strangers in a strange land speaking a foreign computer language to Linux.  Wine is doing the best it can.

---

### Post by 11010110 on 2009-03-25
Yes that makes sense and I realize this but the problem I have is that these programs I wish to use will not work with either the ATI graphics cards or the intel chipset although they work with many other graphics cards just fine. Im sorry that I didnt make that part clear enough in the beginning, I should have lol. I was just wondering how it works with many cards and not mine and why its so hard to make a workaround (seeing as my research has lead to finding nothing lol). I just find it strange that it works with every card under windows yet with all but 2 under Ubuntu.

Thanks for the reply sorry I wasnt clear lol

---

### Post by 3rdalbum on 2009-03-25
Microsoft Windows uses a set of 3D libraries called Direct3D to communicate with the graphics driver and render 3D graphics. Windows games use Direct3D as well, because Direct3D is the "native" Windows library.

There is a cross-platform equivilant called OpenGL that is regarded as the "native" Linux library for 3D.

If your Windows games use Direct3D, then Wine attempts to convert Direct3D calls into OpenGL calls.

Intel graphics chips support all of Direct3D 9, but not all of OpenGL 2. That's why some of your games won't run in Wine unless you use a better graphics processor - because Wine is converting Direct3D calls into OpenGL equivilants that the Intel chip can't understand.

And there are some parts of Direct3D and the Windows API that Wine doesn't yet understand.

---

### Post by mvalviar on 2009-03-25
Ubuntu is not for everyone. If you use your computer for windows games why not use windows?

---

### Post by 11010110 on 2009-03-25
Thanks 3rdalbum thats exactly what I was looking for. I just wanted to understand what the problem was. And I love Ubuntu even though I have only been using it for a few months I find it to be much better structured and more stable and not to mention a lot faster than any Windows version that I have ever experienced. I have a dual boot so in the rare cases where I would like to play such games I can easily switch over to Vista and although having the few games i do play from time to time be able to run on ubuntu would be nice, (only becasue booting up windows and using it is much to slow for me) it is not essential to my user experience. 

Thanks for all of the replies and the useful info. This proves yet again that this is truly the best community out there and the support I get here beats anything I ever got from Micro$oft. 

Thanks again

---

### Post by binbash on 2009-03-25
> **pbpersson said:**
> Wine is a Windows emulator, it is attempting to pretend it is a Windows machine running inside Linux.  It has come a long way but it will not run everything.

Let's pretend that Windows is the United States of America and Linux is Japan.  If you travel over to Japan you will be a stranger in a strange land - you will not understand anything that is said to you and no one will understand you.

You take an interpreter with you - but SOME things said in Japanese do not quite translate correctly into English and vice versa.

Does that make sense?  Your Windows programs are strangers in a strange land speaking a foreign computer language to Linux.  Wine is doing the best it can.

**W**ine **I**s **N**ot an **E**mulator

---

### Post by pbpersson on 2009-03-25
> **binbash said:**
> **W**ine **I**s **N**ot an **E**mulator

No, I see it is a translation layer - that makes my little analogy even more accurate.  :)

---

### Post by thehouseofho on 2009-03-25
> **11010110 said:**
> Hi everyone,

I was just wondering why it is that very few good games (the ones I want to use lol) will not work with wine and my Intel chipset. Shouldn't there be a workaround for this? Also if they work with my windows and my Intel chipset so why dont they work with Ununtu? I was just wondering out of curiosity and also to see if there was any way I could get it to work lol.

Thanks a lot in advance everyone!

I find the best workaround for WINE is a Windows VM.  You can download VMWare Server (free), create a Windows VM, install VMWare Tools and you're good to go.  Sure, it does take some time to get it up and running, but once it is up, you can take a snapshot of the image.  This will ensure you always have a backup, just in case anything goes wrong.

It may not be the best solution, but I think it's the best solution at this moment.

---

### Post by 11010110 on 2009-03-25
yes I use vbox ose (similar to vmware) but the only problem with guest OSes is that they tend to have very little to offer in the graphics department and the few games I dabble in tend to be 3D. Until i upgrade to something from System 76 in the future maybe Ill just have to deal with the dual boot lol. thanks everyone for all of your help and all of the replies

---

### Post by thehouseofho on 2009-03-25
I believe VMWare supports 3D acceleration and DirectX on Windows guest OSes.

---

### Post by 11010110 on 2009-03-25
really? that sounds increadible! Everything I have read about guest OSes is that they are limited in that department but maybe i missed something lol. I tried to set up vmware one time but I could not figure it out for the life of me lol. would it be possible for someone to run me through it real quick?

---

### Post by thehouseofho on 2009-03-25
Here's the how-to on enabling accelerated 3D with VMWare.

[http://ubuntuforums.org/showthread.php?t=84344](http://ubuntuforums.org/showthread.php?t=84344)

If you download VMWare Server, you'll just need to un-tar it and run the Perl script located in the installer directory (I think it's in the installar directory).

---

### Post by 11010110 on 2009-03-25
very cool thank you very much this could be just what I need! also is it possible for me to use the virtual disks that I was using with Vbox with vmware?

---

### Post by thehouseofho on 2009-03-25
I'm not sure.  I think VMWare uses proprietary images.  You can always install VMWare Server (or player) first and test.  If you don't want to go through the hassle of creating a VMWare image, you can download a free one from [http://www.thoughtpolice.co.uk/vmware/](http://www.thoughtpolice.co.uk/vmware/) and configure the guest OS as you please.

---

### Post by 11010110 on 2009-03-25
I ran the installer and it told me I had to uninstall the previous one I had on there (probably from my previous meddling with it a month or so ago) and then it says the uninstallation cannot be completed and it wont let me go any further... bummer lol. If i cant get it to work I guess theres no big worries Ill be installing Jaunty on a fresh ext4 partition in a month anyways so i think i can bear it till then lol. Thanks so much for the info in VMware I will definately keep trying or at least use it under jaunty. 

Thanks again everyone

---

