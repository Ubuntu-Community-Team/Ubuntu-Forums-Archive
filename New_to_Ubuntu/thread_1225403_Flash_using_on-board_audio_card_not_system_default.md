---
title: "Flash using on-board audio card not system default"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by Commander_Bob on 2009-07-28
I recently upgraded to a X-Fi Titanium sound card. I installed the drivers and I have sound in everything except firefox, mainly flash.

I have the system default set to the X-Fi card and rhythmbox uses it, however the audio from flash videos and apps comes out of the onboard audio card.

I know this has been an issue in the past but I could not find any fixes for Ubuntu 9.04.

Thanks,
Justin Rajewski

---

### Post by daimaru on 2009-07-30
try this: install "PulseAudio Device Chooser"
```
sudo apt-get install padevchooser
```While on a youtube page (for example) go to "Applications>Sound&Video>PulseAudio Device Chooser" select "Playback" tab right click on the audio slider and choose your desired sound card as output module. You should be able to set your preferred sound card as default on the "Output devices" Tab (right click again). This worked for me using onboard sound and usb headphones.  When i had no audio in youtube (using headphones) I switched the device under pulse audio chooser and sound worked fine.

Another way;:
If your not using your onboard sound at all, and dont want problems resulting from it being activated just deactivate it under your bios settings.

---

### Post by Commander_Bob on 2009-07-30
Ya, I just deactivated it from the bios. The mic and headphone jacks on the front of my case won't work now but there should be a way to connect them to the card. However Creative does not give the pinout, so I'll have to do some work on that.

Thanks for the help,
Justin

---

