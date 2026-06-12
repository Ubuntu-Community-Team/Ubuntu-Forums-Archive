---
title: "HELP too stuck"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by blastbar on 2009-05-20
i got to here and got completely stuck i have no idea what to do next and as far as i can tell there's no way to continue from that screen

   thanks for any replies

---

### Post by Mornedhel on 2009-05-20
It's asking you to accept the EULA. Press TAB until the <OK> button is highlighted, then press ENTER.

Some packages have an interactive installation procedure, mostly when you need to configure something or agree to a non-free EULA.

---

### Post by Game Over on 2009-05-20
Hey. Um... could you be more specific about how you got here and what versions of software / hardware you are using?

From the looks of it, try...

Menu > Add/Remove... > Show: All Available > Search: Java

You should be able to find the plug in, maybe?

---

### Post by blastbar on 2009-05-20
thank you sooooooo much for the tab idea i think i would have been there forever everything seems to be working fine.....until i break it again    really nice to be a member of this forum everyone seems glad to help and quick to respond
  Josh Cook

---

### Post by blastbar on 2009-05-20
mostly sorted out now i think       any tips on which program i need 2 install to be able to install amsn?   this is all i get atm

---

### Post by Mornedhel on 2009-05-20
Can't you install amsn from the repository ? (Using the same method you've been using so far to install java.)

I should also point out that Pidgin, the IM client that comes installed by default in Ubuntu, can be used to connect to an MSN account, although videoconferencing is not supported.

---

### Post by blastbar on 2009-05-20
the videoconferencing is the only reason i dont use pidgin, i also installed emesene and no one else can send or receive webcam either, but they are on windows so that might block it or something    i don't know its all too confusing  but i will try installing like the others again and post back here with the result  thanks again

---

### Post by blastbar on 2009-05-20
still stuck   god i'm useless        i can download the file but now i get this

 [/home/cook/Desktop/aMSN-0.97.2-tcl85-windows-installer.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/cook/Desktop/aMSN-0.97.2-tcl85-windows-installer.exe or
          /home/cook/Desktop/aMSN-0.97.2-tcl85-windows-installer.exe.zip, and cannot find /home/cook/Desktop/aMSN-0.97.2-tcl85-windows-installer.exe.ZIP, period.

---

### Post by Mornedhel on 2009-05-20
You're trying to install the Windows version of amsn. This will not work unless you install a special compatibility layer for Windows applications called WINE, but this is another subject and not the best method for getting amsn to run.

When you have the time, please read one of the stickies in this forum concerning the installation of software in Ubuntu : [http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404).

Meanwhile, for a quick fix, just open a terminal (Applications > Accessories > Terminal) and run the following command :

```
sudo apt-get install amsn
```

Enter your password when prompted. This will download and install amsn from the Ubuntu software repositories.

---

### Post by Random-penguin on 2009-05-20
Try installing from synaptic (found under system > administration on the tool bar), it will install the latest Ubuntu compatible version.

I'm not sure of your Linux experience (so please don't take offense!), but the best place to install Linux software is using Synaptic. The following link may prove helpful:

[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

[https://help.ubuntu.com/community](https://help.ubuntu.com/community)

Best of luck :D

---

### Post by MontelEdwards on 2009-05-20
Hmm, i see you dont use a CLI a lot.
Well all you do is press the tab button on your keyboard :]
oh, and like FYI when you're in another CLI and you see check boxes, the toggle is the space bar. just a little info;)

---

### Post by blastbar on 2009-05-21
thank you for your replies and links  all very new to me i will definitely read through the info suggested and try out all this stuff =]

---

### Post by blastbar on 2009-05-21
sorry about this, but i have another dopey question
 i'm running ubuntu 9.04 desktop and i have no mouse, Ctrl makes the circley thing around it but it is getting a bit annoying having to constantly press it, i have researched this n the only way i can find of fixing this is with virtualbox, but is there another way??

---

### Post by blastbar on 2009-06-01
hiya yeah more problems now when ever i put anything in teminal i get this:
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

 any help?

---

### Post by LewRockwell on 2009-06-01
do you need to use virtualbox?

---

### Post by MontelEdwards on 2009-06-01
> **blastbar said:**
> hiya yeah more problems now when ever i put anything in teminal i get this:
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

 any help?
It looks like you either have another packaging program running like Synaptic or something.
You need to close that first.

---

