---
title: "Help with 3d effects"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by Ghost_09 on 2009-11-11
I have version 9.10 i'm really new to ubuntu. I was wondering how do I get the cube and other visual effects running. Also all my mp3 are mpeg format what music player would be able to suport them for playback.:guitar:

---

### Post by duds2008 on 2009-11-11
Go to System -> preferences -> appearance -> visual effects. Further more install compiz-config-settings-manager (ccsm). As for mp3 playback check out [https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by CaptainMark on 2009-11-11
alternativley you could use soundconverter which is on the repos to bulk convert your music into a more widely used format

---

### Post by Ghost_09 on 2009-11-11
> **duds2008 said:**
> Go to System -> preferences -> appearance -> visual effects. Further more install compiz-config-settings-manager (ccsm). As for mp3 playback check out [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
Well i already have the visual effects enabled but when i use the ubuntu software center to look up ccsm it's not showing me a option of installing it does that mean i'll have to go to a site?

---

### Post by Ghost_09 on 2009-11-11
> **CaptainMark said:**
> alternativley you could use soundconverter which is on the repos to bulk convert your music into a more widely used format
well i have amarok if i was to convert what format would be best suited for it?

---

### Post by duds2008 on 2009-11-11
Try (from the terminal) sudo aptitude install compizconfig-settings
If you are installing it through synaptic, type "compiz" as your search string and install the above mentioned either by double clicking the entry or single clicking the lhs box and marking it for installation. End by clicking apply.

---

### Post by ninjapirate89 on 2009-11-11
> **Ghost_09 said:**
> well i have amarok if i was to convert what format would be best suited for it?

If you have a large collection, converting all of your music could take a very long time. If you want to play mp3's, wma's, have flash etc then you should install ubuntu-restricted-extras.

Edit -> Just noticed you said you have amarok. If you are using Kubuntu then it would be kubuntu-restricted-extras instead (although I'm not sure of the difference).

---

### Post by Ghost_09 on 2009-11-11
> **ninjapirate89 said:**
> If you have a large collection, converting all of your music could take a very long time. If you want to play mp3's, wma's, have flash etc then you should install ubuntu-restricted-extras.

Edit -> Just noticed you said you have amarok. If you are using Kubuntu then it would be kubuntu-restricted-extras instead (although I'm not sure of the difference).
nope i'm just using ubuntu 9.10, i installed that because i couldn't get rhythmbox working so I figured if I tryed a different program i'd be sucessful on getting my music playing.

---

### Post by duds2008 on 2009-11-11
ubuntu-restricted-extras is a good idea. You could also install w32codecs to help out with media using microsoft products. As for media players, Totem works well for me, and vlc media player seems pretty able to handle almost all formats.:D

---

### Post by duds2008 on 2009-11-11
> **Ghost_09 said:**
> nope i'm just using ubuntu 9.10, i installed that because i couldn't get rhythmbox working so I figured if I tryed a different program i'd be sucessful on getting my music playing.

I went back to 9.04 after having quite a few problems with 9.10. I personally do not believe that 9.10 is fully stable yet. Perhaps you should try installing 9.04 if you are having issues. I find it extremely reliable and stable:D

---

### Post by Ghost_09 on 2009-11-11
> **duds2008 said:**
> ubuntu-restricted-extras is a good idea. You could also install w32codecs to help out with media using microsoft products. As for media players, Totem works well for me, and vlc media player seems pretty able to handle almost all formats.:D
And where might i go to get that? the ubuntu-resticted-extras

---

### Post by ninjapirate89 on 2009-11-11
If you have installed ubuntu-restricted-extras then Amarok should be able to play your mp3s just fine. If it still isn't playing them, try using a different player, I use Banshee personally.

---

### Post by ninjapirate89 on 2009-11-11
> **Ghost_09 said:**
> And where might i go to get that? the ubuntu-resticted-extras

No, w32codecs is separate from the restricted extras. Just type 'sudo apt-get install w32codecs' into the terminal without the quotes.

---

### Post by RonB123123 on 2009-11-11
Im having issues with 3D effects too. I was able to install the compiz package through the terminal and when I click on System > Preferences > CompizConfig Settings Manager, I select the effects I want the cube so I enable 3D windows and other features but none of them work. 

I tried to go to System > Preferences > Appearance to enable the effects because it's set to None and it says "Desktop effects could not be enabled"

What can I do to resolve this?

---

### Post by ninjapirate89 on 2009-11-11
> **RonB123123 said:**
> Im having issues with 3D effects too. I was able to install the compiz package through the terminal and when I click on System > Preferences > CompizConfig Settings Manager, I select the effects I want the cube so I enable 3D windows and other features but none of them work. 

I tried to go to System > Preferences > Appearance to enable the effects because it's set to None and it says "Desktop effects could not be enabled"

What can I do to resolve this?

Try going to System -> Administration -> Hardware Drivers and checking to see if you need to install a driver for your video card.

---

### Post by Ghost_09 on 2009-11-11
> **ninjapirate89 said:**
> No, w32codecs is separate from the restricted extras. Just type 'sudo apt-get install w32codecs' into the terminal without the quotes.
I got both the w32codecs and the restricted extras now but amarok is not working still only one set of files do. Could you maybe help me out with a link to banshee if you think it will work for me. Also I am having trouble finding ccsm. I've done things in the terminal for it but no luck really.

---

### Post by ninjapirate89 on 2009-11-11
> **Ghost_09 said:**
> I got both the w32codecs and the restricted extras now but amarok is not working still only one set of files do. Could you maybe help me out with a link to banshee if you think it will work for me. Also I am having trouble finding ccsm. I've done things in the terminal for it but no luck really.

To install banshee and ccsm type 'sudo apt-get install banshee compizconfig-settings-manager' into the terminal without quotes.

---

### Post by Ghost_09 on 2009-11-11
> **ninjapirate89 said:**
> To install banshee and ccsm type 'sudo apt-get install banshee compizconfig-settings-manager' into the terminal without quotes.
dude your my hero thank you so much both worked ^^:D

---

### Post by ninjapirate89 on 2009-11-11
> **Ghost_09 said:**
> dude your my hero thank you so much both worked ^^:D

Glad to be of help.

---

