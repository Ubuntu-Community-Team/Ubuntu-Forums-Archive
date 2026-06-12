---
title: "Software Channels"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by gmillen on 2009-04-30
Does anyone know where I would find "Software Channels"?
I downloaded aMSN, and when I went to install it, I was warned that it was available in "Software Channels", I looked through Applicatio, Places, and System with no luck, then tried "Help", then tried Ubuntu online help, but they are not terms that are in the "Help" files, is this symptomatic of a virus?  How should I handle this warning?

George

---

### Post by furialis on 2009-04-30
The nice part about Ubuntu is you don't have to "download" anything. Look in the software repositories (synaptic) System>administration>synaptic package manager.

---

### Post by wizard10000 on 2009-04-30
> **gmillen said:**
> Does anyone know where I would find "Software Channels"?
I downloaded aMSN, and when I went to install it, I was warned that it was available in "Software Channels", I looked through Applicatio, Places, and System with no luck, then tried "Help", then tried Ubuntu online help, but they are not terms that are in the "Help" files, is this symptomatic of a virus?  How should I handle this warning?

Hi, George -

That means that you didn't have to download it - that the software's already available in normal distribution channels (software channels).

You can go to System --> Administration --> Synaptic Package Manager and install it from there.  Just put 'amsn' in the search box and you'll find it.

Or you can install it from a terminal window by typing

sudo apt-get install amsn

Good luck -

---

### Post by oldos2er on 2009-04-30
Channels = repositories.

---

### Post by gmillen on 2009-05-02
Thanks for the reply,
My next problem is trying to find something that will play movies, tried Movie Player, but am unable to find plug ins to make it work, the only ones that I can find will not load as I have newer ones,  tried vlc and get the message "seek failed" and tried mplayer, which doesn't do anything.  If you know of anything that would work, I would sure appreciate it.
Thanks  

George

---

### Post by oldos2er on 2009-05-03
For commercial DVDs, you'll need libdvdcss2 from Medibuntu ([http://medibuntu.org](http://medibuntu.org)).

---

### Post by gmillen on 2009-05-04
Thanks again for the reply, this didn't work either.
George

---

### Post by freeman2000 on 2009-05-04
Did you add the Medibuntu repository to Synaptics?  From Synaptics, download/install "totem-xine" + "totem-plugins" + "totem-plugins-extra".  Totem-Xine is a more advanced Totem player.  Hope that works for you.
Oh yeah, also download whatever dependencies it determines that you need to go along with this install.  Good luck.

---

### Post by oldos2er on 2009-05-04
> **gmillen said:**
> Thanks again for the reply, this didn't work either.
George

 Care to explain this? Did you enable Medibuntu? then reload your sources.list? Any error messages? If so, please copy and paste them here.

---

### Post by gmillen on 2009-05-04
Thanks again, the Totem Xine worked,  I had installed  libdvdcss2 but couldn't find the Medibuntu application, looked around the site, and I presume lib* is just the plug in, and that Medibuntu is at a different site
Anyway thank you very much for all the help

George

---

### Post by oldos2er on 2009-05-05
Medibuntu is a repository with a lot of non-free (i.e., non open source) goodies available in it. Here's how to add it to your software sources: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by gmillen on 2009-05-06
Thank you again, my next problem is with my Dell Inspiron 1545, I have sound and it also works on my headset, but very low volume, is there a better driver, it is apparently Intel High Definition audio.

Thanks 

George

---

### Post by freeman2000 on 2009-05-07
Try going to  System -->  Administration -->  Hardware Drivers  and see if there are any recommended "proprietary" drivers.  If not, then try a new post with something like "sound" as the title, so your "new" question doesn't get lost in the forum.  Good luck.

---

