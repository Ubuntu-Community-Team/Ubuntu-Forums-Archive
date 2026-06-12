---
title: "rtorrent help"
date: 2010-07-17
forum: New to Ubuntu
---

### Post by h8uthemost on 2010-07-17
I've recently switched to rtorrent and I have a question. Is it possible to browse folder directories within rtorrent?

For example, I'm having to switch the folder that I'm wanting a specific torrent to download to quite a lot. And so far I've been doing it by, opening up the folder, hitting the Go tab, then Location, then copy/pasting the folder address into rtorrent.

But I was just reading some guide, and it said when you want to add a new torrent, you can hit Enter, then hit the Tab button, and a folder directory comes up. And this is true. If I hit Enter then Tab, the folder directory for my Home folder pops up. But...that's all it does. Terminal/rtorrent won't let me browse those folders.

Is there any way to browse folders within rtorrent?

Thanks.

---

### Post by munkyeetr on 2010-07-17
From the [rtorrent user guide]("http://libtorrent.rakshasa.no/wiki/RTorrentUserGuide"): 

CTRL + o will let you specify the directory to download to "*if torrent has not yet been activated.*"

From there you can tab-complete to see other directories.

---

### Post by h8uthemost on 2010-07-17
What exactly does tab-complete mean? Does the mean pressing the Tab key? Because when I hit Ctrl-0, then Tab, nothing else pops up.

Also, I'm having another problem. I'm trying to get torrents to stop at a certain ratio. For example, if I want a ratio to stop at 1.10, I put this in the config file:

*schedule = ratio,60,60,"stop_on_ratio=100,50000M,150"*

But...the torrent didn't stop at 1.5. So how exactly do I edit that code to make a torrent stop at ratio 1.5?

Thanks.

---

### Post by munkyeetr on 2010-07-17
> **h8uthemost said:**
> What exactly does tab-complete mean? Does the mean pressing the Tab key? Because when I hit Ctrl-0, then Tab, nothing else pops up.

Yes, tab-complete means pressing the Tab key. It works for me (I just tried it), though it doesn't show hidden directories.

When you first press CTRL + o, rtorrent displays the default download location in the bottom left side of the terminal. Pressing the Tab key once adds a / to the path, and pressing it again displays a list of subfolders (if any) in the top left of the terminal. Type the first letter (or first several until the path is unique) of the subfolder, then press Tab again to complete the path...continue on until you have reached the desired path.

Confirm that the directory you want to download to is a subfolder of that default directory, or edit/start a new path after pressing CTRL + o to get you where you want to be.

Hope that helps some,
Munky

---

### Post by h8uthemost on 2010-07-17
Ok, that worked. Except for me, if I hit Tab twice, nothing happens. So for me to get my folder list to display, I have to hit Ctrl+o, then Backspace and delete the whole default folder address, then hit Tab. And only then the folder display pops up.

Well, thank you for the help. I'm not sure if that way is any faster then just popping open the folder, copying the folder address from Location, then pasting it into rtorrent, but I'm glad I know how to pick download locations this way now.

Thanks a lot for your help munkyeetr.

Now, hopefully someone will know how to edit this code to make torrents stop at 1.5 ratio:

*schedule = ratio,60,60,"stop_on_ratio=100,50000M,150"*

---

### Post by techunit on 2010-07-17
transmition bit torrent client works fairly well so I don't see why you don't use that... but ok.. tab complete refers to typing in part of the location and hitting tab to complete the location automatically...

---

### Post by h8uthemost on 2010-07-18
Well, I'm not here to debate which client is better. I've been using Transmission for almost two years now, but I like how light rtorrent is. And thanks for the explanation, techunit.

Anyways, I'm still trying to figure out how to get torrents to stop at a certain ratio. If anyone knows how to do this I would really appreciate the help.

Thanks.

---

### Post by marshmallow1304 on 2010-07-18
> **h8uthemost said:**
> Now, hopefully someone will know how to edit this code to make torrents stop at 1.5 ratio:

*schedule = ratio,60,60,"stop_on_ratio=100,50000M,150"*

