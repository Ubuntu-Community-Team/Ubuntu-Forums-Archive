---
title: "Play Quicktime ONLINE"
date: 2010-04-27
forum: New to Ubuntu
---

### Post by orphanlast on 2010-04-27
Okay... I've made a thread about this already, but it got lost in the fray.

I can't play quicktime on my web browser (firefox). It was suggested that I go to this place:  [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

...
...
...

I gotta say, every tutorial or "helpful" bit of information coming from help.ubuntu.com has been a waste of time. They don't explain anything, and even when you follow their advice to the letter -- nothing happens. (Take their songbird page... blah)

Anyways, I've dealt with that page... and MAYBE it worked... but was it intended to play quicktime on a web browser or was it intended to just play quicktime files when they're downloaded? Huh -- I don't know... and surprise surprise, help.ubuntu.com doesn't even say.

I even did some independent research (which I always do) and I tried this one out:   [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) and I watched my terminal download an ungodly number of programs for 40 minutes.... and I have no idea what it was supposed to do other than play restricted video formats... which I thought was supposed to be a step in the right direction. BUT if I go to apple.com to see any of their quicktime videos... nope... nadda... nothing...

Is there a straight forward way of getting this done?

Is there a specific file I can download from a repository or something?

---

### Post by Troll_the_Great on 2010-04-27
> **orphanlast said:**
> Okay... I've made a thread about this already, but it got lost in the fray.

I can't play quicktime on my web browser (firefox). It was suggested that I go to this place:  [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

...
...
...

I gotta say, every tutorial or "helpful" bit of information coming from help.ubuntu.com has been a waste of time. They don't explain anything, and even when you follow their advice to the letter -- nothing happens. (Take their songbird page... blah)

Anyways, I've dealt with that page... and MAYBE it worked... but was it intended to play quicktime on a web browser or was it intended to just play quicktime files when they're downloaded? Huh -- I don't know... and surprise surprise, help.ubuntu.com doesn't even say.

I even did some independent research (which I always do) and I tried this one out:   [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) and I watched my terminal download an ungodly number of programs for 40 minutes.... and I have no idea what it was supposed to do other than play restricted video formats... which I thought was supposed to be a step in the right direction. BUT if I go to apple.com to see any of their quicktime videos... nope... nadda... nothing...

Is there a straight forward way of getting this done?

Is there a specific file I can download from a repository or something?

I can play quicktime movies from apple using agent switcher with the settings from the attachment.
I can only play HD trailers with this trick:right click on the trailer, then click on "Open in new tab" and it should work.
Good luck!
Cheers!

---

### Post by klytu on 2010-04-27
> **orphanlast said:**
> Okay... I've made a thread about this already, but it got lost in the fray.

I can't play quicktime on my web browser (firefox). It was suggested that I go to this place:  [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

...
...
...

I gotta say, every tutorial or "helpful" bit of information coming from help.ubuntu.com has been a waste of time. They don't explain anything, and even when you follow their advice to the letter -- nothing happens. (Take their songbird page... blah)

Anyways, I've dealt with that page... and MAYBE it worked... but was it intended to play quicktime on a web browser or was it intended to just play quicktime files when they're downloaded? Huh -- I don't know... and surprise surprise, help.ubuntu.com doesn't even say.

I even did some independent research (which I always do) and I tried this one out:   [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) and I watched my terminal download an ungodly number of programs for 40 minutes.... and I have no idea what it was supposed to do other than play restricted video formats... which I thought was supposed to be a step in the right direction. BUT if I go to apple.com to see any of their quicktime videos... nope... nadda... nothing...

Is there a straight forward way of getting this done?

Is there a specific file I can download from a repository or something?

I've been using Ubuntu since its second release and I haven't yet found a way that consistently plays ***all*** online Quicktime video that's embedded within Firefox. (Downloading the files and then playing them outside of Firefox has never been an issue for me and works flawlessly). Recently, I've had relatively good results using Gecko Media Player. But even with that, I've had to use some workarounds. For example, with many videos on [[COLOR="Blue"]_Apple Movie Trailers_[/COLOR]]("http://trailers.apple.com/") I need to right-click and copy the link to the video and then paste it into the address bar of a separate tab to get it to play within Firefox. From what I've observed, the main reason for the difficulty is that Quicktime is a proprietary format that isn't native to Linux, and the format changes on a regular basis. Apple also seems to want people to only view Quicktime with its own proprietary software, so many websites that feature Quicktime videos have countermeasures built in that make it difficult to watch the videos without using that software.

