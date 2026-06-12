---
title: "Flash problem with specific website."
date: 2009-03-05
forum: New to Ubuntu
---

### Post by CRIMPS on 2009-03-05
So, I have now been able to share Ubuntu with my mother, sister, and grandmother because their computers were getting to be outdated for windows.  All three have differing levels of computer experience and everything, so far, has been quite carefree.  

I have one little problem that I believe to be a flash problem on a specific website.  My mother is a huge fan of Alan Jackson.  So, she frequents his [website]("http://www.alanjackson.com") from time to time.  

The website, since she has switched to ubuntu, seems to load successfully, but then seems to display this huge gray field over the top of the toolbar.  I can get a screenshot later if needed.

I have a theory that I was going to try for a resolution but I thought I would run this by the community first.  I use this [guide]("http://www.futuredesktop.org/") when installing Ubuntu and other goodies.  Take a look at step 7c.  Anyone think this should fix the problem?

Thanks for the help

---

### Post by Grifulkin on 2009-03-05
> **CRIMPS said:**
> So, I have now been able to share Ubuntu with my mother, sister, and grandmother because their computers were getting to be outdated for windows.  All three have differing levels of computer experience and everything, so far, has been quite carefree.  

I have one little problem that I believe to be a flash problem on a specific website.  My mother is a huge fan of Alan Jackson.  So, she frequents his [website]("http://www.alanjackson.com") from time to time.  

The website, since she has switched to ubuntu, seems to load successfully, but then seems to display this huge gray field over the top of the toolbar.  I can get a screenshot later if needed.

I have a theory that I was going to try for a resolution but I thought I would run this by the community first.  I use this [guide]("http://www.futuredesktop.org/") when installing Ubuntu and other goodies.  Take a look at step 7c.  Anyone think this should fix the problem?

Thanks for the help

I am assuming you aren't running 64 bit correct?  Also for firefox all you should need to do if you are running 32 bit is just download the deb file from adobe and install, but if you have already done that and that one site just doesn't work that is out of my league as far as ubuntu goes.

---

### Post by pytheas22 on 2009-03-05
The site works for me, although I only visited it for a few seconds--could you provide a screenshot to give us a more precise idea of what you're seeing?  Also, when the gray bar appears, do other flash sites continue to work--for example, can you use Youtube?  Or do they all stop working until you restart Firefox?

What I suspect may be happening is that npviewer.bin is crashing, which is often what causes flash to display.  But that only happens on 64-bit systems.  Is this 64-bit?

It may also be helpful to run Firefox from the terminal, and see if it dumps any relevant output when the flash crashes.  If you see anything that looks relevant, please post it here (or google it to see if any bug reports turn up).

---

### Post by jlochhead on 2009-03-05
Is the system is 64 bit you are better off upgrading to the new native 64 bit of the flash player, which is now in alpha.

---

### Post by CRIMPS on 2009-03-05
The system is a 32bit version of Ubuntu 8.04.  Below, you will see a screenshot of the site.  Its seems like the site completely loads as I can see the home page, then this gray background image comes forward.

I did try loading firefox from the terminal, but nothing was returned. 

Maybe I am wrong, maybe this isn't a flash problem at all.  Or, maybe I need to try reinstalling flash as I can now reproduce this on at least two clean installs of ubuntu 8.04 32bit when I have used that guide.  Maybe I shouldn't use that guide to install Flash.

---

### Post by pytheas22 on 2009-03-05
That's a bit strange.  Normally when flash crashes, you get a plain gray box, but in your case it's a gray box with a design that looks like the normal background for Alan Jackson's site.  This makes me think that the flash isn't actually crashing; it's just not displaying correctly (it looks like it's putting the background image on top of everything else for some reason).  Can you still use Youtube in the same instance of Firefox when this happens?

Also, which flash plugin did you install?  There are three, but the most reliable is Adobe's proprietary plugin, which is called flashplugin-nonfree or Shockwave.  If you go to Tools>Add-ons>Plugins in Firefox, it should say which flash plugin is being used.

---

### Post by CRIMPS on 2009-03-06
Ok, I found that I did have the latest "FlashPlugin - nonfree" installed (version 9.0.159).  However, I tried uninstalling flash altogether.  Then, from adobe's website, I downloaded and installed Flash player 10.  I installed this and rebooted.  When I browse to that specific [website]("http://www.alanjackson.com") I am prompted to install the Flashplayer plugin version 9 again.  So, flash 10 isn't even recognized.  Actually, the latest version of the plugin is 9 and the full version of flash is 10?

Again, this is a pretty fresh install.  I am trying to figure out what conflict I am running into.

---

### Post by kansasnoob on 2009-03-06
Start here:

[http://ubuntuforums.org/showthread.php?t=1088786&page=2](http://ubuntuforums.org/showthread.php?t=1088786&page=2)

But regarding the Flash 9.xx thing you DO want Flash 10. Download it here:

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

Select the .deb for 8.04+ ........... unless you're running an older version of Ubuntu! If you're running anything older than 8.04 it's time to upgrade!

---

### Post by CRIMPS on 2009-03-13
Ok, I found that searching through Synaptic for "flash" I found that there were two different versions of the Flash plugin installed.  For instance, Adobe-flashplugin version 10.xx was installed as well as Flashplugin-nonfree version 9.xx was installed as well.  I completely removed the nonfree plugin.  I then had to reinstall Adobe Flash 10.22.  This seemed to do the trick.

So, I think that there was an issue with the original installation of Flash that I used from my original post.

Thanks to everyone. :)

---

