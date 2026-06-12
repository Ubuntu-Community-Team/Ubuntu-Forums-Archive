---
title: "Help me, please!  I'm about to get rid of Ubuntu, I'm so frustrated!"
date: 2009-04-06
forum: New to Ubuntu
---

### Post by Murderuption on 2009-04-06
Since upgrading to ubuntu, I've had numerous problems.  

1) Only one speaker works on my laptop
2) The headphone jack won't work
3) When typing, the line that indicates where I'm typing tends to jump around, causing me to **** up my research papers.

Could anyone please help me?  The third thread I have started and no one cares to respond.

---

### Post by balloooza on 2009-04-06
Ok first the line that indicates the reserch paper, can you tell me as much as you can, is it JUST openoffice, or everywhere

I can also help you with the audio problem, have you ever opened the voloume conntroller

---

### Post by Murderuption on 2009-04-06
It's not just in open office.  Yes, I have opened the volume control and tried adjusting the balance and everyything.  No luck.

Thanks a whole lot.

---

### Post by Murderuption on 2009-04-06
Well, you know how there's a vertical line as you type?  The kind indicates where you are?  Well, it jumps around.  One minute it'll be right here :: and the next minute, it'll jump to the end of this line ^ or somewhere else causing my words to look like thokayis.

---

### Post by inxygnuu on 2009-04-06
Mine does that too. What kind of laptop do you have? that may be of help.

---

