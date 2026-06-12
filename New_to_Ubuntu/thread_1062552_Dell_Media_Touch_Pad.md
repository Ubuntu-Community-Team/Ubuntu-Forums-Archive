---
title: "Dell Media Touch Pad"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by mpl34 on 2009-02-07
I have been playing around constantly changing the key shortcuts and have been successfully able to get the mute, decrease volume and increase volume working but without any display showing that the volume has changed or that i have muted the sound.

I have also successfully been able to get the decrease and increase volume to display the change in volume, however although it is displaying a change in volume it does not occur. I have not been able to repeat this for the mute button.

I am running Kubuntu 8.10 and this is about my 7 reinstall and have finally sorted out all the correct drivers and applications i need, (except for these media keys of course). Originally on a previous install these keys were working perfectly.

As far as i can tell it is more of a Kmix (the pre-installed kubuntu software to control the sound device) problem and therefore is specific to Kubuntu only.

---

### Post by HavocXphere on 2009-02-07
lols. Same here. Either it controls the sound or it displays the change. Not both. It seems to be changing and displaying different channels.

What follows is potentially dangerous speculation by a noob.;)

Haven't tried editing anything yet, but looking at ~/.kde/share/config/kmixrc

> [Global]
AllowDocking=true
ConfigVersion=3
**DefaultCardOnStart=ALSA::HDA_Intel:1**
Labels=true
MasterMixer=ALSA::Microsoft_LifeChat_LX-3000_:1
MasterMixerDevice=**Speaker:0**
Menubar=true
MixerIgnoreExpression=Modem
Orientation=Vertical
Position=0,0
Size=840,420
Tickmarks=true
TrayVolumeControl=true
Visible=false
startkdeRestore=true
I'm thinking one of the bold parts is causing the problem. Will try editing those later.

---

### Post by mpl34 on 2009-02-07
The problem has been solved!!

For those who are interested i have fixed the problem by assigning the media keys under "system settings --> Keyboard & Mouse --> Keyboard Shortcuts" (ie. the decrease volume button was assigned to the decrease button, not a specific channel) and then changed the master channel to "front" by right clicking the Kmix icon in the system tray and choosing "select master channel.." and all my volume controls seem to work accordingly.

EDIT: Didn't notice your reply there havoc until after i posted this reply but yer.. looks like the display is used to show the change in the master volume channel which for me was PCM however changing the PCM volume did not change the output of my speaker. However, changing the volume of the front channel did make the correct adjustments to my speaker output therefore by making front my master channel the display was instead used to show the changes made to the front channel. (pretty self-explanatory)

---