You can find good instructions for how to get Gecko Media Player (and many other Multimedia players) working in this thread: [[COLOR="Blue"]_Comprehensive Multimedia & Video Howto_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=766683&highlight=quicktime") You'll need to be patient and read through all the commentary within the first post. Ask questions there about anything you don't understand before running any of the commands that are suggested. In particular, you may need to remove some of the Firefox plugins you've already installed to avoid conflicts where more than one plugin is attempting to play the same media format at the same time. Good luck!

---

### Post by klytu on 2010-04-27
> **Troll_the_Great said:**
> I can play quicktime movies from apple using agent switcher with the settings from the attachment.
I can only play HD trailers with this trick:right click on the trailer, then click on "Open in new tab" and it should work.
Good luck!
Cheers!

I also use this workaround for stubborn Quicktime videos, but it doesn't work for all of them.

---

### Post by orphanlast on 2010-04-27
> **Troll_the_Great said:**
> I can play quicktime movies from apple using agent switcher with the settings from the attachment.
I can only play HD trailers with this trick:right click on the trailer, then click on "Open in new tab" and it should work.
Good luck!
Cheers!

So, how do I bring that window up?

---

### Post by Troll_the_Great on 2010-04-27
> **orphanlast said:**
> So, how do I bring that window up?

I don't understand what you mean. What window?

---

### Post by orphanlast on 2010-04-27
> **Troll_the_Great said:**
> I don't understand what you mean. What window?
 
 You supplied an attachment that's a picture of a window. At the top of it it says "Edit User Agent".

---

### Post by Troll_the_Great on 2010-04-27
> **orphanlast said:**
> You supplied an attachment that's a picture of a window. At the top of it it says "Edit User Agent".

You have to install User Agent Switcher for firefox, then click on "Edit" - "New" - "New user agent".

---

### Post by orphanlast on 2010-04-27
Okay, I downloaded useragentswitcher from synaptic and firefox recognized the new information. Just to be safe, I restarted my computer.

But I go into the Edit menu and it doesn't give any "new" option.

---

### Post by Troll_the_Great on 2010-04-27
> **orphanlast said:**
> Okay, I downloaded useragentswitcher from synaptic and firefox recognized the new information. Just to be safe, I restarted my computer.

But I go into the Edit menu and it doesn't give any "new" option.

Not into the firefox Edit menu. Add the user agent to the Toolbar (right click on the toolbar, then Customize, drag the user agent on the toolbar) then click on User Agent - Edit User Agents - New...)
OK?

---

### Post by rayraven on 2010-04-27
This is wierd, i dont have the medibuntu repo added, only the codecs from the universe/multiverse, and yet i have flawless playback when using chrome.

EDIT: Am on Lucid.

---

### Post by orphanlast on 2010-04-27
Okay I've played with the menus with firefox to see about adding this thing as a toolbar and I'm not coming up with any leads.

I don't even know what I've downloaded... I don't know what I'm doing...

---

### Post by Troll_the_Great on 2010-04-28
> **orphanlast said:**
> Okay I've played with the menus with firefox to see about adding this thing as a toolbar and I'm not coming up with any leads.

I don't even know what I've downloaded... I don't know what I'm doing...

To see if you have it installed, go to Tools - Add-Ons - Extensions and check if is there. If not paste this link into your browser's address bar 
```
https://addons.mozilla.org/en-US/firefox/addon/59
```
and click on the green "Add to firefox" button to install it. After that, right click on the to toolbar (in the right side, towards the end)then click on "Customize" and there you should find your agent switcher.
Cheers!

---

### Post by orphanlast on 2010-04-28
Okay I was able to get the user agent to come up and I was able to tinker with it to look like yours and place quicktime into its menus but for some reason I'm still not able to view any quicktime videos.

---

### Post by klytu on 2010-04-28
> **orphanlast said:**
> Okay I was able to get the user agent to come up and I was able to tinker with it to look like yours and place quicktime into its menus but for some reason I'm still not able to view any quicktime videos.

