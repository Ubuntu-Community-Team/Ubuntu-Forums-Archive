---
title: "how to get mic working in skype"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by DarinB on 2009-04-18
i am trying to get a mic working in skype
i have a mic the mic was off on the sound preferences i turned on but the recording capture turns of by defult i don't know if i need it also the device is the hda nvidia alsa mixer, do i change that at all?
not sure what to do.

---

### Post by Tobine on 2009-04-18
[http://techtavern.wordpress.com/2009/03/18/skype-on-ubuntu-810-microphone-and-internal-speaker-issues/](http://techtavern.wordpress.com/2009/03/18/skype-on-ubuntu-810-microphone-and-internal-speaker-issues/)

---

### Post by DarinB on 2009-04-18
any ideas didn't work

---

### Post by DarinB on 2009-04-19
I am wondering why i am using ubuntu for the first time since feisty.
i got a mic to skype a friend over seas and it doesn't work i want e da camera to see my elderly mother doesn't work.
i boot up to my vista partition and boom it works, now that sucks really bad.
SOOOO 
I use intrepid, i plugged in the mic
set the volume settings set to hdnvidia alsa mixer by default i set the mic vol, mic boost, aux,,,,,the mic capture turns off when i close the app and i have to turn it on and leave the window minimized,,,,, 

On skype i set the sound options to pulse all sound in sound out ring the test fails.
i have libpulse0, libpulse-browse0.libpulsecore5,libpulse-mainloop-glib0 installed.

so now what????? please help i am very upset to have to go to wondows just to do something so basic like use a mic????????

---

### Post by acimmarusti on 2009-04-19
skype doesn't work well with pulse. It works best directly with ALSA. So in audio settings, I think it is best if you choose your sound card (plughw for output and hw for input) instead of pulse.

Due to this conflict, skype sound won't work when you are also running another application that uses pulse, such as firefox (in case you are watching a video or listening to music), rhythmbox, totem, etc. You have to run it "alone"

For the webcam, post the output of these commands:

```

lsusb
lsmod

```

---

### Post by DarinB on 2009-04-19
the sound works great and there is no conflict it is the mic only, and the pulse (plughw for output and hw for input) come up with audio problems and the test won't complete. 
regarding the web cam i returned the last one which was the fourth camera i tried. 
can you recommend a web cam?????

---

### Post by acimmarusti on 2009-04-19
I suggest you get a UVC webcam. This is a list of cameras that work (the ones with the green checkmark beside them)

[http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)

I own a logitech quickcam pro for notebooks 2007 model and both the cam and the built-in mic work well in skype. And right out of the box too! (there is no need to further tweaking).

I never said you should set your audio settings to pulse!...choose your soundcard from the list!..if you are not sure, then post the options available to you for both output and input and I will tell you which one to choose

---

### Post by DarinB on 2009-04-19
using the settings you suggested (plughw for output and hw for input) instead of pulse and i was sure to close all apps except the vol preference to make sure the recording capture was on and it didn't work, I wonder if it isn't something really simple i am missing. i do have the aux on in the sound volume preferences?

---

### Post by acimmarusti on 2009-04-19
please post your audio options for output and input

---

### Post by DarinB on 2009-04-19
skype options 
sound in
and sound out hve the same choices
         default device
         HDA NVIDIA (hw:nvidia,0)
         HDA NVIDIA (plughw:Nvidia,0)
         HDA NVIDIA (hw:nvidia,1)
         HDA NVIDIA (plughw:nvidia,1
         HDMI
         headset
         pulse
   Is this what you want? here is my voloume preferences HDA NVIDIA (ALSA MIXER)

---

### Post by superprash2003 on 2009-04-19
i had a similar problem too.. just try various random combinations.. of the sound in of skype and the Sound capture of system->preferences->sound

for reference : [http://www.prash-babu.com/2009/04/how-to-fix-sound-in-and-sound-out-in.html](http://www.prash-babu.com/2009/04/how-to-fix-sound-in-and-sound-out-in.html)

---

### Post by Jazzy_Jeff on 2009-04-19
I had a lot of the same problems. It turned out to be pulse messing things up. I uninstalled pulse and just use alsa and everything works fine now.

---

### Post by XubuRoxMySox on 2009-04-19
**Skype recommends using a [COLOR="Purple"]USB headset[/COLOR].** I haven't tried it yet, but according to others a USB headset should "just work" without any other configuration.

-Robin

---

### Post by DarinB on 2009-04-19
no mine did not work 
what pulse do i uninstall
libpulse0?
libpulse broswer 
libpulse ?????

---

### Post by DarinB on 2009-04-19
i removed pulseaudio no change still wont work. any ideas any body????????
should i reinstall pulse audio?

---

### Post by Jazzy_Jeff on 2009-04-19
The settings I use in Skype are  HDA ATI SB (hw:SB,O) for my sound in. For sound out it is set to Default device (default).

Also go into your sound settings (double click on your sound volume in the upper right corner.) Make sure you see your Microphone and Mic Boost listed. If your using your front mic then make sure they show as well. Then under the options tab make sure the Input source is Mic or Front Mic depending on which one you are using. If it says the one you are using, click on it and change it and then change it back. For some reason I have to do this sometimes for it to work. 

Let us know if this helps.

---

### Post by acimmarusti on 2009-04-19
Yes, perfect, now post the output of these commands:

```

cat /proc/asound/cards

arecord --list-devices


```

---

### Post by DarinB on 2009-04-19
darin@darin-desktop:~$ cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xd6000000 irq 23
darin@darin-desktop:~$ arecord --list-devices
**** List of CAPTURE Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
darin@darin-desktop:~$ 
thanks for the help this is driving me crazy

---

### Post by acimmarusti on 2009-04-19
Ok, try this:

Set as ring and sound output
HDA NVIDIA (plughw:Nvidia,0)

And as input:
HDA NVIDIA (hw:nvidia,0)

Click apply and test sound and test call (be sure to close any other apps).
If mic fails then do this:

```

alsamixer -c 0

```

There follow this instructions:

> 
Be sure to unmute the capture channel, else no sound will be recorded anywhere.

Useful Alsamixer commands:

    * To toggle mute/unmute on a channel, navigate to it using arrow-keys, and press m or M to mute/unmute on both channels.
    * To toggle mute on the right of the stereo channels, press ">".
    * To toggle mute on the left of the stereo channels, press "<".
    * To show the capture-controls only, press F4.
    * To toggle the capture facility, press [space]. 


---

### Post by DarinB on 2009-04-19
ok I went to terminal and alsamixer -c 0 when i pressed F4 for the capture controls only four things where on the screen **line**, which showed no volume above it **mic boost**, **Capture** and **Digita**l all of the above did not show the 00 or the MM the option was not there. i tried with the option settings above but it did not work. at least i feel like i am doing something? now what?

---

### Post by acimmarusti on 2009-04-19
ok try moving with the right/left arrows to the capture column and then increase the volume by using the "up" arrow until you get about 80 in volume. Now using the arrows also move to the mic boost column and press space to activate it. If you can also increase the "volume" of this.

Hopefully this will help, if not, double click on the sound icon on your upper right. You will see a column for the microphone. Make sure it's not muted and raise the volume. Then click on preferences: now check the boxes with "capture, microphone capture, mic boost 20dB" and new tabs besides playback will appear. click on them and enable capture, increase volume and unmute. If you still get nothing then enable mic boost.

This should work...if not try testing the mic using Gnome sound recorder and tell me if it works. If not consider going back to Hardy (I successfully used my sound cards' mic in hardy, but I actually haven't tried on intrepid, because I've using a usb one built-in my webcam, which in turn didn't work well in hardy....but that's another story)

---

### Post by DarinB on 2009-04-20
no doesn't work, bummer could it be the pulse audio?

---

### Post by acimmarusti on 2009-04-20
sorry to hear that. I don't really know which one is the culprit, skype or pulseaudio. I believe both bear some of the guilt. Consider getting a usb mic. Also you could back to Hardy or try out Debian Lenny 5.0 (which has no pulseaudio by default!! :-) )

---

### Post by gandaran on 2009-04-20
> **DarinB said:**
> no doesn't work, bummer could it be the pulse audio?
some PC's with ubuntu have pulseaudio problems, maybe this is your case, you could try fixing pulseaudio maybe it'll work! if you are up to it follow this [guide]("http://ubuntuforums.org/showthread.php?t=789578") .

---

### Post by w0ipl on 2009-04-20
I upgraded to 8.10 just before trying Skype. Drove me knutz!

What finally worked for me was to go in and change all settings to pulse AND disable auto-adjust within Skype.

I tried it with the auto-adjust on and got just a trace of audio from the microphone, readjusted the levels and tried again. Same result so I looked at the settings and found they had been re-set. Turned off the auto-adjust, reset the mic. level and every thing is working.

Something about even a blind squirrel can occasionally find an acorn in the grass. :D

System > Preferences > Sound > Device > Sound Capture to PulseAudio was the setting I missed. That and no auto-adjust fixed it.

---

### Post by J1m on 2009-05-15
Hi Guys,

I updated my ALSA version using this tutorial [http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/](http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/)

I changed all my sound settings in preferences > sound to use ALSA.

I changed ALL my sound settings in Skype to HDA Nvidia (hw:Nvidia,0) thats capture, voice and ring.

Everything is working a treat :)

Hope that helps.

Jim

---

