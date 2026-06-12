---
title: "custom ffmpeg compilation and other programs"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by ralphz on 2009-02-14
Hi

I want to compile ffmpeg with additional codecs on my system I have found excellent guide (here).

So far no problems now I'd like to compile Cinelerra against new version of ffmpeg. How do I know Cinelerra compiling scripts is going to use the new libraries?

The original ones are in /usr/lib but I have compiled and installed new ffmpeg libs in /usr/local/lib.

I don't think there is an option to point to newer libraries in Cinelerra...

I could probably configure and compile ffmpeg to use /usr/lib but I'm afraid that other programs that link to it would crash. (?)

So my question is what would be the best way to compile the ffmpeg so i have no conflicts with repository programs and in the same time be able to compile cinelerra (or other programs) to use custom compiled version?

Thanks

Ralph

---

