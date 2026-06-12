---
title: "Users of Linuxdcpp"
date: 2008-04-13
forum: Networking &amp; Wireless
---

### Post by Shaoline on 2008-04-13
I am using Linuxdcpp, and I have a question about the sharing part of the settings.

There is a tick-box named "Follow links", what does that one actually do? As I cant seem to get it to work the way I want using links to other folders.

Lets say I got a structure like this on my computer
/media
...../drive1/etc
...../drive2/files1/bigfiles
...../drive3/etc

then I would like to make a "DC-folder" inside my /media, then create links to all other drives or folders I want to share. So the structure could be something like this inside of linuxdcpp:

/filelist
...../etc (this is drive1 and drive3, combined into one dir)
...../bigfiles

This is because I really liked the idea of aliasing the folder names, to make my filelist appear much more elegant than it actually is. This I could do under windows and "fuldc".

So, to sum it up, is that tick-box for this kind of operation, and am I maybe doing something wrong? Cause linuxdcpp doesn't seem to want to hash the files I share using links.

I hope I managed to describe this good enough.

---

### Post by Shaoline on 2008-04-13
I may have found a solution somewhat close to what I wanted to achieve..

I will try these steps explained here, tho a bit customized to fit my needs.

[http://ubuntuforums.org/showthread.php?t=538535](http://ubuntuforums.org/showthread.php?t=538535)

---

