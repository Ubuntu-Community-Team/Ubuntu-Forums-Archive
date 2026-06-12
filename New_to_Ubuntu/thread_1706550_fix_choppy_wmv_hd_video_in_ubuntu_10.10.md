---
title: "fix choppy wmv hd video in ubuntu 10.10"
date: 2011-03-14
forum: New to Ubuntu
---

### Post by krishna.988 on 2011-03-14
Hi, I'm trying to play the sample Windows 7 Wildlife.wmv HD Wmv file in totem and vlc but I find the video to be choppy and the audio mutes in the totem player for sometime in the middle also I'm unable to seek the video file in the middle..Can anyone help me out?

Overall its a poor playback quality..comapre wmp12 in windows 7

P.S. I have installed ubuntu restricted extras and medibuntu packages..I'm using Ubuntu 10.10

---

### Post by beew on 2011-03-14
What is the spec of your computer? What graphic card do you use?

In my experience totem is garbage. VLC is usually quite good but since  it uses only one core it may choke on some hd videos (say you have  dual  core machine but each core is not very powerful)
When vlc fails mplayer usually can do the job. You can install a multithreaded version of mplayer from this ppa. [https://launchpad.net/~ripps818/+archive/coreavc]("https://launchpad.net/%7Eripps818/+archive/coreavc")  you can just install mplayer and smplayer if you don't use coreavc  (dishowserver is needed only if you use coreavc, otherwise you don't  need it)

---

### Post by krishna.988 on 2011-03-14
> **beew said:**
> What is the spec of your computer? What graphic card do you use?

In my experience totem is garbage. VLC is usually quite good but since  it uses only one core it may choke on some hd videos (say you have  dual  core machine but each core is not very powerful)
When vlc fails mplayer usually can do the job. You can install a multithreaded version of mplayer from this ppa. [https://launchpad.net/~ripps818/+archive/coreavc]("https://launchpad.net/%7Eripps818/+archive/coreavc")  you can just install mplayer and smplayer if you don't use coreavc  (dishowserver is needed only if you use coreavc, otherwise you don't  need it)

My processor is Intel pentium dual core 2.8 Ghz with 2 GB RAM and built in intel graphics

---

### Post by beew on 2011-03-14
Try install smplayer from the ppa and in preference > peformance choose use 2 core in decodings, in video choose "xv" to for output, for audio output choose alsa (other audio options may work too, but this works best for me)

Your  graphic card probably supports hardware decoding for Windows, I don't know whether it supports it for Linux (better provide the model)  or how to enable it if it does (My machines that use Intel graphic cards are old and they don't support hardware decoding for Linux).  Someone more knowledgeable may be able to help you out

---

### Post by krishna.988 on 2011-03-14
> **beew said:**
> Try install smplayer from the ppa and in preference > peformance choose use 2 core in decodings, in video choose "xv" to for output, for audio output choose alsa (other audio options may work too, but this works best for me)

Your  graphic card probably supports hardware decoding for Windows, I don't know whether it supports it for Linux (better provide the model)  or how to enable it if it does (My machines that use Intel graphic cards are old and they don't support hardware decoding for Linux).  Someone more knowledgeable may be able to help you out


Sometimes I really feel why should I struggle so much with ubuntu which is not able to play a simple HD video properly.. where as Windows plays it flawlessly..

---

### Post by beew on 2011-03-14
Well I play hd video flawlessly (~8% cpu for 1080p) in Linux on my 1 year old laptop (with a Nvidia graphic card which supports hardware decoding in Linux). If Windows play hd video in your system flawlessly  while Linux doesn't it is probably because your card supports features such as hardware decoding in Windows but not Linux. This is hardly the fault of Linux but rather the hardware manufacturer discriminating against Linux.

You have not told us exactly which card do you have btw, so people wouldn't be able to help you if they want to. I know some newer Intel cards do support VAAPI for Linux but like I said I don't have such a card so I am not sure how to enable those features even if your card works.

---

### Post by krishna.988 on 2011-03-14
> **beew said:**
> Well I play hd video flawlessly (~8% cpu for 1080p) in Linux on my 1 year old laptop (with a Nvidia graphic card which supports hardware decoding in Linux). If Windows play hd video in your system flawlessly  while Linux doesn't it is probably because your card supports features such as hardware decoding in Windows but not Linux. This is hardly the fault of Linux but rather the hardware manufacturer discriminating against Linux.

You have not told us exactly which card do you have btw, so people wouldn't be able to help you if they want to. I know some newer Intel cards do support VAAPI for Linux but like I said I don't have such a card so I am not sure how to enable those features even if your card works.


It is Intel G31

---

### Post by krishna.988 on 2011-03-14
> **krishna.988 said:**
> It is Intel G31


Solved !!Installed Gnome mplayer..plays the wildlife.wmv hd video flawlessly..

---

### Post by beew on 2011-03-14
Glad you get it working. I have told you about mplayer in my first reponse. :) (gnome-mpayer is mplayer with a gui front end)

---

