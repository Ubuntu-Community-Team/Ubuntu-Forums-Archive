---
title: "Spotify under Wine choppy playback etc"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by peakshysteria on 2009-10-10
I've just installed Wine and Spotify. I must say I really don't know my way around Wine yet. I've ran in to some boring problems:

1. To open Spotify with Wine I have to open the terminal and:

```
wine "C:\Program Files\Spotify\spotify.exe"
```

Or go to /home/$user/.wine/drive_c/Program Files/Spotify and right-click Spotify.exe and open with Wine. I can't fine another way to run it.

2. Choppy playback. Premium account.

I followed the instructions on the Spotify site:

```
winecfg
```

Go to the Audio tab in the program and click on Test Sound. If you hear something, then you are all set, if an error message appears you have to configure it. Make sure the ALSA checkbox is checked and press OK and restart winecfg (it needs to re-initialize sound drivers) and click on Test Sound again. When you hear something you can continue. If you can&#8217;t get sound to work, it is unlikely you will hear anything in Spotify.

In the DirectSound frame at the bottom enter the following for best sound.

Hardware Acceleration: Emulation
Default Sample Rate: 44100
Default Bits Per Sample: 16
Driver Emulation: unchecked

I have also tried to Enable high bitrate + Use at most 10 GB. Last.Fm scrobbling is also enabled.

