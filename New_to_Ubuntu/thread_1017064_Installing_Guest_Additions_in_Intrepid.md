---
title: "Installing Guest Additions in Intrepid"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by Orographic on 2008-12-20
Hi all, seasons greetings to you!

I've installed Virtual box OSE 2.0.4 from Add/Remove in Intrepid.

VirtualBox is running fine but I can't install guest additions. When I try it says something like, 'Could not find the VirtualBox Guest Additions image file. Would you like to download this file?'

I click yes and then can only download the VBoxGuestAdditions_2.0.4.iso via the link as the download button times out and wont download. I have the above iso downloaded to my desktop but don't know what to do with it. I try to copy it to the path where VB is looking for it in /usr/lib/virtualbox/ or /usr/lib/virtualbox/additions but I can't copy it there for some reason.

What do I do to get guest additions installed and do I really need it if all is running fine?

Secondly, how do I save this windows XP file I've created, so I can store it offline somewhere, so as to not have to re-activate Windows again. I haven't actually actived it yet but guess I will have to.

Thirdly, should I just install the .deb version from the VB website instead of the OSE version in Add/Remove?

Thanks all. I'm still a Linux newbie but its great stuff to play with!

---

### Post by Kareeser on 2008-12-20
1. You'll have to either mount the CD in Windows (using Daemon Tools, for example), or butn it onto a CD.

From there, open it in Windows, and run the setup file. It's as simple as that :)

2. What Windows XP File? The .vdi Virtual drive?

3. The OSE does not support USB functionality... among several other functions... the full list is on the virtualbox website. Since VirtualBox itself is free for personal use, may as well spring for the good stuff.

I use the OSE myself, and I don't find any problems with it, however.

---

### Post by nhasian on 2008-12-20
the OSE doesnt support USB like the version from the website.  I just created a guide you may find useful here:

[http://ubuntuforums.org/showpost.php?p=6393900&postcount=1](http://ubuntuforums.org/showpost.php?p=6393900&postcount=1)

---

### Post by Orographic on 2008-12-20
Thanks for the reply and that link, excellent stuff, I do appreciate it. I did a re-image of my drive prior to VB OSE install with Acronis and then installed again as per the link above. All good now.

My second question was referring to the virtual machine file (in my case Windows XP). Can I actually save that file to an external drive, so I don't have to re-activate Windows again, if I need to re-install XP in Virtual Box?

How would I do that?

---

