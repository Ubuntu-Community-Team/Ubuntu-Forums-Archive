---
title: "Mythbuntu Home Theatre help"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by zrclshn on 2009-03-21
I currently have Vista Media Center, with a rather large DVD collection already ripped to disk. I have seen demos of Linux MCE, and was impressed at how much better it appeared to be. I was told that a good place to start was to use the Ubuntu live CD to ensure that my current sustem would work properly before venturing on to Linux MCE. I followed this advice, and starting up the system with Ubuntu 8.1 gave me the following problems.

1) No sound
Sound on the system in Onboard Optical that runs directly to my home theatre receiver.
Note: Will ALSA drivers fix this?

2) OverScan
Samsung 61" HD DLP 1080p connected via DVI to HDMI cable. Top and bottom edges
of the screen are not visible, correct resolutions are available.
Note: I read that it may be possible to use the Nvidia utility that comes with the Nvidia
drivers to correct this, but am not sure.

3) Bluetooth Mouse must be connected at startup
Logitech MX5500 Keyboard & mouse, jeyboard works on startup, but mouse must be 
connected via the Bluetooth utility
Note: I am running from the live cd, I do not know if I have to do this each time.

I would like to know if anyone can address these issues with certainty before I blow away my current installation of Vista, and if anyone has any other pointers or gotchas I need to look out for?
Please keep in mind, where as I am very capable on a Windows box, I have almost no experience with Linux.

Thanks for any and all help

System


Motherboard
Asus P5N72-T Premium Nvidia nForce 780i SLI Chipset

Disk Drives
2 TB Raid 0 Striped

Video Card
Nvidia 9600 GT

Processor
Intel Core 2 Quad Q6600

Sound
SoundMAX Integrated Digital HD Audio

---

### Post by hypocratus on 2009-03-21
I would recommend dual-booting Ubuntu and Vista for a while. That way you can see if Ubuntu works for you and see if any problems you might have with Ubuntu are ones that you are willing to work out. Or you can try using wubi, which installs Ubuntu in Windows so you don't have to do any partitioning, just to check for hardware issues. You can uninstall Ubuntu later just like any other program in Windows if you decide that you don't like it or if you decide to move to a dual boot or Ubuntu only system.

---

### Post by zrclshn on 2009-03-21
Thanks 4 your response... The wubi options sounds like it might not be a bad idea, but if it is running from inside Windows, can I expect to see the same issues I would if it were installed solo?  e.g. would the video problem still be there?  I would imagine that it would not be if it is running from within a Vista window.  Thoughts?  Also, do you have any suggestions for the problems I have already detected and listed here?  The overscan, no sound ... etc?

Thanks again

---

### Post by 4ebees on 2009-05-03
Hi there,

I can't say I have the answers to your problems, but agree with the previous poster. Dual boot your machine and then you have time to work out the solutions.

I'd suggest joining your local Linux User Group. See if one is listed here:

[COLOR="Orange"][http://www.linux.org/groups/](http://www.linux.org/groups/)[/COLOR]

Then you can get local support.

Regarding your questions:


> 
2) OverScan
Samsung 61" HD DLP 1080p connected via DVI to HDMI cable. Top and bottom edges
of the screen are not visible, correct resolutions are available.
Note: I read that it may be possible to use the Nvidia utility that comes with the Nvidia
drivers to correct this, but am not sure.


There is a utility in the mythbuntu front end (?backend?) which allows you to change the screen overscan. I can't recall where exactly (my youngest is watching "Go Diego" so I can't check :))

If you check the manual - which is found at the mythbuntu home site:

[COLOR="Orange"][www.mythbuntu.org](www.mythbuntu.org)[/COLOR]

something like setup - appearance - screen settings


> 
3) Bluetooth Mouse must be connected at startup
Logitech MX5500 Keyboard & mouse, jeyboard works on startup, but mouse must be 
connected via the Bluetooth utility
Note: I am running from the live cd, I do not know if I have to do this each time.


Bluetooth devices seem a bit tricky. You'll have to search the forums more I'd say.


>  Sound SoundMAX Integrated Digital HD Audio


You'll need to type the following into a terminal:

[COLOR="Orange"]lspci[/COLOR] 

This will list your pci cards and hopefully your sound card. You'll then need to search ALSA:

[COLOR="Orange"][http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)[/COLOR]

However 

[COLOR="Orange"][http://osdir.com/ml/linux.alsa.user/2002-07/msg00291.html](http://osdir.com/ml/linux.alsa.user/2002-07/msg00291.html)[/COLOR]

would suggest the sound card will work but you may need to find out why it's not producing sound. For instance, you can open a terminal and type in:

[COLOR="Orange"]alsamixer[/COLOR]

This will bring up a list of sound devices and elements that may have their audio turned down or not activated.

If still stuck, you can the write back to this forum or check with your local Linux User Group - almost all of them are very friendly. 

You can also join:

[COLOR="Orange"][www.marcelgagne.com/wftl-lug.html](www.marcelgagne.com/wftl-lug.html)[/COLOR]

Another great LUG.

See how you go.

I'm sure you'll appreciate that learning something new is a pain in the ****, fun, exciting and annoying all at the same time :)

---

### Post by inobe on 2009-05-03
for sound

for ubuntu



1) double click volume icon.

2) select preferences.

3) tick IEC958.

4) close preferences.

5) click switches tab.

6) put a check mark for IEC958.

7) close mixer and enjoy digital spdif.



for kubuntu


1) click volume icon, then click mixer button.

2) right click in mixer dialog and select channels.

3) put a check mark IEC958 and click ok.

4) remove the check mark from mute for IEC958.

5) put a check mark for capture and enjoy spdif digital sound.

---

