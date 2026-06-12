---
title: "No sound with Cheese when doing video recording"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by linuxneeewb on 2009-05-04
Hello. I am using Ubuntu 9.04 64 bit edition, and I recently was able to get the video recorder working in the program Cheese Webcam Booth. My problem is that while I can get the webcam to make videos of images, I cannot get it to record sound. Any help is appreciate with getting the webcam program to record sound with the videos. I know that I can make videos with audio in Windows Vista, so I assume that I can do it in Ubuntu.  

Thanks

:guitar:

---

### Post by kpkeerthi on 2009-05-04
Double-click on the speaker icon in the tray and check if mic is muted

---

### Post by linuxneeewb on 2009-05-04
My sound is fully up. Mic is not muted. I wish the problem were that simple. 

:guitar:

---

### Post by Potters Son on 2009-05-09
Can you record using Audacity? I know that I can't get sound in Cheese, but I can't get it Audacity either.

---

### Post by bob12564 on 2009-07-20
I'm having the same problem.  I think the problem is that the built-in mike is a USB device and enabling "microphone" in the sound mixer won't work.  Webcams are USB devices and you don't plug anything into the computer's microphone jack.  My webcam works fine in Skype but I get a USB device listed in the "sound in" list.  I haven't figured out what to select to get Cheese working.  The video is fine.

---

### Post by slughappy1 on 2009-07-29
I am also running 64 bit Jaunty. I have a Logitech QuickCam Pro 400. I was able to get video AND sound in Cheese finally. I had to go into System -> Preferences -> Sound. Then under "Audio Conferencing" I had to change the "Sound capture:" I changed it to USB Device ... USB Audio (ALSA). The OSS version didn't work, and none of the other choices did anything. Hope that can help.

---

### Post by bob12564 on 2009-07-29
That did the trick!  Thank you.  I have sound now.  

However, the video is very slow and jerky along with the sound when set at 640x480.  I'm using A Logitech QC3000 for Business.  320x240 resolution was much better.  Any ideas on what is causing the video problem at full resolution?

---

### Post by slughappy1 on 2009-07-30
I'm glad that helped. I have no idea why it would be jerky. Perhaps not so great drivers?

---

### Post by jbiggs12 on 2011-02-26
I realize that this is a bit late, but those looking for help on getting cheese to be un-jerky should try lowering their resolution in their preferences.

---

### Post by felixq78 on 2011-05-07
> **Potters Son said:**
> Can you record using Audacity? I know that I can't get sound in Cheese, but I can't get it Audacity either.

If you're getting video in Cheese check that your audio has the USB cam selected for audio.
Left click on the speaker icon at top panel
Left click "sound preferences"
Left click the "input" tag and then select your webcam from the list.

---

### Post by rx007 on 2011-05-07
> **felixq78 said:**
> If you're getting video in Cheese check that your audio has the USB cam selected for audio.
Left click on the speaker icon at top panel
Left click "sound preferences"
Left click the "input" tag and then select your webcam from the list.

this one did the trick for me. :)

---

