---
title: "Yamaha AC-XG audio linux driver"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by Joycem3 on 2009-01-16
Hi,

I am brand new to ubuntu.  I successfully installed Ubuntu 8.10 on my Toshiba Tecra 9100; however I cannot get the sound card to work.  The sound card does work in Windows so I believe that I just don't have the drivers installed correctly.  My volume control has a circle with a line through it and clicking on it tells me "No volume control GStreamer plugins and/or devices found".

Does anyone know how I can fix this?  And if you do, could you please give it to me in little baby-steps?

Thank you kindly,

Joyce

---

### Post by SteveDee on 2009-01-17
If you haven't already done so, go to System > Preferences > Sound > Devices and experiment with any Sound Playback options you have listed for Sound Events.

You can click the Test button at each stage to see if anything is happening.

---

### Post by Joycem3 on 2009-01-17
Thank you for your response.  Unfortunately, that was not the fix (but it is good to know where that box is!).  When I moved through the drop downs and pressed test I received this response:


audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.


Iaudiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not get/set settings from/on resource.


There are slight differences, but I think they amount to the same thing.

Any information would be appreciated.

Thank you.

Joyce

---

### Post by SteveDee on 2009-01-17
I'm no expert on sound problems, but at least this post will move you back up to the top, and maybe someone bright will notice & respond!

In the meantime it might be an idea to see if 'buntu recognizes your sound card.

Goto Applications > Accessories > Terminal
In the Terminal type; aplay -l

Hopefully you should see some confirmation of your soundcard. My system produces this:-

steve@davis-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
steve@davis-desktop:~$ 


Or you might get a response which includes; "...no soundcard found..."

Maybe you should copy & paste the output in your next post.

{By the way "-l" is lower case L}

---

### Post by Joycem3 on 2009-01-17
Thank you that is very kind of you.  I ran the command you suggested in the terminal box and it tells me "no sound card found".  I know the card was there in Windows....How can I convince Linux that it is there?

Any suggestions appreciated.

Thank you.

Joyce

---

### Post by SteveDee on 2009-01-18
Maybe the best approach is for you to take a look at the sound guide here: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

If that looks too complicated you could just add a post to the thread above. You may have more luck getting help in that forum as it concentrates on multimedia issues.

---

### Post by treesurf on 2009-01-18
What is the output when you go to the terminal and type "lspci" ?

---

### Post by OneMixDJ on 2009-01-22
I'm also experiencing the same problem.

My desktop (as per manufacturer's specs) also has a Yamaha sound card.

Like Joycem3, my "aplay -l" output reads that there is no sound card.

With respect to treesurf's question, I'll sit on the sidelines to let Joycem3 reply with some info. Besides, I don't want to jump in the middle of this dialogue and complicate things. :)

Thanks!

---

