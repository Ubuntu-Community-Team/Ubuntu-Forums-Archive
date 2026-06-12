---
title: "Movie Player keeps crashing"
date: 2010-12-01
forum: New to Ubuntu
---

### Post by maryalesia on 2010-12-01
Recently movie player has started crashing when playing a movie in full screen. It doesn't freeze or anything; the program simply closes out. Once second I'm watching a movie, the next I'm staring at my desktop. VLC media seems unaffected but I like movie player ... is there a way to fix this? I watched four movies without a hitch in the last couple of days, but today I can't get five minutes in without a crash. 

Does anyone know why this happens? I'm running lucid. I don't know if that is relevant or not.

---

### Post by maryalesia on 2010-12-06
No ideas? 

If it helps at all, I updated to maverick and since then movie player has not crashed.

---

### Post by drake18746 on 2010-12-13
I am also experiencing this problem however it only started happening today after I fully upgraded my system.

In addition, I believe it might only be happening with mkv files since I was able to play an avi uninterrupted.

---

### Post by Supergoo on 2010-12-13
Did you install something before this started happening ? Updates ? New codecs ? something along these lines ?

---

### Post by drake18746 on 2010-12-13
I obviously can't speak for the OP but I know that, after updating, the only thing I installed was flash.

I have also tested this via three different avi files, all of them played correctly without any sudden closing of the application.

---

### Post by Supergoo on 2010-12-13
I know this might be something you have already tryed, but restart your ubuntu and do a memtest , long shot I know wonder if it might be wonky memory. If it passes try this, use the package manager to uninstall the movie player, then reinstall it, see if that fixs it.

---

### Post by mikechant on 2010-12-13
Assuming we're talking about the default player, this is called totem, and if you run it from the command line/terminal (just using the 'totem' command) it may give a useful error message on the terminal when it crashes, which you can post here/google for etc.

---

### Post by drake18746 on 2010-12-13
This is certainly a much better idea since the machine is a file server and needs to stay up as much as possible.  I'll definitely run it via command next time I plan on playing an mkv file though.

---

### Post by drake18746 on 2010-12-14
I've tried running totem via command line for the past few videos.  Every video (only mkv and avi at this point) that I have tried, regardless of whether I ran it via sudo, has given me the same warning:

Totem-WARNING **: Failed to create dbus proxy for org.gnome.SettingsDaemon: Could not get owner of name 'org.gnome.SettingsDawmon': no such name

As for the MKV files, they are still crashing.  I'm not sure how long it takes for the video the crash but it seems like about the same amount of time each instance.  Additionally, the only information I'm given in the terminal when they crash is "Aborted."

This is after successfully reinstalling totem via the Synaptic Package Manager.

---

### Post by bartekklimczak on 2011-03-04
i have also started crashing
mkv files only after recent updates
have tried uninstallingand reinstalling with no help
annoyed it seems everytime i do updates something stops working, 

sigh

---

### Post by eilhart on 2011-03-12
Isn't there a solution for this?
 
I've installed VLC and using it instead, works fine but I'd like to use Totem because of it's simple yet easy to use interface.

---

### Post by sussexslanter on 2012-06-22
I have experienced a similar problem with Totem.  When attempting to run a mkv file it just gives me a blank screen.  Then it will not close unless I go to system monitor and end the process.  This only happens with mkv files.  

I agree that totem is nice and easy, but when it comes to reliability it falls short.

Incidentally, I then attempted it in vlc, it also didn't work reliably, but did eventually but the cpu maxed out until I was forced to restart.

---

### Post by nothingspecial on 2012-06-22
Old thread.

Closed.

---

