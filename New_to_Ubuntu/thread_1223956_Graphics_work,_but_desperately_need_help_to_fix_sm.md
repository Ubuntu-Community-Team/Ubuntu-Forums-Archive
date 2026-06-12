---
title: "Graphics work, but desperately need help to fix small annoying problems!!"
date: 2009-07-26
forum: New to Ubuntu
---

### Post by MarkTX on 2009-07-26
Can anyone help?

I have the system up and running.  The display works, but there are certain times that it just doesn't work.  I've tried searching through the posts for the various answers but haven't found anything that truly helps.

Here are a list of the problems;

1. Webcam works for a short time, if at all.  Not reliable at all. Its a Creative Labs PD1120. I think this is a driver problem.

2. When running Celestia (OpenGL i believe) i get random video results, none of which allow me to use the program.

3. Cannot seem to get any version of Flash Plugin that 'works' for me.  This might be because of the above openGL problem with a driver perhaps?

Those are the main ones i can think of, i'd really appreciate if someone could 'sit down' and help me through fixing it!! And yes, i've searched and tried quite a few posts/fixes on the forum.


Thanks in advance guys, your knowledge is a blessing!!

---

### Post by llamabr on 2009-07-26
You say it's a driver problem.  Why do you believe that?

And how did you install flash?

---

### Post by MarkTX on 2009-07-27
Well, i guess i think its a driver problem because i still think that anything i 'add' to my computer, such as this USB webcam, requires a driver to use.

I'm still very new to this whole Linux thing, so please ignore any ignorance i show :)

I originally installed flash from the Synaptic program, but after having problems with it working i searched a few posts on this forum and found a link to a repository of all the various flash versions.  I removed the flash i had already on the system and then installed a different version as recommended by that post (sorry, i can't find that post!)

Same results.

---

### Post by Moop on 2009-07-27
Go to System-Preferences-Appearance and click on the visual effects tab. Check the box for "none" and close, then try celestia and see if it works any better. 

You can have problems with flash if you have different versions installed. Go to synaptic and search for flash to see what's installed. If you have gnash or swdec installed, un-install them.

---

### Post by Mark Phelps on 2009-07-28
Are you running Ubuntu 9.04? If so, you're likely to have some real performance problems running Celestia because there are no ATI restricted 3D video drivers for your video chipset that work in Ubuntu 9.04.

---

### Post by MarkTX on 2009-07-28
Thanks Moop, removing SWDEC allowed flash to work much better!

Mark Phelps, do you think its probably wise for me to 'downgrade' my ubuntu to a more, encompassing version?  If so, how hard is it to do?

Thanks for the help guys, keep it coming.  I still need some help getting the Creative Labs pd1120 webcam to work properly too!

---

### Post by Mark Phelps on 2009-07-30
> **MarkTX said:**
> Mark Phelps, do you think its probably wise for me to 'downgrade' my ubuntu to a more, encompassing version?  If so, how hard is it to do?

Yes ... except that there is no straightforward way to "downgrade" from one Ubuntu version to another.  A reinstall is generally required.

Plus, it's not that 9.04 is a "less ecompassing" version than 8.10, it's just that the Xserver version in 9.04 is incompatible with ATI Catalyst versions prior to 9.4 -- which includes a host of "legacy" cards/chips no longer supported by newer driver versions. So, it's really an AMD/ATI driver "cutoff" problem.

---

