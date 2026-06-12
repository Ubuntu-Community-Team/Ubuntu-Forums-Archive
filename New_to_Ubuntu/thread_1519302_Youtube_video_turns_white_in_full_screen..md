---
title: "Youtube video turns white in full screen."
date: 2010-06-27
forum: New to Ubuntu
---

### Post by Apostolique on 2010-06-27
I saw that this question had already been asked a couple times, but I still couldn't resolve my problem.

When I try to put YouTube videos in full screen mode in Firefox/Google Chrome, all I get is a white screen. I can still hear the sound in the background. When I press Esc to go back in normal mode, Firefox will crash and Google Chrome will display a message saying that the following plugin was blocked: /urs/lib/flashplugin-installer/libflashplayer.so

When I am not in full screen mode, the video plays normally.

I currently have Ubuntu version 10.04.

---

### Post by lovinglinux on 2010-06-28
Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here.

---

### Post by Apostolique on 2010-06-29
Path: /usr/lib/flashplugin-installer/libflashplayer.so
Version: Shockwave Flash 10.1 r53

---

### Post by lovinglinux on 2010-06-29
You have the latest version of flash 32bit and path is ok.

Assuming that you are using effects (compiz), then try to disable "Unredirect Fullscreen Windows" in Compiz. Go to “System >> Preferences >> CompizConfig Settings Manager >> General Options >> General”.

If you don't have "CompizConfig Settings Manager" in the menu, then you need to [install it](apt:compizconfig-settings-manager).

I'm not sure this will help, but usually this kind of problem is Compiz related.

---

### Post by Apostolique on 2010-06-30
Seems like "Unredirect Fullscreen Windows" was already disabled. Now, in google chrome, it says that the plugin that was blocked is /opt/google/chrome/libgcflashplayer.so when I toggle on and off the full screen mode on youtube (The video appears white but I can still hear the sound.) I went to check that file and I saw that there was no permissions set and it doesn't allow me to turn it on since I don't own that file.

---

### Post by lovinglinux on 2010-06-30
> **Apostolique said:**
> Seems like "Unredirect Fullscreen Windows" was already disabled. Now, in google chrome, it says that the plugin that was blocked is /opt/google/chrome/libgcflashplayer.so when I toggle on and off the full screen mode on youtube (The video appears white but I can still hear the sound.) I went to check that file and I saw that there was no permissions set and it doesn't allow me to turn it on since I don't own that file.

Check [http://blog.chromium.org/2010/06/enabling-adobe-flash-player-support-in.html](http://blog.chromium.org/2010/06/enabling-adobe-flash-player-support-in.html)

---

### Post by Apostolique on 2010-07-12
I didn't get to fix this yet.

---

### Post by lovinglinux on 2010-07-12
Try my extension [FLASH-AID](https://addons.mozilla.org/en-US/firefox/addon/161939/). It was designed to install the proper version of flash (which you already have) and fix conflicting plugin issues (which seems you don't have), but I have seen some people fixing other problems I wasn't expecting to fix with it.

---

### Post by Apostolique on 2010-07-12
> **lovinglinux said:**
> Try my extension [FLASH-AID](https://addons.mozilla.org/en-US/firefox/addon/161939/). It was designed to install the proper version of flash (which you already have) and fix conflicting plugin issues (which seems you don't have), but I have seen some people fixing other problems I wasn't expecting to fix with it.

The extension executed normally but the problem wasn't fixed.

---

### Post by lovinglinux on 2010-07-12
> **Apostolique said:**
> The extension executed normally but the problem wasn't fixed.

I was hoping for a miracle :)

---

### Post by Apostolique on 2010-07-15
I tried settings permissions (CHMOD)  for /opt/google/chrome/libgcflashplayer.so to 777 but it didn't make the full screen work.

---

### Post by Apostolique on 2010-07-17
Anything else I could do in order to fix the full screen mode problem?

I have tried to go on different website with videos to try the full screen mode, and every time I got a white screen with sound in the background. Up to now, no flash worked on full screen.

---

### Post by sc0ttdotnet on 2010-07-18
Saw your question while looking on google for the solution to this myself. Try right clicking on the video while it's playing in normal mode and going to settings, then uncheck enable hardware acceleration. Hope it helps. 

[http://www.google.com/support/forum/p/Chrome/thread?tid=7b09acf1defb2ddb&hl=en](http://www.google.com/support/forum/p/Chrome/thread?tid=7b09acf1defb2ddb&hl=en)

---

### Post by wizi on 2010-07-21
> **sc0ttdotnet said:**
> Saw your question while looking on google for  the solution to this myself. Try right clicking on the video while it's  playing in normal mode and going to settings, then uncheck enable  hardware acceleration. Hope it helps. 

[http://www.google.com/support/forum/p/Chrome/thread?tid=7b09acf1defb2ddb&hl=en](http://www.google.com/support/forum/p/Chrome/thread?tid=7b09acf1defb2ddb&hl=en)

I got the same problem with youtube cant play when in fullscreen mode. Uncheck "enable hardware acceleration" can help but the video gets smaller (even smaller than normal) when you hit fullscreen.

---

### Post by Apostolique on 2010-07-30
> **sc0ttdotnet said:**
> Saw your question while looking on google for the solution to this myself. Try right clicking on the video while it's playing in normal mode and going to settings, then uncheck enable hardware acceleration. Hope it helps. 

[http://www.google.com/support/forum/p/Chrome/thread?tid=7b09acf1defb2ddb&hl=en](http://www.google.com/support/forum/p/Chrome/thread?tid=7b09acf1defb2ddb&hl=en)

Great, it seemed to fix it for me. For people that didn't get to fix it yet, I found a temporary fix. I think it only works for youtube but I didn't check other websites.

[LIST=1]
[*]Go to a youtube video.
[*]Naviguate to /tmp/. (Example: /home/user/ -> Now it's only /tmp/)
[*]Find the video you are watching. (The file should be named: Flash + the video ID you can see in your URL bar.)
[*]Open that file and you will be able to see the video but without youtube.
[*]Press F11 for full screen.)
[/LIST]

---

### Post by lovinglinux on 2010-07-30
> **Apostolique said:**
> Great, it seemed to fix it for me. For people that didn't get to fix it yet, I found a temporary fix. I think it only works for youtube but I didn't check other websites.

[LIST=1]
[*]Go to a youtube video.
[*]Naviguate to /tmp/. (Example: /home/user/ -> Now it's only /tmp/)
[*]Find the video you are watching. (The file should be named: Flash + the video ID you can see in your URL bar.)
[*]Open that file and you will be able to see the video but without youtube.
[*]Press F11 for full screen.)
[/LIST]

It's easier to use my extension [FlashVideoReplacer]("https://addons.mozilla.org/en-US/firefox/addon/161869/"), which allows to watch YouTube with a different plugin, without the need to download the video or manually launching it from the tmp folder. It replaces the video on site.

---

### Post by xXDestroyerGRXx on 2011-01-23
> **lovinglinux said:**
> Try my extension [FLASH-AID]("https://addons.mozilla.org/en-US/firefox/addon/161939/"). It was designed to install the proper version of flash (which you already have) and fix conflicting plugin issues (which seems you don't have), but I have seen some people fixing other problems I wasn't expecting to fix with it.


it worked for me

+1

---

### Post by FrDarryl on 2011-02-20
Clearing the checkbox for acceleration in context-menu->Settings did it for me (persistently, i.e., running subsequent videos).

Cheers for the fix

---

