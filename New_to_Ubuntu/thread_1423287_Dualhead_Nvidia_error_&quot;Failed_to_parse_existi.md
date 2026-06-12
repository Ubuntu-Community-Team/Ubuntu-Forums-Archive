---
title: "Dualhead Nvidia error &quot;Failed to parse existing X config file '/etc/X11/xorg.conf'&quot;"
date: 2010-03-06
forum: New to Ubuntu
---

### Post by Lucidmez on 2010-03-06
This is my solution to the problem "Failed to parse existing X config file '/etc/X11/xorg.conf'" that I wanted to share because it took so long for me to find it.

Let me start by saying I am completely new to Ubuntu and Linux so take everything that follows knowing that this is just how it happened to work out for me.  I'll try to explain the reasons why I think it worked out but again I'm new so take it with a grain of salt.

I first installed Ubuntu 9.10 using wubi on my Windows Vista computer so that I could try it out.  I ran into a problem setting it up to allow 2 monitors in the "separate X screen" mode in Nvidia X Server Settings.  I was able to find the answer fairly easy through this forum topic:

[https://help.ubuntu.com/community/NvidiaMultiMonitors](https://help.ubuntu.com/community/NvidiaMultiMonitors)

I later decided to get rid of windows completely on this computer and run a fresh install of Ubunto 9.10 only.

Once again I was faced with correcting the 2 monitor issue only this time the fix I'd used before didn't work.  After days of flipping through the forums and trying several things I more or less stumbled across the solution that worked.  It seems the xorg.conf file is completely missing in Ubuntu 9.10.  My understanding is that you have to create it yourself under certain circumstances, aka-you need it.  I have a Nvidia Geforce FX 5900 and apparently I needed it to run Nvidia X Server Settings.  It seemed no matter what I did, though, I could not create it.  What ended up working for whatever reason was first using the procedure in the following post to create an xorg.conf file:  FYI-thanks to whomever wrote this I couldn't find a name to give credit to...

[http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html](http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html)

**How to create xorg.conf in Ubuntu 9.10                                                                              Monday, 23 November 2009 02:52  **         
 
One of the changes on the new Ubuntu 9.10 is that xorg.conf is missing. The reason for this is that the configuration to be done on user level. The file xorg.conf will be in use only if it exists. Only the time will show if this new concept is good but I personally thing it is.
  
     
 Sometimes you do need to have the xorg.conf though. Mainly when you need to use some hidden options of your graphic device or touchpad for example.
  
 Firstly we need to create the file xorg.conf. Fortunately there is automatic way of doing this with generating xorg.conf with the detected devices from the X.
  
 In order to generate xorg.conf you need to switch to one virtual console using the key combination CTRL + ALT + F1.
 Now execute the following commands:
 user@ubuntu ~# sudo service gdm stop
 This command will stop the X.
 Now we need to generate the xorg.conf file:
 user@ubuntu ~# sudo Xorg -configure
 This has generated the file in ~/xorg.conf.new.
 We need to make the X using it so we have to put this file inside /etc/X11/
 user@ubuntu ~# sudo mv ~/xorg.conf.new /etc/X11/xorg.conf
 After moving this file to the proper location you can start the X again and see what happens:
 user@ubuntu ~# sudo service gdm start

------------
Once I had created the xorg.conf file I tried to open the Nvidia X Server Settings and was given an error that said something like there is no Nvidia X something (run nvidia-xconfig at root).  Sorry, I don't have that error in front of me anymore so I don't know exactly what was said.  At any rate what I did was thinking back to the instructions directly above I did this:

CTRL+ALT+F1

sudo nvidia-xconfig

sudo reboot

I was now able to run Nvidia X Server Settings.  After changing my settings to separate X screen I tried to save and was given the error "Unable to remove old X config backup file '/etc/X11/xorg.conf.backup'.  This is solved by going back to the original helper post I used: [https://help.ubuntu.com/community/NvidiaMultiMonitors](https://help.ubuntu.com/community/NvidiaMultiMonitors) and following the instructions under the "Saving" section where they talk about copy and pasting from the preview.

Once again I'm not going to say this will help everyone but it helped me.  Perhaps I overlooked something that could have saved me some steps but in the end it seemed that I just needed to create an xorg.conf in the first place to make everything else work.

Good Luck!!

---

### Post by talking Llama on 2010-03-09
Just thought I'd say thanks! 
Fixed my problem. Then had to do the save thing it mentions in the other guide. Was annoying having to sort out the setup each time I booted up. Now it works and displays properly on both screens! Thanks again! :D

---

