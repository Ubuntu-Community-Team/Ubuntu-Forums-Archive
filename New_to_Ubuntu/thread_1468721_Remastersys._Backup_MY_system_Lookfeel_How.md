---
title: "Remastersys. Backup MY system Look/feel How??"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by Fenris_rising on 2010-05-01
Hi Chaps

I need a little guidance, please, with the use of remastersys. I have read various threads and other on line documentation and have a basic grasp of it. I have used it before but my Ubuntu installation was fairly basic and had only a minimal personal footprint on it.

Now what I wish to do is, with my Ubuntu setup visually tweaked to my taste and programs added removed to suit my use, create a backup/live DVD of my setup as is that when I install from it gives me exactly what I had.

I understand that the Proprietary driver for my Nvidia card will not be a part of the ISO that is created and will need installing post a re-install.

Everything in red I have tried and got the answers to. Skip to the bottom for my final query's

[COLOR="Red"]So to the main bit. My main tweaks are -

Awn installed and configured
Compiz installed and configured
Firefox with add-ons. For Persona add-on I have 2 images in a folder in my
/home/fenris folder

My own background images are in the usr/share/backgrounds folder

For play back of video files, audio, DVD's the medibuntu repo's were added to facilitate using the media mentioned. Restricted extra's were also installed.

If I understand correctly - For Awn and Compiz the '.config' Folder is all that is needed and for Firefox I need the '.mozilla' Folder and move them to etc/skel?

I presume that if this is correct compiz will only function on a re-install once the GPU drivers are reinstalled?

Will the persona folder with images and my images in the backgrounds folder be saved to the backup?

Are the restricted extra's saved to the backup image or do I need to do something with them?

Of particular interest is my fstab and xorg.conf files. Will these be saved to the backup. I have a second internal drive which I had to add by hand to the fstab so if it doesn't save I need to put it somewhere where it will save on the backup so I can access it and put it in place to get my second drive back up with minimal fuss.

The xorg.conf file. Because the proprietary driver for the GPU are not saved and have to be installed post re-install is the xorg file lost saved or in danger of being buggered up during the process. Should I save a copy of it in a folder that will be saved to backup so I can, again, just put it back in place post re-install?

Is there anything else I should be aware of to make the backup disk a successful item. I know of the ISO size limit.
[/COLOR]
EDIT: I bit the bullet and used my last DVD to try out the theory. It works and as a live cd installing the nvidia drivers worked.

BUT: The compiz settings were all cleared. Is there a way of keeping the settings I set??
That is the only thing I need to know now seeing as I got everything else sorted.

Found this thread. would copying the compiz folder to the /etc/skel folder do the trick?

[http://ubuntuforums.org/showpost.php?p=4394694&postcount=5](http://ubuntuforums.org/showpost.php?p=4394694&postcount=5)

No worry's got the answer. You can export the settings under the preferences heading in compiz itself. So my plan is to have a folder in the /home folder that contains my fstab, xorg and compiz files.

Funny I couldn't find the answer until after I asked =D

All help appreciated

regards

Fenris

---

