---
title: "Can the features of a Tablet PC work on Ubuntu Linux?"
date: 2009-12-26
forum: New to Ubuntu
---

### Post by jrozo17 on 2009-12-26
Right now I'm running Linux on a Tablet PC laptop, and Im curious if I can "enable" the touchscreen?

I dont HAVE to have it, but itd be nice to put it to use. Is this possible on Ubuntu 9.10?

---

### Post by cartisdm on 2009-12-26
This person [here]("http://john-main.blogspot.com/2008/06/getting-tablet-pc-touchscreen-working.html") wrote a guide that he says should cover most tablets.  From what I found getting the touch feature on tablets is a little finicky in ubuntu and running updates can sometimes break it...

---

### Post by Favux on 2009-12-26
Hi jrozo17,

Sure you can get most tablet pc's working in Karmic.  We need to know the brandname and model you have.

Not strictly necessary but it also helps if you know which touchscreen/digitizer you have.  For example Wacom, N-trig, UMPC, etc.  Also whether it is serial or usb in its internal connection, but .

---

### Post by jrozo17 on 2009-12-27
> **Favux said:**
> Hi jrozo17,

Sure you can get most tablet pc's working in Karmic.  We need to know the brandname and model you have.

Not strictly necessary but it also helps if you know which touchscreen/digitizer you have.  For example Wacom, N-trig, UMPC, etc.  Also whether it is serial or usb in its internal connection, but .


Sure thing Favux. :)

I have a Gateway CX2724 laptop.. although i cant find what the name of the touchscreen is :(

---

### Post by Favux on 2009-12-27
Hi jrozo17,

It has a serial Finepoint digitizer.  First before you do anything else run this command in a terminal:
```
dmesg | grep ttyS
```
or maybe:
```
sudo dmesg | grep ttyS
```
What we want to see and preserve is output that looks something like:
```
serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
```

Once we have that you can install the driver which is called 'fpit' (xserver-xorg-input-fpit) through Synaptic Package Manager.  Then reboot.

So far we haven't figured out how to install it through a fpit.fdi (device information file) and have had to revert back to the xorg.conf.  Unless you want to experiment with developing a .fdi that's what we'll do.

---

### Post by jrozo17 on 2009-12-27
> **Favux said:**
> Hi jrozo17,

It has a serial Finepoint digitizer.  First before you do anything else run this command in a terminal:
```
dmesg | grep ttyS
```or maybe:
```
sudo dmesg | grep ttyS
```What we want to see and preserve is output that looks something like:
```
serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
```Once we have that you can install the driver which is called 'fpit' (xserver-xorg-input-fpit) through Synaptic Package Manager.  Then reboot.

So far we haven't figured out how to install it through a fpit.fdi (device information file) and have had to revert back to the xorg.conf.  Unless you want to experiment with developing a .fdi that's what we'll do.


Ok so following the directions you just gave me, should it work? Or is there more to it that your gonna tell me?

Im just makin sure so i dont get confused.. you know how us linux noobs are :lolflag:

---

### Post by Favux on 2009-12-27
Hi jrozo17,

There's more.  It depends on what you want to do.  Try to come up with a .fdi file or use the proven xorg.conf method which requires other stuff to be setup along with the xorg.conf.

---

### Post by jrozo17 on 2009-12-27
> **Favux said:**
> Hi jrozo17,

There's more.  It depends on what you want to do.  Try to come up with a .fdi file or use the proven xorg.conf method which requires other stuff to be setup along with the xorg.conf.

I have no idea what those file extensions mean or how to do it. :confused: If its gonna be pretty complicated then I wont worry about it, its not necessarily the #1 thing on my mind.. but i do appreciate all the help i can get. :)

---

### Post by Favux on 2009-12-27
Hi jrozo17,

Well complicated is a relative term.  We're talking about 10 to 40 minutes depending on how quickly you "get it".  It's pretty straight forward to edit the 4 files you'll need to change for the xorg.conf method which it sounds like is the way you prefer to go.  Have you done the other stuff yet?

---

### Post by jrozo17 on 2009-12-27
> **Favux said:**
> Hi jrozo17,

Well complicated is a relative term.  We're talking about 10 to 40 minutes depending on how quickly you "get it".  It's pretty straight forward to edit the 4 files you'll need to change for the xorg.conf method which it sounds like is the way you prefer to go.  Have you done the other stuff yet?

Okay that sounds perfect. Just as long as you guide me through, id appreciate it. I installed the thing through Synaptic Manager like you said. Whats next?

---

### Post by Favux on 2009-12-27
What was in "dmesg | grep ttyS" before you installed fpit?  Or if you didn't do it try it now.

---

### Post by jrozo17 on 2009-12-27
> **Favux said:**
> What was in "dmesg | grep ttyS" before you installed fpit?  Or if you didn't do it try it now.

It said 

0.920952] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A


