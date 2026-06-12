---
title: "my sound will not work"
date: 2010-03-24
forum: New to Ubuntu
---

### Post by thelostubunt on 2010-03-24
Hi
my sound in ubuntu is not working. Also this is the only place i can figure out how to post a new  topic please help.

---

### Post by garvinrick4 on 2010-03-24
> **thelostubunt said:**
> Hi
my sound in ubuntu is not working. Also this is the only place i can figure out how to post a new  topic please help.
      This works for me everytime I do fresh install or upgrade. Give it a crack. Do not forget to reboot when finished.                         

   [COLOR=#000000][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]sudo apt-get install ubuntu-restricted-extras gstreamer0.10-ffmpeg gstreamer0.10-pulseaudio gstreamer0.10-alsa gstreamer0.10-plugins-good gstreamer0.10-plugins-base gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse[/SIZE][/FONT][/COLOR]
 

 [COLOR=#000000][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]sudo apt-get install libasound2-plugins padevchooser libsdl1.2debian-pulseaudio[/SIZE][/FONT][/COLOR]
 

 

 [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2][SIZE=4]**Part A: Common instructions (Hardy, Intrepid, Jaunty & Karmic)**[/SIZE]
*All users must must follow the steps in this section to guarantee a fully working PulseAudio configuration.*

1. Backup (and then delete) your previous configuration files: [/SIZE][/FONT][/COLOR] 
  [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Code:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ rm -r ~/.pulse ~/.asound* [/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ sudo rm /etc/asound.conf[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2][COLOR=#ff0000]**Warning:**[/COLOR][COLOR=#ff0000] As always, use caution when removing files on your system. Any typos can potentially cause data loss.[/COLOR]
[COLOR=#0000ff]**Note:**[/COLOR][COLOR=#0000ff] Don't worry if some of these files did not exist on your system.[/COLOR]


2. Ensure you have the necessary PulseAudio libraries and configuration utilities installed:[/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Code:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000] [FONT=Verdana, Arial, Tahoma][SIZE=2]$ sudo apt-get install libasound2-plugins padevchooser libsdl1.2debian-pulseaudio[/SIZE][/FONT][/COLOR] [[COLOR=#444444][FONT=Verdana, Arial, Tahoma][SIZE=2]_3_[/SIZE][/FONT][/COLOR]]("https://bugs.launchpad.net/bugs/192888")[COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]. Ensure the evil "libflashsupport" library is [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]**not**[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2] installed: [/SIZE][/FONT][/COLOR] 
  [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Code:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ sudo apt-get remove --purge libflashsupport flashplugin-nonfree-extrasound[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2][COLOR=#0000ff]**Note:**[/COLOR][COLOR=#0000ff] the libflashsupport library was (and to a certain extent, still is) the most common cause of Firefox instability since the Hardy release, because many users have been misled into thinking they must install it to ensure Flash & PulseAudio can work correctly. If you notice any postings that recommend this library to be installed, please reply to the post and point them to this thread, or the bug report linked. The more people that are aware of this issue the better. Thanks![/COLOR]

4. (Karmic users - please skip this step, it's not necessary). Open System/Preferences/Sound. In the Devices section, ensure that all "Sound playback" options are set to Autodetect. Set the "Sound capture" item to "ALSA", or the appropriate hardware definition. Close the application when you're finished.
[COLOR=#0000ff]**Note:**[/COLOR][COLOR=#0000ff] Choosing PulseAudio for sound capture may result in crashes, so you are advised to choose the "direct" ALSA device instead.[/COLOR]

5. Open the PulseAudio Volume Control application ("pavucontrol", or you can launch "Applications/Sound & Video/PulseAudio Device Chooser" and select Volume Control from this applet's menu). In the Output Devices section you will see a listing of the playback devices available on your system. Right-click on the entry that you desire to be made the default playback device on your system and enable the "Default" checkmark. Similarly, navigate to Input Devices, then right-click on the device you wish to set as your default input device (microphone), and ensure the "Default" setting is checked. Close the application when you're finished.

[COLOR=#0000ff]**Note:**[/COLOR][COLOR=#0000ff] If you are greeted with the error "Connection failed: Connection refused", manually launch PulseAudio before opening the PulseAudio Volume Control application:[/COLOR][/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Code:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ pulseaudio & pavucontrol[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]6. Ensure that your sound card's PCM mixer is not muted or set to 0% volume (this appears to be a common bug in Intrepid and Jaunty):[/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Code:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ alsamixer [COLOR=#0000ff]-Dhw[/COLOR][/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2][COLOR=#0000ff]**Note:**[/COLOR][COLOR=#0000ff] When the PulseAudio ALSA plugins are active, you must explicitly specify your hardware device in alsamixer (marked in blue above), otherwise it will open the PulseAudio mixer.[/COLOR]

7. Continue to **Part B** if you are running Hardy Heron (8.04), or **Part C** if you are running Intrepid Ibex (8.10). If you are running Karmic Koala (9.10) or Jaunty Jackalope (9.04), you're finished - log out and back in for changes to take effect![/SIZE][/FONT][/COLOR]


[COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Reboot machine to make sure takes effect.
[/SIZE][/FONT][/COLOR]

---

### Post by thelostubunt on 2010-03-24
it still douse not work

---

### Post by grouchyolddude on 2010-03-24
> **thelostubunt said:**
> it still douse not work
this was a simplt fix for me 
 
> 
sudo apt-get remove pulseaudio
then
> 
sudo apt-get install esound
reboot ..
fixed the issue entirely for me..

EDIT: I did have to go into systems-preferences-sound and put everything on alsa from the drop menu

---

### Post by vedek on 2010-03-24
can you give us abit more info, is a laptop with inbuilt speakers or is it a desktop with external speakers, or a headset?

if it is a laptop and a desktop try to see if it is being picked up by doing the following. 

Click on to [B]Applications -> Accessories -> Terminal.

[/B]A black window with appear then type in ```
 lspci
```and just post the results in the next post.

---

