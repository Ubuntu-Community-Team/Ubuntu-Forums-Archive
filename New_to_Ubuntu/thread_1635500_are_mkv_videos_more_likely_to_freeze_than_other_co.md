---
title: "are mkv videos more likely to freeze than other codecs?"
date: 2010-12-01
forum: New to Ubuntu
---

### Post by maryalesia on 2010-12-01
This is probably a stupid question. I have this one mkv video file that freezes at the same point everytime I play it. I have tried playing it in both movie player and VLC. 

I'm assuming it's just a bad file (especially since it only freezes in that one spot - like a scratch on a DVD) but I would like to know if any video codecs are better / more compatible with ubuntu than others ... if that even makes sense.

(I'm not entirely sure how all this computer business works ... I remain afloat due to wonderful forums such as this, copy-pasting code, and sheer persistence.)

---

### Post by Zzl1xndd on 2010-12-01
MKV is actually a container and not a codec.  

[http://en.wikipedia.org/wiki/Container_format_(digital](http://en.wikipedia.org/wiki/Container_format_(digital))

[http://en.wikipedia.org/wiki/Codec](http://en.wikipedia.org/wiki/Codec)

Most of the time the container files (MKV, AVI, Etc) should cause much issue.

---

### Post by themusicalduck on 2010-12-01
I had this problem. It seemed to happen mostly with HD videos that use chapters. I think there is a bug in VLC that means it can't handle chapters well.

I started using smplayer instead and have never had the same problem, so I'd recommend using that instead. It should be in the software centre.

---

### Post by maryalesia on 2010-12-01
> **tweakedenigma said:**
> MKV is actually a container and not a codec.

*smacks forehead* I am such a n00b ... maybe one day I'll tell y'all about that one time that I accidentally deleted GRUB. 

> **themusicalduck said:**
> I had this problem. It seemed to happen mostly with HD videos that use chapters. I think there is a bug in VLC that means it can't handle chapters well.

I started using smplayer instead and have never had the same problem, so I'd recommend using that instead. It should be in the software centre.

This makes perfect sense! I will definitely try it. I'm an HD junkie and will do anything for those extra pixels ...

---

### Post by rykel on 2010-12-02
Hi, try another solution... if you are using NVIDIA official driver, simply deactivate it and use the default open source Noveau/NV driver. It will play MKV files smoothly. Not sure why, but it works for me!

Does anyone know why the official NVIDIA driver will NOT play MKV videos smoothly?

---

### Post by cascade9 on 2010-12-02
> **rykel said:**
> Hi, try another solution... if you are using NVIDIA official driver, simply deactivate it and use the default open source Noveau/NV driver. It will play MKV files smoothly. Not sure why, but it works for me!

Does anyone know why the official NVIDIA driver will NOT play MKV videos smoothly?

I've never had any issues with .mkv and the nvidia drivers. But I dont have many .mkvs, maybe I've been lucky.

---

### Post by maryalesia on 2010-12-02
> **rykel said:**
> Hi, try another solution... if you are using NVIDIA official driver, simply deactivate it and use the default open source Noveau/NV driver. It will play MKV files smoothly. Not sure why, but it works for me!

Does anyone know why the official NVIDIA driver will NOT play MKV videos smoothly?

I'm not sure about nvidia drivers. In my experience, they don't play well with Linux. The last time I turned mine off I had some pretty intense screen tearing, which is extremely irritating. Even with them on it took a while to fix that problem.

Also, in nvidia settings, you cant change the refresh rate from 60, which means that my tv tears in twin view. I have to disable my laptop screen to get it to stop.(i don't think the drivers can handle using two different refresh rates for two different screens - which is annoying because in Windows you can choose the refresh rate for each screen) 

QUESTION: when I don't have nvidia drivers enabled, the ubuntu logo at log-in is crisp and nice-looking. When I DO have them enabled, the logo is significantly larger and very pixelated. Why is this?

---

### Post by maryalesia on 2010-12-02
you know what? I'm going to start another thread that is solely about nvidia drivers. Ignore my last post.

---

### Post by rykel on 2010-12-03
> **maryalesia said:**
> QUESTION: when I don't have nvidia drivers enabled, the ubuntu logo at log-in is crisp and nice-looking. When I DO have them enabled, the logo is significantly larger and very pixelated. Why is this?

I am facing this issue too, and perplexed about it... but it does show that Nouveau is VERY MUCH needed, because Nvidia is not giving us the best driver and driver behaviour possible. I hope to use Nouveau in 3D soon!!

p/s. Anyone found the truth about Nvidia vs MKV??

---

### Post by 3rdalbum on 2010-12-03
The NVIDIA problem cannot be specific to MKVs. Mkv is just a container format.

The problem is probably specific to a codec such as H264 and the VDPAU decoder/output supported by NVIDIA cards. Disabling VDPAU will probably work around the problem in a less drastic way than changing to Nouveau drivers.

---

### Post by beew on 2010-12-04
> **rykel said:**
> Hi, try another solution... if you are using NVIDIA official driver, simply deactivate it and use the default open source Noveau/NV driver. It will play MKV files smoothly. Not sure why, but it works for me!

Does anyone know why the official NVIDIA driver will NOT play MKV videos smoothly?

If you "deactivate" (you mean remove?) the Nvidia driver you would have no 3d effect and depending on your card, no gpu acceleration as well. At least for me vpdau works nicely, it reduces cpu usage from 70%-80% for high resolution files to barely 10%.

---

### Post by cascade9 on 2010-12-04
> **maryalesia said:**
> I'm not sure about nvidia drivers. In my experience, they don't play well with Linux. The last time I turned mine off I had some pretty intense screen tearing, which is extremely irritating. Even with them on it took a while to fix that problem.

I think you might have got this backward? 

The drivers may 'taint the kernel' but they work just fine for me and almost everybody else, and have done for years. 

> **maryalesia said:**
> Also, in nvidia settings, you cant change the refresh rate from 60, which means that my tv tears in twin view. I have to disable my laptop screen to get it to stop.(i don't think the drivers can handle using two different refresh rates for two different screens - which is annoying because in Windows you can choose the refresh rate for each screen) 

Ummm...I have noidea what is causing your issues, but there is not 60Hz limit to the refresh rate. One of the machine here runs a 17'' CRT 1280x960 @ 85Hz, and another is running 1 17'' CRT 1024x768 @ 85Hz and a TV @ 60Hz. Both running nvidia drivers. 
 
> **maryalesia said:**
> QUESTION: when I don't have nvidia drivers enabled, the ubuntu logo at log-in is crisp and nice-looking. When I DO have them enabled, the logo is significantly larger and very pixelated. Why is this?

Its because of KMS (keernel mode setting) Heres some info on that (probably not quite what your after, but I cant be bothered to find a page that fits what you are after more exactly)- 

[http://www.netsplit.com/2010/03/30/all-about-kernel-mode-setting/](http://www.netsplit.com/2010/03/30/all-about-kernel-mode-setting/)

Its fixable with very little effort- 

[http://www.webupd8.org/2010/10/script-to-fix-ubuntu-plymouth-for.html](http://www.webupd8.org/2010/10/script-to-fix-ubuntu-plymouth-for.html)

> **rykel said:**
> I am facing this issue too, and perplexed about it... but it does show that Nouveau is VERY MUCH needed, because Nvidia is not giving us the best driver and driver behaviour possible. I hope to use Nouveau in 3D soon!!

p/s. Anyone found the truth about Nvidia vs MKV??

If you really want an opensource driver for your video card, from what I know ATIs open source drivers are better than nouveau. 

I dispute that 'nvidia isnt giving us the best driver and driver behaviour'...ever used ATI catalyst? LOL 

BTW, I tried a different .mkv video on the machines here running nvidia cards, not a single issue.....

---

### Post by maryalesia on 2010-12-04
> **cascade9 said:**
> I think you might have got this backward? 

The drivers may 'taint the kernel' but they work just fine for me and almost everybody else, and have done for years.

I got it right I just wasn't being very clear. The screen tearing occurs with both the accelerated driver and the open source driver. It is worse with the open source driver, though.  


> **cascade9 said:**
> 
Ummm...I have noidea what is causing your issues, but there is not 60Hz limit to the refresh rate. One of the machine here runs a 17'' CRT 1280x960 @ 85Hz, and another is running 1 17'' CRT 1024x768 @ 85Hz and a TV @ 60Hz. Both running nvidia drivers. 
 
I mean in nvidia settings. I'm sure its actually running at whatever speed is necessary when I hook it up to a TV, but it always SAYS its running at 60Hz. My problems with this, however, are specific to when I am using TV-out or twinview or whatever, when the settings automatically default to the refresh rate of my laptop screen. This creates tearing on the television. 

> **cascade9 said:**
> 

[http://www.netsplit.com/2010/03/30/all-about-kernel-mode-setting/](http://www.netsplit.com/2010/03/30/all-about-kernel-mode-setting/)

Its fixable with very little effort- 

[http://www.webupd8.org/2010/10/script-to-fix-ubuntu-plymouth-for.html](http://www.webupd8.org/2010/10/script-to-fix-ubuntu-plymouth-for.html)

I will definitely look into that.

---

### Post by maryalesia on 2010-12-05
> **cascade9 said:**
> 
Its fixable with very little effort- 

[http://www.webupd8.org/2010/10/script-to-fix-ubuntu-plymouth-for.html](http://www.webupd8.org/2010/10/script-to-fix-ubuntu-plymouth-for.html)




I ran this script and picked my resolution (I even checked twice to make sure it was the correct one!) and now what I have is:
in 10.10, the boot screen with accelerated drivers doesn't have graphics, it is in terminal font. The colors are correct but you still see the text loading. After this script it was the same ... but tinier. 

HOWEVER ... after I ran this script I also got to see the *perfect* boot screen ... as I shut down my computer. 

The revert script is gibberish to me. I purged and reinstalled grub and it is still the same. Can anyone make sense of the revert script?

---

### Post by maryalesia on 2010-12-05
actually, I started another thread just about that one script and how to reverse it.

---

