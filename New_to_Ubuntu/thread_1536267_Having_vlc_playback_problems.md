---
title: "Having vlc playback problems"
date: 2010-07-21
forum: New to Ubuntu
---

### Post by SolusRising on 2010-07-21
I'm trying to run a dvd with .vob files in vlc on ubuntu 10.04.  Initially, the dvd wouldn't play at all and I'd get a message in the terminal that told me the dvd was encrypted.  Then I added libdvdcss2 and followed the instructions here:[ https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu") and managed to get the dvd to play... but only by right clicking the desktop icon for the disk and selecting "open with vlc."  
If I try to run vlc in the terminal I get this error message 
> libdvdread: can't stat /home/user/desktop/movie
no such file or directory
libdvdnav: vm: failed to open/read the dvd
[0x8487d40] access_file access error: cannot open file /home/user/desktop/movie (no such file or directory)
[0xb7301010] main input error: open of ` /home/user/desktop/movie` failed no suitable access module
^C[0x8178800] signals interface error: caught Interrupt signal, exiting...Now, when I open the disk with right clicking, I get this error message before it sort of plays:
> playback failure:
VLC cannot set the DVD's title.  It possibly cannot decrypt the entire disk.What then follows is incredibly choppy audio and a few seconds of choppy video before that gives out and I'm left with the (deeply flawed) audio only.

So, in summation, I'm really new to linux (I only figured out how to work the terminal properly today) and I'm having some problems simply watching a film, and I'm wondering if any of you would be able to help me.

---

### Post by lidex on 2010-07-22
Open a nautilus window, go to 'Edit>Preferences>Media'. For 'dvd media' change selection to vlc. Have you tried opening vlc and using the 'Media>Open Disk' menu?

---

