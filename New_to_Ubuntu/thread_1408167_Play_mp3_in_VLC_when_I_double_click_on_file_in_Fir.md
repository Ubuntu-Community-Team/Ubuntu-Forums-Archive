---
title: "Play mp3 in VLC when I double click on file in Firefox's Downloads Window"
date: 2010-02-16
forum: New to Ubuntu
---

### Post by hanzj on 2010-02-16
When I double-click on an MP3 in Firefox's Downloads window, I want VLC to play the file. But Totem-MoviePlayer is what opens and plays it. 

In Firefox/Edit/Preferences/ApplicationsTab, mp3 audio is set to this action: "Use VLC Multimedia Plugin (co...).


When I double-click on an MP3 outside of firefox (e.g., on my desktop) VLC opens. 

Please tell me how I can make VLC play the file when I double-click on an MP3 in Firefox's Downloads window.

---

### Post by mutex023 on 2010-02-16
In Firefox/Edit/Preferences/ApplicationsTab set the mp3 audio to 'Other', and browse to /usr/bin and select 'vlc'.

---

### Post by hanzj on 2010-02-21
it works when I choose to "open"/"run" the mp3. (By this, I mean, clicking on the mp3 link). But when that mp3 link appears in my Firefox/Downloads window, Movie Player (Totem) starts up and plays the mp3 file.

---

### Post by hanzj on 2010-03-05
bump

---

### Post by mathay on 2010-03-05
Hey, hanzj.

This is in spite of changing the default Applications in the Firefox preference window? Also, if you go to System > Preferences > Preferred Applications, what is your preferred multimedia application? (I'm figuring thoroughness won't hurt in this case.)

---

### Post by hanzj on 2010-03-05
Yes, in spite of changing the default Applications in Firefox/Edit/Preferences/Applications.
Specifically, these content type are either "use vlc" or "use VLC Multimedia Plugin (compatible Totem 2.28.2) (in Firefox)":

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=149113&stc=1&d=1267819693[/IMG]




In System > Preferences > Preferred Applications > Multimedia Tab
I have "Custom" in dropdown box and "vlc" in "Command:" box.

---

### Post by HalfEmptyHero on 2010-03-05
This is not a firefox thing, you need to change your system preferences. In Nautilus, right click any mp3 (that is already downloaded) and hit properties. Go to open with, and select vlc and then close.

---

### Post by hanzj on 2010-03-05
HalfEmptyHero,
VLC is already the selected player in somemp3.mp3/Properties/[Open With]. But the problem still remains.

---

### Post by hanzj on 2010-05-29
bump

---

### Post by Tmantiko on 2010-07-06
Hi,

I'm having the exact same problem described above. Note - the problem is not opening a mp3 link but rather files that are downloaded and are showing in the bottom toolbar (I'm using the Firefox's Download Statusbar extension) - as hanzj described above.

Similarly my preferred application is vlc, and also all mp3 mime types in firefox preferences are set to vlc, but still Totem-MoviePlayer is the application which is launched.

---

### Post by Ancanus on 2010-10-02
Exact problem, bump.
Removing totem-player causes firefox to open it using Audacius. It must be pulling these alternatives from somewhere.

---

