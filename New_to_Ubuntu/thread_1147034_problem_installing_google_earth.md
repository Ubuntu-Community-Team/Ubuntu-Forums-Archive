---
title: "problem installing google earth"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by stef-l on 2009-05-03
I'm new to Linux (ubuntu 8.04) but trying my best! Iwant to install Google Earth. Have tried via medibuntu, via the google earth website, via synaptic. I have not had any error messages, and have a google earth icon in Applications/Internet, but whenever I try & launch the program, I get the small google earth splashscreen, then I'm back to my ubuntu logon and password screen. Nothing else ever happens. And if I try & look for google earth in add/remove programs it's not there!

so - do I have anything installed?

do I have something garbled installed? if so how do I get rid of it?

and how do I get google earth installed?  I have read the community pages and tried the suggestions there really carefully (or so I thought) and this is where I have ended up:(

very grateful for any suggestions

---

### Post by Sef on 2009-05-03
Are you using the 32-bit or 64-bit version?

---

### Post by stef-l on 2009-05-03
I'm afraid I don't know, as I wasn't aware of being offered the choice at any point.  If you tell me where to look to find out I will.  On synaptic the medibuntu offers me both google earth 4.2 and 4.3 but doesn't say anything more than that

Thanks

---

### Post by jespdj on 2009-05-03
Try running Google Earth from a terminal, because error messages might appear in the terminal that can be useful to find out what's wrong.

Open a terminal (Applications > Accessories > Terminal) and enter the command:
```
googleearth
```
Google Earth will probably not work, but copy and paste text that appears in the terminal here.

Note that for Google Earth to work, you must have a graphics card and driver that supports accelerated 3D graphics. What graphics card do you have and what driver are you using? Check with System > Administration > Hardware Drivers if there's a driver for your graphics card available. If there is, enable it (which probably requires rebooting) and try to run Google Earth again.

---

### Post by stef-l on 2009-05-03
When I open the terminal and type in the googleearth command, I get the splash screen and then am logged out of ubuntu and have to login again.  Nothing else happens...

In the hardware drivers screen it just says 'no proprietary drivers are in use on this system' and doesn't offer me any options.

Google Earth used to work fine when I ran Windows XP on my system, if that information is any use.

Also, I've been doing some exploring (not tinkering!) and in my home folder there's a folder called '.googleearth' containing a folder called 'cache' and another file called 'instance-running-lock' which is listed as 'broken'

thanks for suggestions so far...

---

### Post by stef-l on 2009-05-04
well, I'm getting a little more frustrated here, with the lack of suggestions... I've read a lot of other posts on people's issues with google earth and it seems like a nightmare to me - and I'd really been enjoying playing with ubuntu and learning new stuff.  But some of the posts on Absolute Beginner Talk seem to demand a fair level of expertise!  anyhow, can someone out there perhaps tell me how to get all traces of the broken google earth out of my system so that I can at least have a new attempt?

Thanx:(:(:(

---

### Post by oldos2er on 2009-05-04
If you install Google Earth with a package manager, use that package manager again to uninstall. If you installed the *.bin, there should be an uninstall script you can run, /opt/google-earth/uninstall (assuming you installed in /opt).

 Google Earth requires a video card running with 3d hardware acceleration.

---

### Post by lukeinvancouver on 2009-05-30
> **oldos2er said:**
> If you install Google Earth with a package manager, use that package manager again to uninstall. If you installed the *.bin, there should be an uninstall script you can run, /opt/google-earth/uninstall (assuming you installed in /opt).

 Google Earth requires a video card running with 3d hardware acceleration.

I am at an even "more beginner" level. I downloaded Google Earth and saved the bin file.

Dumb question: How do I install it?

P.S. My video is integrated in the cheap Intel Atom board. Would that be a problem (assuming I'll succeed in installing it)?

Thank you in advance oldos2er. You've helped me before and might again.

Cheers.

P.P.S. I AM making enormous progress though and "that little cheap machine" is fast becoming My Star of the house. I AM making the transition to Linux, finally.

---

### Post by oldos2er on 2009-05-30
> **lukeinvancouver said:**
> I am at an even "more beginner" level. I downloaded Google Earth and saved the bin file.

Dumb question: How do I install it?

P.S. My video is integrated in the cheap Intel Atom board. Would that be a problem (assuming I'll succeed in installing it)?

Thank you in advance oldos2er. You've helped me before and might again.

Cheers.

P.P.S. I AM making enormous progress though and "that little cheap machine" is fast becoming My Star of the house. I AM making the transition to Linux, finally.

 If the file is on your desktop, run these commands in a terminal, one at a time:
```
cd Desktop
chmod a+x GoogleEarthLinux.bin
sudo ./GoogleEarthLinux.bin
```

 Is there Intel video on the Intel Atom board you have? There are issues with some Intel video adapters running Ubuntu 9.04, so I don't know if Google Earth is going to work for you or not.

---

### Post by jman5555 on 2009-05-30
Yeah it sounds like it is a graphics card problem not a "google earth" problem. Are you running an older computer? If so you might be out of luck. Gettings the proper kernels installed can be some what of problem. If you do any more searches I would be searching for your graphics card's compatibility with linux.

---

### Post by lukeinvancouver on 2009-05-31
> **oldos2er said:**
> If the file is on your desktop, run these commands in a terminal, one at a time:
```
cd Desktop
chmod a+x GoogleEarthLinux.bin
sudo ./GoogleEarthLinux.bin
```

 Is there Intel video on the Intel Atom board you have? There are issues with some Intel video adapters running Ubuntu 9.04, so I don't know if Google Earth is going to work for you or not.

Thank you for your help. 
:)

Following your instructions I managed to install it but there must be a problem with the video adapter. (I **assume** it is an Intel adapter since the MB is made by Intel and the video is integrated.) It loads very sluggishly and reacts to commands only after a long delay. In other words, it's one program that does not work with my computer.

---

### Post by lukeinvancouver on 2009-05-31
If I may add another 'complication' it would be this:

I have one PCI expansion slot and I can't decide what it should be used for.

I was leaning towards a video capture card.

Should I go for a graphics card instead and disable (not that I know how) the built in graphics adapter?

The machine only cost CAD 300.- (excluding monitor) and is kind of an experiment.

So far Ubuntu is beating everything else.

Yeeehaw!

Maybe some day I'll use an 'expensive' machine to run Ubuntu but it doesn't seem necessary.

All this is a wonderful learning experience for an old man, who has learned other things before.

Thanks.

---

