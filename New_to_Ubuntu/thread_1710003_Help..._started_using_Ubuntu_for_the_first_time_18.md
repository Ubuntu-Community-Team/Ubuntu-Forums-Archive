---
title: "Help... started using Ubuntu for the first time 18/03/11"
date: 2011-03-19
forum: New to Ubuntu
---

### Post by chris_vw_1987 on 2011-03-19
Hey guys, hope you can help.

I am a trainee techy that is fluent in windows, but never ever used anything with Linux before..

I have been assigned a mission through work to learn about Ubuntu and learn how to use Fog to send images of harddrives across networks (I think).

Since yesterday so far I have:

1 - Installed Ubuntu onto my spare netbook (freedom zoostorm netbook)
2 - I managed to get the wifi working
3 - Installed the updates from Ubuntu
4 - Installed windows wine??
5 - Looked for graphics drivers and grasped that you have to copy and paste code into terminal to get information about hardware on your computer?? lol
6 - Found out my graphics card is a Intel 945GME mobile express
7 - posting on here

lol, hope you can help guys... Everyone at work knows very little about linux, and im being the test subject to learn about it, any help will be much appreciated and anyone who wants to offer clear telephone help I will pay you for your time.

Cheers guys

---

### Post by mikewhatever on 2011-03-19
Why do you think you need a graphics driver? Are there graphical problems?

---

### Post by chris_vw_1987 on 2011-03-19
Yeah, there be problems lol... Ill take a picture now and show you what i mean :

[https://dl-web.dropbox.com/get/Photos/WP_000082.jpg?w=ee10fbc8](https://dl-web.dropbox.com/get/Photos/WP_000082.jpg?w=ee10fbc8)

[https://dl-web.dropbox.com/get/Photos/WP_000081.jpg?w=79a1e0a9](https://dl-web.dropbox.com/get/Photos/WP_000081.jpg?w=79a1e0a9)

As you can see, the netbook itself doesnt use the full width of the monitor, and when its connected to the external monitor the resolution is crap.. plus on the netbook I cant use the touch pad as the computer goes crazy whenever I touch it :)

---

### Post by Dutch70 on 2011-03-19
Those links aren't working for me. Try attaching the pics to your next post with the paper clip in the toolbar.

This is what they lead me to...

---

### Post by chris_vw_1987 on 2011-03-19
Ah, didnt see the paper clip.

---

### Post by fabricator4 on 2011-03-19
> **chris_vw_1987 said:**
> Ah, didnt see the paper clip.

You're mirroring a low res netbook monitor onto a larger LCD, with a different ratio.  It's confused, though I don't know why the netbook screen is so messed up.

You can turn off the netbook screen in BIOS and set the LCD to whatever resolution you want, or unplug the LCD screen, or go into monitor preferences and uncheck "same in image in all monitors" so that you have two independent desktops (and then orient the correctly to each other) and set the resolutions appropriate to the physical screen capabilities.  I like to keep system stuff on the smaller screen, and put applications on the larger one.

Chris.

---

### Post by chris_vw_1987 on 2011-03-19
Thanks, thats a little better now I've disabled the netbooks screen.. however the detail on the LCD monitor is still a little crap... resolution only goes up to 1024 x 768 in a 4:3 aspect ratio then it jumps to 1360 x 768 for a 16:9 ratio, the max 4:3 aspect ratio resolution should be higher 

I tried to use xandr (or somthing like that) to change the resolution but its still scetchy..


Any ideas guys? :)

---

### Post by chris_vw_1987 on 2011-03-19
any ideas guys?

---

### Post by Hedgehog1 on 2011-03-19
> **chris_vw_1987 said:**
> 
Since yesterday so far I have:

1 - Installed Ubuntu onto my spare netbook (freedom zoostorm netbook)
2 - I managed to get the wifi working
3 - Installed the updates from Ubuntu
[B]4 - Installed windows wine??
5 - Looked for graphics drivers[/B] and grasped that you have to copy and paste code into terminal to get information about hardware on your computer?? lol
6 - Found out my graphics card is a Intel 945GME mobile express
7 - posting on here


You will not be using any Windows video drivers; in fact you would be better off (for learning Linux purposes) not to install Wine.  Your goal is to learn Linux.

Menu to System >> Preferences >> Monitors.  This is where you set screen resolution in an Ubuntu install.

***The Hedge***

:KS

---

### Post by chris_vw_1987 on 2011-03-19
> **Hedgehog1 said:**
> You will not be using any Windows video drivers; in fact you would be better off (for learning Linux purposes) not to install Wine.  Your goal is to learn Linux.

Menu to System >> Preferences >> Monitors.  This is where you set screen resolution in an Ubuntu install.

***The Hedge***

:KS


Ok, so I should uninstall windows wine?

Also, I know Menu to System >> Preferences >> Monitors, but the maximum resolution is still not good enough.. I know my monitor will display higher/clearer image :) how do I change my resolution to one thats not listed on the drop down box?

---

### Post by chris_vw_1987 on 2011-03-19
Well thanks for the help you guys, in the end I just had to create a new mode in xrandr and then apply it to the VGA1 monitor.

Problem sorted now.

---

### Post by Dutch70 on 2011-03-20
> **chris_vw_1987 said:**
> Well thanks for the help you guys, in the end I just had to create a new mode in xrandr and then apply it to the VGA1 monitor.

Problem sorted now.

 Would you mind telling us how you did that & marking this thread solved so others with this problem can find your answer?

---