### Post by Temposs on 2009-04-06
Your issue with the cursor(that's what the vertical line is called) may be from you accidentally tapping your touchpad with your wrist as you type. Are you using a laptop with a touchpad? Can you tap to click? If this is the case, you probably want to turn off the tap clicking.

---

### Post by Murderuption on 2009-04-06
I have a Gateway.

---

### Post by mechoid9 on 2009-04-06
Hmm...

Which Audio Driver are you using?

---

### Post by Murderuption on 2009-04-06
how would i turn off tap clicking?

---

### Post by Temposs on 2009-04-06
> **Murderuption said:**
> I have a Gateway.

Saying you have a Gateway isn't particularly helpful. You need to give the particular model that you have.

---

### Post by Murderuption on 2009-04-06
HDA Intel is the audio driver.

---

### Post by Murderuption on 2009-04-06
It's a Gateway M-Series.

Thanks.

---

### Post by Mulenmar on 2009-04-06
> **Temposs said:**
> Your issue with the cursor(that's what the vertical line is called) may be from you accidentally tapping your touchpad with your wrist as you type. Are you using a laptop with a touchpad? Can you tap to click? If this is the case, you probably want to turn off the tap clicking.

That's always been the problem on my laptop. There's a function in the BIOS menu (what comes up when you hit F1 or whatever button it says to enter Setup) on mine to disable the trackpad, but be careful looking in there.

I assume (stupid question here) that the speaker worked before (in Windoze)?

---

### Post by Twitch6000 on 2009-04-06
> **Temposs said:**
> Your issue with the cursor(that's what the vertical line is called) may be from you accidentally tapping your touchpad with your wrist as you type. Are you using a laptop with a touchpad? Can you tap to click? If this is the case, you probably want to turn off the tap clicking.

This is indeed his problem with the verticle line,I know from experience sadly lol..

As for your audio only half way working put in your headphones then go to sound devices and mess around with what sound settings to use.

Normally OSS or ALSA work best.

---

### Post by Murderuption on 2009-04-06
The headphone jack doesn't work.  :(

---

### Post by Temposs on 2009-04-06
> **Murderuption said:**
> how would i turn off tap clicking?

Open a terminal with Applications->Accessories->Terminal. Type this:

```
sudo apt-get install gsynaptics
```

After you type in your password and the install process is finished, go to System->Preferences->Mouse, and click the Touchpad tab. Make sure that "Enable mouse clicks with touchpad" is not checked. If it is, uncheck it. Then touching your touchpad will no longer register a click.

---

### Post by Murderuption on 2009-04-06
Done.  Thanks a whole lot. :D  Hopefully, it'll solve that problem.

What about the headphone jack and speaker problems?  Do you know anything about that?

Thank you.

---

### Post by SunnyRabbiera on 2009-04-06
> **Murderuption said:**
> The headphone jack doesn't work.  :(

Does it have any other output jacks?
Speakers?
I have an issue with my front headphone jack, thats why I use my back jack for sound.
It could be a device that is linux unfriendly, would not be surprised as its a gateway.

---

### Post by Murderuption on 2009-04-06
It's a laptop and only has a mic jack and a headphone/speaker jack. :(

---

### Post by sneeks on 2009-04-06
> **Murderuption said:**
> It's a laptop and only has a mic jack and a headphone/speaker jack. :(

ahh,had this a little while ago,have you fully opened the volume control panel and ticked all the boxes that apply to you,if you have not do so,and adjust the jack in question..
hope it helps..

---

### Post by Murderuption on 2009-04-06
what do you mean?

---

### Post by Hellstudios on 2009-04-06
if you have a dual boot of windows and ubuntu just pop in the ubuntu live CD go to 


system >> admin >> partition editor


delete the ubuntu partition then reformat it to FAT32, reboot, and you should be good to go.


(by the way the new partition will be detected as another hard drive)


sorry ubuntu didn't work out for you.

---

### Post by Murderuption on 2009-04-06
i don't have a dual boot and i don't want windows.  it sucks.  i like ubuntu, there's just stupid little problems that pop up.

---

### Post by lhb1142 on 2009-04-06
:KS May I suggest that you go here:

< [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) >

and scroll down to near the bottom of the page where you'll see the header:

--PART 5/5, MISCELLANEOUS & TROUBLESHOOTING--

Under "Various Tips and Tricks," after "Firefox Add-ons" and "Firefox Fonts," you'll see "Laptop Touchpad," the instructions for which are version-specific.

These instructions should help you with your cursor "jumping" problem.

This Comprehensive Multimedia Guide may also help you with your audio problems.

When I right-click on my Volume Control icon (at the right side of the top panel), I do NOT click on "Preferences," but, rather, I click on "Open Volume Control."

Within that box, at the lower right, you will see another "Preferences" choice on which to click. (I always make sure that every choice within that "Preferences" is activated so I can see the whole picture).

This may show you any untoward setting(s) which may be present. Among other things, make sure that your Headphone setting is not muted and that all settings DO have their channels "locked" together so that one side cannot be attenuated individually (you do not want adjustments to be able to be made to individual channels except in certain unusual situations). In other words, when you attenuate any of the choices (Master, Headphone, PCM, etc.), both of the channels should operate together.

I hope that this is of some help to you. ):P

---

### Post by Hellstudios on 2009-04-06
> **Murderuption said:**
> i don't have a dual boot and i don't want windows.  it sucks.  i like ubuntu, there's just stupid little problems that pop up.

Thank God. :p

---

### Post by Temposs on 2009-04-06
If the above ideas don't work for you, try this:

I'm seeing some folks around the forums saying that their headphone jack will actually work if it's plugged in when the computer is turned on. Why don't you try plugging in your headphones and restarting the computer. See if your headphones work then.

If it works, it'll at least provide a partial solution while you search for a better solution.

---

### Post by Murderuption on 2009-04-06
None of the aforementioned seems to be working.  Any help?

---

### Post by lhb1142 on 2009-04-06
:KS  The only further suggestion I can make is to "wipe" your computer (using DBAN or similar) and then do a clean standard re-install of Ubuntu (preferably v. 8.10). Hopefully that will allow all functions of your computer to work normally.

I understand that on rare occasions the installation of Ubuntu (or any other operating system) does not proceed smoothly, for whatever reason. A second installation, as I have described above, should proceed without difficulty.

I wish you the best of luck. ):P

---

### Post by albinootje on 2009-04-06
> **Murderuption said:**
> None of the aforementioned seems to be working.  Any help?

Are those normal headphones or usb headphones ?
Several weeks ago I've done some research before buying usb headphones, and after I bought the compatible-with-Linux headset I had some problems making them work.
I had to go into -> System -> Preferences -> Sound, and make some changes because the autodetect didn't work with it.

Are you using a newer Ubuntu release ? At a certain moment Ubuntu switched to pulseaudio as the default sound software, but you still have the option to try Alsa, and OSS.

---

### Post by albinootje on 2009-04-06
> **lhb1142 said:**
> :KS  The only further suggestion I can make is to "wipe" your computer (using DBAN or similar) and then do a clean standard re-install of Ubuntu (preferably v. 8.10).

If you want to do this, then I recommend at least testing the "try without installing" option of an Ubuntu Jaunty Beta desktop cdrom.
Jaunty is looking very good I think, and it's only a few weeks before it will be officially released. 
Just give it a try, why not ? You can try without installing :)

---

### Post by Volt9000 on 2009-04-06
Try this: double-click the speaker icon in your systray to bring up the volume control. Choose your device from the drop-down list at the top then select the Playback tab. Click the Preferences button and look for anything that looks like it may pertain to the headphone jack, and place a checkmark next to that. If in doubt, just place checkmarks next to all "Playback" items listed. When you click Close the volume control window should be updated with the selected devices. Crank up the volume on all of them and click Close, then try out your sound again.

I may just be grasping at straws here, but it may also be possible that Linux sees your headphone output as a separate device. In that case go to System > Preferences > Sound and under Music and Movies choose a specified device, instead of "Autodetect". Try different devices, as it may be one you don't suspect.

---

### Post by krzysz00 on 2009-04-06
Try getting rid of pulseaudio
```
sudo apt-get remove pulseaudio
```

---

