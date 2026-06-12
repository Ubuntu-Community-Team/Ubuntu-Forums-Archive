---
title: "iPod touch 4 not supporting mp3s"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by lilredcougar07 on 2010-10-11
Hey friends,

So, I just got my iPod touch yesterday, 32GB from Walmart. I was told that Banshee supports it. I plugged it in, computer recognized it as a camera, which I understand. Pulled up Banshee, it had it as Apple iPod. Awesome. Tried to add music, error. The specific error says:

The mp3 format is not supported by the device, and no converter was found to convert it

The mp3 that I used is just a regular mp3, so I have no idea why it wouldn't work. I also tried to use Rhythmbox and it didn't recognize it at all. Is there anything I can do or should I just take it back? I added some music from my friend's Windows computer after searching the internet for some sort of solution and it worked just fine. I don't know what to do and everything that I've looked at so far has just been saying it should work right out of the box. Help please!

---

### Post by robsoles on 2010-10-11
Hi. I killed the one and only Apple device I ever allowed into my life  and I haven't tried banshee before but I think maybe connecting as a camera  will do for now...

When the OS detects your ipod as a camera, does it show it as having  storage? If so then can you just copy mp3 files to that storage,  disconnect the ipod from PC and check if it works out this way?

---

### Post by ibizatunes on 2010-10-11
I have a ipod, it works fine in banshee (but i have the lastest install via PPA's), which version of ubuntu do you have installed? and which banshee
run these command to update banshee
```
sudo add-apt-repository ppa:banshee-team/ppa
```
```
sudo apt-get update && sudo apt-get upgrade
```

if the music is DRM protected your basically screwed for playing on linux

---

### Post by lilredcougar07 on 2010-10-11
I have the Lucid Lynx and Banshee 1.8.0. When I connect my ipod to my computer, it doesn't give me any storage options. It just mounts it asks me if I want to use a photo program with it. I know the music isn't DRM because I was able to put it on my old iPod without any problems.

EDIT: When I looked at a video of an iPhone working with ubuntu, it popped up with it being recognized as a camera and then a media device. Mine doesn't pop up with the media device part, only the camera. Here's the video I am referencing.

[http://www.youtube.com/watch?v=WGf4i_kxqRU&feature=player_embedded](http://www.youtube.com/watch?v=WGf4i_kxqRU&feature=player_embedded)

---

### Post by lilredcougar07 on 2010-10-13
bump

---

### Post by robsoles on 2010-10-13
> **lilredcougar07 said:**
> I have the Lucid Lynx and Banshee 1.8.0. When I connect my ipod to my computer, it doesn't give me any storage options. It just mounts it asks me if I want to use a photo program with it. I know the music isn't DRM because I was able to put it on my old iPod without any problems.

EDIT: When I looked at a video of an iPhone working with ubuntu, it popped up with it being recognized as a camera and then a media device. Mine doesn't pop up with the media device part, only the camera. Here's the video I am referencing.

[http://www.youtube.com/watch?v=WGf4i_kxqRU&feature=player_embedded](http://www.youtube.com/watch?v=WGf4i_kxqRU&feature=player_embedded)

If it offers the 'photo program' then it is seeing storage. Isn't there an extra drive/file-system available under 'Places' (in same section as 'Computer')? If there is an extra drive/file-system under 'places' have you checked it out and if you can put music there, disconnect the ipod and see the music on it?

---

### Post by lilredcougar07 on 2010-10-20
Tried doing that. Didn't work. It acts like it is not staying mounted. I got this error when I tried to open it up:

org.freedesktop.DBus.Error.UnknownMethod: Method "Enumerate" with signature "ayssus" on interface "org.gtk.vfs.Mount" doesn't exist

I have no idea what that means. I looked it up and still don't understand it.

---

### Post by l3lackEyedAngels on 2010-11-24
> **lilredcougar07 said:**
> Hey friends,

So, I just got my iPod touch yesterday, 32GB from Walmart. I was told that Banshee supports it. I plugged it in, computer recognized it as a camera, which I understand. Pulled up Banshee, it had it as Apple iPod. Awesome. Tried to add music, error. The specific error says:

The mp3 format is not supported by the device, and no converter was found to convert it

The mp3 that I used is just a regular mp3, so I have no idea why it wouldn't work. I also tried to use Rhythmbox and it didn't recognize it at all. Is there anything I can do or should I just take it back? I added some music from my friend's Windows computer after searching the internet for some sort of solution and it worked just fine. I don't know what to do and everything that I've looked at so far has just been saying it should work right out of the box. Help please!
I have nearly the same problem, except that I'm dealing with an 8GB iPod Touch and am running 10.04. Looking for a solution...

---

### Post by Flash858 on 2010-11-29
Same exact issue here. Was thinking it was due to mine being jailbroken, but if your devices are not, then I will just wait. I have tried several formats (that the iPod supports), and all return the same error.

I have tried this on 3 machines with Lucid and Maverick, and initially I had to uninstall Rhythmbox to get Banshee to recognise the device.

This is a pity, as it worked perfectly in 4.0 with an older 2nd gen...

---

### Post by l3lackEyedAngels on 2010-11-29
> **Flash858 said:**
> Same exact issue here. Was thinking it was due to mine being jailbroken, but if your devices are not, then I will just wait...Mine, or rather, my nephew's hasn't been jail broken.

I recall another thread which recommends jail breaking the device to make it work properly.

---

### Post by cake nom nom on 2010-12-27
still no solution?

---

### Post by JeffoOfMetal on 2010-12-27
I've got the same trouble here. Are we average users just going to have to wait till some wizard developers create a fix?

---

### Post by sandyd on 2010-12-27
a) did anyone upgrade their firmware
b) you have to sync an itouch to a windows computer w/ itunes ONCE before use

---

### Post by no2498 on 2010-12-27
this is a long shot in the dark
lets see if its a code thing
i do not have 1
but this loads more codes for winff
open a terminal type smplayer click enter
it tells you how to install it
im not sure if you need to restart the computer or not but do not think it will hurt you
retry what you have done so far
as i said a long shot but hay

---

### Post by Benson2175 on 2010-12-29
A new version of usbmuxd and libimobile have just come out and seem to solve the problem for my ipod touch 4.  The way I got them was by having the ppa for Paul Mcenery in my software sources. 

[https://launchpad.net/~pmcenery/+archive/ppa](https://launchpad.net/~pmcenery/+archive/ppa)

There's instructions how to add it at the top of the page. 

One good thing that's come out of this is that for a while there I had to boot up my old Windows XP and use iTunes; it made me realize how much better faster and easier Linux is.  I feel sorry for all the people that use that crap.

Okay wait; it's still not working.  Linux recognizes my touch; it can see all the files that are on it and play them but I can't put anything on to it.  It syncs but I can't find using the device later.

---

### Post by robsoles on 2010-12-29
> **Benson2175 said:**
> ...

Okay wait; it's still not working.  Linux recognizes my touch; it can see all the files that are on it and play them but I can't put anything on to it.  It syncs but I can't find using the device later.

You have an Apple Ipod 4{?|.} Apple has tried to lock each of it's  devices to their own software for a very long time and techniques for  doing so are only improving. Systems by which to allow the 'user' to  store anything but only play 'authorised' content are too easy to  implement these days...

I am not positive because I can't be bothered reading a EULA to a device I wouldn't dream of buying but: I think that anybody ***trying***  to use third-party (<- it means "not Apple") software on an actual  ipod 4 is breaking the EULA associated with the device by it's maker.


While you are waiting for a better 'crack' you may as well install [www.virtualbox.org]("http://www.virtualbox.org/"),  set up a virtual machine of XP or MAC OS X and run itunes in there - if  like me you never ever want to see itunes again then give your Apple  devices to someone you don't like and get a good generic player with no  particular name.


It's the last of my two cents, I hope I don't have to apologise for it  too much later - I remain subscribed but I won't post again unless I  just know I will be making you people a lot happier than I imagine this  post is managing :wink:

---

### Post by Flash858 on 2011-01-03
Yes, still a no go with the new iPod touch. Seriously thinking of trading for a 3rd gen with 3.1.3 on it...and I have had the PPA in my sources for a very long time. I can say it WAS working with the 2nd Gen iPod touch and Rhythmbox flawlessly, but so far, both with the iPod touch 4th gen and the iPad, I get the same result - syncs, but not readable by the device...I am jailkbroken, so maybe I will try once more and then ssh into the device to see if I can fing the music/podcasts, but I am not hopeful at this juncture...

---

### Post by Benson2175 on 2011-01-22
Come on.  Someone fix this.

---

### Post by kamus on 2011-03-23
> **Benson2175 said:**
> Come on.  Someone fix this.

see [https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/705716](https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/705716)

---

### Post by Benson2175 on 2013-02-07
> **Benson2175 said:**
> Come on.  Someone fix this.

Actually fixed myself by getting rid of the ipod.  Apple can eat me.  Android and even Blackberry are much better and more innovative. It's what we use around my house.  It's so sad seeing the plebs wait in line to buy the next Apple crap box. :P

---

### Post by wildmanne39 on 2013-02-07
Old thread closed.

---

