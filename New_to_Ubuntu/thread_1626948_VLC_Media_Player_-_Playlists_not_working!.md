---
title: "VLC Media Player - Playlists not working!"
date: 2010-11-20
forum: New to Ubuntu
---

### Post by Dark7man on 2010-11-20
Hey, just looking to check if anyone else has been having this issue.

I arrange a playlist and save it in "HomeDir/Playlists" when I open it later though, it loads VLC but just shows the name of the playlist in the playlist editor, pressing play etc has no effect.

I listed the location as I new to ubuntu but I see its pretty secure in terms of permissions, I dont suspect this to be the problem, but like I say I'm new to Ubuntu.

Any help or advice would be greatly appreciated!
~D

Ubuntu 10.10 64bit
HP DV6 1340sa 2.4 Intel Core2Duo
Dual Booting Windows 7 64bit

---

### Post by Dark7man on 2010-11-22
..just a bump... still have this issue... How do I go about updating VLC Media Player?  Is it one of the applications checked automatically in "Update Manager" or do I need to add a PPA for it?

---

### Post by mc4man on 2010-11-22
if I'm understanding you correctly you're saving a playlist in vlc to a folder in your home dir. (something like screen 1

If so, then by default vlc is making .xspf playlist file, which is fine, but you need to add the extension to the name given or vlc will not load. -  Screen 2

So if your saved playlist file has no extension then give it one. (r.click on - rename  - add a .xspf

---

### Post by Dark7man on 2010-11-22
mc4man - Thank You mate, I was being silly, completely overlooked that the files I was creating didn't have an extension.  (.xspf)  When I was saving the file I seen in the drop down box that .xspf was selection and made the assumption that it was automatically assigning that extension.  DOH! haha

Thank You very much indeed mate for a swift reply and I've learnt a lesson or 2 today.  CHECK EXTENSION IN FILENAMES + Assumptions = are the mother of all F* up's! haha

Many thanks again mate!

---

### Post by mc4man on 2010-11-22
As far as an updated vlc in Maverick (I'll assume

The latest 'release' is vlc 1.1.5 - maverick will not update to it. I sure there is a ppa for, maybe search it out (make sure it's for maverick

I use the dev version - 1.2+ which may occasionally experience a small regression, nothing very dramatic and generally fixed quickly. (or never noticed at all depending on usage

If you are inclined to try/use then Videolan has a daily ppa for maverick  - it updated every day or so - you don't have to update that often

[https://launchpad.net/~videolan/+archive/master-daily](https://launchpad.net/~videolan/+archive/master-daily)

---

### Post by Dark7man on 2010-11-22
Thanks mate - added the VLC PPA for future updates... thanks for the info mate! :)

---

### Post by AlexanderDGreat on 2011-02-18
But if I save the Playlist - it doesn't keep the ORDER of the SONGS! :(

---

### Post by AlexanderDGreat on 2011-08-13
It's not working even if I save it as xspf!

VLC sucks?

---

### Post by hakermania on 2011-08-13
> **AlexanderDGreat said:**
> It's not working even if I save it as xspf!

VLC sucks?

OMG, I could have argue with you I'd have all the Windows, Mac and Linux users with me!

You could possibly post a bug report or describe the problem further rather than posting pointless posts?

---

### Post by AlexanderDGreat on 2011-08-14
Sorry about that, I didn't want to say VLC is a bad program.

But on Ubuntu 10.04 LTS, 2.6.32-25-generic-pae i686 GNU/Linux, VLC media player 1.0.6 Goldeneye

Playlists are saved but everytime you launch it, the order changes, which is so frustrating, I've had this problem for 1 year now. I'm shocked I didn't know I posted here before...

I'll try to fill up a bug, but in the mean time, any thoughts why this happens? I save it as xspf.

---

### Post by AlexanderDGreat on 2011-08-24
Just update your VLC and it will work out fine.

---

