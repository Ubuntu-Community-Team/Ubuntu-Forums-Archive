---
title: "IMWHEEL help and Mouse button help"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by adventure man on 2009-05-26
Hi guys I have a Microsoft Comfort Optical Mouse 3000.  It has a side button that I have always used for "back" in firefox.  It doesn't seem to work in my ubuntu 8.04.2.  I have installed the program "IMWHEEL", unfortunately I can't find it in my applications:confused:

I then hit this thread up and did all that was told, but it didn't work.
 
[http://ubuntuforums.org/showthread.php?t=252467&highlight=Microsoft+Comfort+Optical+Mouse+3000](http://ubuntuforums.org/showthread.php?t=252467&highlight=Microsoft+Comfort+Optical+Mouse+3000)

So three questions, 1. how do i start IMWHEEL?  2. Why is that config file stuff not doing anything for me? 3. How do i make the scroll wheel scroll faster/slower?

my laptop specs:
Ibuypower.com
amd 3400+
ati 9700 mobile
2 gig crucial ddr400
ubuntu 8.04.2
hitachi hard drive 7200rpm 60gb
unknown mobo :confused:

---

### Post by Didius Falco on 2009-05-26
> **adventure man said:**
> Hi guys I have a Microsoft Comfort Optical Mouse 3000.  It has a side button that I have always used for "back" in firefox.  It doesn't seem to work in my ubuntu 8.04.2.  I have installed the program "IMWHEEL", unfortunately I can't find it in my applications:confused:

I then hit this thread up and did all that was told, but it didn't work.
 
[http://ubuntuforums.org/showthread.php?t=252467&highlight=Microsoft+Comfort+Optical+Mouse+3000](http://ubuntuforums.org/showthread.php?t=252467&highlight=Microsoft+Comfort+Optical+Mouse+3000)

So three questions, 1. how do i start IMWHEEL?  2. Why is that config file stuff not doing anything for me? 3. How do i make the scroll wheel scroll faster/slower?

my laptop specs:
Ibuypower.com
amd 3400+
ati 9700 mobile
2 gig crucial ddr400
ubuntu 8.04.2
hitachi hard drive 7200rpm 60gb
unknown mobo :confused:

I can help with #1:

Open a Terminal shell and type ```
man imwheel
``` for the manual pages, then type ```
imwheel -c
``` and it will open the gui.

This web page may be helpful as well:

[http://imwheel.sourceforge.net/imwheel.1.html#lbAE](http://imwheel.sourceforge.net/imwheel.1.html#lbAE)

Regards,

Didius

---

### Post by adventure man on 2009-05-26
> **Didius Falco said:**
> I can help with #1:

Open a Terminal shell and type ```
man imwheel
``` for the manual pages, then type ```
imwheel -c
``` and it will open the gui.

This web page may be helpful as well:

[http://imwheel.sourceforge.net/imwheel.1.html#lbAE](http://imwheel.sourceforge.net/imwheel.1.html#lbAE)

Regards,

Didius
thanks didius, I open imwheel configuration helper and hit "grab wheel action" for my side button. It says "Wheel: Left (Button 6)"

any idea how I use this information to configure my side button to work as "back" in firefox?

---

### Post by Didius Falco on 2009-05-26
Sorry, I use a three button (two buttons and a wheel that doubles as a button) mouse. I'm driving a Pinto and you have a Ferrari. <G> 

I think I may have stumbled across a better app for you to use, though. Go to Synaptic and have a look at **btnx** and its companion **btnx-config** gui. It's in the repo for Karmic, so it should definitely be available for you.

Here is a thread about it that includes a link to the home page and the manual, plus it says it has a manual built into the gui:

[http://ubuntuforums.org/showthread.php?t=455656](http://ubuntuforums.org/showthread.php?t=455656)

I hope this helps...

Regards,

Didius

---

### Post by adventure man on 2009-05-26
hmm strange, couldn't find btnx in synaptic package manager.  Looks like a good program though, any deb around i can download?:D

---

### Post by Didius Falco on 2009-05-26
I went to the btnx website and it is now recommending an app called **easystroke**. Again, I'm finding it in Synaptic, but if it doesn't show up in yours, here is the website:

[http://sourceforge.net/projects/easystroke/](http://sourceforge.net/projects/easystroke/)

Here is the download page:

[http://sourceforge.net/project/showfiles.php?group_id=229797&package_id=278455&release_id=682157](http://sourceforge.net/project/showfiles.php?group_id=229797&package_id=278455&release_id=682157)

If you use the web page to download  the deb file, make sure you get the version that matches your install.

Regards,

Didius

---

### Post by adventure man on 2009-05-27
> **Didius Falco said:**
> I went to the btnx website and it is now recommending an app called **easystroke**. Again, I'm finding it in Synaptic, but if it doesn't show up in yours, here is the website:

[http://sourceforge.net/projects/easystroke/](http://sourceforge.net/projects/easystroke/)

Here is the download page:

[http://sourceforge.net/project/showfiles.php?group_id=229797&package_id=278455&release_id=682157](http://sourceforge.net/project/showfiles.php?group_id=229797&package_id=278455&release_id=682157)

If you use the web page to download  the deb file, make sure you get the version that matches your install.

Regards,

Didius

I couldn't find it in synaptic.  But i did download the deb.  It solved my issue with the scrolling :D  BUT  my side button of my mouse aka "button 6" apparently isn't being detected by this program. :(

perhaps i need to upgrade to Jaunty :confused:

Windows has that little area in Control Panel where you can adjust most anything for "most" mice.  Is it that complex to do that for Ubuntu?  I mean I'm completely clueless on programming, but the mouse properties in System Prefences in Ubuntu 8 just seems lacking :(

It's hard to complain though, with a few very very minor flaws, Ubuntu still blows me away, I can't stop raving about it to friends. :D

---

