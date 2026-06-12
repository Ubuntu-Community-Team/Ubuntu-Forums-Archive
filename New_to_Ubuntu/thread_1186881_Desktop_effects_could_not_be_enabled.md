---
title: "Desktop effects could not be enabled"
date: 2009-06-13
forum: New to Ubuntu
---

### Post by JoeNZ on 2009-06-13
Hello from NZ,

On the Visual Effects tab, it is set to 'none'. When I go to change it to 'normal' or 'extra', it comes up with this error message:

Desktop effects could not be enabled

I am running an Ati Radeon 9250 with 128mb.

Am I doing something wrong? Have I not enabled/installed something I should have? Or is this graphics card not supported in Ubuntu?

Thank you in advance for any help.

Regards
JoeNZ

---

### Post by QIII on 2009-06-13
Go to System -> Administration -> Hardware Drivers

Is the ATI/AMD proprietary driver enabled?

(Enable it for now, although there is an open source driver available).

See if that works.  I'm not sure if the open source driver works well with Advanced settings.

Also, ATI has a new driver you can download and install, but maybe that is a task for another day.

---

### Post by JoeNZ on 2009-06-13
I went to *System -> Administration -> Hardware Drivers* and it listed nothing. I have just gone to the ATI website and it lists 2 packages:

XFree86 4.3
X.Org 6.8 

Should I install both?

---

### Post by QIII on 2009-06-14
Don't do anything with those yet.

Give me a moment.  It'll take me a minute to figure out how to get at that ATI driver.

---

### Post by QIII on 2009-06-14
Go to System -> Administration -> Software Sources.

See if "Proprietary Drivers for Devices" is checked.

---

### Post by JoeNZ on 2009-06-14
Yes it is checked.

---

### Post by QIII on 2009-06-14
OK.  Understand that I am going to help you install proprietary drivers that are available in the Ubuntu restricted repository.  At some point in the future, you will probably want to install a better solution from ATI, but we need to get you up and running and familiar with Ubuntu before we launch into that.

So.

Go to System -> Administration -> Synaptic Package Manager.

You will be asked for a password.  That's just the one you use to sign in with.

At the top, you will see a "Search" text box.  Type the letters ATI there.

It should give you a list of a whole bunch of things.

Look in the description column for

X.Org X server -- ATI display driver wrapper
and
X.Org X server -- ATI Radeon display driver

Check those two boxes.

The "Apply" button should now be enabled.

Click Apply and say yes when it asks you if you are sure.

You may get a big, long list of other things that will be applied.  That is normal.  All the dependencies will be applied.

When it is done downloading and applying the changes, give me a "thumbs up" and we'll go from there.

---

### Post by JoeNZ on 2009-06-14
Done. Thumbs up.

---

### Post by eternalnewbee on 2009-06-14
In Add/Remove Applications there are some ATI drivers, although I'm not sure they are useful or not, as I use Geforce.

---

### Post by QIII on 2009-06-14
eternalnewbee -- Oh.  I'd forgotten about that.  No problem.  They'll be added to the list when we get done, anyway.

---

### Post by QIII on 2009-06-14
OK, Joe --

Next step.  Is there any data you really do not want to lose if something goes horribly wrong in a big hurry?  Are you dual booting Windows and Ubuntu or anything like that?

---

### Post by eternalnewbee on 2009-06-14
Good luck.

---

### Post by JoeNZ on 2009-06-14
No not really, just a bunch of music, some avi's etc. Nothing important. Also, no dual-boot here. Windows XP is on the laptop.

---

### Post by JoeNZ on 2009-06-14
Thanks eternalnewbee.

---

### Post by QIII on 2009-06-14
Go back toSystem -> Administration -> Hardware Drivers and see if the ATI/AMD proprietary driver shows up now.

---

### Post by JoeNZ on 2009-06-14
No still nothing.

---

### Post by eternalnewbee on 2009-06-14
Try restarting your system first.

