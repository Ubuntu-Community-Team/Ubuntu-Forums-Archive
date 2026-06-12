---
title: "JetAudio needs file"
date: 2010-08-07
forum: New to Ubuntu
---

### Post by DayLite on 2010-08-07
I installed JetAudio on Ubuntu 10.04. I also have winetricks and wine installed also. JetAudio plays audio but cannot play my videos.  It says I need WindowsMedia 9 Runtime Files.

I spoofed Firefox and installed Windows Media player 9 from Microsoft. I still cannot play videos on JetAudio.

Can you please tell me what to look for on my Windows XP.  Then I could copy it over to my virtual C drive in Ubuntu.

---

### Post by Paddy Landau on 2010-08-07
I'm curious: Why would you want JetAudio, and not a native Linux program?

Here's what I would suggest:

[LIST=1]
[*]Uninstall JetAudio from Ubuntu.
[*]Install [PlayOnLinux]("http://playonlinux.com/").
[*]In PlayOnLinux, press Install > Multimedia > Windows Media Player > Apply. Follow the instructions.
[*]Finally, still in PlayOnLinux, press Install > Install a .pol package or an unsupported application > Manual installation > Forward > Edit an application already installed > (select the prefix where you installed Windows Media Play) > Forward, and follow the instructions to install JetAudio.
[/LIST]
I strongly recommend using PlayOnLinux to install all Wine programs for the ease that it provides in installing, running and uninstalling Windows programs.

If PlayOnLinux can't help you get it to work, then you may be out of luck. According to Crossover, [=1&date_start[2]=1&date_start[0]=2000&date_start[3]=0&date_start[4]=00&date_end[1]=8&date_end[2]=8&date_end[0]=2010&date_end[3]=3&date_end[4]=29&search=app"]JetAudio is untested]("http://www.codeweavers.com/compatibility/search?name=jetaudio&company=&medal=&date_start[1) on Wine.

---

### Post by DayLite on 2010-08-07
> **Paddy Landau said:**
> I'm curious: Why would you want JetAudio, and not a native Linux program?
.

Thank you for replying. I like using JetAudio because it displays the lyrics. I can also choose the interface.

[IMG]http://inlinethumb38.webshots.com/8421/2539068950012428738S425x425Q85.jpg[/IMG]

---

### Post by Paddy Landau on 2010-08-08
> **DayLite said:**
> I like using JetAudio because it displays the lyrics.
That's cool.

Apparently, there are Linux players that can do that. I've never tried, but [anewmorning lists four]("http://www.anewmorning.com/2008/05/21/10-best-linux-audio-players/") that (supposedly) do:

[LIST]
[*]Rhythmbox
[*]GMPC
[*]Exaile
[*]Sonata
[/LIST]
It may be worth trying them out, or asking in a new thread what people suggest as a Linux alternative to JetAudio, specifying that you want to display the lyrics.

Did you try the PlayOnLinux method that I described?

---

### Post by ankspo71 on 2010-08-08
Hi,
I don't know if this will help, but here is a link to Windows Media Format Runtime 11. [http://www.softpedia.com/get/Multimedia/Video/Codec-Packs-Video-Codecs/Windows-Media-Format-Runtime-11.shtml](http://www.softpedia.com/get/Multimedia/Video/Codec-Packs-Video-Codecs/Windows-Media-Format-Runtime-11.shtml)

