---
title: "Cannot run (x)ubuntu LiveCD."
date: 2009-01-15
forum: New to Ubuntu
---

### Post by Gavros on 2009-01-15
N.B.: Sorry if this doesn't belong in Absolute Beginner Talk, I wasn't quite sure where to put it.

I've been trying to install Ubuntu and Xubuntu on my laptop, but the liveCD just loads and then ends in a black screen with a command line. I've burned two different instances of Ubuntu, one at 8x and another at 1x burn speed, ditto with Xubuntu, and the same thing seems to happen each time. I've tried using safe graphics mode, it just ends the same way. The furthest I got was seeing a cursor in the middle-right of my screen, not moving, and no background (this was the 1x burnt Xubuntu in Safe Graphics mode.)

My laptop's specs:
1.73 GHz Intel Celeron processor
1 GB of RAM
64mb Graphics card

It's not the best laptop ever, but why on earth can't I even run a liveCD of it? I downloaded Xubuntu because I read it needed lower system requirements, but my system's requirements very much surpass what's required and it didn't make the slightest bit of difference.

Can anyone help?
Thanks

-Gav

---

### Post by albinootje on 2009-01-15
> **Gavros said:**
> The furthest I got was seeing a cursor in the middle-right of my screen, not moving, and no background (this was the 1x burnt Xubuntu in Safe Graphics mode.)

What's the laptop brand and type ?
And which graphics card do you have exactly (brand and type) ?

Safe graphics mode should almost always work. If not, then you might need some boot parameters to pass on.

See here for options :
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by mjheagle8 on 2009-01-15
did you get any error messages to indicate that there may be something wrong during the boot?

---

### Post by Gavros on 2009-01-15
VIA Chrome9 HC IGP, and my Laptop's brand is MaxData. It's an intergrated graphics card, yeah, but does that make a difference? I thought Ubuntu was low-spec.

And, no. No error messages whatsoever.

---

### Post by mjheagle8 on 2009-01-15
ubuntu is lo spec. espescially xubuntu, because it runs the lightweight xfce desktop environment.  look at the link albinootje posted. read that article, boot in text only mode. safe graphics.  watch to make sure everything loads ok and nothing says fail during the boot.

---

### Post by Gavros on 2009-01-15
Sorry, but I can't find text-only on that boot list. Can you tell me which one it is?

---

### Post by albinootje on 2009-01-15
> **Gavros said:**
> VIA Chrome9 HC IGP, and my Laptop's brand is MaxData. It's an intergrated graphics card, yeah, but does that make a difference? I thought Ubuntu was low-spec.

And, no. No error messages whatsoever.

VIA Chrome.. that explains things.
I'm sorry to tell you that I've seen serious problems with VIA Chrome video cards and Linux.

You can do an installation from the alternate installation cdrom, and then configure your graphics configuration later.

Here's a link to the alternate cdrom image for 8.04.1 :
[http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-alternate-i386.iso](http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-alternate-i386.iso)

The alternate installation cdrom is a text based installation cdrom, which can be used to do an Ubuntu installation in cases where a graphical installation is not possible.

After the installation go for the "vesa" video driver when you're gonna reconfigure the graphical environment.

---

### Post by Gavros on 2009-01-15
Oh, fantastic. Just my luck, eh?

If it's a text-based installation, does that mean it'll install a text-based Ubuntu? I can't understand all this boot text stuff. Sorry if I'm acting like a complete newb, but I don't have the slightest amount of knowledge except the fact I'd like Ubuntu on my laptop.

---

### Post by mjheagle8 on 2009-01-15
its ok, we're glad to help you however. you will be able to run video, but it will require some configuration. there will be guides to help you through it. you will have to do a text based INSTALLATION, but after it is installed, as albinajoote described, you will be able to get video up and running using vesa, which is a video driver that will work with your hardware.

---

### Post by halitech on 2009-01-15
only the instal is text based, it will install a gui as well and hopefully the video will work properly for you.

---

### Post by albinootje on 2009-01-15
> **Gavros said:**
> Oh, fantastic. Just my luck, eh?

Sorry about that :(
For a colleague I've ended up using the "vesa" driver with a VIA Chrome card.
It's a little slower, and you have no hardware acceleration with that driver.
> 
If it's a text-based installation, does that mean it'll install a text-based Ubuntu? I can't understand all this boot text stuff. 

The alternate installation cdrom will give you the full desktop installation (it's not a server install).

See also here for more info :
[http://ubuntuforums.org/showthread.php?t=639464](http://ubuntuforums.org/showthread.php?t=639464)
[https://answers.launchpad.net/ubuntu/+question/11807](https://answers.launchpad.net/ubuntu/+question/11807)

Good news is that the company VIA is slowly getting more updated video card drivers out for Linux themselves (but that's my quick impression, I didn't have luck with their drivers, and their websites are a little messy imho).

---

### Post by Gavros on 2009-01-15
I've just had a thought
If there aren't any Linux drivers for my "RT73 USB Wireless Lan Card", there's no point in me even starting. Do you know anything about this?

---

### Post by mjheagle8 on 2009-01-15
try searching on google to see if anyone else has found drivers for it in linux.

---

### Post by albinootje on 2009-01-15
> **Gavros said:**
> I've just had a thought
If there aren't any Linux drivers for my "RT73 USB Wireless Lan Card", there's no point in me even starting. Do you know anything about this?

Should work it looks like. 
Here is really old documentation for it :
[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73)

It's possible that it will work with less hassle than described there.

---