And also with no luck: [https://www.spotify.com/en/help/faq/#tech-problemsays:](https://www.spotify.com/en/help/faq/#tech-problemsays:)

[QUOTE]Music fast-forwards or jumps ahead when I play it, what can I do? (Windows Only)
    To solve this problem disable Hardware Acceleration in the system preferences by going to Edit -> Preferences -> and unchecking &#8220;Enable hardware acceleration&#8221;.[QUOTE]

Can anyone help me to make Spotify play smooth and to tell me how to make Spotify appear in applications and or in the panel??

---

### Post by guriinii on 2009-10-10
I don't know how to solve your playback problem but as for the icon in the panel:

copy or drag the spotify.exe or the spotify.ink file into your panel and voilá.

---

### Post by peakshysteria on 2009-10-10
> **guriinii said:**
> I don't know how to solve your playback problem but as for the icon in the panel:

copy or drag the spotify.exe or the spotify.ink file into your panel and voilá.

Thanks man. But that didn't work. I tried the .exe file. No .ink file. I got no icon and I could not open the program.

---

### Post by guriinii on 2009-10-10
If you couldn't open spotify you are having the same problem as me. It's a right pain in the ***. Look at this:

[http://ubuntuforums.org/showthread.php?t=1282339](http://ubuntuforums.org/showthread.php?t=1282339)

Hope this helps.

---

### Post by kostkon on 2009-10-10
To create a menu item in your menu or a shortcut on your panel:
for *Command* put:
```
env WINEPREFIX="/home/yourusername/.wine" wine "C:\Program Files\Spotify\spotify.exe"
```
whereas *yourusername* is your user name in Ubuntu.

For the icon, press the button to select an icon for the shortcut, and then select *Browse*. Go to the folder
```
/home/yourusername/.local/share/icons/
```
and then press *Open* to see all the available icons it it. Find the spotify icon and press OK.

To make the spotify links work on your browser just google for something like [this]("http://www.google.com/search?q=Opening+spotify+URIs+from+browsers").

For your playback problem, try disabling the *Enable volume normalization* in Spotify. Also, run *winecfg* and make sure that only ALSA is selected in the audio preferences.

Furthemore, you could try this: right-click on the speaker in your system tray and select the volume control and then try lowering the PCM volume level a little.

BTW, what version of Wine do you have?

---

### Post by peakshysteria on 2009-10-18
> **kostkon said:**
> To create a menu item in your menu or a shortcut on your panel:
for *Command* put:
```
env WINEPREFIX="/home/yourusername/.wine" wine "C:\Program Files\Spotify\spotify.exe"
```
whereas *yourusername* is your user name in Ubuntu.

For the icon, press the button to select an icon for the shortcut, and then select *Browse*. Go to the folder
```
/home/yourusername/.local/share/icons/
```
and then press *Open* to see all the available icons it it. Find the spotify icon and press OK.

To make the spotify links work on your browser just google for something like [this]("http://www.google.com/search?q=Opening+spotify+URIs+from+browsers").

For your playback problem, try disabling the *Enable volume normalization* in Spotify. Also, run *winecfg* and make sure that only ALSA is selected in the audio preferences.

Furthemore, you could try this: right-click on the speaker in your system tray and select the volume control and then try lowering the PCM volume level a little.

BTW, what version of Wine do you have?

Thanks a million man. We're now able to play flawlessly. But not always.Sometimes it work sometimes it don't. We can't see a pattern. But most of the times we're able to use it.

But we can't seem to be able to make a shortcut on the panel.

Wine is latest version 1.0.1. Spotify is version 0.3.21 (rev. 56306).

---

### Post by peakshysteria on 2009-10-24
*BUMP*

1.When opened and not played for a while playback is very choppy. Seems like the playback alternates between speeding up and slowing down together with normal playback.

2. Randomly when opened Spotify will not play and gives us an error message telling usthere is something wrong with our soundcard. Then when exiting and re-opening Spotify runs smooth.

3. When played for a longer period Spotify just stop to work sometimes.

4. When played for a longer period Spotify reacts like told in nr. 1.

Anyone?

---

### Post by lettas on 2009-10-25
Clean Karmic install and success with spotify:

```
sudo aptitude install wine1.2
wget http://www.spotify.com/download/Spotify%20Installer.exe && wine Spoti*.exe
winecfg
```
Change audio to esound and hardware acceleration to emulation

---

### Post by joppei on 2009-10-29
Code:
 	> sudo aptitude install wine1.2
wget [http://www.spotify.com/download/Spotify%20Installer.exe](http://www.spotify.com/download/Spotify%20Installer.exe) && wine Spoti*.exe
winecfg

Thx this worked smooth :)

Change audio to esound and hardware acceleration to emulation

---

### Post by guriinii on 2009-10-30
> **lettas said:**
> sudo aptitude install wine1.2
wget [http://www.spotify.com/download/Spotify%20Installer.exe](http://www.spotify.com/download/Spotify%20Installer.exe) && wine Spoti*.exe
winecfg[/code]Change audio to esound and hardware acceleration to emulation

Thank you, spotify went mental after upgrading to Karmic, now its running perfectly.

---

### Post by Langleyo on 2009-11-01
Thanks for this, got me working...I was about to get really annoyed... my upgrade didn't go smooth to start with and this was the final straw :-)

---

### Post by soelk on 2009-11-02
Ah, that's right. I knew there was a simple solution for the chopping sound problem, but I had forgotten what. 

Wine Configuration --> Audio --> Sound Driver --> EsounD Driver

---

### Post by Kulgan on 2009-11-03
Using OSS also solved it for me. Disabling volume normalisation can get annoying in Spotify >_>

I'm still having the problem where it sometimes stops playing though, as mentioned previously in this thread.

---

### Post by lordL on 2009-11-12
> **Kulgan said:**
> Using OSS also solved it for me. Disabling volume normalisation can get annoying in Spotify >_>

I'm still having the problem where it sometimes stops playing though, as mentioned previously in this thread.

After upgrading to Karmic from Jaunty I also experienced choppy sound, which would last for about 3 seconds, and then playback would stop entirely. Restarting Spotify would make it start playing again, but then only for about 3 seconds more, again with the choppy sound.  Switching to OSS solved this problem.

To confirm, I also tried switching back and forth between ALSA and OSS a couple of times, and it seems consistent that OSS works, whilst ALSA don't.

---

### Post by tep200377 on 2009-11-15
I installed Wine1.2 and that did it for me!
Plays smoooth now...

I allso read on the norwegian ubuntu forum that OSS drivers are preffered over ALSA.

---

### Post by MyTer on 2009-11-17
> **tep200377 said:**
> I installed Wine1.2 and that did it for me!
Plays smoooth now...


Works fine for me to now
Thanks!

---

### Post by peakshysteria on 2009-11-18
Strangely it's been working for at least a week now (mostly). I still sometimes get the; ```
There is something wrong with your soundcard...
```

But most of the time it works like a charm. So I must say it's worth the Premium membership and all :)

---

### Post by Joergen Marmalade on 2009-11-20
> **lettas said:**
> Change audio to esound and hardware acceleration to emulation

"Far out man, far ******* out!" - The Dude

---

### Post by phil_ on 2010-01-19
> **lettas said:**
> Clean Karmic install and success with spotify:

```
sudo aptitude install wine1.2
wget http://www.spotify.com/download/Spotify%20Installer.exe && wine Spoti*.exe
winecfg
```
Change audio to esound and hardware acceleration to emulation

I had a similar problem, spotify would start up fine and play on some occasions, other times it would stop after about 10 seconds of song. 

Changed the winecfg settings as above, and all seems to be well, had about an hours play and no choppiness! ... so far so good.... (running xubuntu karmic)

btw. my problems appeared to start before my upgrade to karmic - i needed some equalizer functionality and installed pulseaudio manually... i upgraded because there was additional pulseaudio functionality that required Karmic, and I could never get rid of the choppiness..!

All good now though, Thanks for the advice. :)

---

### Post by slight on 2010-05-07
It was stopping playing after a few seconds for me too (I'd have to restart it to get it to play again, but still only for a few seconds.)

Changing the hardware acceleration in the audio tab of winecfg to "emulation" fixed it for me (other settings: alsa / default sample rate 44.1k, 16 bits per sample)

---

