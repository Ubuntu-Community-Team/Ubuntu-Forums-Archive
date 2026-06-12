---
title: "Downloads to use movie player"
date: 2010-10-18
forum: New to Ubuntu
---

### Post by technoinquirer on 2010-10-18
Hello,

I am new to Ubuntu and am wanting to play DVD's on my laptop. I am wondering if anyone has any download suggestions for windows movie player? I assume i need a download because the media player is displaying an error message. 

Any help is much appreciated!

Technoinquirer

---

### Post by cascade9 on 2010-10-18
Windows Media Player...yuck. I didnt use that when I used windows, horrible thing it was. 

If you cant play DVDs on your current media player, you probably need to install DVDcss.  Open a terminal (CLI), and then do this- 

>  sudo apt-get install libdvdread4

 sudo /usr/share/doc/libdvdread4/install-css.sh

Rebooting may be necessary. 

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by Old *ix Geek on 2010-10-19
> **technoinquirer said:**
> I am new to Ubuntu and am wanting to play DVD's on my laptop. I am wondering if anyone has any download suggestions for windows movie player?Why do you want windoze movie player? There are many wonderful media players available on (K)Ubuntu, and I'm sure they're better than anything from Micro$oft, so I don't get it!
> I assume i need a download because the media player is displaying an error message.What media player? And what error message?

---

### Post by sKuarecircle on 2010-10-19
vlc... You will never look back.

---

### Post by rado1 on 2010-10-19
try xine, you can find it in repositories. 
system-> administration -> synaptic package manager.

---

### Post by ddiamon1 on 2010-10-28
I am having the same problem and i have tried to use VLC and Xine, i am currently looking for the solution also.

---

### Post by Perfect Storm on 2010-10-28
Add medibuntu: [http://medibuntu.org/](http://medibuntu.org/)
and install libdvdcss2 afterwards.

---

### Post by amjjawad on 2010-10-29
[http://www.linux.com/news/software/applications/287828:the-five-best-linux-video-players](http://www.linux.com/news/software/applications/287828:the-five-best-linux-video-players)

---

