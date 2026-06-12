---
title: "Nvidia Video Card Drivers causing problems."
date: 2010-05-14
forum: New to Ubuntu
---

### Post by trevzilla on 2010-05-14
First off, I am a complete noob to Ubuntu.  So far, I love what I see, but I am running into some video card driver issues that I hope to get resolved.

Here is the info that terminal gave me on the video card I have installed.

02:00.0 VGA compatible controller: nVidia Corporation NV25 [GeForce4 Ti 4400] (rev a2)

I've been to System->Admin->Hardware Drivers, and it looks for the drivers.  It finds a proprietary driver.  But as soon as I activate this proprietary driver, when I reboot I am only given the option of displaying a resolution of 640x480 and no higher.  When the driver is not activated, my resolution is 1024x768.  The problem is, when the driver is not activated, any video I try to watch is extremely jerky.  

Does anyone have any suggestions on how to get a working driver installed for my video card?

And as one last request, any instructions you give, please make them nice and easy to understand...Like I said, I'm a noob and haven't quite learned my way around Ubuntu yet.

Thank you so much!
Trevor

---

### Post by themusicalduck on 2010-05-14
How are you trying to change the resolution?

Normally it should detect it correctly, but to change any settings when using the nvidia drivers, you need to run nvidia-settings.

Press alt+f2 and type ```
gksu nvidia-settings
``` (you need to run it as root so that you can save your configuration and have it load right every bootup.)

Hopefully there will be an option to set it to the right resolution there.

---

### Post by trevzilla on 2010-05-15
I was trying to change the resolution by going to System->Preferences->Monitors.

When I do that, I get an error message that says:
"It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?"

If I hit "Yes" I am brought to the same window that I get to when I typed "gksu nvidia-settings" in terminal.

If I hit "No" I am brought to a Ubuntu window with some resolution options.

Regardless, either way, the only screen resolutions I am able to choose are 640x480 or 320x240.

Any other thoughts on how to get a good resolution?
Thanks so much!

Trevor

---

### Post by jkxx on 2010-05-15
Your card is not supported by the Nvidia binary drivers, at least not the latest version. If you are given more than one choice, choose the oldest version driver you are offered and try booting with that.

If not, there are two drivers which will/should give you some more resolutions to try: vesa and nouveau, although of those the second one is better if it can detect your card.

I have an Nvidia card but have never seen the nouveau driver offered, though the blurb on how to test it just says

> Testing Nouveau in Ubuntu 10.04

The Nouveau should be used by default in systems with Nvidia hardware.

If you have since installed the proprietary driver and would like to switch back to using Nouveau to test it then simply disable it via the Hardware Drivers menu, reboot (you may see a lovely low-graphics mode, so be warned) and then enable the Nouveau driver. 

So you should be able to get it from the Hardware Drivers app.

---

### Post by trevzilla on 2010-05-16
I went to System->Admin->Hardware drivers, and the ONLY driver that is offered is the proprietary nvidia driver.

So, I went to Synaptic and did a search for both "nouveau" and "vesa" and the only package it found was for a nouveau driver.  I tried installing that, however I'm still getting very jerky video.  I since went back to Hardware drivers, and there still was no nouveau driver in there.  Just the as of now not activated nvidia proprietary driver.

I found this page talking about installing nouveau:
[http://nouveau.freedesktop.org/wiki/InstallNouveau](http://nouveau.freedesktop.org/wiki/InstallNouveau)

But those install instructions seem pretty long and drawn out for an operating system that people are toting as being user friendly.  I'll try to go through those instructions if you think it actually will help...

However, as of now, I'm still not having luck with this driver situation. Thoughts?  Thanks!

---

### Post by -humanaut- on 2010-05-16
What driver version are you using 96,173, or Current?

---

### Post by lindsay7 on 2010-05-16
.

---

### Post by lindsay7 on 2010-05-16
You change the resolution from the Nvidia x server settings found under system/administration

---

### Post by StonedRaider on 2010-05-16
You can download drivers from nvidia.

here are the drivers[U]
[/U][64bit ]("http://www.nvidia.co.uk/object/linux_display_amd64_96.43.16_uk.html")

[32bit ]("http://www.nvidia.co.uk/object/linux_display_ia32_100.14.11_uk.html")

download drivers then cd to directory they are in then run command 

sudo sh (then linux driver name here)

---

### Post by lyall on 2010-05-16
the Nvidia driver 96.43.17 should work the best for you
and most of the old AGP card

I have an old AGP Quadro4 980 XGL and is works best with the 96.43.17

good luck and have fun learni9ng

---

### Post by trevzilla on 2010-05-17
Thank you for all the help!

@humanaut - When I go to System->Admin->Hardware Drivers, the proprietary driver it gives me an option to install is 96.

@lindsay7 - There isn't a Nvidia Xserver Settings under System->Administration.  (But I looked when the proprietary driver was deactivated.  I'll have another look when I activate it...)

