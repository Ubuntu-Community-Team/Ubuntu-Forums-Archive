---
title: "Microphone not working"
date: 2011-04-02
forum: New to Ubuntu
---

### Post by leomyster on 2011-04-02
Hello All,

I am using Ubuntu 10.04 on my Acer Aspire 5745.
It had many issues in the beginning with my wireless not working and DVD ROM not working. All of them got fixed. Now, I am trying to use Skype.

It installed fine, but I was not able to work with the Microphone.
I have external microphone which I have plugged into the jack provided for the mic. But still it does not work.

I first checked with my Dekstop which has windows to see if the mic was working in the first place. And it was working fine indeed.

But, I am not able to use the mic on my acer laptop.

I tried many tutorials on the web, ranging for tweaking the alsamixer, downloading (and then uninstalling) the pulse audio controller, none of them worked.

What I observed is that in the sound preferences, for the Input category, there is only one device "Internal audio analog stereo". Shouldn't I have another device indicating External as such? Can somebody please help me out with  this.

Thanks,
Mithun

---

### Post by Bölvaður on 2011-04-02
> **leomyster said:**
> 
What I observed is that in the sound preferences, for the Input category, there is only one device "Internal audio analog stereo". Shouldn't I have another device indicating External as such? Can somebody please help me out with  this.
No, "Internal audio analog stereo" is exactly what you should see for a microphone with a jack, instead of usb microphone.

Click the volume button from the panel and then *sound preferences*.
Select *"Internal audio analog stereo*" for sound input.
Select something like "*Microphone 1 / Microphone*" as Connector.

There should only see an external device indicated if you got a webcam, usb mic another soudcard or tv tuner in your computer.

Check every option there to see if you have any input detected... so prepare yourself saying "test, test, testing 1, 2 ,3" a lot today.

*Pulse Audio Controller* is much more powerful and you should use it to redirect the correct input to skype when you find it.

There are two reasons why I could see this not work for you.
1. Drivers for your audiocard are not good enough, or the audiocard is so old it's not added to the kernel when compiled for ubuntu.. in that case you'll need to compile it yourself.
2. The micraphone is muted. One way to unmute it is via alsamixer, if it is muted it will be indicated with an M.


You really should say everything you've done in great details... I have no idea about your computer nor what you have tried so it's like trying to hunt for a fish with a slingshot while blindfolded in a desert...

---

### Post by Kezevi on 2011-06-15
Hello :)

I'm also having the similar problem. I have the Acer Aspire 5745; 64 BIT. My microphone does not work. I clicked on the Sound Recorder from the apps. The output is just noisy distored cracky sounds. Is there something wrong with my sound adapter/card or with the Ubuntu OS itself.

PS: I have checked the sound preferences too. Connecter: Internal microphone - Internal Audio Analog Signal and the Audio Hardware is on Analog Stereo Duplex. I don't have those ALSA mixer, etc.

Please Help. 

 - Kevin

---

