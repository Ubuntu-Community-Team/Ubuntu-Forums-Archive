---
title: "Printers"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by som1special2 on 2009-08-18
I recently purchased a new printer that did not work with Ubuntu 9.04. I bought an Epson Stylus NX300 and also use a Canon MP190. Both printers work fine, but the scanners don't. I started using windows vista and now have virus problems galore and can't get anything to work. I HATE windows. I want to know if there are ANY LINUX distro's out there that would run either one of these two printers out of the box. Any help is greatly appreciated.

---

### Post by mgmiller on 2009-08-18
I looked up both of your scanners in the sane database:
[http://www.sane-project.org/cgi-bin/driver.pl](http://www.sane-project.org/cgi-bin/driver.pl)

And they are both supported.  The Canon for quite a long time, the Epson since version 1.0.19.

Assuming you are running Ubuntu 9.04, they should both work.

1) Make sure they are plugged into a working USB port.
2) Turn on the scanner.
3) Run xsane  (Applications > Graphics > xsane)

This is the standard scanner application in Ubuntu.

It should detect the scanner and start right up.

Note, the scanner MUST be turned on before starting xsane, or it won't work.

Good Luck.

---

### Post by Dark Aspect on 2009-08-18
Let me google that for you [here]("http://lmgtfy.com/?q=Epson+Stylus+NX300+Ubuntu") and [here]("http://lmgtfy.com/?q=Canon+MP190+Ubuntu"). More specifically the [Canon MP190 drivers are here]("http://software.canon-europe.com/products/0010639.asp").

---

### Post by mgmiller on 2009-08-18
That's a very useful link for the canon.  They actually supply .deb's.  If he chooses that route, he should install the common file first, then the mp190 series file.

This will install scangear, which will need to be run from a terminal. 
```
scangearamp
```
Later he can create a menu entry for it.

Theoretically, this should not be needed as I believe both scanners are natively supported and should run in xsane without doing anything else.

---

### Post by som1special2 on 2009-08-18
this does not work. I am completely in the dark on all this.

---

### Post by som1special2 on 2009-08-18
don know how to install tar.gz ????

---

### Post by mgmiller on 2009-08-18
I tried downloading the file from the canon link and it was a .tar, not a .tar.gz.

If you right click it and select "extract here". it will create a folder called mp190 debian drivers.  In there are 2 more .tar files  You want the one that says mp190_debian_scangear.tar

Again just right click it and tell it extract here and you will have a folder called mp190_debian_scangear containing 3 files.

You can ignore the file ending in .tar.gz.  It is a more generic linux install file that you don't need here because they were nice enough to give you .deb's.

You want to install the one called "scangearmp-common_1.20-1_i386.deb" first, then the one called "scangearmp-mp190series_1.20-1_i386.deb"

These files end in .deb and are installed by simple double click.  Just follow the prompts and click the "Install Package" button when it's presented.  It will ask you for a password, just use your regular log in password.

After both packages are installed, open a terminal (Applications > Accessories > Terminal)  and try typing:
```
scangearamp
```and hit enter.

Again, the scanner must be turned on before you run the program.

If all works well, you can make a nice entry in your menu system for this.

I am surprised xsane does not work.  It should.  What happens when you run that?

---

### Post by som1special2 on 2009-08-19
I have the canon at my shop and will try it later as I have installed the items you helped with. I am more concerned about the epson and when I try to start xsane it says:
failed to open device 'v4l:/dev/video0' invalid argument.

---

### Post by mgmiller on 2009-08-19
> when I try to start xsane it says:
failed to open device 'v4l:/dev/video0' invalid argument.

It sounds like xsane is seeing a tv tuner card or other video capture card in the system.  I get the same message on my system if the scanner is not turned on.

Make sure the power is on at the multifunction machine and it has been placed in scanner mode.  By default, when you power it on, it's only a printer until you tell it to be a scanner.  Somewhere on it is a button to place it in scanner mode.

Another thing to try, if the above is not successful,  is to try running xsane as root.  Open a terminal and type:
```
gksu xsane
```
Give it your password.

Or if you are using the scangear method, try:
```
gksu scangearamp
```
Give it your password.

If it works, then you have a permissions problem with your groups.  This used to happen in some of the older versions of Ubuntu up through maybe 7.10 or 8.04.  

This is especially true if you are using the scangear softwear.  There is a fix for this, but we don't need to use it until I know you have the problem.

Which version of ubuntu are you running.

---

### Post by mgmiller on 2009-08-19
I just thought of something else that the scangear install needed.  My son has a canon multifunction that we needed to get going a while back.  At that time, I also had to install the package libpng3 for the scangear software to work correctly.
```
sudo apt-get install libpng3
```I believe the right way was to install that first, then the other 2 .debs you got from canon.  This was a few years ago and Canon did not supply a .deb, I had to build one from a .rpm file they provided, so it may have missed the dependency as a result.