@StonedRaider - Thank you very much for the links!  I tried installing the 32bit driver, and it seemed to be the closest I got.   However, inside terminal it told me that the driver was not compatible with my GPU.

From there I took lyall's advice, and started looking for the 96.43.17 driver.  I found one (I think) and tried installing it once again using "sudo sh (driver name)"

It told me I had x server running and I could not install the driver with that running.  I looked at some forums on how to quit x server, and got into some trouble...

First off, I hit ctrl-alt-f1, and I found that puts me into a full screen terminal window of sorts, that I have NO IDEA how to get out of.  I had to reboot.  :s

After I got back into Ubuntu, I tried running this command:
"/etc/init.d/gdm stop"
And the computer seemed to just go to black with a little blinking dot in the upper left corner.

I hope I'm at least on the right track...thoughts?

---

### Post by 4Orbs on 2010-05-17
My computer uses the 96.43.17 proprietary driver, and I have never been able to get it working correctly by using the nvidia settings mgr. But I do get it working by manually adding the xorg.conf file. If you are interested in trying this, here are the steps:

1. If your Hardware Drivers Mgr shows the nvidia driver is already activated, move on to step #2. If not then - Go to System>> Hardware Drivers and activate the recommended 96.43.17 driver, but don't reboot yet. If you get the warning that the driver is not compatible with your gpu... you will need to open the Synaptic Package Manager and install it by selecting nvidia-96 and choose "mark for installation" (which should also mark 3 other packages for installation automatically). Then click the green check mark at the top of Synaptic to make the install happen. After it installs, close Synaptic. DON'T REBOOT YET. Also, if you used Synaptic to install the driver, be aware that the Hardware Drivers Mgr will NOT show the driver as activated, but don't try to activate it. That will only mess things up.

2. Open your text editor as root by entering this into a terminal. You will be asked for your admin password.
```
gksudo gedit
```

3. Paste the following into the blank page of the text editor.
```

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
	Option	"AddARGBGLXVisuals"	"True"
   SubSection "Display"
   Depth 24
   Modes "1024x768" "800x600" "640x480"
   EndSubSection
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection


```

4. At the top menu of the text editor click "File" and select "Save As" and save the file with this name:
```
/etc/X11/xorg.conf
```

5. If you get a warning that the file already exists, choose to replace it with this new file.

6. When the file has saved, close the text editor and terminal and browser and reboot.

7. If this works for you... in order to change screen resolution from now on, you will need to manually edit the xorg.conf by changing the first resolution entry in the file's "Modes" line, as root to whatever new resolution you desire. Or just add another resolution, enclosed in quotes, as the first entry among the others. Don't try to change resolution with the system monitor settings or the nvidia settings mgr... that will only mess up things.

8. Also be aware that, if you are using Ubuntu 10.04. and this works... the Ubuntu splash screen (when you first boot up) will appear oversized and ugly. That can be fixed later.

9. If this doesn't work... hopefully you will still be able to log in at Low Graphics Mode and simply delete the /etc/X11/xorg.conf file as root by entering in a terminal:
> sudo rm /etc/X11/xorg.conf

---

### Post by trevzilla on 2010-05-17
Thank you very much for your detailed reply, 4orbs.

I followed your instructions to the T.  I was able to activate the proprietary driver through System->Admin->Hardware Drivers, and I activated (version 96) which was my only option.