This should do it.
schedule = ratio,60,60,"stop_on_ratio=150"

---

### Post by h8uthemost on 2010-07-18
Thank you so much for this marshmallow. I'll give this a shot with the next torrent I try, and let you know how it went.

By the way, should I edit my rtorrent.rc with _just_ this string:

*schedule = ratio,60,60,"stop_on_ratio=100,50000M,150"*

or use all of this instead:

[I]# stop_on_ratio = min_ratio,min_upload,max_ratio
#
# Example: 
schedule = ratio,60,60,"stop_on_ratio=150"[/I]

Thanks again for the help. I"ll let you know how it goes.

---

### Post by h8uthemost on 2010-07-19
Nope. Unfortunately marshmallow1304's suggestion didn't work. I've tried at a 1.5 ratio(putting 150 in the .rc) at a 1.0 ratio(putting 100 in the .rc) and at a 0.45 ratio(putting a 045 in the .rc), and all three haven't worked.

I tried putting in the string:

*schedule = ratio,60,60,"stop_on_ratio=100,50000M,150"*

And I also tried the string(just like it shows in the example .rc on the rtorrent wiki):

[I]# stop_on_ratio = min_ratio,min_upload,max_ratio
#
# Example: 

schedule = ratio,60,60,"stop_on_ratio=150"[/I]

And neither of those worked. Anyone else have any suggestions? If I can't get this to work then I'm going to have no other choice but to switch back to Transmission as I need this feature. And I'm unable to get any of the rtorrent webui's to work.

Thanks.

EDIT: By the way, I keep getting the error: *Scheduled command failed: ratio: Command "stop_on_ratio" does not exist.* at the bottom of my rtorrent. And I get this error with either above string inputed in the .rc.

---

### Post by marshmallow1304 on 2010-07-19
Sorry, it was just a guess.  I'll try some things and see if I can figure it out.

The lines with '#' at the beginning are comments, so they can be left in and they won't affect anything.

---

### Post by h8uthemost on 2010-07-19
Oh no problem at all. I really appreciate you taking a guess for me, as I really have no clue about this. So any suggestions at all will always be welcomed.

And thanks for the explanation on the lines with '#'. I wasn't sure if those had to be in there or not.

---

### Post by MrWES on 2010-07-19
> **h8uthemost said:**
> Nope. Unfortunately marshmallow1304's suggestion didn't work. I've tried at a 1.5 ratio(putting 150 in the .rc) at a 1.0 ratio(putting 100 in the .rc) and at a 0.45 ratio(putting a 045 in the .rc), and all three haven't worked.

I tried putting in the string:

*schedule = ratio,60,60,"stop_on_ratio=100,50000M,150"*

And I also tried the string(just like it shows in the example .rc on the rtorrent wiki):

[I]# stop_on_ratio = min_ratio,min_upload,max_ratio
#
# Example: 

schedule = ratio,60,60,"stop_on_ratio=150"[/I]

And neither of those worked. Anyone else have any suggestions? If I can't get this to work then I'm going to have no other choice but to switch back to Transmission as I need this feature. And I'm unable to get any of the rtorrent webui's to work.

Thanks.

EDIT: By the way, I keep getting the error: *Scheduled command failed: ratio: Command "stop_on_ratio" does not exist.* at the bottom of my rtorrent. And I get this error with either above string inputed in the .rc.

I believe there was an update in rtorrent 0.8.4. Try this reading here:

[http://libtorrent.rakshasa.no/wiki/RTorrentRatioHandling]("http://libtorrent.rakshasa.no/wiki/RTorrentRatioHandling")



Bill

---

### Post by h8uthemost on 2010-07-20
EDIT: Ha! I finally got it. I used this setting for a 1.5 ratio:

[I]ratio.enable= 
ratio.min.set = 150 
ratio.max.set = 150[/I]

That did it. Now my torrents are stopping at the ratio. Thank MrWES for pointing out that part of the wiki. And thank you to everyone else(especially marshmallow) for trying to help.

---

### Post by MrWES on 2010-07-20
Bitte.

---

