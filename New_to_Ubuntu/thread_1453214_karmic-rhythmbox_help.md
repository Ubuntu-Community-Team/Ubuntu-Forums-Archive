---
title: "karmic-rhythmbox help"
date: 2010-04-12
forum: New to Ubuntu
---

### Post by stevek123 on 2010-04-12
After many struggles I've succeeded in getting Karmic installed and configured to my liking. This comp replaces a cooked winXP sys and is linked to my Hardy system upstairs thru the modem. I got my sound module configured. I setup my shared folders and mounted my 2 rather lrg folders of music upstairs to down here. I imported the folders into Rhythmbox. All fine & dandy...
When I play the music files thru the home network, they play for maybe 30 seconds then music stops...but the position indicator starts running thru the songs very rapidly, to the end of the one playing then on thru the next & so on. What's going on??? and how do I fix?
I know the easiest solution is to just copy the files to the HD down here, but I'd prefer to try and get it right first. FWIW, I run the System Monitor showing CPU, mem, network on my Taskbar & they are not pegged when this is happening. Please don't suggest another player like Amarok or such. I don't want them (didnt like amarok or banshee but DO like Rhythmbox).

---

### Post by r-senior on 2010-04-13
How are you sharing the files across the network? Samba, NFS? Something else? Do you have Windows machines connecting to the network?

How are you connecting to the Hardy server? Wireless or wired?

As a test, are you able to copy files successfully from the server to the downstairs mahine across the network? Do they play OK in that case?

---

### Post by stevek123 on 2010-04-13
Files shared thru windows network. samba. 
Something I hadnt tried yet was actually copying files over. I dropped a small music folder successfully onto my desktop...then tried to play it. I discovered its happening when i just try to play a file with mplayer or vlc or others _if I have rhythmbox open_. As soon as I close Rhythmbox the files play just fine. Either thru the network or off my desktop. Looks like the problem is in rhythmbox! Works fine on my Hardy sys. Any suggestions???

---

### Post by stevek123 on 2010-04-14
This was really bugging me so I went to google - one post suggested uninstall and re-install. I did this thru the basic Ubuntu Software Ctr. Just removed and reinstalled. It automatically mounted the network music folders and kept the playlist. It worked for one song and moved to the next - then began that fastforward soundless skipping again. Seems like it did not fully uninstall. Is there an easy way to purge the whole thing and reinstall? If I do, what will I break in the process?

---

### Post by stevek123 on 2010-04-14
No - I've found that this problem extends beyond Rhythmbox. I moved a huge 7 GB folder of music over the network (again = MORE issues = a bunch of stuff didnt copy over = some BS error msg...they play fine upstairs), then set mplayer to play thru some music while I tried to work. Things play better but there are still small sections of music that stall or skip. It does not appear to be consistent but is fairly regular throughout playback.

---

### Post by r-senior on 2010-04-15
I understand it's confusing when you are trying to work on an intermittent problem but there seems to be no really clear pattern. 

You get network problems copying files, problems playing files across the network and local files (that were copied across the network) show intermittent problems. Is it safe to assume that you've discarded the idea that it's because Rhythmbox is open - sounds like a red herring?

The only common denominator as far as I can see is the network. I guess the next logical thing to try is to get a USB drive and copy across a good quantity of files from upstairs to downstairs and see if they play OK.

You might want to try using "diff" against a USB copy and a network copy of the same file that has been mis-playing. Or compute a checksum against each file using md5sum and see if they are the same.

$ md5sum /media/<your_usb>/<file>
$ md5sum <file>

It would also be worth looking at /var/log/syslog, /var/log/messages and /var/log/debug on each machine and see if any odd errors were reported around the time of the copying/playing.

---

### Post by stevek123 on 2010-04-24
This turned out to be a sound driver issue. es1968 sound card driver is lousy. I replaced the card  with a soundblaster oldie i bummed and solved this - karmic picked it right up.

---

