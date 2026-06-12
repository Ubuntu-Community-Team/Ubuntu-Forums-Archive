---
title: "Minor problems"
date: 2010-08-31
forum: New to Ubuntu
---

### Post by mg1234 on 2010-08-31
I want to start off by saying that I really do love Ubuntu so far. There are just a couple of quite minor issues that I'm having. Please bear in mind that I am a complete Linux newbie, so for the purposes of this thread, treat me like a three-year old.

The first few times I logged into Ubuntu 10.04, everything was fine. However, after I switched my NVIDIA GeForce 8400M Video Card Driver to the latest proprietary version for the purposes of using Compiz, I noticed that on startup, everything that was displayed pre-login was at a substantially lower resolution than the one I use normally (1680x1080). As soon as the desktop shows and the jungle sound sounds, it is back to normal. The lower resolution pixellates an otherwise attractive graphic (purple background, white/orange dots, white logo), and being a perfectionist, I find that annoying.

[IMG]http://i1-news.softpedia-static.com/images/extra/LINUX/large/ubuntu1004installation-large_000.jpg[/IMG]

I also wanted to know if there is any way to get rid of showing command line/command prompt/terminal text from showing as I log in. Having migrated from Windows, I really think it looks nicer if that sort of thing happens in private.

Finally, I wonder if there is a way to change the icons for some programs that show up in the indicator applet. Applications like Spotify and Banshee look rather ugly because there is a white cube and some pixellation.

Thanks a million,
Max

---

### Post by themusicalduck on 2010-08-31
The low resolution problem is an unfortunate result of using the closed source Nvidia driver. They haven't implemented the particular feature that is needed to work well with the bootloader like the open source drivers have.

This is a workaround - [http://www.ubunturoot.com/2010/04/how-to-get-plymouth-working-with.html](http://www.ubunturoot.com/2010/04/how-to-get-plymouth-working-with.html)

but it is a bit complicated and although it worked fine for me, I heard it stopped someone else from being able to boot into Ubuntu.

Or of course you could just uninstall the Nvidia driver and switch back to the open source, but then you can't have 3D.

The icon thing is a problem that is to do with the particular software. It can't really be helped annoyingly. I assume you are using the Windows version of Spotify with Wine? If you have an unlimited or premium account you could use the Linux preview version - [http://www.spotify.com/int/download/previews/](http://www.spotify.com/int/download/previews/) which displays the icon properly.

---

### Post by mg1234 on 2010-08-31
Thanks for the quick reply.
That workaround looks good, I'll give it a go now.
Yeah, I'm using Spotify WINE at the moment. Unfortunately I can't use the Linux preview, as I am a free user.
The icon thing is particularly annoying, I noticed the same thing also happens in VLC.

---

### Post by mg1234 on 2010-08-31
Well, the workaround worked! The logo and progress bar have for whatever reason moved to the left-hand side of the screen, but I can live with that. Unfortunately, the first terminal that appears is still low-res, but hopefully I can find a way to eradicate this text altogether...
Thanks again themusicalduck!

---

