---
title: "Notebook Touchpad Drivers For Scroll and Enlarge?"
date: 2010-11-06
forum: New to Ubuntu
---

### Post by onaridge on 2010-11-06
Is there any way in Ubuntu notebook or 10.10 to get my touchpad working the way it was in Windows? I was able to scroll with my fingers on the pad and also to enlarge type in browsers when desired. These were two nice features that I would hate to lose. I have a HP Pavillion Dm3 13 inch.

---

### Post by sully101 on 2010-11-12
> **onaridge said:**
> Is there any way in Ubuntu notebook or 10.10 to get my touchpad working the way it was in Windows? I was able to scroll with my fingers on the pad and also to enlarge type in browsers when desired. These were two nice features that I would hate to lose. I have a HP Pavillion Dm3 13 inch.

Scrolling up and down works on my dell mini9, by using the right side of the touch pad. Sorry havn't used windows in a long long time. Could you elaborate a bit. Keyboard shortcut Ctrl+Plus enlarges text in firefox. If you open System>Preferences>Assistive Technologies>Mouse Accessibility, (ubuntu 10.04) you will get a settings dialog with a tab "Touchpad" you can change scrolling from there. Hope this helps. sorry havn't got 10.10.

---

### Post by onaridge on 2010-11-12
I have no touchpad tabs anywhere. I guess I am out of luck unless i can find something in synaptic or elsewhere.

I have 10.04 now :-)

---

### Post by sully101 on 2010-11-13
have a look for the package xserver-xorg-input-synaptics, its installed on my netbook and seems to provide what you need.

---

### Post by sully101 on 2010-11-13
You need to read this article [http://mitchtowner.net/?p=840]("http://mitchtowner.net/?p=840")

---

### Post by onaridge on 2010-11-13
Thanks sully but I got this message after the line:

sudo tar xjvf linux-source-2.6.32.tar.bz2
tar: old option 'f'requires an argument

and needless to say, don't know what to do next.

---

### Post by sully101 on 2010-11-13
> **onaridge said:**
> Thanks sully but I got this message after the line:

sudo tar xjvf linux-source-2.6.32.tar.bz2
tar: old option 'f'requires an argument

and needless to say, don't know what to do next.

It looks like you are trying to install a new kernel (the hard way). If you look at the responses to the article you will see the last one 

> Hi Matthew,
The kernel with the fix for this issue is now in the “lucid-proposed” repo. See [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550625]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550625")for more info. Hopefully this new kernel should hit lucid-updates soon & we won’t need to work-around the issue any more :)

So I think you need to open Software Sources and click on the Updates Tab and enable Pre-Release Updates Lucid proposed. Then Reload your package Information in Synaptic and you should be able to search for 2.6.32-26 and mark linux-image-2.6.32-26-generic for installation click apply, when it finishes reboot. And see if that works.

To check that you have booted into the new kernel type uname -a in a terminal

You should get 

$ uname -a
Linux mini9 2.6.32-26-generic #46-Ubuntu SMP Tue Oct 26 16:46:46 UTC 2010 i686 GNU/Linux

or similar

Hopefully that will fix it. But there seem to be several kernels floating around with varying degrees of support for your hardware. Lucid 10.04 may not get the updates you need but 10.10 probably will. I'm really not sure and I have only really read the above post. There may be more information in the bug reports, including a fix?

Please let me know how you get on and Good luck :)

---

### Post by onaridge on 2010-11-13
Looks like the kernel didn't install as it's still 2.6.32.25 instead of 2.6.32.26 and generic #45.

---

### Post by sully101 on 2010-11-14
I think it should work with anything above 2.6.32-23 but I,m getting confused now.

According to this [http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-maverick.git;a=commitdiff;h=bd79df42218fe1db5e683b567791d4bb97b60685]("http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-maverick.git;a=commitdiff;h=bd79df42218fe1db5e683b567791d4bb97b60685") The upstream developers probably wont fix it any time soon!

From [https://wiki.ubuntu.com/LucidLynx/ReleaseNotes]("https://wiki.ubuntu.com/LucidLynx/ReleaseNotes") you can get to grub boot options by pressing any key during boot. If my memory serves correct the shift key works. You can use the up/down keys to select the kernel that you want.

---

### Post by sully101 on 2010-11-14
> sudo tar xjvf linux-source-2.6.32.tar.bz2
tar: old option 'f'requires an argument

Usually means you entered 

tar xjvf

instead of

cd /usr/src
sudo tar xjvf linux-source-2.6.32.tar.bz2

The f needs an option because the tar command is looking for a file. (sometimes when you copy and paste things get mixed up) As a side note if you use the up arrow key in the terminal you can scroll through a history of your previous commands.

---

### Post by onaridge on 2010-11-14
2.6.32.26 is the kernel I have been using. After I installed this: xserver-xorg-input-synaptics and then rebooted this morning, I couldn't boot into that kernel anymore. It gave me an error mentioning Xorg. I booted into a terminal. How do I uninstall that from a command line. That may fix the booting problem. I was able to boot into 2.6.32.25.
What is the difference between the kernels? One is more updated than the other?

---

### Post by onaridge on 2010-11-14
The error on booting into the 26 kernel: Ubuntu is running in low grpahics mode the following error was encountered
(EE) fglrx(0) hasn't established DRM connection,

then same EE fglrx and : atiddxDriScreenlnit failed, gps not initialized
then failed to map FP memory and finally firegl_setsuspendresumestate failed -9

________________

Update

I managed to get that kernel back and all is as it was before. I think I should probably wait and see if they ever develop a proper fix for this touchpad.

Thanks very much for your help :-)

---

### Post by onaridge on 2010-11-14
fixed the low graphics problem

---

### Post by sully101 on 2010-11-14
> I think I should probably wait and see if they ever develop a proper fix for this touchpad.

 
Well things could be more broke than they are now. I dont have your hardware so I cant trial any solution here. I would suggest that you could leave your system as is and perhaps use a usb stick to install ubuntu on and boot that to try and get things working. If your computer will boot from usb?

The end result of all this is. I am sure there is a workaround and its here [http://mitchtowner.net/?p=840]("http://mitchtowner.net/?p=840"). other people have done it. And I'm sure in time there will be a kernel released that will fix the issue. Sorry I could not be of more help. Perhaps you could post a comment to the above link.

---

### Post by onaridge on 2010-11-14
Thanks Sully I do appreciate you taking the time to help. Since my kernel is 26 and that article is referring to 23, rather than going back especially now that my HDMI is working I will live with what I have as in the scheme of things it's not too terribly important. I will heartily anticipate the next kernel release! :-)

---