This next part has nothing to do with JetAudio, but I thought you might like seeing it:
[http://www.omgubuntu.co.uk/2010/06/display-lyrics-on-desktop-ubuntu-linux.html](http://www.omgubuntu.co.uk/2010/06/display-lyrics-on-desktop-ubuntu-linux.html)
Hope something I said helps.

---

### Post by DayLite on 2010-08-08
> **ankspo71 said:**
> Hi,
I don't know if this will help, but here is a link to Windows Media Format Runtime 11. [http://www.softpedia.com/get/Multimedia/Video/Codec-Packs-Video-Codecs/Windows-Media-Format-Runtime-11.shtml](http://www.softpedia.com/get/Multimedia/Video/Codec-Packs-Video-Codecs/Windows-Media-Format-Runtime-11.shtml)

This next part has nothing to do with JetAudio, but I thought you might like seeing it:
[http://www.omgubuntu.co.uk/2010/06/display-lyrics-on-desktop-ubuntu-linux.html](http://www.omgubuntu.co.uk/2010/06/display-lyrics-on-desktop-ubuntu-linux.html)
Hope something I said helps.

Thank you, I will try it. JetAudio runs perfectly on Ubuntu as a audio player, so far I have tried others and they don't match up to it. What I was hoping is to have one player that could do both audio and video.

---

### Post by cascade9 on 2010-08-08
> **DayLite said:**
> Thank you, I will try it. JetAudio runs perfectly on Ubuntu as a audio player, so far I have tried others and they don't match up to it. What I was hoping is to have one player that could do both audio and video.

VLC should do what you want- choosable interface, plays audio + video. As far as I know, the lyrics plugin (minilyrics) is windows only at this time, but hopefully there will be a linux version at some point. 

BTW, when I tried jetaudio on an nLited WinXP with WMP removed, I couldnt get it to play videos no matter what I did. That doesnt mean its not possible, but it might be a huge amount to stuffing around to get it to play videos.

---

### Post by DayLite on 2010-08-08
> **ankspo71 said:**
> Hi,
This next part has nothing to do with JetAudio, but I thought you might like seeing it:
[http://www.omgubuntu.co.uk/2010/06/display-lyrics-on-desktop-ubuntu-linux.html](http://www.omgubuntu.co.uk/2010/06/display-lyrics-on-desktop-ubuntu-linux.html)
Hope something I said helps.

[IMG]http://inlinethumb36.webshots.com/43427/2657160540012428738S500x500Q85.jpg[/IMG]

[COLOR=Red]**[SIZE=5]HELP[/SIZE]**[/COLOR] :confused:

I follwed these instructions:
**Installation**
  OSDLyrics can be installed  easily in Ubuntu via the official PPA. Open a terminal and enter the  following lines, hitting return after each and entering your password  where prompted.
  
[LIST]
[*]*sudo add-apt-repository ppa:osd-lyrics/ppa*
[*]*sudo apt-get update && sudo aptitude install osdlyrics*
[/LIST]
When it wouldn't launch I decided to remove the repository. Now I get the above warning and I don't understand :(

The Software Center says 0 installed and it will not load anything to 'get software'.

---

### Post by ankspo71 on 2010-08-09
Hi DayLite,
Ubuntu has a list of download locations to download software and updates from located at /etc/apt/sources.list. It is saying that something is wrong with line 49 of that file. Can you post the entire contents of: 
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by DayLite on 2010-08-09
> **Paddy Landau said:**
> That's cool.
Did you try the PlayOnLinux method that I described?

No I didn't. It is mainly for games and apps. I resolved to be thankful that JetAudio is the best audio player. I did try the others mentioned and since the lyrics are already in the property of the mp3 file, having a program that will download lyrics doesn't apply to me.

I will just use another program to play my videos.

Thank you.

---

### Post by DayLite on 2010-08-09
> **ankspo71 said:**
> Hi DayLite,
Ubuntu has a list of download locations to download software and updates from located at /etc/apt/sources.list. It is saying that something is wrong with line 49 of that file. Can you post the entire contents of: 
```
gksudo gedit /etc/apt/sources.list
```

I went on [Launchpad]("https://answers.edge.launchpad.net/ubuntu/+source/update-manager/+question/120450") and kindly was helped to resolve the problem.

---

### Post by Paddy Landau on 2010-08-09
> **DayLite said:**
> No I didn't. It is mainly for games and apps.
:confused: No, PlayOnLinux is to make it easier to use Wine. If you tried the method I described, you'd have Windows Media 9 installed, ready to install JetAudio.

Anyway, you seem to be solving your problem, so good luck with that.

---

