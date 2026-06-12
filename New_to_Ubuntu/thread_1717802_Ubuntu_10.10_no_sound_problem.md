---
title: "Ubuntu 10.10 no sound problem"
date: 2011-03-30
forum: New to Ubuntu
---

### Post by Cindy&amp;Me on 2011-03-30
I'm sorry if this thread has been posted already . I just installed ubuntu 10.10 desktop edition ,updated it but I have no sound. I am totaly new to ubuntu and need help urgently. Thank you all. I saw somewhere this and I ran it in terminal and I don't know what it even means

*-multimedia            
       description: Multimedia audio controller
       product: CK804 AC'97 Audio Controller
       vendor: nVidia Corporation
       physical id: 5
       bus info: pci@0000:00:04.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2
       resources: irq:22 ioport:dc00(size=256) ioport:e000(size=256) memory:d3003000-d3003fff

---

### Post by metalf8801 on 2011-03-30
Ok lets start with the basics 
If you are using a desktop have you had sure your speaker are on and properly plugged in. 

You should have speaker icon on your top panel on the right side. Click on it then click on Sound Preferences which should be at the bottom. 
If you don't see the speaker icon you can get to Sound Preferences by 
System > Preferences > Sound 
Once you have Sound Preferences open click on the Hardware tab 

These steps will sound obvious, but they still need to be checked. While you are doing this make sure you have some audio playing in the back ground so that you will be able to hear if you have your speakers working. I would play a CD. 

1st make sure there is something listed under "Choose a device to configure:" Please write down what every you see and post it back here. 
2nd make sure the check box next to mute isn't checked 
3rd make sure the speakers are turned up loud enough  
4th try the different options listed in the drop down menu next to Profile:

If any of these things work please post what worked. If not please post what you did trying. 

I hope this helps 
Dan

---

### Post by Cindy&amp;Me on 2011-03-31
Thank you so much for your reply . When I open sound preferences /hardware it shows 
choose a device to configure : 
1 output/1 input
analog stereo duplex
I have blue,green and red jack but no mater which jack I choose  there is no sound .I really appreciate your help.

---

### Post by mastablasta on 2011-03-31
I am assuming it actually shows a device in preferences for you to configure (a small computer card like icon).
 
If not you can try going to terminal and then type in
 
alsamixer
 
a sound mixer will open. set all volumes high up.
 
if it doesn't work then see this thread for more troubleshooting and solutions: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by Cindy&amp;Me on 2011-03-31
I tried with alsa but no luck. I will read the book but I doubt it will fix my sound issue. Thanks anyway.

---

### Post by metalf8801 on 2011-03-31
> **Cindy&Me said:**
> Thank you so much for your reply . When I open sound preferences /hardware it shows 
choose a device to configure : 
1 output/1 input
analog stereo duplex
I have blue,green and red jack but no mater which jack I choose  there is no sound .I really appreciate your help.

Have you tried changing Analog Stereo Duplex to something else?

---

