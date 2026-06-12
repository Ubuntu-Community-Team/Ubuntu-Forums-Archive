---
title: "Ubuntu 10.04 no screens found"
date: 2010-09-05
forum: New to Ubuntu
---

### Post by Tracy177 on 2010-09-05
could someone help me?
 
i have two OSes win7 and ubuntu 10.04 sometimes i boot up win 7 sometimes ubuntu.
 
i just tried to boot up ubuntu and after grub is dropping me to command prompt 
 
and when im trying startx it says no screens found.
 
i tried fixvesa
 
it say no command found
 
i use ati card with fglrx 
 
how to boot in save graphic mode or something? 
 
 
i think i have to fix xorg or something dont know how to do it could someone help me tnx



i found it i had to remove flglrx reconfigure xorg boot ubuntu in low graphic startx reinstall fglrx and now is working again but mighty god if i had to use ubuntu for work or something important  i would shoot myself or the people who build it.


God bless windows

---

### Post by realzippy on 2010-09-05
Tightrope walk.
If you continue behaving [like you do]("http://ubuntuforums.org/search.php?do=finduser&u=1139759") this might be interesting for you:

[http://ubuntuforums.org/showthread.php?t=122434](http://ubuntuforums.org/showthread.php?t=122434)

---

### Post by trekki on 2010-10-31
> **realzippy said:**
> Tightrope walk.
If you continue behaving [like you do]("http://ubuntuforums.org/search.php?do=finduser&u=1139759") this might be interesting for you:

[http://ubuntuforums.org/showthread.php?t=122434](http://ubuntuforums.org/showthread.php?t=122434)
Maybe somebody else than realzippy can give me a hint? I have the same error message in Version 10.04.01 LTS.
Until some weeks ago my installation of Ubuntu was working fine. One boot stopped at the console in text mode. Login was no problem, so i tried with the command startx -> error message as in the title. Please don't ask me, what have changed. I don't know about any.
Since then i just started windows (sorry for this, but thats the truth) and could work fine. Now i am missing the possibilities of Ubuntu and want it back. How?

Thank you in advance for any constructional hit!

-trekki

---

### Post by Mark Phelps on 2010-10-31
Can you get to a GRUB menu by holding down the SHIFT key?

If so, do that, and when the menu shows, select what is usually the second entry -- it will have "(recover mode)" in it.

See if booting into that, and then entering "startx" gets you back into a desktop again.

If it does, then shutdown as usual, and when you reboot again, you should be OK.

---

### Post by trekki on 2010-10-31
Hi Mark,
thanks for your hint. But the result is the same. I did the following
boot 2.6.32-24-generic (recovery mode)
select "resume"[INDENT]startx -> no screens found
reboot via shell command shutdown
[/INDENT] boot 2.6.32-24-generic (recovery mode)
select "failsavex"[INDENT]no screens found, jumps back to selection
[/INDENT]Do you have any other idea?

If you need any logfile please also give me assistance, how to transfer them via shell commands. I have a USB stick

-trekki

---

### Post by Rex Bouwense on 2010-10-31
This may or may not work for you.  Last week I believe I had a similar problem (but I am not dual booting).  I just booted with an older kernel (not recovery) which worked fine.  Then I rebooted again and everything was fine.  I don't know why, but it just worked.

---

### Post by anewguy on 2010-10-31
> **trekki said:**
> Maybe somebody else than realzippy can give me a hint? I have the same error message in Version 10.04.01 LTS.
Until some weeks ago my installation of Ubuntu was working fine. One boot stopped at the console in text mode. Login was no problem, so i tried with the command startx -> error message as in the title. Please don't ask me, what have changed. I don't know about any.
Since then i just started windows (sorry for this, but thats the truth) and could work fine. Now i am missing the possibilities of Ubuntu and want it back. How?

Thank you in advance for any constructional hit!

-trekki

I hope you can re-read the original post, especially the last paragraph and then you'll understand why realzippy directed the OP to the thread he did.  Then also follow the first link in realzippy's post and you'll find this is a habit for this user.  realzippy's second link is to inform the OP what happens if they continue down the road they have been following.

In the mean time, are you also using an ATI video adapter?  Do you know if you have an xorg.conf file?

Thanks
Dave ;)

---

### Post by trekki on 2010-11-01
Hi Rex,
when booting i have the coice of 4 Ubuntu Kernels. This list varies, it gets longer by updates and shorter when i remove older versions. The most recent is the default in version 2.6.32-24. The only older version is 2.6.32-23, but the same result.

Hi Dave,
yes i read the last paragraph but not all other posts of the OP. He was frustated about the missing GUI. The same is for me, but i would like to like to have a technical answer. Therefore i am glad for yours! Therefore back to the topic:
My screen is a Belinea 10 19 03, the video card is integrated on the motherboard and is named NVIDIA GeForce 6150SE nForce 430. The motherboard is an AliveNF6G-DVI. My installation of Ubuntu ist just default. If the default generates the file xorg.conf then the answer is YES. Otherwise: where should the file be? If a copy of this or any other file helps, how can i transfer this to my installation of the "*He*-*Who-Must*-*Not-Be-Named*"?

-trekki

---

### Post by anewguy on 2010-11-01
Wow - you've got some hardware I know nothing about!  However, since it is an nVidia adapter and not an ATI adapter, perhaps we can have you try something that works for some other nVidia problems - I have no idea if it would do anything here, but it can't hurt to try!

When you get the boot menu, edit the boot line and add nomodeset and then boot.  If it works better, we can make the change permanent.  If it doesn't do anything or even makes it worse, we have made no permanent change so you can reboot as before.

When you get these problems, what does the /var/log  current xorg log file show (I don't remember the name right now, but it's something like "Xorg-0log.log or some such thing).

Dave ;)

---

### Post by trekki on 2010-11-02
Hi Dave,
yes my hardware is a little old but it is powerful enough for my needs. I spend more €€€ for my bicycles than my pc:)

