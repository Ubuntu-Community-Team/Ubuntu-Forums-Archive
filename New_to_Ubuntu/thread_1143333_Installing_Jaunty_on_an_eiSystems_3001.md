---
title: "Installing Jaunty on an eiSystems 3001"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by BacchusPaul on 2009-04-29
Hey there.

I've posted this exact post in the Installation and Upgrades thread, but thought that it would perhaps be better here, given how little I know about Linux. I'm very sorry for the clutter that is caused by repeating threads like this, so if a mod could delete my other thread that'd be great.

First off, I'm a complete noob with Linux, so your patience is greatly appreciated. Also, I apologise if this post has a glut of unnecessary information in it, but none of this means anything to me, so I don't know what is worth mentioning or not.

I've always been impressed with Ubuntu in the past and felt the time was right for me to try to run it on one of my machines. This will be my first intimate experience with any OS other than Windows and MacOS.

I am booting off the disk, and after I choose the option to install, and after the loading screen I get several pages of script. Any guides I have seen do not mention this, so I'm assuming that something's not right.

This is what I get
[B]
X server exited with return code " +str(status)
__main__.XSartupError: X server exited with return code 1
0% Scanning disks...[/B]

Then the pages move quicker than I can type, and I end up on a screen with:
[B]
[      5.776343] IO APIC resources could not be allocated.
Loading, please wait...
Linux ubuntu 2.6.28-11generic ~42-Ubuntu SMP Fri APR 17 01:57:59 UTC 2009 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the 
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
[http://help.ubuntu.com/](http://help.ubuntu.com/)
To run a command as administrator (user "root"), use "sudo <command>"/
See "man sudo_root" for details.

ubuntu @ubuntu:~$ [/B]

Any ideas? I have checked the disc using the option from the main menu, and that seemed fine. Given how old my machine is, ought I try an earlier version of Ubuntu?

The spec of the laptop:

VIA C7 Processor 1.5GHz

133 MHz FSB

64 KB Cache

256 MB RAM

20 GB Hard Drive

DVD ROM/ CD ReWriter Drive

14.1" Display

Microsoft Windows XP Home

64 MB integrated graphics                      

I've tried Xubuntu as well and the same thing happens. I have freed up as much space as is possible on the hard drive, have defragmented it, and have checked for Windows filesystem errors.


Thanks in advance for any help with this.

---

### Post by BacchusPaul on 2009-04-29
Since the last time I tired this I've left the mavhine running on that screen for about an hour and a half, and now some more text has appeared.

Could it be that patience is the answer and that I should just leave it alone for a couple of hours?

---

### Post by floatingpoint on 2009-04-29
That's not what the installer should do. It could well be a problem with your hardware. The end of the text seems to be a command prompt though. Can you type anything there?

---

### Post by BacchusPaul on 2009-04-29
Yes.

I've spent a while typing things like "man sudo_root" in there, and other commands that I discovered after that. This was more me trying to work out what was happening rather than trying to fix anything.

---

### Post by skeetre on 2009-04-29
It's got a problem loading the Xserver. The GUI. You could try the text mode installer and then trouble shoot the video, or try to get the video working first. Try to boot from the install CD in the safe video / safe graphics mode. There should be a boot option to select that. If that works, then you can post more info about your video hardware and someone here should be able to help you with getting X running on it.

---

### Post by BacchusPaul on 2009-04-29
I just tried the safe graphics mode and the same thing has happened. For the text based installer should I be looking for the Alternate Install? For Xubuntu is this just the Debian Installer?


Perhaps I should point out that the disk scan doesn't get finished and that it reports and error of some type.

---

### Post by floatingpoint on 2009-04-29
Perhaps, sounds like the disc is ******. Best to make a new one! And check it for errors, make sure it's 100% A-OK.

---

### Post by BacchusPaul on 2009-04-29
I thought that might have been the case, so when I burnt a second disc (when I decided to try my luck with Xubuntu) I chose the slowest burn speen I had available.

It's still the exact same thing.

Could it be anything to do with the fact that I'm using DVD's instead of CD's? I know it should cause a problem, and my machine has a DVD drive, but I think someone mentioned unexpected difficulties that were resolved by switching to CD/DVD.

---

### Post by BacchusPaul on 2009-05-03
Bump.

Any ideas, folks?

---

### Post by sneeks on 2009-05-03
make a new disc mate first,but for your specs and too give you a learning curve so to say,d/l xubuntu 9.04 jaunty,its the best xubuntu imo,and should work well with your specs.
but if you want to duel boot im not sure...
but for a single install you should have no problems.
also if it still wont install try the alternate cd,which is text based but easy(my son can do it,so can you).use cd's

---

### Post by BacchusPaul on 2009-05-03
I'm happy enough having Ununtu as my only operating system, so I don't need a dual boot setup. I don't rely on this machine for anything other than a bit of casual browsing and playing media, so I don't need it do da very much. I'd like to be able to browse the internet, and at the same time get a bit of experience with Ubuntu.

I'll give the text based Ubuntu installer a go. I'd have thought that Xubuntu would have made more sense because of my specs though.

Cheers.

---

### Post by BacchusPaul on 2009-05-03
I've just tried the text-based installer, and I've had more luck with that, sort of...

After I choose "install" from menu screen, it takes me to a broken screen that looks as though it is supposed to be a list of options, but is impossible to make out, as it looks as though the whole screen were distorted. I can make out individual rows of pixels that are probably supposed to be options on this screen, and one row is highlighted in red. I can choose which row is selected by using the up and down arrows.

Does this suggest anything? I'm beginning to think that it may be impossible to get Ubuntu to run on this laptop, and I'm close to giving up.

---

### Post by sneeks on 2009-05-08
i see your problem now,you need to go with the safe graphics mode which off the top of my head i cant remember,it may be f4,but dont quote me on it.
iv'e only had to use it once before.
give me a minite or two and will get back to ya

---

### Post by sneeks on 2009-05-08
ok,yes it is f4,from there you should be able to get to safe graphics mode i think,i didn't try it though,so give it a go.

---

