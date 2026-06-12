---
title: "ATI Mobility with S-video trying to Clone to a TV on Ubuntu 8.10"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by kestal on 2008-12-25
With 8.04 it was pretty simple. I enabled the ATI proprietary driver via hardware drivers program in the administration panel then I installed ATIconfig... now it does not seem so simple.

[COLOR="Gray"]**My Horrible Luck:**
1) I went to the ATI website and installed the 8.12 version of the ATI drivers and that borked my system and I was stuck at a text screen that kept asking for my login. Without knowing much on how to restore my laptop, I reformatted and tried again.

2) I tried envyng-qt to only find out that after installing it, the ATI drivers were not compatible (go figure). I found this out by taking the risk and trying anyway. To my mistake, I reformatted again.

3) I then figured I could install ATIconfig via terminal using sudo, so I did. It then mentions that I do not have the proprietary driver needed to run. (that was kind of expected, but I hoped).
[/COLOR]

What can I do? I want to be able to plug in my laptop to my TV via an S-video and have my laptop screen on my TV, or projector (for class). Are there any viable options for me? I wish to stick with 8.10 intrepid, especially after the 2.6.27-11 kernel update... as that fixed a lot of my slow boot up times, among other problems...

---

### Post by wootah on 2008-12-25
> **kestal said:**
> With 8.04 it was pretty simple. I enabled the ATI proprietary driver via hardware drivers program in the administration panel then I installed ATIconfig... now it does not seem so simple.

[COLOR=Gray]**My Horrible Luck:**
1) I went to the ATI website and installed the 8.12 version of the ATI drivers and that borked my system and I was stuck at a text screen that kept asking for my login. Without knowing much on how to restore my laptop, I reformatted and tried again.

2) I tried envyng-qt to only find out that after installing it, the ATI drivers were not compatible (go figure). I found this out by taking the risk and trying anyway. To my mistake, I reformatted again.

3) I then figured I could install ATIconfig via terminal using sudo, so I did. It then mentions that I do not have the proprietary driver needed to run. (that was kind of expected, but I hoped).
[/COLOR]

What can I do? I want to be able to plug in my laptop to my TV via an S-video and have my laptop screen on my TV, or projector (for class). Are there any viable options for me? I wish to stick with 8.10 intrepid, especially after the 2.6.27-11 kernel update... as that fixed a lot of my slow boot up times, among other problems...

You have a rough road ahead. I was able to get clone via s-video and also separate X-Sessions, but I had to disable any sort of compositing by the later.

I must admit though, ATI has made very good strides but there is still much more work to do.

EDIT: I forgot about my sig link :) Give it a try... it is old, so proceed with caution!

---

### Post by kestal on 2008-12-26
not sure if this is what I need. I am, afterall, using Ubuntu 8.10. I cannot seem to use the proprietary ATI drivers and I am trying to just clone my screen to my TV with svideo.

I am losing all hope really. I wish to stick with Intrepid, but if I cannot find a viable solution, i might switch back to Hardy :(

I also tried xrandr with no luck, too.

---

