---
title: "How to play MKV files?"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by papuccino1 on 2009-09-09
Hi there, I'm downloading some videos in MKV format, usually in Windows I just downloaded CCCP and I could watch them easily with Media Player Classic. What can I use in Ubuntu?

Keep in mind that I haven't downloaded/installed a single codec or restricted extras with my fresh Linux install so she's still a virgin ;)

---

### Post by ramjet_1953 on 2009-09-09
As far as I know VLC media player can play a MKV file straight-up.

You may want to check-out this link:

[http://www.afterdawn.com/guides/archive/how_to_play_mkv.cfm](http://www.afterdawn.com/guides/archive/how_to_play_mkv.cfm)

Regards,
Roger:)

---

### Post by binbash on 2009-09-10
VLC is the best and fastest solution for you.

---

### Post by credobyte on 2009-09-10
As previously mentioned, VLC should do the job. If not, take a look at ubuntu-restricted-extras and w32codecs/non-free-codecs from Mediabuntu!

---

### Post by andrew.46 on 2009-09-10
Hi papuccino,

> **papuccino1 said:**
> Hi there, I'm downloading some videos in MKV format, usually in Windows I just downloaded CCCP and I could watch them easily with Media Player Classic. What can I use in Ubuntu?)

I suspect that you will have less of a problem with the matroska *container* than potential problems with the actual codecs contained *within* the container. And standing in front of the tidalwave of support for vlc let me put a vote in for MPlayer :). In conjunction with the w32codecs held by [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") (which I might mention will do nothing for the repository vlc which is missing the vital *--enable-loader* option) MPlayer will play almost anything that can be contained within a matroska container.

All the best,

Andrew

---

### Post by MrWES on 2009-09-10
+1 for Mplayer -- it's my player of choice.

---

### Post by snakeman21 on 2009-09-10
I didn't even know what MKV was until yesterday when a video I downloaded ended up being one.  I didn't even notice until after I had played it in VLC with no problem!

---

### Post by andrew.46 on 2009-09-10
Hi snakeman,

> **snakeman21 said:**
> I didn't even know what MKV was until yesterday when a video I downloaded ended up being one.  I didn't even notice until after I had played it in VLC with no problem!

Let me be the first to tell you that these files are also *very* easy to produce under Ubuntu by simply dragging and dropping files onto a great little program called mkvmerge, which you can find in the Ubuntu repository as mkvtoolnix-gui. I attach a screenshot of mkvmerge in action...

Andrew

---

### Post by PunkLV on 2009-09-10
go for VLC: good interface, lots of ways to adjust its behaviour for your needs, one-key hotkeys etc. Plays anythig, even .mod and .xm

---

### Post by snakeman21 on 2009-09-10
Cool, I will have to check that out, Andrew.  Thanks!

---

