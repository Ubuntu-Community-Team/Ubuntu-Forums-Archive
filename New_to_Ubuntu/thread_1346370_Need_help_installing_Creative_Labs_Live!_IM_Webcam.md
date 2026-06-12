---
title: "Need help installing Creative Labs Live! IM Webcam (VF0350)"
date: 2009-12-05
forum: New to Ubuntu
---

### Post by tin.w on 2009-12-05
Hello,

I just downloaded linux and am enjoying it so far, but I can't seem to get my webcam to work. I found this guide ([http://www.ubuntuhcl.org/browse/product+creative-labs-live-cam-video-im-vf0350?id=4929](http://www.ubuntuhcl.org/browse/product+creative-labs-live-cam-video-im-vf0350?id=4929)) but it goes way over my head. I downloaded the source code and dragged it to my desktop, but I'm not sure what to do next. I opened the terminal and typed gzip -cd ov51x-jpeg-1.5.9.tar.gz | tar xvf - and got the message "gzip: ov51x-jpeg-1.5.9.tar.gz: No such file or directory
tar: This does not look like a tar archive
tar: Exiting with failure status due to previous errors".

Any help appreciated!

---

### Post by natex on 2009-12-05
First, I would make sure that you've completely downloaded the file... that is, it is not corrupt.

Second, try using "**tar xzf ov51x-jpeg-1.5.9.tar.gz"**. This will unpack the file into whatever directory you are in (current directory). Then you can **ls** to see what the new directory's name is, **cd** into it (such as **cd ov51x-jpeg-1.5.9**), then you can do your sudo make install business.

Hope this helps.
natex

---

### Post by tin.w on 2009-12-05
I tried your suggestion and get

justin@justin-laptop:~$ tar xzf ov51x-jpeg-1.5.9.tar.gz
tar: ov51x-jpeg-1.5.9.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
justin@justin-laptop:~$ 

I really have no idea what I'm doing.. could be going about this completely the wrong way.

---

### Post by krissy86 on 2010-01-26
if you need the web cam you can get it at one of those [free giveaways]("http://www.ezwingame.com/") sites and I must say it's a pretty sweet deal since it's for free!

---

