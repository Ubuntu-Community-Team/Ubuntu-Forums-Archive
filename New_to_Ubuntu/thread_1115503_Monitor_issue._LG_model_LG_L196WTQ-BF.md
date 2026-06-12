---
title: "Monitor issue. LG model LG L196WTQ-BF"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by lentomies on 2009-04-03
Hello everyone!

I have a LG monitor model LG L196WTQ-BF. This monitor was connected to my PC which was running 8.04LTS 64 bit. When this monitor was connected to my 64 bit machine I could look under

System --> Preferences ---> Screen Resolution and see this monitor correctly identified as LG 1440x900 {I think these dimensions are correct?}

Anyway, I changed this same monitor to my older PC which is running 8.04LTS but 32 bit... Now the PC cannot see that it is an LG monitor.

The best settings under screen resoultion that I can get are only 1280X768.

Could somebody give me advice as to how I can get Ubuntu to see that this as an LG monitor????

I attached a pic which I hope helps you see my situation.

Thank you for your help and suggestions!!!

---

### Post by asmoore82 on 2009-04-03
I would check the "/etc/X11/xorg.conf" file and see if the monitor capabilities have been hard coded in there.

---

### Post by lentomies on 2009-04-03
Oh boy asmoore82, how do I do that... Yep you guessed it, I'm a novice....

---

### Post by lentomies on 2009-04-03
asmoore82,

I went into the directory you mentioned in your post. I'm hesitant to do these things for the simple fact that I don't want to screw anything up!

When I opened this file up I found a message that said:

"# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg"

asmoore82, I opened up terminal and ran the sudo command that was suggested above.

Then I rebooted my PC and went to System-->Preferences -->screen Resolution

As the attached picture shows I now have the chance to choose settings 1440X900

So I choose these settings and re-booted my pc again.

The other pic I attached shows the name "Guest" in wrong place. Also, When I look at my monitor only the letters "Gues" appear. BUT snap shot shows the entire word... This is strange. Also, the "off" button is suppose to be in top right corner of monitor and not GUEST...!!!!

Finally, LG name does not appear in "screen resolution" settings?????

Sir, you have brought me quite close in getting this problem taken care of.... BUT what can we do about these little details....????

Thank You very much!!!

---

### Post by asmoore82 on 2009-04-04
Great strides have been made in recent years towards having no "xorg.conf" file at all
and the graphical subsystem just probing for the right settings on-the-fly.

To try this out, rename "xorg.conf" to a backup location.
BUT, if it doesn't work, you will need to be prepared to log in
the text console you are left with and rename it back.

```
sudo mv /etc/xorg.conf /etc/xorg.conf.mybackup
```

and to restore it later if necessary:
```
sudo mv /etc/xorg.conf.mybackup /etc/xorg.conf
```

as for not quite fitting the screen, you probably just need
to find/hit the "auto-adjust" on the monitor itself.

for the panel not having things where you want,
you can "middle-click" or "wheel-click" and drag all of that stuff around.
(you may need to right-click and uncheck "Lock to Panel" first -
a lot of locked items seem to get shuffled when shifting resolutions)

---

### Post by lentomies on 2009-04-04
asmoore82!

Your the best! The "autoset" was all I needed to press and the desktop centred itself correctly. Talk about feeling like an idiot..... Anyway, now I can see everything! Thanks for the tip on the "middle-click". That too solved the other issue.

I tried the:

sudo mv /etc/xorg.conf /etc/xorg.conf.mybackup

Command you offered and that didn't work. I then edited the line thinking you may have omitted the folder "X11" but that too didn't work. See attached pictures.

At the end of the day, is it really important for the "Screen Resolution" to report the LG monitor? As you can see from the attached pic it currently reports "Unknown".

What are your thoughts?

Thanks again for your continued support.

Suomalainen

---

### Post by lentomies on 2009-04-05
bump

---

### Post by presence1960 on 2009-04-05
> **lentomies said:**
> asmoore82!

Your the best! The "autoset" was all I needed to press and the desktop centred itself correctly. Talk about feeling like an idiot..... Anyway, now I can see everything! Thanks for the tip on the "middle-click". That too solved the other issue.

I tried the:

sudo mv /etc/xorg.conf /etc/xorg.conf.mybackup

Command you offered and that didn't work. I then edited the line thinking you may have omitted the folder "X11" but that too didn't work. See attached pictures.

At the end of the day, is it really important for the "Screen Resolution" to report the LG monitor? As you can see from the attached pic it currently reports "Unknown".

What are your thoughts?

Thanks again for your continued support.

Suomalainen

I had an LG 17 inch monitor and it always reported "unknown". It worked fine so I never gave it any mind, after all the fact that it worked properly was all that mattered.

