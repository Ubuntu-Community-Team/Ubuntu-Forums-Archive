---
title: "default action on device &quot;mount&quot;"
date: 2011-05-13
forum: New to Ubuntu
---

### Post by wep940 on 2011-05-13
I'm a little curious here, and have searched the /etc/udev/rules.d and the /lib/udev/rules.d rules files but haven't found the answer - I assume it must be somewhere else.

When a device like a hot-plug USB device is "mounted" (don't know if it's happening at mount or post-mount) you are given a default action and allowed to select what you want to do with the device.  If you make a selection such as open folder and make it the default action, where does this information get stored?  Reason:  I was trying something as 1-shot but didn't see the make this action the default checked until my stupid finger just wouldn't stop clicking the mouse button.

Thanks in advance!

---

### Post by wep940 on 2011-05-14
Bump.  For example, my Kindle was coming up asking if I wanted to open it with Banshee, thinking it was an audio device.  I changed it to open in file explorer and selected use as default action.  Afterwards I found I could comment out a rule in one of the udev rules files to stop it thinking it was an audio device, so now by default it opens it in the file explorer anyway. 
 
This got me to thinking - where is this "use as default action" stored so it is rememberd, and how do you reset it (hence why I wondered where it is stored)?

---

### Post by wep940 on 2011-05-16
Bump.

---

### Post by wildmanne39 on 2011-05-16
> **wep940 said:**
> Bump.

Hi, I am sorry it looks like no one know the answer or they would have posted, but if you read the forum rules you are only suppose to post your question once, I wish I knew but I have never used a kindle.

---

### Post by wep940 on 2011-05-16
Thanks for the suggestion on questions, but I already knew that.  These are very distinctly different questions.  The one on the udev rule I have marked as solved.
 
This is a different question than the other - the other was about what the possible ENV variable names are in a udev rule.  This question is about the default action taken when the device is mounted, in particular where ubuntu/linux stores things like "open with file browser" when it has been checked as the default action when the mount first happened.
 
Remember that when you plug in a device such as USB audio device it comes up and gives you a list of options of what to do with the device - such as "Open with Banshee", "Open Folder", etc.?  And in that same box is a "Use as default action" or some such wording?  This is what I'm asking about here.  I didn't want it to keep asking, so I selected Open Folder (or whatever the exact wording is) and checked "use as default action" (or whatever the exact working is).
 
So, yes I solved my Kindle problem via the udev rule - that's the other post.  What I'm wanting to know in this post is where this default action is stored and how you change it.  I searched the udev rules thinking it might have been updated there, but haven't found anything.
 
So, as I've stated, these are 2 very different questions.  Any help on this question would be appreciated.

---

### Post by audiomick on 2011-05-16
If I understood correctly what you are after, I think you are looking in the wrong place. I sounds like something you can set in Nautilus. My screenshot is edit> preferences from Nautilus, and shows tab in which you can specify what happens when specific things are plugged in.

Maybe the thing you are looking for is somewhere in the Nautllus config files.

---

### Post by wep940 on 2011-05-16
I tried what you said and went hunting through the config files for nautilus.  I found one (they seemed to be XML files) labeled as kindle, so I deleted it then rebooted and plugged the kindle in - still went to the file browser opened on the kindle.  So, it looks like the defaults are still hidden from me somewhere.  I think my next thing will be to search on kindle.  If I find nothing there, perhaps I can find somewhere where USB default assignments are made.

Thanks!

---

### Post by compmodder26 on 2011-05-16
I'm not sure where those preferences are stored, but if you are making that preference without being root or having to enter your password to become root, then I can say with 99.999% confidence that the setting is stored somewhere inside your home folder.  So hope that helps you narrow down your search somewhat.

---

### Post by compmodder26 on 2011-05-16
This might point you in the right direction:

[https://help.ubuntu.com/community/Mount/USB#Configuring](https://help.ubuntu.com/community/Mount/USB#Configuring) Program Autostart

---

### Post by wep940 on 2011-05-17
Thanks for the replies - I looked in the nautilus part of gconf-editor (learned something right there!! ;) ) but couldn't find anything that did it.  Automount open looked promising, but it wasn't it.  I am, however, going to go back into gconf-editor and check the other places and see if something shows up.  I'm wondering how it knows a specific device, so I'm hoping I find it.  Probably will be under something that matches the ENV variable from udev - ID_MEDIA_PLAYER, but yet since I commented out the kindle entry there and it still does the default, perhaps it is something by uuid or something like that.

Thanks again!

---

### Post by wep940 on 2011-05-17
I still haven't found any reference in gconf-editor or the udev rules to the kindle either by name or by USB id's, except of course for the 1 rule I commented out.

Still confused, still lost!  Help?  ;)

---

### Post by wep940 on 2011-05-17
I just spent literally alll night trying to go through all the folders and files in /etc, as well as /lib/udev/rules.d.  I have not found anything.  I don't know if this has something to do with Device Actions, but what I found on the net that referenced Device Actions didn't appear to be present in Ubuntu.  I have to believe this is being stored somewhere by device (that is, a device "exception" to the norm) since it would appear to either be doing this by device name or in this case by USB id.  I cannot find it, and I'd really like to know how this works, where it is stored and how to set/reset it.

I'm giving up for now with the hope SOMEONE with a LOT of knowledge of Ubuntu will eventually see this and provide the answer.

---

### Post by wep940 on 2011-05-18
An extremely shameless bump.  If one of the moderators or someone "in the know" can provide me with an answer it would be appreciated.
 
Thanks in advance for your time!

---

### Post by DHavener on 2011-09-09
Not sure if you're still tracking this thread.  This might help (not sure if you've got a specific action for your Kindle, or if the OS is just seeing as class "Removable Media"):

Open a File Browser
Edit -> Preferences -> Media Tab

There's lots of settings for different media here, but at the bottom uncheck:

[] Browse media when inserted

This will disable popping up a file browser when media is detected/mounted

Cheers

---

### Post by anewguy on 2011-09-12
Hi, and thanks for the response.  I'm back to using my regular id now of anewguy, so that's why the reply is from a different userid.

I appreciate your reply, and indeed this is what I figured out after my last post.  The udev rule obviously sets the device type, and the preferences say what to do with a device type by default.  Sorry I never posted back that solution, and thank you for posting it here to remind me I needed to finish up this thread.

Thanks again!
Dave ;)

---

