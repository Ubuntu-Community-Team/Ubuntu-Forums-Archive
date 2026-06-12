---
title: "Saving audio configuration"
date: 2010-12-31
forum: New to Ubuntu
---

### Post by Nagle75 on 2010-12-31
For some reason I'm having trouble saving my audio configuration. Sometimes when I turn on my machine, it's loud as hell. When I go into the sound preferences & click on the "Hardware" tab it shows me the onboard audio, video card, & the Audigy sound card. When I click on the card & then test the speakers, it works, but then when I close out of the preferences & then reopen them & go back to the hardware tab, once again, the onboard audio is highlighted instead of the audigy card. When I go into the "Output" tab, the Audigy card is selected. Am I to assume that the card is being used, as long as the hardware tab is showing me that the card is selected?  Also, if I go into the "Applications" tab, it shows me 2 things... "Output Volume" & "ALSA-plug-in[wine-preloader]. Are these 2 things separate? I'm not sure which is the main one I should be adjusting. Thanks in advance for your time :)
[http://www.flickr.com/photos/dharma_bum07/5310255204/](http://www.flickr.com/photos/dharma_bum07/5310255204/)
[http://www.flickr.com/photos/dharma_bum07/5310255086/](http://www.flickr.com/photos/dharma_bum07/5310255086/)
[http://www.flickr.com/photos/dharma_bum07/5310254966/](http://www.flickr.com/photos/dharma_bum07/5310254966/)
[http://www.flickr.com/photos/dharma_bum07/5310254852/](http://www.flickr.com/photos/dharma_bum07/5310254852/)

---

### Post by cariboo on 2010-12-31
Is there no way you can disable the internal sound card in the bios? If not, you can use alasmixer to select what sound card to use. Open a terminal and type:

```
alsamixer
```

Press F6 to select your sound card, then use the arrow keys to set the sound levels. Once you are happy with the settings, press esc to exit alsamixer. Next in the same terminal type:

```
sudo alsactl store
```

to save the settings.

---

### Post by Nagle75 on 2011-01-01
Thanks for the commands! It's good to know how to access ALSA like that. Seeing ALSA-mixer, helped me understand that I was indeed using my sound card, like I wanted. I still think that the sound preferences are slightly confusing... under the "Applications" tab I had both the "Output" & "ALSA plugin" turned down below halfway. I did follow your directions, so I'm hoping that locked it in. I think it would be less confusing if there were simply one switch for adjusting the audio instead of 2. Thanks for your help :)

---

### Post by Nagle75 on 2011-01-01
UPDATE...

I just restarted & my speakers didn't blow me away, so it must have saved the settings. Thanks again! :)

---