just like you said it should..

---

### Post by Favux on 2009-12-27
Hi jrozo17,

OK, to look at xorg.conf in a terminal enter:
```
gedit /etc/X11/xorg.conf
```
gedit is the text editor.  The path to the xorg.conf file is "/etc/X11/xorg.conf".  Copy the contents of xorg.conf and post it.  You can use the code tags (# in upper right) to "box" what you copy and paste.

To edit a file use:
```
gksudo gedit /etc/X11//xorg.conf
```
sudo or gksudo make you root/super user.  You use gksudo when using a graphical program like gedit (text editor).  Be careful when root.  It allows you to make changes to system files so you only want to do what you need to and then Save and Close so you don't inadvertantly change something else.

Now you need to follow the instructions in "Setting up configuration files" here:  [https://help.ubuntu.com/community/FujitsuStylus](https://help.ubuntu.com/community/FujitsuStylus)  Read it through a couple of times so you know what you want to do.

Except you want to tailor the line to your output, so use this one:
```
/dev/ttyS0 port 0x3f8 uart 16954 irq 4 baud_base 38400
```
instead of the one they show.

Meanwhile I'll write your xorg.conf.

---

### Post by jrozo17 on 2009-12-27
> **Favux said:**
> Hi jrozo17,

OK, to look at xorg.conf in a terminal enter:
```
gedit /etc/X11/xorg.conf
```gedit is the text editor.  The path to the xorg.conf file is "/etc/X11/xorg.conf".  Copy the contents of xorg.conf and post it.  You can use the code tags (# in upper right) to "box" what you copy and paste.

To edit a file use:
```
gksudo gedit /etc/X11//xorg.conf
```sudo or gksudo make you root/super user.  You use gksudo when using a graphical program like gedit (text editor).  Be careful when root.  It allows you to make changes to system files so you only want to do what you need to and then Save and Close so you don't inadvertantly change something else.

Now you need to follow the instructions in "Setting up configuration files" here:  [https://help.ubuntu.com/community/FujitsuStylus](https://help.ubuntu.com/community/FujitsuStylus)  Read it through a couple of times so you know what you want to do.

Except you want to tailor the line to your output, so use this one:
```
/dev/ttyS0 port 0x3f8 uart 16954 irq 4 baud_base 38400
```instead of the one they show.

Meanwhile I'll write your xorg.conf.


So you're writing the xorg.conf file, and then when your done, ill do all of this right?

---

### Post by Favux on 2009-12-27
Hi,

No, I need you to post your current xorg.conf and then you can do the other stuff.

---

### Post by jrozo17 on 2009-12-27
> **Favux said:**
> Hi,

No, I need you to post your current xorg.conf and then you can do the other stuff.

I tried all the codes and its just blank. I'll attach a snapshot instead.

---

### Post by Favux on 2009-12-27
Hi Hi jrozo17,

OK, that's normal now with Karmic.  Unless you have a Nvidia video card/chipset.  So go ahead and follow the FujitsuStylus instructions.  Ask if you have questions.

---

### Post by Favux on 2009-12-27
Hi Hi jrozo17,

Alright.  If you had a xorg.conf you would back it up using the cp (copy) command like:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
And then if X didn't start (the xorg.conf broke it) so your gui (graphical user interface) i.e. Desktop didn't start what you would do is restore it from the command line interface (CLI i.e. terminal) by reversing it:
```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```
Since it isn't there right now you would use the mv (move) command to rename it like so:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
So when you reboot it would be called xorg.conf.bak and wouldn't be read by the system.

Attached to the bottom of the post is the xorg.conf.  Click on it to download.  Open the download in text editor (right click on it).  Open/create your xorg.conf with the root command I showed you before:
```
gksudo gedit /etc/X11/xorg.conf
```
Copy & paste the entire contents of the downloaded one into the root gedit.  Save, Close, reboot and the digitizer should work.

If we're lucky.  :)

---

### Post by redxine on 2010-01-03
Hey!
I've been running Intrepid on my Gateway CX210X this whole time because the tablet broke when I tried to upgrade, but this thread gives me hope! I'll have to make room and put Karmic in a new partition or on an external drive and try this out. Has anyone else had a problem with X on shutdown with this configuration? Whenever X11 is killed (and the tablet is configured in xorg.conf) the display goes haywire and displays several interlaced frames, often with corrupt cursor where the pointer used to be.

---

### Post by fachex on 2010-05-03
Everything was working for me in my Gateway CX200x until Lucid Lynx :( Broken dependencies for xorg-fpit drivers...

---

### Post by redxine on 2010-05-03
Same problem here. A bug has been filed and is in the works.

---

### Post by Favux on 2010-05-03
Yes.  I don't know if fpit has been updated/patched to work with the new 1.7 Xserver in Lucid.  I can't find it if it has.  So follow the bug report.  Redxine could you link it?

---

### Post by redxine on 2010-05-03
Doesn't look like it's completely done for - this has happened before and a patch had fixed it.

---

### Post by Favux on 2010-05-03
Here's the link to the bug report so you can monitor it:  [https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-input-fpit/+bug/565540](https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-input-fpit/+bug/565540)

---

### Post by fachex on 2010-05-04
Well, here is the source code for the fpit driver if any genius dares to fix it
[http://packages.debian.org/source/sid/xserver-xorg-input-fpit](http://packages.debian.org/source/sid/xserver-xorg-input-fpit)

---

### Post by fachex on 2010-05-05
Ok, the fpit drivers appears to be working and the solution for this is found [here]("https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates"). But I can't make my stylus or my screen to work still. Everything seems to be working fine. All the setserial stuff show to be working properly, the xorg.conf was the one I was using in Karmic (may be that's the problem). I don't know what else to do. How do I check if the system is actually using the new updated fpit driver? I will appreciate any input at this point that would help me to have my tablet pc fully working.
Fabian

---

### Post by bornagainlinux on 2010-05-14
Hi fachex,

I have a couple of questions for you. I also have a Gateway CX200X, and I am having a problem with the tablet. I just recently upgraded from 9.10 to 10.04. I have the latest fpit driver from launchpad.net. Setup /etc/X11/xorg.conf. And it basically works except the tracking is off. The tracking works fine up and down. Left and right it is off. On the far let it is fine, but the more you move right the farther away to the right it moves. At about a third of the way right the mouse pointer is half way. At half way right the mouse pointer is about 4/5ths of the way right. I already tried adjusting the max X but it does not seem to make any change.

Any thoughts? 

Thank you in advance.

Don

---

### Post by redxine on 2010-05-14
I have the same problem, and filed a bug here: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-fpit/+bug/576677](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-fpit/+bug/576677)

---

### Post by bornagainlinux on 2010-05-14
Thanks fachex,

I thought I was doing something wrong and lost my trouble shooting skills. LOL That makes sense because I even tried to calculate the aspect ratio and was coming up right there. So a bug in the fpit driver itself. Anyone else having this problem? And what about the right-click? Is that a separate bug? 

Thanks! I am pretty excited about getting it to work. I really do not like Windows and I am telling everyone that complains about Windows about Ubuntu! 

Don

---

### Post by bornagainlinux on 2010-05-25
Greetings all!

Good news. The latest fpit driver at launchpad.net seems to be working and the stylus tracking is much better. Download it at [https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/+packages?field.name_filter=&field.status_filter=published&field.series_filter=lucid ]("https://edge.launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/+packages?field.name_filter=&field.status_filter=published&field.series_filter=lucid")

The bad news is that at least for me, the click no longer seems to work.

Hope this helps anyone! And thanks for the help! 

Don

---