Then before rebooting I followed the rest of the instructions.

When I rebooted, I was greeted with an over sized splash screen, like you said would happen.  But when I logged in, My resolution was still very low.  640x480 instead of 1024x768.

I figured it didn't work, so using your command, I deleted the xorg file.  And then rebooted again.  Now I am not even greeted with a splash screen.  All I get is a login to "livingroom" and Password.  (This is all in a "terminal" like view.  Just full screen...no GUI to work with)

Now I'm completely stumped.  No idea how to get back to the GUI ubuntu, and still no working driver...

On the bright side, I watched video when I was in the low graphics mode, and the video DID run smoothly.

What now though?  And once again, all your help is greatly appreciated.  I would've given up ages ago if I was working on this by myself!

Thanks!
Trev

---

### Post by 4Orbs on 2010-05-17
I think, since you booted and got the ugly splash screen, that the driver and xorg.conf are the solution. I also think the reason you were still 640x480 after logging in is because you had probably (prior to adding the new xorg.conf file) used the monitor settings to choose 640x480, and that configuration was still working (because 640x480 is one of the available options in the new xorg.conf). It might have been easily fixed by just using the monitor settings to set the resolution to "Auto" or 1024x768 while keeping the new xorg.conf in place. But I told you not to do that, so it was a big mistake on my part... I apologize.

Anyway, since all you did was remove the new xorg.conf, it should be easy to get back to the previous state. I think all you need to do is login to your "livingroom" terminal screen. Once you're logged in (it will still be a terminal) enter:
```
sudo nvidia-xconfig
```
which will create a new xorg.conf file, although it will be considerably different from the file you added manually.

You should be able to then shutdown you system by entering sudo halt then turn it back on and boot into a gui. And if something wonderful happens, you might even be able to login to your preferred resolution.

If you make it this far, let me know what happened.

EDIT: When you logged into the 640x480, did Ubuntu tell you that you were running in Low Graphics Mode? Or did you just get the low resolution with no warnings?

---

### Post by trevzilla on 2010-05-18
O.K.  I don't know if this is good or bad...

Followed your instructions to recreate the xorg.conf file.  Then typed sudo halt to reboot.

Now, I get a quick splash screen that looks normal.  However it quickly disappears, and the monitor is now completely blank with a message from the monitor that says "not support mode."

I probably F-d up because I am looking at the info sheet of the monitor I am using, and it says the display is 1280x720...not 1024x768 as I previously assumed would work (as that was what ubuntu said was displaying when the driver was not activated.)  This probably doesn't help our situation at all.  Sorry!  I feel like a total douche for overlooking that.

So, now that I have a blank screen and "not support mode" what's next?

---

### Post by 4Orbs on 2010-05-18
Ok. That's something I should have asked you about. Whether you had a wide screen monitor or an old CRT monitor. On the plus side is that we should be able to get through this fairly easily. Give me a few minutes and I'll be back, hopefully with a REAL solution.

---

### Post by trevzilla on 2010-05-18
Sweet.  Take your time!

If it helps at all, I can take a monitor from my other computer that definitely displays at 1024x768... at least that way maybe we can get somewhere in which we could see something.

If it's easy not to do that, then I'd prefer not to, but if it comes to it, I want you to know that the option exists.

Thanks again!
Trev

---

### Post by 4Orbs on 2010-05-18
Using the other monitor might actually be the better idea. I'm starting to get the feeling that the 96. driver doesn't support widescreen resolutions, or maybe only a few. But before doing that we might try one thing.

When you get the grub menu hit "e" and let's try editing the grub boot line. Look for the part that says vga=whatever and change the whatever number to 768 then hit ctrl+x to boot and see if you get to the login screen.

---

### Post by 4Orbs on 2010-05-18
To get the grub menu; when you first turn the computer on... and before it normally boots into Ubuntu... just keep hitting the "Esc" key and it should cause the grub menu to pop open. Grub lists the different kernels, recovery mode, memtest, etc. Use the arrow keys to highlight the top entry and hit "e" to edit the boot parameters for the kernel. Then do what I described above.

---

### Post by trevzilla on 2010-05-18
Well, something seems to gone horribly awry now...

