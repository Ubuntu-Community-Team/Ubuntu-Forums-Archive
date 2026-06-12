---
title: "Help me fix flash."
date: 2010-03-25
forum: New to Ubuntu
---

### Post by Vannak on 2010-03-25
So I need flash help. I've been trying to install flash for firefox for several days now, and can't get it to work. I've gone through synaptic, compltely removed anything even looking like it had to do with flash, reinstalled it. I've tried at least a dozen scripts, guides, and work arounds and only one of them worked, and that was a solution hosted here that involved downloading a script, get64bitflash. It worked right out of the box, installed like a charm but for some reason as soon as I closed firefox, and booted it back up, no flash, and the script isn't working any more. I'm at my wit's end, and I have no idea what I should do. I've uninstalled and completely removed all of the following

Ubuntu Restricted Extras
Flashplugin-installer
Flashplugin-nonfree

and I've gone through both /.mozilla/plugins/ and /usr/lib/Mozilla and every directory and deleted every preference file available to me, every fresh install works perfectly (as in, no error messages or freakouts of any kind) but simply does not translate into my firefox browser getting flash. Flash neither shows up under "About : plugins" or the Tools>Add ons>Plugins inside of firefox. This is simply driving me mad and I would just like to be able to get this working. 

I'm running an AMD64 Ubuntu 9.10 Karmic with firefox 64bit 3.5.8

---

### Post by andrewthomas on 2010-03-25
Download from here.

[http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)

Once downloaded, simply open the Tar archive, look for a file named  "libflashplayer.so", copy that file to your desktop, then both 32-bit  and 64-bit users execute the following command in the terminal:

**sudo mkdir /usr/lib/flashplugin-nonfree && sudo cp -f  ~/Desktop/libflashplayer.so /usr/lib/flashplugin-nonfree/ &&  sudo ln -sf /usr/lib/flashplugin-nonfree/libflashplayer.so  /etc/alternatives/firefox-flashplugin && sudo ln -sf  /etc/alternatives/firefox-flashplugin  /usr/lib/firefox-addons/plugins/flashplayer-alternative.so**

---

### Post by Vannak on 2010-03-25
Thank you. Working well so far.

---

### Post by andrewthomas on 2010-03-25
You're welcome.
If you have any other multimedia problems I would suggest you read the [B]Comprehensive Multimedia & Video Howto.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

[/B]

---

### Post by Vannak on 2010-03-26
Stopped working. Every time I restart my computer, flash becomes broken again. I have no idea why, this is baffling. I go to youtube to test, and the entire area where the player would be is filled in back. Refreshing doesn't work, and no other flash apps load. I don't even get the, "Please install flash blah blah blah" message any more.

---

### Post by no2498 on 2010-03-26
get opera some thing is changing in flash fire fox dont like
[http://www.opera.com/](http://www.opera.com/)

hope this helps

---

### Post by QIII on 2010-03-26
First, go to Synaptic and remove swfdec and gnash if they exist.

Next, open Firefox and type "about: plugins" (remove the space.  The dang smily face comes up if I type it without the space) in the navigation bar.  See if there is anything about Flash in there.

Then, take a look at Carlee's posts here:

[http://ubuntuforums.org/showthread.php?t=1414595&highlight=carlee](http://ubuntuforums.org/showthread.php?t=1414595&highlight=carlee)

Read down through, because I think she has made some changes.

See if that helps.

Also look at lovinglinux guide here:

[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by Vannak on 2010-03-27
QIII: It doesn't work. Her script only effected my system in that now I can't launch symantic due to another software manager running. Might not have been that script, but a restart didn't fix it, and now I'm worse off than before. 

I'm really confused. About: Plugins lists no instance of flash, but tools>addons does. I do not get "Please install the latest version of flash" error messages, and I can't even uninstall any flash packages I have now.

---

### Post by Gixxy on 2010-03-27
Maybe this will help...

[http://ubuntuforums.org/showthread.php?t=733078]("http://ubuntuforums.org/showthread.php?t=733078")

then reinstall

---

### Post by QIII on 2010-03-27
When you are trying to use Synaptic, do you have the terminal open for any reason?

Were you logged in as root, or were you ever running from the root prompt?

We need to the bottom of that.  I would be very, very surprised that Carlee's process affected Synaptic directly in such a fashion.

Would you please add a post to that thread and let her know what is up so she can take a look.  I don't know if she takes private messages, but you might let her know your post is there.  I doubt she will help you work through the problem in a private message exchange, because that would not be helpful to the rest of the community.  Just tell her it's there and ask if she could take a look at it and respond in the thread.

---

