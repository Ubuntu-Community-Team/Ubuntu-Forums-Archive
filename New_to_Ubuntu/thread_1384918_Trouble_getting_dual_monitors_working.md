---
title: "Trouble getting dual monitors working"
date: 2010-01-19
forum: New to Ubuntu
---

### Post by ployer on 2010-01-19
Hi all, I am really new to linux and ubuntu other than a class i took in college years ago. But I installed it succesfully on a computer i built which has 2 Nvidia 9800 GX2 Graphics cards in it, which essentially is setup to run quad SLI on occasion. However I have a monitor plugged into each card, yet I can only detect one of them in Ubuntu, I think I really could get into the whole Ubuntu thing but with my other monitor sitting there dead it kind of kills it for me lol. I noticed I had restricted drivers and I installed those, I am not sure though if they were the latest. Any suggestions? Thanks

---

### Post by sandyd on 2010-01-19
have you tried looking in the nvidia control panel.

---

### Post by pietro_spina on 2010-01-19
in the terminal
```
/usr/bin/nvidia-settings
```
or use you favorite cliky method to launch the control panel.

and check the settings under display configurations...

also for some settings I have had to launch the control panel with ```
sudo /usr/bin/nvidia-settings
```
But I usually see if I can set things up the way I want **without** using 'sudo'

---

### Post by ployer on 2010-01-20
Thanks for the responses Ill try these when I get home this evening.

---

### Post by fooman on 2010-01-20
> **pietro_spina said:**
> in the terminal
```
/usr/bin/nvidia-settings
```or use you favorite cliky method to launch the control panel.

and check the settings under display configurations...

also for some settings I have had to launch the control panel with ```
sudo /usr/bin/nvidia-settings
```But I usually see if I can set things up the way I want **without** using 'sudo'

when opening the nvidia-settings for editing with root privileges....you should open it with the "gksudo" prefix,  like so:

```
gksudo nvidia-settings
```the same is true when using any gui editor with root privileges.  if using a command line editor,  you can just use "sudo".  see here for more:

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by pietro_spina on 2010-01-20
> **fooman said:**
> when opening the nvidia-settings for editing with root privileges....you should open it with the "gksudo" prefix,  like so:

```
gksudo nvidia-settings
```the same is true when using any gui editor with root privileges.  if using a command line editor,  you can just use "sudo".  see here for more:

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

It is because of that behavior of opening the GUI from the user config file that I choose to use sudo in this case rather than gksudo.
nvidia-settings has a user config file  ~/.nvidia-settings-rc that I want to load but sometimes I also want it to have the ability to save changes to /etc/X11/xorg.conf

This is the **one** case where I do this. Usually I use gksudo as mentioned in the link(which BTW _ployer_ is a good resource since you are new to linux). On the other hand I could be totally misguided in my understanding of these things, and welcome being educated further.

regards,
-p

---

### Post by ployer on 2010-01-20
Ok i gave your suggestions a whirl but no dice, it seems that my second monitor is not being detected. I clicked on the Detect Monitors button but that didn't seem to do anything. I'm going to do some Googling to see if I can figure this out. It does however seem to be detecting both GPU's as they both show up in the control panel so that's a positive thing atleast.

---

### Post by pietro_spina on 2010-01-20
These are a couple links to old threads... it looks like as of early 2009 multiple card multiple monitors were not working. you might find more information by searching in bug-reports or the xorg mailing lists. depending on you technical knowhow and willingness to roll up your sleeves, those places may have a solution.

[http://ubuntuforums.org/showthread.php?t=1076492](http://ubuntuforums.org/showthread.php?t=1076492)
[http://ubuntuforums.org/showthread.php?t=1058961](http://ubuntuforums.org/showthread.php?t=1058961)

You should of course confirm that all is well with your other monitor, and that it can be recognized. (shutdown, unplug the one that was recognized, reboot)

by the end of this MONUMENTAL thread [http://ubuntuforums.org/showthread.php?t=884161](http://ubuntuforums.org/showthread.php?t=884161) people are claiming success so the answer is out there somewhere I'm sorry I don't have it for you. best of luck.

---

### Post by lyall on 2010-01-20
check the following link for dual monitors setup
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Configure_Dual_Monitors_with_nVidia]("http://ubuntuguide.org/wiki/Ubuntu:Karmic#Configure_Dual_Monitors_with_nVidia")

hope this helps

good luck and have fun learning

---

### Post by ployer on 2010-01-21
Thanks for the respones.

I am able to get to the X Server Configuration utility, After reading some more though i think i was wrong in my earlier post and both of my video cards are not being detected. Currently I can see GPU0 and GPU1 in my Nvidia X Server configuration utility. This is because a single card houses 2 GPU's for a total of 4 GPU's in my entire system. So this has lead me to believe both cards are not being detected. 

Last night I was about to get the most up to date driver installed from Nvidia, 195.53 if memory serves me correctly.

---

### Post by DenysT on 2010-01-22
The nvidia-settings app sees both monitors but when I try to save settings I get an error parsing the etc/X11/xorg.conf file and the app just shuts down. This in turn disables the second monitor again if I reopen nvidia-settings. Doesn't seem to make a diff whether I use gksudo or not. As I understand it 9.10 doesn't use the xorg.conf file so this may be the problem eh? Whatever 9.10 is DOA for dual monitors as far as I can tell with nVidia unless a newer driver is available for 9.10.

---

