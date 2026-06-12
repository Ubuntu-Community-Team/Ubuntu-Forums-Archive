---
title: "Help with converting media"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by 289531.EXE on 2009-09-15
Can anyone help?

When i put a music cd in my  computer  and drag the  files onto my desktop they come out as .wav format.

how can i  convert thes files into .mp3 format?

can anyone help?

---

### Post by 73ckn797 on 2009-09-15
> **289531.EXE said:**
> Can anyone help?

When i put a music cd in my  computer  and drag the  files onto my desktop they come out as .wav format.

how can i  convert thes files into .mp3 format?

can anyone help?

Look in the repositories and you will find "sound converter". That will probably do the trick.

---

### Post by scratman on 2009-09-15
As the wav files are already on your desktop, WinFF may be easier for you.  It can convert between dozens of file formats, both audio and video, and even grab audio from video clips.  It's not exactly required for your current needs, but is a very useful tool.

---

### Post by 289531.EXE on 2009-09-15
ok,where are the repositories and/or how do i get winff?

---

### Post by Darkwing-Duck on 2009-09-15
For information on the repositories you can look at this page. 
 
_[COLOR=#800080][https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)[/COLOR]_[]("https://help.ubuntu.com/community/Repositories")
 
Go to System > Administration > Software Sourses
 
Under the Ubuntu Software tab check the box that says Universe.
 
Close the window and close out anything Synaptic.
 
Go to your terminal and follow along for the ride :)
 
sudo apt-get update
 
sudo apt-get install winff
 
[http://packages.ubuntu.com](http://packages.ubuntu.com) is a good place to search for what a package is called and what repositories they are in. The following link will give you what you need to know about WinFF.
 
[http://packages.ubuntu.com/jaunty/winff](http://packages.ubuntu.com/jaunty/winff)
 
If you need any more help please let us know!

---

### Post by 73ckn797 on 2009-09-15
The GUI way is to add the universe repo's from System/Administration/Software Sources. You will be asked to "reload".
Then go to System/Administration/Synaptic Package Manager. There you should then find "winff" and "sound-converter". Right click on the name  of the program then select install.

---

### Post by majiciannz on 2009-09-15
If you want to rip a cd directly to mp3 you can do that with "audio cd extractor".

Go to Applications>Add/Remove
Make sure you have under "Show" "All available applications"
Select "Sound and Video"
Look for "Audio CD Extractor"
Tick the box and install it.

Once installed, load a cd and in preferences select mp3 and the destination folder.
It's fast and easy to use.

Hope this helps

---

### Post by andrew.46 on 2009-09-16
Hi 289531,

> **289531.EXE said:**
> 
When i put a music cd in my  computer  and drag the  files onto my desktop they come out as .wav format.

how can i  convert these files into .mp3 format?

An excellent starting point is here:

CDRipping - Community Ubuntu Documentation
[https://help.ubuntu.com/community/CDRipping](https://help.ubuntu.com/community/CDRipping)

All the best with this,

Andrew

---