What Quicktime videos are you trying to watch online? Can you post a link?

If it's Apple Movie Trailers and you are getting a pop-up that states you need to download Quicktime, the following might work. Set your user agent to Quicktime and refresh the page where you are trying to play the video. Click the small triangle next to "Watch Now" and then right-click the top link under download. Then select "open link in a new tab" in the context menu that appears when you right-click. For me, the video loads in a new tab when I do this. I can get almost all the Quicktime videos on the Apple Movie Trailers site to play this way via Gecko Media Player.

---

### Post by orphanlast on 2010-04-28
> **klytu said:**
> What Quicktime videos are you trying to watch online? Can you post a link? 

[http://www.apple.com/ipad/guided-tours/](http://www.apple.com/ipad/guided-tours/)

> 
If it's Apple Movie Trailers and you are getting a pop-up that states you need to download Quicktime, the following might work. Set your user agent to Quicktime and refresh the page where you are trying to play the video. Click the small triangle next to "Watch Now" and then right-click the top link under download. Then select "open link in a new tab" in the context menu that appears when you right-click. For me, the video loads in a new tab when I do this. I can get almost all the Quicktime videos on the Apple Movie Trailers site to play this way via Gecko Media Player.It doesn't bring me to any screen where it even tries to play the quicktime. I have attachments that'll demonstrate exactly what's happening every time.

---

### Post by carl4926 on 2010-04-28
No magic spells required.

Just install gecko-mediaplayer
And it works
Just make sure you don't have any other plugins (eg; vlc)

---

### Post by WinterRain on 2010-04-28
> **carl4926 said:**
> No magic spells required.

**Just install gecko-mediaplayer**
And it works
Just make sure you don't have any other plugins (eg; vlc)

I use the same plugin and can see the videos over at apple.com. It works.

---

### Post by orphanlast on 2010-04-29
... Okay... it looks like it switched the settings back to its default. Well, I put them back to reflect what they were supposed to say in order to help out with watching Quicktime

Here's how it looks like now, and I'm still not able to watch quicktime... and now I can't attach files. It's as though my whole browser turned to crap.

[http://i49.photobucket.com/albums/f286/laimtoe/1.png](http://i49.photobucket.com/albums/f286/laimtoe/1.png)

You can look at the modifications right there.

I'm must going to delete this User Agent Switcher because it's causing my browser to act really weird and outdated, and it's not playing quicktime.

---

### Post by WinterRain on 2010-04-29
You don't need the user agent thingy. Remove it and install gecko-mediaplayer, as suggested above.

---

### Post by orphanlast on 2010-04-29
Sweet! The gecko-mediaplayer worked. I can't pause or rewind the video but I can tell it to open in a different program once it starts going.

THANK YOU!!!

Thank you 
thank you
THANK YOU!

---

### Post by carl4926 on 2010-04-29
> **orphanlast said:**
> Sweet! The gecko-mediaplayer worked. I can't pause or rewind the video but I can tell it to open in a different program once it starts going.

THANK YOU!!!

Thank you 
thank you
THANK YOU!

It had already been mentioned. But perhaps you missed it.
Happy it's working though.

---

### Post by orphanlast on 2010-04-29
Yeah, it was the first response... dang... that's just frustrating. lol.

---

### Post by johnaaronrose on 2010-05-23
I just installed gecko-media-player but still no good with Quicktime on Firefox. I have previously installed vlc (as I've found that it's the only app that will play any DVD). vlc-plugin-pulse was automatically installed (on install of vlc) but mozilla-plugin-vlc is not installed. Any ideas anybody?

---

### Post by johnaaronrose on 2010-05-23
Found solution on another thread:
-Close Firefox.
-Delete the plugins registry file. That should be in your ~/.mozilla/firefox/<profile (like xxxxxxxx.default)> folder, where ~/.mozilla is generally /home/<yourname>/.mozilla. Delete the file pluginreg.dat, which firefox will recreate when it starts.
-Using Synaptic Package Manager, ensure that the multiverse repository is enabled.
-Remove the totem mozilla plugin named totem-mozilla.
-Install gecko-mediaplayer, which automatically installs all of the mplayer goodness as well.

---

