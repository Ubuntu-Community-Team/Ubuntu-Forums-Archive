---
title: "Problem dual-booting ubuntu &amp; windows XP"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by oingk on 2009-12-28
Hi everyone.

I have recently installed Ubuntu 9.10. With the help of the installation CD I made a dual boot system with my already installed Windows XP Pro (SP3). The CD was obtained from Linux magazine though I don't think that matters.

When I switch on my computer it automatically starts with Ubuntu's bootloader GRUB and asks me if I want to boot into XP or Ubuntu. It has a time limit of 10 secs after which if I don't make a choice it automatically boots into Ubuntu.

I have two concerns. One is that my windows XP has become really slow to start up after I installed Ubuntu. The other is that I would prefer if my computer would automaticaly boot into XP after say 10 secs of turing it on, instead of automatically booting into Ubuntu. Can I do this and also fix the slow XP booting?

I am a student and I have all my study-related things on XP (this is also the reason why I can't completely abandon XP for now) so the way things are now causes me inconvenience. 

Please help me find a way that I can have Ubuntu and XP coexist on my computer peacefully, without one or the other losing any of its speed to start up. If you answer this, please also explain step-by-step what I should do as I am only a beginner in regards to Linux.


NOTES: I have Thinkpad SL500, 2GB RAM, Inter core 2 Duo 2.2GHz, don't know if these play a role here. Also I run full scans with antivirus and antispyware on Windows and I have no issues.


Thanks, 
Oingk

---

### Post by iMisspell on 2009-12-28
To change what starts up first...
<snip>
[]("http://www.howtogeek.com/howto/ubuntu/set-windows-as-default-os-when-dual-booting-ubuntu/")

---

### Post by Sef on 2009-12-28
9.10 uses [GRUB 2]("http://https://help.ubuntu.com/community/Grub2"), which works differently than grub legacy.  Since the links were for grub legacy, I snipped them.

---

### Post by oingk on 2009-12-28
Hey thanks for the attention.

What do you guys mean by snip and snipping?

---

### Post by wirate on 2009-12-28
Not sure if this will work.

open /boot/grub/grub.cfg in gedit. you will see the windows and ubuntu entries there. cut and paste the windows entry before ubuntu, save the file and reboot.

Note: To edit the above file, you will have to change permissions, open a terminal and type "su", enter your password. Now navigate to /boot/grub in nautilus, open properties of grub.cfg. Set the permissions so you can read and write the file.

And one more thing, always make backups before editing any system files.

---

### Post by Sef on 2009-12-28
> What do you guys mean by snip and snipping?


To remove something by deleting it.

---

### Post by nathansoz on 2009-12-28
Hey, this should solve your problem of default os

Open up a terminal and type:
```
sudo apt-get install startupmanager
```

Then after going through the install... (entering your password, saying yes to install... etc...)

type this into the same terminal

```
sudo startupmanager
```

A window will pop up and you can select default OS

Hope that helps :)

EDIT:

If it says the package cannot be found try running this command and then go through the above

```
sudo apt-get update
```

---

### Post by oingk on 2009-12-28
Ok, are you saying I should delete something then? If so, what?

---

### Post by TheLunticIsInMyHead on 2009-12-28
Hi,
I'm not sure about the difference between grub and grub 2 so this might get snipped too but this is how I used to change the default operating system, and it looks like the option is still there on 9.10.

Load Ubuntu and go to the main menu -> system -> administration -> Start Up Manager

(Note: Perhaps under the default settings the system option is on the panel to start with not under the main menu).

Once here it will ask you to put in the root password, and then you will get a little box that will allow you to change the default operating system, and also that default time before it chooses an OS.

Not sure why it takes so long to boot into Windows so I'll leave someone else to think about that.

Hope this helps.
Mike

---

### Post by nathansoz on 2009-12-28
> **TheLunticIsInMyHead said:**
> Hi,
I'm not sure about the difference between grub and grub 2 so this might get snipped too but this is how I used to change the default operating system, and it looks like the option is still there on 9.10.

Load Ubuntu and go to the main menu -> system -> administration -> Start Up Manager

(Note: Perhaps under the default settings the system option is on the panel to start with not under the main menu).

Once here it will ask you to put in the root password, and then you will get a little box that will allow you to change the default operating system, and also that default time before it chooses an OS.

Not sure why it takes so long to boot into Windows so I'll leave someone else to think about that.

Hope this helps.
Mike

Mike, for some reason startupmanager wasn't in my installation until just now, when I installed it. Wasn't a big deal to me, I never have needed it.

> **oingk said:**
> Ok, are you saying I should delete something then? If so, what?

I wouldn't delete anything. Messing with your grub config file can be dangerous if you aren't quite sure of what you are doing (though the best way to learn is experience!) If you want a quick simple fix, startupmanager is the way to go.

---

### Post by lloyd_b on 2009-12-28
> **oingk said:**
> Ok, are you saying I should delete something then? If so, what?

The "snips" were the moderators removing incorrect answers - the person posted info for an older version of Grub that doesn't apply to you.  You don't have to delete anything.

Follow the advice from previous posts regarding "Startup Manager", and it should fix your problems.

Lloyd B.

---

### Post by oingk on 2009-12-28
thanks.

about system manager I couldn't find it in system>administration.

how did the previous poster install it?

---

### Post by nathansoz on 2009-12-28
> **nathansoz said:**
> Hey, this should solve your problem of default os

Open up a terminal and type:
```
sudo apt-get install startupmanager
```

Then after going through the install... (entering your password, saying yes to install... etc...)

type this into the same terminal

```
sudo startupmanager
```

A window will pop up and you can select default OS

Hope that helps :)

EDIT:

If it says the package cannot be found try running this command and then go through the above

```
sudo apt-get update
```

Here is my previous post :)

HTH

---

### Post by oingk on 2009-12-28
ok I think I get it I will try nathansozs method

---

### Post by nathansoz on 2009-12-28
> **oingk said:**
> ok I think I get it I will try nathansozs method

Remember to change your post heading to SOLVED after you get a problem worked out. I would maybe consider making a different post about the slow booting of XP, thats really strange. I am sure there are brilliant minds out there on the forums that could figure it out though, they've never failed me. Oh and if you run into problems let us know.

---

### Post by oingk on 2009-12-28
:P
It worked! 

Thanks very much to you people!

Yes my problem with windows XP being slow is still there. I just got the idea though now that it may be just my imagination after installing ubuntu and seeing how fast it is I may be seeing windows XP as really slow but it may be its normal, I'm not sure. I will do some research and as you said if I think there is a problem I'll start another thread.

Again thanks

---

### Post by oingk on 2009-12-28
hey how do i make it as "SOLVED"?

---

### Post by lidex on 2009-12-28
> hey how do i make it as "SOLVED"? 

Click on the red "Thread Tools" near top of page.

---

