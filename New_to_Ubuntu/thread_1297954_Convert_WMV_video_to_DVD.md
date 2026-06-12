---
title: "Convert WMV video to DVD"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by cwmoser on 2009-10-22
Is there a tool I can use on Ubuntu to convert an *.wmv video so that it can be played on DVD player on my television?

I tried to use ffmpeg but keep getting errors like this "Error while decoding stream #0.1"

Thanks

Carl

---

### Post by howefield on 2009-10-22
Devede

Install using Synaptic Package Manager, although depending on the version of Ubuntu you are running, there may be a more up to date .deb file at the devede website.

Devede will create an iso image of your wmv file which you can then burn to a dvd.

---

### Post by Hospadar on 2009-10-22
+1 for devede it is super super easy, just give it a a video file and it will give you a dvd iso.

If you want to do wmv, you'll probably need the w32 or w64 codecs from medibuntu.

If you don't know, medibuntu hosts a lot of stuff kept out of the main repositories for legal/ip reasons in some countries.  Most importantly the windows codecs and the dvd decryption library so you can rip dvd's.

Anywho: go here: [http://www.medibuntu.org/](http://www.medibuntu.org/) go to "repository howto" follow the instructions for your distribution (intrepid/jaunty/karmic/etc), then install either w32codecs or w64codecs (from synaptic or the command line) depending on whether you are running 32 or 64 bit (if you arn't sure, run 'uname -m' in a terminal, if it says 'x86', than 32 bit, if it says 'x84_64', than 64 bit).  Afterwords you *should* be able to convert those wmv's to dvd.


Furthermore, I think the "error decoding stream" is probably coming from the fact that you don't have the w32/w64 codecs installed, so even if you don't want to use devede, you once you install the codecs, you should be able to  convert with your favorite program (mencoder/ffmpeg/etc)

---