You suggestion to insert nomodeset into the bootline is done. As i have 3 lines, i guessed to use the "kernel" line. OK?
The result is, that nothing changes. The logfile is /var/log/Xorg.0.log and contains 3 error messages
>   [drm] KMW not enabled
VESA(0): No valid modes
Screens found, but non have a usable configurationwich results in the fatal error no screens found. See also my hardcopy. Excuse me for the dust on the screen, this is almost not visible in real life.
-trekki

---

### Post by trekki on 2010-11-02
... the attachment was missing

---

### Post by anewguy on 2010-11-02
You know, I feel a little more than stupid right now, as I NEVER asked if you had installed a driver or not.  I do not know if ubuntu supports your adapter out of the box or not, so please do the following:

- open a terminal window (Applications/Accessories/Terminal)
- type:

lshw <press enter>

There will be quite a bit of output from that.  Look for a section that looks similar to the following:

```
           *-display:0
                description: VGA compatible controller
                product: RV280 [Radeon 9200 PRO]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=32 mingnt=8
                resources: irq:16 memory:c0000000-c7ffffff ioport:a800(size=256) memory:cfef0000-cfefffff memory:cfec0000-cfedffff

```

Post just that section back here - if there is more than 1 "display:" sections (like *-display:1) copy and post those sections back here as well.  From that we can determine what driver the video is using by default, see if it's valid for your adapter, and research problems with that adapter and/or driver and ubuntu 10.10.

Dave ;)

---

### Post by trekki on 2010-11-03
Hi Dave,
here is the section of lshw, today without dust on the scren. I cannot remember, that i installed other drivers than the default one's.

The first installation of the computer is some years ago and i followed all updates. So i think the whole issue comes from an update. Until the issue started the graphical user interface was working fine.

One thing i did not mention until now: in the final phase of booting the computer the login prompt is shown and immediately blanked out again. This repeats about 5 times, finally the screen is stable. This is not a blinking of the screen itself, because my typing is removed.

If you think, the graphics card is not supported anymore i can buy a new one. What brand / chipset / ... do you suggest? Although i like the existing one because it is integrated on the motherboard.

-trekki

---

### Post by trekki on 2010-11-08
The issue is solved for my side.
Dave's questions gave me the idea to connect 2 screens to my computer. One on the VGA connector and one on the DVI connector. When booting both screens showed the same information. Via the screen config menu i wanted to change this to have a bigger desktop area over both screens. Here the first question was, if i want to install the nvidia driver to get support for this. After installation and reboot the desktop was shown on one screen only and the second stayed blank.
Now the situation is, that i have removed the blank screen and can work fine with ubuntu. But i can only assume, that the reason for the error was an updated driver. Now i work with the nvidia driver.

Thanks to all for support and ideas!

-trekki

---

### Post by ericfontaine on 2011-03-30
I had this no screens found error just now on Ubuntu 10.10.  I think I may have installed the proprietary Nvidia graphics driver when I really didn't need to.  Anyway, I rebooted my machine, selected the second boot option (Recovery), selected the low-graphics recovery option, and then reset my graphics driver to the default condition.  Restarted, and now it works fine.

---