---

### Post by QIII on 2009-06-14
Interesting.

Go to Applications -> Add/Remove

In the Search box, type ATI Driver.

One of the first hits should be ATI binary X.Org driver.

See if that is checked.  That's the 2D, but for the Advance effects we need to get you the 3D.

---

### Post by JoeNZ on 2009-06-14
Eternalnewbee. I restarted my system and still nothing.

---

### Post by JoeNZ on 2009-06-14
Yes the first hit is the ATI binary X.Org driver, but it is not enabled. To start with, should I install that?

---

### Post by JoeNZ on 2009-06-14
I have installed the ATI binary X.Org driver if that helps?

---

### Post by eternalnewbee on 2009-06-14
Go to System > Administration > Hardware Drivers, and see if the Driver is there.

---

### Post by JoeNZ on 2009-06-14
Apologies for not replying sooner. At the same time i was doing this thread, I was also doing this thread [http://ubuntuforums.org/showthread.php?t=1186894](http://ubuntuforums.org/showthread.php?t=1186894).

This was the last post from myself - *"HELP. I am now typing this from our laptop running XP. I installed the Kubuntu desktop package through Synaptic, it went through it's motions and so I restarted the system. It got past the boot screen and that's it, I am now staring at a black screen."*

Are these two threads associated?

---

### Post by QIII on 2009-06-14
Sorry so long to get back.  This may be a bit delayed since we are on opposite sides of the Date Line.    

Can you run the LiveCD without problems?

---

### Post by JoeNZ on 2009-06-15
I installed the ATI driver through Add/Remove, restarted the machine and got the blank screen. I found through google the command *apt-get remove xorg-driver-fglrx* that I executed in recovery mode which enabled me to get back to the desktop.
Since then, I found on another thread the command *lspci | grep VGA* which gave me this result:

01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)

Does this help at all?

I have downloaded the official ATI graphics driver but when I followed their install instructions with this command[FONT=verdana][SIZE=2]* sh ./ati-driver-installer-8.28.8.run*[/SIZE][/FONT] , I got this error:

Detected configuration:
Architecture: i686 (32-bit)
**X Server: unable to detect**
Removing temporary directory: fglrx-install

I have even tried running this command *sudo apt-get install xorg-driver-fglrx* but when i restart the machine I get the blank screen again.

Scratching my head a little bit now.

---

### Post by QIII on 2009-06-15
I'm scratching, too.

OK.

There are two branches we can take.

One of them might be painful, and it depends on how much you have done on the machine and if you have anything saved that you don't want to lose.  But we'll try the easiest first.

The first option to try is to just get the fglrx driver back.  That is a problematic driver.  If you search the forum, you will find all sorts of complaints about it.  It also means you will probably not be able to use the fancy desktop effects, but you can use Compiz.

sudo apt-get install --reinstall xorg-driver-fglrx

If that doesn't work, we may have to fall back to the worst-case scenario.

Reinsert your LiveCD.  Poke around a bit and see if things work the way you think they should.  If so, then (sorry) a new install may be in order.

---

### Post by JoeNZ on 2009-06-16
Unfortunately *sudo apt-get install --reinstall xorg-driver-fglrx* did not work, blank screen upon reboot.
Mate I have given up. Reinstall it is. See you on the other side.

I will post when I am back up and running and we'll try again. Cheers.

---

### Post by QIII on 2009-06-16
Grrr.  Sorry, buddy (that's Yank for "Mate").

Was hoping it wouldn't come to that.

Hey.  When you get a chance, would you wave your bare behind in the general direction of Australia?  My oldest brother is an ExPat living there.

---

### Post by JoeNZ on 2009-06-16
Lol, yeah sweet as bud.

Well I ended up doing a full reinstall and I couldn't believe it, I can now change my visual effects. It makes me think "what the hell did I do before to lose my graphics capabilities?".

Unbelievable.

---