---

### Post by tad1073 on 2009-04-05
It is X11 not x11

---

### Post by nandemonai on 2009-04-05
> **presence1960 said:**
> I had an LG 17 inch monitor and it always reported "unknown". It worked fine so I never gave it any mind, after all the fact that it worked properly was all that mattered.

+1

If it works I wouldn't worry about it not being reported correctly ;)

---

### Post by suomalainen on 2009-04-05
People & friends,

Yes, I agree, if it "appears" to be working then ignore the fact that it isn't being reported correctly and get on with life!!!!!!!!!


As I already mentioned above, this very same monitor was being used on my Ubuntu 8.04LTS 64 bit machine and WAS being reported correctly!!!

However, I recently swapped monitors as already mentioned. The new machine which this monitor is connected to is also a Ubuntu 8.04 but 32 bit. It is reporting this monitor as being unknown.

Last night I discovered an issue. I wanted to select the screen saver "sky rocket" and was unable to do so. There are a few that I can select but not too many. I eventually selected "cosmos". As a test, I allowed 10 minutes of inactivity to pass and the screen saver automatically activated. It then stayed on for about 5 minutes and then the screen went black....

So maybe I really do need it recognised if such issues are being discovered such as this one????

Any ideas or suggestions?

---

### Post by lentomies on 2009-04-05
tad1073,

I made the change you noted from x11 to X11 and edited the command line accordingly but still got another error message. It's attached for reference.

Thanks!

---

### Post by asmoore82 on 2009-04-05
> **lentomies said:**
> tad1073,

I made the change you noted from x11 to X11 and edited the command line accordingly but still got another error message. It's attached for reference.

Thanks!

I feel silly leaving out the "X11"

^^according to that pic, you seem to be already running "config-less"

---

### Post by lentomies on 2009-04-05
Hello Everyone,

I have my monitor in the following state, please refer to the two attached pics.

As you can see from the 2 pics this is how my monitor is setup today. If I was, however, to untick the NVIDIA device driver then I would not be able to use the "skyrocket" screen saver. Also, Google Earth would reboot itself...

This is so strange problem because this very same monitor works with my other PC which is Ubuntu 8.04 64 bit and then when I changed it to this 32 bit PC... PROBLEMS......

If anyone knows how I can get my screen resolution to 1440X900 that would be awesome!!!

Thank You!

---

### Post by asmoore82 on 2009-04-05
Aha!

If you are using nVidia's driver, the nVidia X Server Settings app
mentioned in the other thread is the only way to go.

Disabling nVidia's driver and using the Open Source one should make
the built-in resolution settings dialog work the same as on other PC's,
but then of course you won't have great 3D acceleration from the nVidia  Video card.

```
sudo apt-get install nvidia-settings
```

---

### Post by lentomies on 2009-04-05
Thanks for the info asmoore82!

On this specific PC I don't need 3D. I also don't think it can handle it! But I do need Google Earth to work and sky rockets to work and that is as intense as it will get for this baby....{Dell Optiplex GX300}

Should I still do the:

sudo apt-get install nvidia-settings

You noted????

thanks!

---

### Post by lentomies on 2009-04-05
asmoore82,

I ran the code:

sudo apt-get install nvidia-settings

You suggested and got the following error message which is attached as a pic.

What next?

Thanks!

---

### Post by asmoore82 on 2009-04-06
That's a little odd seeing as how nVidia was checked in that earlier screenshot ...

but I guess do what it says and see what happens:
```
sudo nvidia-xconfig
```

---

### Post by lentomies on 2009-04-06
asmoore82,

This code:

sudo nvidia-xconfig

Does not work. See pic.

---

### Post by lentomies on 2009-04-07
Hi All,

I made some changes that I'd like to report. The reason I made the following changes is because the screen resolution and layout simply stunk!

Here are two attached pics which highlight my new and most current settings. Please note Envy has been removed. Nvidia X Server Settings was also removed.

As mentioned, I have a LG model LG L196WTQ-BF display. This monitor replaced a HP w1907 that was connected to this PC. I'd like to note that when the HP was connected to this PC I DID NOTE HAVE THE NVIDIA X SERVER SETTINGS INSTALLED and the screen resolution was detected automatically as 1440X900 and I was also able to use skyrockets screen saver.

Is there a way that Screen Resolution can detect my LG monitor?

---

### Post by lentomies on 2009-04-07
Hi Again,

Well this is strange. After I wrote my post I re-booted my PC. Now for the first time, I can see the "Sky Rocket" screen saver. but it is very slow....

I don't know if this is due to all the installs then removal of software and programs but things work now but sssslowly....................

---

