---
title: "I need a computer. Any suggestions for Film editing?"
date: 2011-07-06
forum: New to Ubuntu
---

### Post by boreen on 2011-07-06
Hello,

I would like to build an Ubuntu based computer that will be well suited for video editing.

I am hoping that some knowledgeable people can help me choose a setup that will work well. I have been using macs for the past ten years and have really lost touch with the PC market.

I was told that an AMD based system would be the best bang for my buck, which is important because I'm on a limited budget. I can spend about $500-800 at most at the moment, but I don't need any peripherals like a monitor, speakers or mouse. If the system can be upgraded later, that'd be great.

Someone has already advised me to load Ubuntu Studio rather than the regular release.

If people could provide me  with some advice, I'd be very grateful as I'd really like to launch into a project I've been thinking about.

I will be shooting HD footage with a Canon Rebel T2i.

Thanks,
Jon

---

### Post by boreen on 2011-07-06
bump

---

### Post by LowSky on 2011-07-06
Um.. 

newegg.com

best place to go for building a PC.

I'm not really sure what you're looking for besides cheaper than a Mac.
AMD is great and a 6-core Phenom II runs under $250 these days. Much cheaper than Intel's offerings. Nvidia is the graphics card company to use, as they have better Linux support at the moment... 

Newegg has customer reviews for nearly every product, so it will help with your choices too.

---

### Post by Perkins on 2011-07-06
Tigerdirect.com  The Wal-Mart of the computer world.  It's usually a tossup whether they or newegg are cheaper for new equipment.  They tend to have a larger selection of refurbished and off-lease models.


For video editing, you'll want something with plenty of memory.  Your second concern will be processing power.  You'll want at least two cores, but more is better.  It's generally not worth it to pay the premium for anything over 3Ghz.  It's cheaper to just get more cores.

Depending on what you are planning to use for software, it might be worth it to get a good video card to go along with it.  But then I'm not currently aware of Linux video editing software that makes use of a video card's ability to render pictures at high speed.

Personally, I have an old, two-core Pentium D machine that more than keeps up with the editing I do.  Pentium D and Core 2 Duo machines are actually 64 bit, even though they were sold as 32.  ;)  Running the 64-bit version of Linux Mint Debian it's fast enough that the bottleneck becomes the speed of my hard drive.

Speaking of which, you'll probably want a large disk for storage, but if you're doing complex editing, you may find that you need something with a higher data-throughput rate to get it done quickly.  Either a high-performance drive, or a RAID controller, or get a motherboard that has plenty of SATA ports and set up dmraid.  Linux software RAID is reasonably good on a modern machine, just leave one processor core unloaded to handle the disk array.

Those are the basic suggestions.  If you want more detailed advice, let me know.

---

### Post by terrykiwi83 on 2011-07-06
CPU wise you might want to get yourself an Intel i7 cpu (higher end) as they are in simple words awesome at editing and encoding. People may also say other wise but I also recommend the X58 chipset and at least 8GB of good DDR3 RAM. That's just my personal recommendations from experience.

Edit: For under $800 you could get a decent i7 (maybe i7 950? or 2600) and a good mobo + 6GB Ram - that would be a good start

---

### Post by qyot27 on 2011-07-06
With editing apps, you may find yourself in a bind, especially if you're coming from a background of using Final Cut Pro.  Most Linux-based NLEs are more on the level of Windows Movie Maker or iMovie than they are FCP or Premiere or Vegas or Avid.  The two that might fall closer to the latter group are Cinelerra (or maybe Lumiera...wow, I didn't know that'd been released already; gonna have to go try it out on here) and *possibly* Blender's 2D timeline mode.

I'll be one of the unpopular ones and say that if you need to do intensive pre- or post- work, Wine will come in really handy just so you can use AviSynth.


As others have noted, video editing or encoding means that the more power, the better.  Especially concerning processor/memory/bandwidth, not so much graphics because few NLEs will use them aside from how much the OS itself does, but for playback: Nvidia is a must so that you can use VDPAU.  CPU clock speed is only a minimal factor - what I'd look more closely at is the L2 or L3 cache size, # of cores, and the connection interface, and to get lots of RAM that will take full advantage of that bandwidth (which also means either using 64-bit or the 32-bit PAE kernel).

---

### Post by uRock on 2011-07-06
If you are going to be doing lots of movie/video making/editing, then I'd get a server with multiple CPU slots. Kinda like this one [http://zareason.com/shop/ZR-6220.html](http://zareason.com/shop/ZR-6220.html)

---

### Post by scatteredstones on 2011-07-06
This is just an FYI. There looks to be a pretty cool video editing project that just launched a new kickstarter campaign called [Novacut]("http://novacut.com/"). Not only is it an open source project, but I believe  that it's being created primarily for Ubuntu. It's of course not an immediate solution for you software-wise, but it's definitely that looks pretty promising. 

I'm not connected to the project in any way; I simply like what they've envisioned.

---

### Post by decoherence on 2011-07-06
As someone who just installed Windows in order to get a decent NLE, I wish you great luck!

Two tips I picked up in my struggles:

1. Linux NLEs are generally quite lenient about what formats they will import. That doesn't mean the format will work well. I assume you know about broadcast vs. editable formats -- depending on the NLE you use, you will likely want to manually re-encode any broadcast formats in to editable formats. I was going nuts trying to get frame/sample accurate cuts in kdenlive until I manually re-encoded my source footage as MJPEG to get rid of that gnarly temporal compression in MPEG-based formats. I have had good luck with the following command

ffmpeg -i <input_file> -vcodec mjpeg -qscale 1 -an output.avi 

2. Keep an eye on this project [http://www.lightworksbeta.com/](http://www.lightworksbeta.com/) Currently Windows only but soon to be open sourced and their roadmap ([http://www.lightworksbeta.com/index.php?option=com_content&view=article&id=112&Itemid=246](http://www.lightworksbeta.com/index.php?option=com_content&view=article&id=112&Itemid=246)) indicates a linux version is in the works. A free program of this calibre would truly change the face of video editing on linux.

Anyway, best wishes! I hope you have a better experience than I did!

---

### Post by oldsoundguy on 2011-07-06
Industrial Light & Magic, Lucas Film and many others use Sun Workstations.(there are 6 at Skywalker Ranch.)

But, spend some time searching through Google to find what is in your price range.

Atari 1000 along with Video Toaster software is still a viable unit .. many outfits that do commercials still use them!

---