Theoretically, if they supplied the .deb, it should satisfy the dependency for libpng3 if it needs it.  It should even tell you that it's going to install it if it's needed.

I'm curious, let me know.

---

### Post by som1special2 on 2009-08-19
running new install of 9.04, (not an update) tried to run gksu with no effect. no scangear and now i am not sure I got the common files for canon in there...

---

### Post by mgmiller on 2009-08-19
Did you download and extract the files from the canon site?

Do you have the 2 .deb files I referred to earlier?

Did you try installing them?

---

### Post by som1special2 on 2009-08-19
nope, still says invalid argument in xsane and does not pull up scangear. Have any clue about the epson? There isn't a scan function button on it. I appreciate the help you are giving me!

---

### Post by mgmiller on 2009-08-19
For the canon scanner:
Have you installed the 2 .deb files?
What happens when you run 
```
scangearamp
```in a terminal?

What about:
```
gksu scangearamp
```
in a terminal?

scangear is a proprietary scanner interface from canon.  It looks nothing like xsane and is run from its own command.

I have rechecked the sane database and the mp190 is definitely in the current version that you are running.

It really should work with xsane.

For the epson scanner:
I looked again at the sane database and it is not in the current version 1.0.19, it is in the upcoming version 1.0.21.  I can't find the list for the about to be released version 1.0.20.

Confused yet?

Ubuntu 9.04 uses 1.0.19 which does not support the epson.
Ubuntu 9.10 uses 1.0.20 which "might" support it.
Ubuntu 10.04 will use 1.0.21 which does support it.


You can try downloading a live CD for the alpha version of 9.10 and see if both of the the scanners work with xsane there.

I have a Fujitsu scanner that works very well in the live cd for 9.10, but does not work at all in the current 9.04.

Some times patience is a virtue.

---

### Post by mgmiller on 2009-08-19
Here is a link to the sane scanner driver for the canon.  If you are still having issues after trying the liveCD, maybe you can contact the developer of the driver.  His email address is on the site:

[http://home.arcor.de/wittawat/pixma/](http://home.arcor.de/wittawat/pixma/)

---

### Post by som1special2 on 2009-08-19
tried everything twice, no good. I got 9.10 and the canon works native. I did notice the other option in xsane is my camera which is embedded in the laptop. I never had a problem before with it; but I noticed the error message I sent to you the last time was an error for the camera! does that make any difference? I am looking at some other distro's, any suggestions?

---

### Post by mgmiller on 2009-08-20
It looks like the easiest course for the canon will be to use 9.10 which comes out in October.  Once the beta is released in early October, you could work with that.  It will get automatically upgraded right along till it becomes the final version by the end of the month.  There will be many updates and an occaisional breakage, but I find the betas to be pretty stable overall.  I installed the beta of 8.04 on 5 machines in my office at work in early April, 2008 and have been using it since then with no problems.  It's the LTS version, so it has upgraded itself to 8.04.3.  I won't be upgrading it beyond 8.04.x till the next LTS version comes out in April, 2010.

The camera error message is not critical, as xsane seems to try to use video devices, even though it can't.  Try installing a camera utility like cheese:
```
sudo apt-get install cheese
``` And see if it works with your camera.  Not all will.  Some camera chipsets don't have Linux support.

As far as other distros go, if they are using the same version of sane, I don't think you will get any better results.  That being said, some popular ones are Linux-mint which is sort of Ubuntu based, but has lots of stuff already installed.  Many people report hardware works there when it doesn't work in Ubuntu.  The main one is KDE based, but there is a gnome version out there somewhere, so be sure to get the one you want.  Ubuntu uses Gnome, so if you are happy with that, find the gnome version of mint.

You could also try live cd's of kubuntu (the KDE version of Ubuntu), it may impliment hardware detection a little differently.

There is also fedora which is redhat based and openSUSE which is very popular.

Take a look at distrowatch:
[http://distrowatch.com/](http://distrowatch.com/)

There is a page hit ranking low on the right side, that gives a sort of "popularity rating" for different distros.

The beauty of Linux is that you can try all these as live cd's to see which works best for you.

Of course, I'm partial to Ubuntu because of the great forum.

---

### Post by som1special2 on 2009-08-21
how, in detail can one upgrade SANE? thank you so very much for all your help!

---

### Post by coldReactive on 2009-08-21
> **som1special2 said:**
> how, in detail can one upgrade SANE? thank you so very much for all your help!

You're going to have a field day with terminal however.

[http://ubuntuforums.org/showpost.php?p=7497237&postcount=6](http://ubuntuforums.org/showpost.php?p=7497237&postcount=6)

After this, your MP190 will require root usage of xsane:

```
gksudo xsane
```

There is no way to get it not to do root at this time, as the PIXMA Scanner won't give us its usb bus, and only gives the device ID.

---

