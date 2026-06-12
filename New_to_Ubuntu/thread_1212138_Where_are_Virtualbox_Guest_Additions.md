---
title: "Where are Virtualbox Guest Additions"
date: 2009-07-13
forum: New to Ubuntu
---

### Post by mystmaiden on 2009-07-13
I had posted this on the end of another virtualbox thread but it was a bit off the original topic so I'll try here.

I just plain can not find the guest additions. In their help file it sounds like it is in a file downloaded when you download the program. I looked in .Virtualbox and found nothing. I've searched high and low online and no luck at all.  I'm running Ubuntu 8.04 and Virtualbox 3.0 

Anyone know where the guest additions are hiding? I think there is a little fiddling to do to get them working with 8.04 but I haven't gotten that far yet.


myst

---

### Post by adzik on 2009-07-13
Do you mean where they are located in the guest machine or host?

---

### Post by philinux on 2009-07-13
[http://ubuntu-tutorials.com/2007/10/13/installing-guest-additions-for-ubuntu-guests-in-virtualbox/](http://ubuntu-tutorials.com/2007/10/13/installing-guest-additions-for-ubuntu-guests-in-virtualbox/)

---

### Post by mystmaiden on 2009-07-13
Thanks philinux,  this seems to be a little clearer tutorial than the one I was using, unfortunately, nothing happens when I click on devices/install guest additions. I waited ten minutes the last time to be sure I was not rushing it.

Most the reading I've done seems to indicate there was some fiddling to be done with getting guest additions to work with Hardy but - I really did not understand some of it because I couldn't get past this point to see what happens next.

Maybe there is a work around for this part?

myst

---

### Post by tacantara on 2009-07-13
Have you tried mounting the Guest Additions "cd-rom" through the terminal?  Normally, you can click the device in Virtual Box and it will install, but apparently that's where your troubles lie.  I found this terminal command through a Google search.  The info is from tombuntu.com, and was written for your version of Ubuntu, but an earlier version of VirtualBox.  I hope this helps some.

sudo /media/cdrom/VBoxLinuxAdditions-x86.run

---

### Post by philinux on 2009-07-13
> **mystmaiden said:**
> Thanks philinux,  this seems to be a little clearer tutorial than the one I was using, unfortunately, nothing happens when I click on devices/install guest additions. I waited ten minutes the last time to be sure I was not rushing it.

Most the reading I've done seems to indicate there was some fiddling to be done with getting guest additions to work with Hardy but - I really did not understand some of it because I couldn't get past this point to see what happens next.

Maybe there is a work around for this part?

myst

I got it going here. Machine>Settings>CD/DVD

---

### Post by mystmaiden on 2009-07-13
Again thanks philinux, I'm making progress over here thanks to you. I found it in the cd/rom, selected that. I'm sketchy now on what step is next though - what seems to be happening is that I don't see any of the prompts that were shown in the tutorial. 

The terminal commands are to be typed in the virtual box somehow? Or in the regular terminal in Ubuntu? When I finally got a terminal window to come up in the guest os. I chose run in terminal and typed 

cd/ media/cdrom 

and got: Could not open location 'file:///home/mystmaiden/cd%20/media/cdrom'
location or file can not be found

---

### Post by philinux on 2009-07-13
> **mystmaiden said:**
> Again thanks philinux, I'm making progress over here thanks to you. I found it in the cd/rom, selected that. I'm sketchy now on what step is next though - what seems to be happening is that I don't see any of the prompts that were shown in the tutorial. 

The terminal commands are to be typed in the virtual box somehow? Or in the regular terminal in Ubuntu?

Should not need any terminal commands I didn't. If your machine state looks like this then it's good to go. As you can see the additions are loaded ready to roll.

---

### Post by mystmaiden on 2009-07-13
Nice, cause that's what it looks like now. I really appreciate you taking the time to do all this to help me. 

myst

edited to add: This may be where we run into the issues I read about with Ubuntu 8.04 because I've restarted the virtual machine and its still looks and acts exactly as it did before, seamless mode greyed out etc. I will see if I can find the articles that spoke of editing the xorg file and post the link.

Edited again to add: Haven't found the articles that mention having to edit a xorg file but this article show the install screens and all that - 

 [html]http://seogadget.co.uk/how-to-install-virtualbox-guest-additions/
[/html]But none of that happens after I select the iso in the cd/rom drive   No prompts come up, nor do any of the install screens. It doesn't do anything at all. And ...

[code]mystmaiden@hal:~$ sudo /media/cdrom/VBoxLinuxAdditions-x86.run
sudo: /media/cdrom/VBoxLinuxAdditions-x86.run: command not found [code]

---

### Post by philinux on 2009-07-13
Hope you got it sorted. ;)

