---
title: "Can't get mic to work."
date: 2011-04-06
forum: New to Ubuntu
---

### Post by swt on 2011-04-06
EDIT: Problem has been solved. Thanks.

Hello, I've recently installed ubuntu 10.10, and this is my first time running a non windows os on my own machine. I've been able to get the sound playback running, but I cannot get my microphone to work. I've checked the mic, and it works fine, so I'm assuming I have something setup wrong.

After reading through some of the threads here I went through alsamixer and pavucontrol to try and get it working, but I really don't know what I am doing. In the sound preferences I have the option to choose Line, Mic 1, or Mic 2, but none of them seem to produce anything. Also, I went through in alsamixer and put everything as high as it could go.

My chip is: Realtek ALC892, and my card is: HDA ATI SB.

Anyone have any ideas on how to get it to work? Any input is greatly appreciated.

---

### Post by kailkitsune on 2011-04-07
your best bet would be "pulse audio" (at least its the best i found, easy to use and understand) when it comes to sound mangers. 

now as to the mic, is it usb? if so you need to select it under the hardware drop down menu, if its a regular jack make sure its getting good connection (mine is about a mm out of the jack itself.).

let me know if this help i had some mic problems to but there resolved now, so i should be able to help.

---

### Post by Soulcage on 2011-04-07
So if you open alsamixer you have 2 tabs playback and recording. If you want to hear yourself go over to mic and hit up arrow so its at 100, and if there's 2 MM's hit m to unmute it, then go to mic boost and hit up to make it 100 too.

For recording and programs go to the capture tab then you can set mic boost to 100 and then go to capture and set it to 100 and set the input source to mic. I think thats all you should need.

---

### Post by swt on 2011-04-07
Its a normal jack mic. I'm certain the connection is good because when I boot into Windows without touching it, it works.

In alsamixer everything is at 100, and unmuted. Still doesn't seem to be working.

---

### Post by swt on 2011-04-07
Started working all of sudden. Thanks.

---