I tried hitting "esc" when my computer was hooked to the widescreen monitor.  Still got a "not support mode" error.  Couldn't see any menus or anything.

I finally got fed up with it, and bit the bullet.  I stole a monitor from my computer in my room and brought it to the livingroom where I am doing the Ubuntu install...

Looking at my new monitor, I was able to boot into the user selection screen.  However, both my mouse and keyboard were not working.  I unplugged them, replugged them in, reboot, and now I get a "Disc Boot Failure"

I just barely get past the Bios when this error pops up.  And it is a Bios error as well.  I've tried multiple times, and checked and double checked that my bios boot sequence is correct, yet I am still getting the "Disc Boot Failure" error.

Might just be easier to try another fresh install of Ubuntu eh?  At least it installs easily.

What are your thoughts?  (Plus, I'll still have the driver problem if I do a fresh install.)

Trev

---

### Post by 4Orbs on 2010-05-18
Yeah, a fresh install would be the least time consuming way to get back to a better place. Here is what I can tell you about the "not support mode" error from your monitor. With version 10.04, Ubuntu switched to "Plymouth" which creates the splash screen that turns ugly when you activate the nvidia driver. Plymouth is also responsible for not being able to deal with some resolution changes that affect it prior to getting to the login screen. It's my understanding that the Ubuntu developers are still working out the bugs with Plymouth.

Here's how the nvidia driver is SUPPOSED to work; you activate the driver and reboot and the driver should have made the resolution re-adjust automatically to your monitor's native resolution. Then if you want to change resolution you open the nvidia settings manager as root (sudo nvidia-settings) change to the desired resolution, and click the "save settings" button which will create a new, altered xorg.conf file. But typically, opening the nvidia settings manager for the first time presents you with a warning "you don't appear to be using the nvidia driver"... and in order to use the settings manager you first must run the command sudo nvidia-xconfig which creates the initial xorg.conf file which is later altered whenever you change resolution. After following these steps, you should be able to change resolution repeatedly thereafter by using the nvidia settings mgr and clicking the save button. This actually works for some people... but not me. And now Plymouth comes along and introduces a new fly in the soup. While the chosen resolution might actually be perfect for you login screen and desktop, it is not perfect for Plymouth and so your monitor presents you with the "not support mode" error.

Sorry for the long-winded explanation.

Anyway here's the skinny, in my opinion, if you had installed Ubuntu 9.10 and activated your nvidia driver and then used the nvidia settings manager as described above, everything would have probably worked well for you. But using Ubuntu 10.04 you are going to have to find the right compromise that will first allow Plymouth to function in a usable way, and second provide you with a suitable screen resolution.

My suggestion is to just re-install Ubuntu 10.04 and don't change anything until you get a "REAL" answer here on the forums from one of the Ubuntu guru's. If you choose to experiment with the nvidia settings mgr as described above, be aware that the "not supported mode" is not a complete system error, it is only a problem with Plymouth. If you can get past Plymouth in the beginning, everything else should be ok. However, I could be completely wrong.

---

### Post by trevzilla on 2010-05-19
Well, here is the new stuff...

I gave my computer a night to rest.  Before I tried starting from a fresh install, I tried booting it up again.  Lo and behold, it booted just fine.  No Boot disc error this time.  (And the subsequent times)

Since I was able to boot up, I changed the xorg.conf file to a proper resolution.  1280x720.  I then booted with my regular "livingroom" monitor, and it booted fine.  However, the splash screen was not distorted in any way, and when it booted, the resolution was definitely not 1280x720.  It was still 640x480.

I definitely appreciate your help 4orbs.  Thanks for trying to work through this with me.  If you have any other thoughts or crazy things I might try, I'm all ears...

I have an old Voodoo 3 3000 laying around.  Do you think if I switched out my video cards, from the nvidia geforce ti4400 to the voodoo 3 3DFx, I might have more luck?  Do you even know which card is better?

(This computer is pretty much used for watching streaming movies, and testing ubuntu so I don't really need an amazing video card.  Just working drivers.  ;)  )

---

### Post by 2hot6ft2 on 2010-05-19
> **trevzilla said:**
> However, the splash screen was not distorted in any way, and when it booted, the resolution was definitely not 1280x720.  It was still 640x480.

System > Administration > StartUp-Manager
Set the boot screen resolution on both tabs and the color depth on the first tab. If you don't have it you can install it with:
```
sudo apt-get install startupmanager
```
:popcorn:

---

### Post by 4Orbs on 2010-05-19
Hi trevzilla. I'm totally baffled that you were able to boot back into your system... but it's good news. I'm also very hesitant to offer any suggestions for fear of sending you back into a horrible situation. Still, I'll tell you what I would do if this was my computer. I think you are best off keeping the nvidia card simply because nvidia has the best reputation for working well with Linux.

It looks possible that your card and monitor MIGHT just work well together by using the nvidia settings manager rather than manually adding the xorg.conf file. If you're willing to take the risk, this is what I would do.

1. Save the current xorg.conf file as a backup by entering in the terminal:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
but don't reboot yet.

2. Run this command in the terminal so nvidia will create it's new, initial xorg.conf file:
```
sudo nvidia-xconfig
```
but don't reboot yet. This step will give you an error (warning) saying no xorg.conf file was found, so a new one was created. which is what you want (in other words, it's a good error)

3. Open the nvidia settings mgr as root:
```
gksudo nvidia-settings
```
and open the X Settings Configuration tab and set the resolution and refresh rate both to Auto.

4. Click the "Save Settings" button and save the settings to /etc/X11/xorg.conf and if asked choose to merge the settings with the current xorg.conf file.

5. Now if any of these steps returns an error (except for step #2), don't reboot, but come back here and let me know what happened. If you don't get any errors for these steps, reboot and cross your fingers.

---

### Post by trevzilla on 2010-05-20
Well, here is the news...

First, I want you to know that you shouldn't be hesitant about any help you are offering.  A little about my computer that I am working on...This machine is literally a test machine.  I've heard so many good things about Ubuntu, that I want to make the switch for my regular computer.  However, I wanted to test a few things before making that switch.  I have an extra "junker" computer in my living room that I pieced together from spare parts.  There is no important data on it whatsoever, and it's main purpose is to dink around with it.  So, if something goes terribly wrong, I'm not too worried about it.  Probably nothing a fresh install wouldn't fix.  :)

Secondly, I have successfully run those last commands you gave me, with no extra warnings or errors.  Everything went exactly how you said it would...(Except I didn't get the option to turn the refresh rate to Auto...It was grayed out, but grayed out on Auto)  It seemed that those two options have been on Auto this entire time though...  I didn't have to change anything there.

But I did save the file, and merge it with the new xorg file, crossed my fingers and rebooted.

Alas, still no luck.  I'm currently typing this on a huge resolution.  (What I am assuming is still the 640x480 size)

I can't imagine this is a problem, as this whole issue seems to be a driver issue paired with a widescreen monitor...But just so you know, my "monitor" is a Rear Projection Zenith T.V.  I had windows installed on this computer prior to the switch to Ubuntu though, and it worked just fine with this T.V.  I got a very nice 1280x720 resolution when I was working in windows.

Once again, Thank you for all the help!  Maybe I can buy you a beer via paypal or something if we get this thing working!  :)

Trev

---

### Post by 4Orbs on 2010-05-20
I kinda didn't expect it to work, but the good thing is that you didn't get the "not support mode" error. 1280x720 is a HDMI resolution (for HD television) and I don't think any of those HDMI resolutions will work because (if I understand correctly) your video card doesn't support HDMI, but maybe if you try only VGA resolutions it will work. You might try other resolutions available through the nvidia settings manager, as root each time rebooting after saving. From what I read on other forums the 1366xwhatever resolution seems to be the best choice. My guess is that any resolution which works with your card and TV is going to cause Plymouth to give the "not support mode" error. Catch 22 situation. Windows works with HDMI resolutions because it buffers the resolution or driver to compensate (or something like that, it's all way over my head).

EDIT: And if any of the other resolutions do cause a change, but appear weird (like not filling the screen or split in half, etc) then keep that resolution and try changing the refresh rate with said resolution. Save (as root) and reboot each time you make a change.

---

