---
title: "Problems after upgrading to 11.04."
date: 2011-04-30
forum: New to Ubuntu
---

### Post by enetic on 2011-04-30
Im having some problems after i upgraded to 11.04 on my computer. The thing is that the microphone is not working, and the volume applet is gone. And, yes, I have tried adding "indicator applet" to the panel, but its gone..

---

### Post by rvchari on 2011-04-30
> **enetic said:**
> Im having some problems after i upgraded to 11.04 on my computer. The thing is that the microphone is not working, and the volume applet is gone. And, yes, I have tried adding "indicator applet" to the panel, but its gone..

i am currently trying natty thru my usb stick. it is as of now functioning well. initially i too had sound problems and video problems. (i am currently using 32 bit maverick on my hdd) and i am running 64 bit natty thru my usb stick.

i simply double click on the audio / video file and made it to play thru the default media player. be sure you are connected to the internet. if sound (alsa) is configured then it will play by default. if some plugins are missing it will automatically install. i solved this problem like this... may b u ll find a solution too.

i wish to go for a clean install of natty once all the hitch is cleared, so i decided to keep using it thru the usb stick. another new thing for me is the unity 2d... have to get used to this system. i also installed awn for ease of access of my routine apps.


NOTE: if you are using conky then hardware soesor for acpi temp will indicate as "0". edit the conky rc file from acpitemp to hw sensor temp 1. the problem will be solved. (acpi is not functioning in conky) just felt i ll share the info with you

---

### Post by lidex on 2011-04-30
Do you have 'indicator-sound' installed?
Using a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get install indicator-sound
```
Reboot. 

Mic:
> Changing default subdevice configuration

    Some sound devices have multiple capture subdevices (eg. hda-intel), but pulseaudio only seems to detect the parent device, and only listens to subdevice #0. ALSA may not be configured to use your preferred device as subdevice #0 by default.

        Open the pulseaudio record meter (pavumeter --record)
        Talk into your chosen device while you carry out the process and watch the meter.
            Some channels are quite noisy even with no input (especially on integrated chipsets), so we are watching for movements that correspond to our voice. 

        Use alsamixer -c n (where n is your sound card number, probably 0)
            Press F4 to get to the capture console
            Make sure the first capture channel is enabled ("CAPTUR" in red, press space to toggle), and the volume turned up.
            Check the first input source is switched to your chosen plug (Mic, in my case) 
        At this point, you should see the record meter bouncing in response to your voice.
        I found that I had to repeat this procedure each time I wanted to use the Mic, even though the settings "stuck" in the mixer, something in the soundcard wasn't initialized until it was repeated.
        This also works if you use the "Options" tab in the standard mixer app to do the same thing. 

---

### Post by enetic on 2011-05-02
> **lidex said:**
> Do you have 'indicator-sound' installed?
Using a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get install indicator-sound
```
Reboot. 

Mic:

Yea, thank you, it turned out that it was removed for some reason, so I installed it again. 

Still having problems with the microphone though. I tried the commands in your quote, and it seems like the microphone may be muted or something, but it doesnt show in the "sound preferences", so im not really sure what to do to fix it... ?

Anyone?

---

