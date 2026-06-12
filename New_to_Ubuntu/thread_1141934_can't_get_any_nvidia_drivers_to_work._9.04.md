---
title: "can't get any nvidia drivers to work. 9.04"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by iansane on 2009-04-28
Hi,

I've had video issues with every dist of ubuntu since I started using it about 2 years ago. I usually get the nvidia driver or glx installed and solve the problem but with 9.04 64 bit, none of the drivers work.

I install the driver, then reboot and after the first ubuntu screen with the progress bar, I get a blank screen instead of a log in screen. I reboot and go into recovery mode and let xfix auto fix it where it apparently changes me back to the default Ubuntu driver. Then a normal boot gets me up and going but with only 800x600 max resolution.

I've tried the driver from nvidia, the glx 180 , and glx 173. I've installed them myself and I've tried using envy to install them but still have the same problem.

Anyone know what I can do to solve this? I don't care about compiz or beryl. I just want higher resolution. I turn all the affects off anyway.

If it's of any help my PC is a Gateway GM5072 with onboard nvidia everything, made by some unknown mobo manufacturer that hasn't updated there site since the stone age. The video is in the 6 series or at least that's the driver I usually get that works from nvidia.

Thanks in advance.

---

### Post by iansane on 2009-05-02
Was trying to get help in another post I found after posting this one. Thought the problem was fixed yesterday but it was just a fluke that it worked one time. After starting up today, I get the same black screen. I noticed there is about a 1mm line across the top of the screen and it is displaying gdm. I can watch the color change as I log in blindly and tell it is the display but it's only about 1 mm high. Same issue with all nvidia drivers on 8.10 and 9.04 32 and 64 bit. Last time video worked was with 8.04 and the glx-new driver which isn't available any more. 

Any ideas?

Thanks

---

### Post by iansane on 2009-05-02
what is it? People don't like my picture? :-)

Just kidding. I guess my problem is just as confusing to others because I've done everything I'm supposed to do and it doesn't work.

Well, I gave linux mint a try just in case there was something different that allowed the nvidia to work right. Same problem.

However I read in a how to about using envyng -t because the gtk was incomplete? Anyway I tried it and chose the option to uninstall the nvidia driver so I could start over again and when I rebooted it's working again even though envy uninstalled it? Anyway if it continues to work after a few reboots I'm going back to Jaunty and try doing the same thing. Mint has too many other problems. (error messages, vbox kernel won't compile, some message about not being able to capture my mouse because someone is eavesdropping on me when I try to open synaptic?) LOL it's crazy buggy!

---

### Post by anewguy on 2009-05-03
Okay, I don't claim to be an expert here, so please forgive me if this is stupid.  I remember having a similar problem in earlier releases - turned out I had to specify the clock ranges for my monitor and specifically state the desired resolutions.  I was under the impression that xorg.conf doesn't really do all of that anymore, but thought I'd ask if you tried them anyway.

Good Luck!
Dave :)

---

### Post by iansane on 2009-05-03
> **anewguy said:**
> Okay, I don't claim to be an expert here, so please forgive me if this is stupid.  I remember having a similar problem in earlier releases - turned out I had to specify the clock ranges for my monitor and specifically state the desired resolutions.  I was under the impression that xorg.conf doesn't really do all of that anymore, but thought I'd ask if you tried them anyway.

Good Luck!
Dave :)

That might work but I have no idea how and where to specify those things. Apparently the xorg.conf is not the only thing at play here though because when I tell the system to use nv or let xfix take me back to default, jockey says another version of the nvidia driver is in use.

I did finally figure out how to get good resolution which is what I was after.

I found out because of playing with envyng -t and the uninstall option.
The nv driver is apparently used by default and telling envy to remove the nvidia driver makes it remove nv.

After a reboot vesa shows up in xorg.conf and my resolution is high.

So nvidia drivers don't work for me but vesa gives me what I want.

I'd still like to figure out specifying the clock and resolution though so I'll play around with that and see if I can figure it out.

Thanks anewguy

---

