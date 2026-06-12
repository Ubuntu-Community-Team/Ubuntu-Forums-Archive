---
title: "Skype problem"
date: 2009-09-13
forum: New to Ubuntu
---

### Post by solissydney on 2009-09-13
SKYPE PROBLEM

When I first downloaded Skype from the skype site, using an USB VOIP phone I successfully made a test call to Skype. Now however, I can only sign in to skype on my first attempt each time I start the PC, and  even then, I am unable to get  sound on the phone. The message says: Another skype instance may exist. It seems to me that Ubuntu is unable to recognise the USB phone?.
I use Ubuntu 10.1 and System 32. I have searched past skype problems and tried different  advice given then.
The phone does work under Windows.Further, under System Monitor I found three instances of Skype. I killed two. 
The test call to skype results in the voice going to external speakers, but not to my phone.
Two instances of skype now under System Monitor???

---

### Post by expatCM on 2009-09-14
I recently had a bit of bother with skype on a 32 bit machine.  Your problem sounds a little bit similar in some respects.  I would suggest that you uninstall skype and remove all settings.  The download the new .deb from the skype site and install.

This is the thread, for me the solution was right at the very end ....

---

### Post by solissydney on 2009-09-14
I have been trying at lenghtto delete skype, but unable to work out how?

---

### Post by expatCM on 2009-09-14
Depending on what repositories you have enabled you may find an entry in Synaptic ....  right click and select to remove.

Or from the command line

sudo apt-get remove skype

I think that the following will remove skype and also the config files

sudo apt-get --purge remove skype

---

### Post by 3rdalbum on 2009-09-14
You have two problems here.

1. Skype doesn't know where to route its audio. This can easily be solved by downloading the "padevchooser" package and adding "padevchooser" to your startup applications. This puts an icon in your notification area that looks like an audio cable.

When you run the Skype Test Call, left-click this icon and go to Volume Control. Under the Inputs and Outputs tabs, where it gives a volume control for Skype, press the little arrow for more options, and tell it what devices to use for Skype's input and output.

This setting will be remembered for the future.

2. Your other problem is that Skype is not quitting, causing the "Another instance running" error message. By default, when you close the Skype window, it still runs in your notification area (as you will be able to see). If you are using the Quit command and Skype still is present in your system monitor, then you should send a bug report to Skype's developers.

---

### Post by expatCM on 2009-09-14
That looks like a nice suggestion although the latest version of skype seems to solve these problems, especially the sound configuration ....

[http://www.skype.com/intl/en/download/skype/linux/choose/](http://www.skype.com/intl/en/download/skype/linux/choose/)

---

### Post by 3rdalbum on 2009-09-14
> **expatCM said:**
> That looks like a nice suggestion although the latest version of skype seems to solve these problems, especially the sound configuration ....

I'm using the latest Skype and I needed padevchooser.

---

### Post by solissydney on 2009-09-14
Great, thanks. By typing in command line: sudo apt-get remove skype
I managed to remove skype. Now to download and re install.

---

### Post by 3rdalbum on 2009-09-14
> **solissydney said:**
> Great, thanks. By typing in command line: sudo apt-get remove skype
I managed to remove skype. Now to download and re install.

Merely reinstalling software tends not to do anything on Linux. Reinstalling software only works if the problem is a corrupted binary - and that's rare on Linux due to the permissions system. I don't think you have a corrupted binary.

Some good advice given earlier was to delete the Skype preferences, which are stored in the hidden ".skype" folder inside your home directory. This can help if the preferences file is corrupted.

---

### Post by teutonic on 2009-09-14
> **solissydney said:**
> Great, thanks. By typing in command line: sudo apt-get remove skype
I managed to remove skype. Now to download and re install.

When your up and running again remember to quit skype properly with the  quit icon as per pic - if you just click the top right X as 'normal' an instance is left running in the background like the poster said before - i had the same prob as you

[IMG]http://www.ukimagehost.com/uploads/1290e239db.jpg[/IMG]

---

### Post by solissydney on 2009-09-14
I take your points about not re-installing and also how to quit skype.

Clicking on volume control I tried all settings, without success. Which would be the most likely correct setting: playback voip usb phone, capture monitor of usb phone or capture usb phone? Test call to skype results in the recorded voice comes over the ext speakers only.

---

### Post by solissydney on 2009-09-14
Clicking on volume control I tried all settings without success. Which selection would be the most likely correct choice: voip usb phone alsa mix, playback voip usb phone, capture monitor of usb phone or capture usb phone?

---

### Post by solissydney on 2009-09-15
I am getting closer to solving the problem.

I appreciate your assistance very much, warm regards
Ken

---

### Post by xx58 on 2009-09-18
:rolleyes:DON'T use BETA version Skype, because it have many problems, like audio....... Install STABLE Skype version and everything works just perfectly.....

---

### Post by expatCM on 2009-09-18
I note the earlier response (xx58) where it is suggested not to use the beta version.  I agree that it is always good practice to respect that a beta version is not yet final and perhaps subject to the unexpected.

However, in the case of the skype beta I have found on both 32 and 64 bit systems that use of the latest version, even though it is beta has solved so many problems.  Perhaps it has no impact for you but we live in a location where quality Internet connections and reality are not spoken together.  The latest offering from skype is really very good.  At least for us.

---