---

### Post by mystmaiden on 2009-07-13
Thanks, philinux :)  Unfortunately I haven't. I am baffled but I decided to let it sit and try it again tomorrow. 
 
If anyone else has ideas - I'd love to hear 'em
 
myst

---

### Post by philinux on 2009-07-14
The guest-additions are installed to the guest, not the host.

Start your virtual machine. Then choose Devices. At the bottom of the dropdown box is "Install guest additions".

Hope this helps.

---

### Post by mystmaiden on 2009-07-14
Thanks, yeah I've done that, and it never brings up the install screen. When I did it according to the help contents in VB (clicking add) on the mount screen I got a error saying that it could not register the iso because it already existed in the media registry home\ mystmaiden\.VirtualBox\VirtualBox.xml

It looks like its installed but nothing happens to change Vbox at all, still no seamless mode and the screen is tiny. I can use 'full screen' mode but it doesn't actually change the size of the working screen just makes the border around it bigger


myst

---

### Post by cjv8888 on 2009-07-14
What guest OS are you running? because not all OS is supported by guest additions.


[http://www.virtualbox.org/manual/UserManual.html#id2495055]("http://www.virtualbox.org/manual/UserManual.html#id2495055")

---

### Post by lkraemer on 2009-07-14
Try going into the setup screen for the CDROM drive and setting the
Guest additions as not selected, then try the install of the Guest
Additions.

I've included a png of what should be selected before you try the
Guest Additions install.

Hopefully, that will make it install.

lkraemer

---

### Post by moma on 2009-07-14
Hello,

See also these notes.
[http://www.futuredesktop.org/virtualization-solutions-ubuntu-9.04.html](http://www.futuredesktop.org/virtualization-solutions-ubuntu-9.04.html)
There is special picture that shows how to install Guest Additions in Ubuntu.
Last [picture]("http://www.futuredesktop.org/jaunty/images/virtualbox-guestadd-6b.png") in **"C10-4) Install the Guest Additions."**

---

### Post by mystmaiden on 2009-07-14
At last I've found the trouble. Seems I was missing the virtual box utilities, installed them through synaptic and then opened the guest os, clicked install guest additions and it worked like a charm.

Many thanks to everyone.
mystmaiden

---

### Post by philinux on 2009-07-14
> **mystmaiden said:**
> At last I've found the trouble. Seems I was missing the virtual box utilities, installed them through synaptic and then opened the guest os, clicked install guest additions and it worked like a charm.

Many thanks to everyone.
mystmaiden

Glad you're sorted. Strange though as I haven't got the utilities package installed. :confused:

---

### Post by mystmaiden on 2009-07-14
philinux wrote:

Glad you're sorted. Strange though as I haven't got the utilities package installed

That is weird, are you running Jaunty or Hardy? I don't know why it worked for me but I'm glad it did! Makes me crazy when I can't get stuff to behave.  :)

---

### Post by philinux on 2009-07-14
> **mystmaiden said:**
> philinux wrote:

Glad you're sorted. Strange though as I haven't got the utilities package installed

That is weird, are you running Jaunty or Hardy? I don't know why it worked for me but I'm glad it did! Makes me crazy when I can't get stuff to behave.  :)

Jaunty kiddo. Always testing the latest. Got karmic koala on disk 2 :lolflag:

---

