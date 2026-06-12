---
title: "Firefox plugin selection problem"
date: 2009-12-19
forum: New to Ubuntu
---

### Post by JavaRat on 2009-12-19
First of all I appologize if I am posting this question in the wrong forum.

I am having a problem using FireFox 3.5.6 in Ubuntu 9.10.
I am trying to listen to a radiostream from [http://www.sr.se/webbradio/include/CreatePlaylist.asp?SkipDetect=1&id=SR-Extra12&type=live&AvailableAudioFormats=2&AudioFormat=2&IsBlock=](http://www.sr.se/webbradio/include/CreatePlaylist.asp?SkipDetect=1&id=SR-Extra12&type=live&AvailableAudioFormats=2&AudioFormat=2&IsBlock=) which is only in windows media player format.

Unfortunately the Gstream that comes with Firefox and Ubuntu with a fresh install does not seem to work for me. So what I have tried is too download a few different plugins which I thought might help me solve my issue. If I (in Firefox) click Tools>Addons I see several plugins installed a few of them are : Windows Media Player plug-in , VLC media player-plugin , Realplayer 9, Mplayer and a few others.
How do I make firefox choose one of these instead of Gstream (totem something)?
I want to try each one out one at a time to see if they might help solve my problem?

Thank you in advance.

---

### Post by shredder12 on 2009-12-19
Go to Edit->Preferences and open the applications tab.
Here you can select which content type to be opened from windows media player plugin..

---

### Post by ajgreeny on 2009-12-19
I have just tried your problem site and it plays without problem using gecko-mediaplayer plugin.  It is in the repos so worth trying.

I also suggest you uninstall totem-mozilla if you have it installed as it is not nearly as good as gecko-mediaplayer, and also perhaps the vlc plugin, which I have never found is as good as the gecko-mediaplayer, even though I really like vlc as a desktop player.

---

### Post by JavaRat on 2009-12-26
Thank you both Shredder and Ajgreeny for your replies and suggestions.

I have tried to uninstall both xine and totem-mozilla plugin to make sure it does not try and pick either when I start the radiochannel page.
I also installed gecko-mediaplayer which shows up when i click Tools>Addons (in Firefox of course). However if I go to the page nothing will start, before I got a small square with a play-button and stop and forward buttons also. (I think there was a small volume controle too) Not completely sure but I assume this was the Xine or Totemplayer which did not work anyway so it is not a great loss.

Is there something I have missed? Since it worked for you I might be missing something? I used Synaptic Package Manager while uninstalling and installing of course.

Second, when I went to Edit>Settings and selected the Programs(tab) in Firefox I could view a list of plugins and which one was selected for which format. When I looked at Windows Media-Sound there was a preselection made. Clicking this dropdown I was hoping I could select my new gecko-mediaplayer but it does not show in the list? There was also a select program option but even though I tried to select /usr/lib/firefox/plugins/gecko-mediaplayer.so nothing seems to happen. I also tried selecting gecko-mediaplayer-dvx.so but that didn't help either. 

Very greatful for any further help in this matter if you know what I am doing wrong here.

---

### Post by shredder12 on 2009-12-28
I had  a similar problem once..nd it was solved by installing flashplugin-nonfree..
```
sudo apt-get install flashplugin-nonfree
```
hope that it helps..

---

### Post by JavaRat on 2009-12-28
Thank you for reply again,

The "square" now appears again as before with a play, pause, stop, forward, volume and fullscreen option. However after the "cache fill" is complete (I can see this text briefly) it stops dead in it's tracks and none of the buttons are selected. The text "stoped" is displayed :confused: dang heh. I was so happy to see the audiocontroles again. Any suggestions or ideas where I am going wrong here?

---

