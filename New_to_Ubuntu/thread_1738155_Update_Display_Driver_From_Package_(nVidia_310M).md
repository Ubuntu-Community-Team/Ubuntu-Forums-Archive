---
title: "Update Display Driver From Package (nVidia 310M)"
date: 2011-04-24
forum: New to Ubuntu
---

### Post by rez182 on 2011-04-24
I am downloading the nvidia display driver from nvidia.com for linux 32, i am using ubuntu 32, how can i install this driver? the filename and extension is 
nvidia-linux-x86-270.41.06.run

BTW i have the nvidia x server settings installed, (popped up after ubuntu installation)

how can i install this package or driver?

i noticed video play back in linux is not so good. if a video has too much motion in it, something happens like the video breaks a little, not smooth. why does this happen? and how can we fix it?

sorry for the second question.

---

### Post by yetiman64 on 2011-04-24
> **rez182 said:**
> I am downloading the nvidia display driver from nvidia.com for linux 32, i am using ubuntu 32, how can i install this driver? the filename and extension is
nvidia-linux-x86-270.41.06.run

BTW i have the nvidia x server settings installed, (popped up after ubuntu installation)

how can i install this package or driver?

i noticed video play back in linux is not so good. if a video has too much motion in it, something happens like the video breaks a little, not smooth. why does this happen? and how can we fix it?

sorry for the second question.

I don't recommend the use of that driver for a beginner, first up. The problem is with nvidia cards not working well with compiz.

Have you tried the nvidia-current drivers in System > Administration > Hardware drivers first. I use these with an nvidia gt240 card but noticed what you state with the breaking of video playback.

I managed to fix the problem with a thread on this site. The thread has been moved to the archives but I have managed to find it here [http://ubuntuforums.org/archive/index.php/t-1390284.html](http://ubuntuforums.org/archive/index.php/t-1390284.html)

I would suggest you check that you have the ubuntu nvidia-current drivers installed and try the link for a fix before trying the downloaded drivers you show above. If the fix fails to work for you then I would suggest trying the above drivers.

The fix linked above worked perfectly for me.

**Edit**: In the link, try the "View full version" link at the top of the thread for a better format. It's much easier to read.

---

### Post by rez182 on 2011-05-04
really sorry for the late reply, im facing worse problems right now with the 11.04. it does not work if i let it install the drivers while installation so i turn off the internet to install. im only able to use 11.04 in classic. which sucks. so right now im in 11.04 classic without driver, and wanted to play a MKV video file which needed aditional plugins to play, and in the auto installation process it for some reason delete all my media players which were installed by default like bashee, movie player etc. what the hell.. im really hating ubuntu now... anwyasy jus wanted to say sorry for calling u in here and not replying...thanks btw...i will try this once i get to use ubuntu...

---

### Post by rez182 on 2011-05-06
thanks alot :D:D:D it workd great...btw i had to switch back to 10.10 :( 

i don know if its the display driver or the thing called plymouth, is not compatible with my graphics card (nvidia gforce 310M)

anyways thanks a million for this tip...

---

### Post by yetiman64 on 2011-05-06
You're welcome, It's a pity you couldn't get it working in 11.04 though, just discovering how interesting it is (using a gt240 nVidia card here with unity).

If you're happy with the video (playback/tearing wise) could you mark the thread as solved please, link #5 in my sig has instructions if needed.

Regards from yetiman64 :)

---

