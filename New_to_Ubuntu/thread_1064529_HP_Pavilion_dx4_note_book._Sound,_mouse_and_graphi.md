---
title: "HP Pavilion dx4 note book. Sound, mouse and graphics fixes"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by Peterpapertiger on 2009-02-08
HP Pavilion dv4, set up Ubuntu 8.10 problems and fixes
I am new to Ubuntu LINUX. I find it to be great. Every aspect is better than Vista. I was driven to it by the awful VISA that was a compulsory install on my newish HP, which also isn't all that great. The burning hot touch pad (CPU directly underneath) is a  particularly Special Feature. Anyway this is what worked for me and it will save any other lucky owners of Pavilions a heap of time and effort :). my inexperience means that there are almost certainly better approaches. I suspect I've excessively restarted the computer for example.
 
If , like me, you want to max' the special effects in Ubuntu you run into a problem.
You cannot have
[B]System Preferences Appearance Themes Customize pointer
Settings Redglass or Whiteglass[/B]

and 

**System Preferences Visual Effects Extra**.

You get weird trailing persistent  image debris from around the mouse pointer when you move windows around. These will appear only after you restart the computer, not before. The next day when you switch it back on for example and you're not sure which of the many changes you made yesterday are causing it.

To fix this you need to change the pointer settings to anything other than Redglass Whiteglass and restart the computer.  The large DMZ size pointers are OK

There is a sound card problem with HP's.
To be clear, since this is a problem for newbie's like me, who might be reading this.
You need to run some code (type in & return) in a terminal
(To get to a TERMINAL- See top LHS of screen   click** Applications Accessories Terminal**)
(to ovoid typing You can Control C to copy and  in terminal you can hold  Shift-Control-V for paste.
As you probably know, Control C and Control V are well known shortcut keys for copy and paste. In the Ubuntu  terminal mode you also need to hold the shift key to get them to work)

Thanks to REMU for this sound fix.
[http://ubuntuforums.org/showthread.php?t=912896&page=5](http://ubuntuforums.org/showthread.php?t=912896&page=5)


First:
Code:(copy the next line exactly)
gksu gedit /etc/modprobe.d/alsa-base
Then add the following to the end of the file:
Code:
options snd-hda-intel enable_msi=1

He also warns you to undo any Kernel changes you might have made to try and fix the problem. There were a few beauts floating around.
(you may need to restart the computer)
I also went to  **System Preferences Sound** and set every thing to ALSA.
And right clicked on the speaker icon (top of screen), left click Open volume control and pushed all the slides to the max. Sound is now better than Vista (Shock).


The graphics driver problem (to switch on visual effects extra)
 and to fix a problem with your external monitor not working.
If you go to **System Administration NIVIDA X server settings**, and find your graphics is not switched on try opening a terminal and running
sudo nvidia-xconfig.
If that fails try this 

(From this site)
[http://www.usefuls.net/2008/02/05/3-ways-to-fix-a-bad-ubuntu-screen-resolution.html](http://www.usefuls.net/2008/02/05/3-ways-to-fix-a-bad-ubuntu-screen-resolution.html)

sudo apt-get install xserver-xorg-video-intel

restart the computer,
If that fails you may also need to run
sudo dpkg-reconfigure xserver-xorg
and restart computer.

If you  find (it's likely) that your external monitor is not working (VGA outlet).
Open a terminal and enter
gksudo nvidia-settings
Then click Xserver display setting
click  the “disabled” icon and twin view, then click position clones, apply
then “save X conficuration file”
I was not able to save the config'  file from System Adminstration NVIDIA, hence the “force it”' sudo approach. A matter of Permissions.

When you've done all this you can then got to **System Preferences Visual Effects** and click on extra, which is worth the trouble you will find.

Finally, If you have a Cannon printer In my case a MP210.
From here
[http://ubuntuforums.org/showthread.php?t=872162](http://ubuntuforums.org/showthread.php?t=872162)

thanks to naildeca

IJ Printer Driver Ver. 2.80 for Linux(debian Common package)
and
IJ Printer Driver Ver. 2.80 for Linux(debian Package for the MP210 series)

The download button is a the bottom of the page of "terms and conditions" and license to read. After checking the box saying you have read, etc. A "Download" button appears.

Downloaded both files and save them to the desktop.

The printer should be on connected to the computer. Then the common package should be installed first (double click in the icon and the installer, gdebi, begins)

Then do the same for the MP210 file.

Then you can go to System -> Administration -> Printng and add your printer.

---

