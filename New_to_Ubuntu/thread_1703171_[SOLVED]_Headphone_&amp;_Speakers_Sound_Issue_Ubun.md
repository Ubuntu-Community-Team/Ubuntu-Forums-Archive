---
title: "[SOLVED] Headphone &amp; Speakers Sound Issue Ubuntu10.10"
date: 2011-03-08
forum: New to Ubuntu
---

### Post by temman on 2011-03-08
Hi all,
      Not sure if I posted in the right section I am new to linux  I know very little and certainly no computer savvy.This is simply what has worked for me layed out in lay terms, hopefully it will help other newcomers like myself with linux.

       Having said that there may very well be a more efficient and better way but I am yet to find it! 

       The issue I was having was this, some days my headphones work and my speakers wont and other days it would be the opposite way round. Anyhow this is what I did after days of frustration.   

         Please Note! for this to work I made sure "Sound Preferances" was  figured out correctly! If any help regarding this is required I am more  thane happy to post what I did!  

  1:   I went to Applications > Ubuntu Software Center and searched for "Gnome Alsa Mixer" and Installed it   then rebooted my pc.     

  2:   In Terminal copy and paste the following Code:   
                                                                     sudo apt-get upgrade gnome alsa mixer  

  3:   When upgrade was completed I rebooted my pc.       

  4:   Once done I went to Applications > Sound & Video > Gnome Alsa Mixer and clicked on it.  

  5:   The Gnome Alsa Mixer window opened up, made sure my current card chip was selected, all bar levels up to their limit, also nothing is muted, and headphone is selected (activated) once done > exit.

  6:   Next opened Terminal entered Code: 
                                                                                                                      alsamixer

  7:   Expanded terminal so to see more bars and made sure all bar levels are up to their limit, used right/left and up/down arrow keys on keyboard to navigate to them.Some bars were not activated you will know this by the (MM) below the bar to activate navigate to each one and press the (m) key on your keyboard and it will change to (00) which means it is activated, then raise the level as mentioned previously. 

  8:   While in Terminal with alsamixer showing still > hit F4 key to find any additional bars as it was in my case if there is deal with them accordingly.Once done hit F6 key and make sure "default" is selected when done hit Esc key then Exit > Reboot Pc. 
                           That's it!
PS:Considering jumping out of any Windows wish you  safe landing on Linux pad! :D

---

### Post by ikt on 2011-03-08
> **temman said:**
> sudo apt-get upgrade **gnome alsa mixer**

Heya,

Just quickly afaik apt-get will take the argument 'upgrade', and then try and do a full upgrade, anything after 'sudo apt-get upgrade' is ignored.

Also you might want to do "sudo apt-get update" before the upgrade to make sure you have the latest updates :)

---

### Post by temman on 2011-03-09
Hi
   I did what I posted : sudo apt-get upgrade  gnome alsa mixer and it worked fine no problem what so ever nothing was ignored, but thanks anyway I will take that on board ;)!

---

### Post by ikt on 2011-03-11
> **temman said:**
> Hi
   I did what I posted : sudo apt-get upgrade  gnome alsa mixer and it worked fine no problem what so ever nothing was ignored, but thanks anyway I will take that on board ;)!

No I mean that was my point :p

It will do a full upgrade because you said 'sudo apt-get upgrade', anything after the text 'upgrade' will be ignored, and it will do a full upgrade anyway :)

For example if you have updates awaiting to be installed, and type 'sudo apt-get upgrade ahjioedahdiua' it will still present you with all the upgrades that need installing.

---

