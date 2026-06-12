---
title: "updates have stolen all hard drive space"
date: 2010-02-10
forum: New to Ubuntu
---

### Post by biomedtech on 2010-02-10
I was very happy to install Karmic on my Eee PC netbook, but over time I have been slowly losing space to these automatic updates. In another thread, I was told to use a couple of commands (sudo apt-get autoremove, sudo apt-get autoclean) to fix the situation. That helped initially, but as every 45 MB update would be announced through the Update Manager, it would eat 130 Megs of actual hard drive space.

Now I am down to a mere 50 MB of space of a 3.8GB partition. I don't keep downloads on this drive. I don't have videos, or mp3, or jpg files hidden away. This is just the Karmic OS, and now my netbook is almost useless as everything is super slow. 

I began peeking into a few system folders to see what, if anything could be taking up so much room, and I ran into an odd thing. 

X-11

Whatever X11 is, showed a folder with 1,343 items, identified as a 'link to folder' .  When I tried to open it, it opened another 'link to folder', which opened another 'link to folder', and so forth, over and over again. I eventually stopped trying to open it after about the 14th 'link to folder' loop.   It had a modification date of two days ago, the last time I allowed Update Manager to run. 

I don't mind starting over with a fresh Karmic install, but I hate to think this will happen again in 6 months. 

Any ideas about what is happening here?  Thank you.

---

### Post by solitaire on 2010-02-10
Run: 
```
sudo apt-get clean 
```("clean" removes all the apt cache files where "autoclean" only removes ones older than 30 days I think)

Then try doing the updates one at a time.

Also go through synaptic and remove any apps you don't need.

If you have multiple kernels at boot you can remove the older ones...

---

### Post by kgarbutt on 2010-02-10
Hey biomedtech,

I have a 4G 701 eeepc so I know what you mean. There are a few command lines which will help you to reclaim extra space. Type these from your terminal:

sudo apt-get autoclean
sudo apt-get clean
sudo aptitude clean
sudo apt-get autoremove

This will reclaim some of your space from those automatic updates. Finally, download & install the deb file for 'Ubuntu Tweak.' You can get it here: [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/). When it is installed goto: Aplications/Package Cleaner and there are 4 areas which will help you reclaim your remaining space. If you have enough space on your HD then just use Ubuntu Tweak to reclaim your space. This should help because it is how I do it since we both have similar laptops.

---

### Post by biomedtech on 2010-02-10
> **solitaire said:**
> Run: 
```
sudo apt-get clean 
```("clean" removes all the apt cache files where "autoclean" only removes ones older than 30 days I think)

Then try doing the updates one at a time.

Also go through synaptic and remove any apps you don't need.

If you have multiple kernels at boot you can remove the older ones...

Thanks. It sounds like your solution only applies to a new installation. How can I go back to the original iso image, and get my 1.5 Gigs returned?

As far as I know, I am only running Karmic. I added VLC, one game from the Ubuntu store, and installed Google Chrome. That's it. Everything else is stock with the initial install. 

I don't mean to sound critical, but if Karmic is going to fill my initial Gig-and-a-half of free space over the course of only a few months, that would make it more bloated than Windows.

And what is going on with X-11?

---

### Post by biomedtech on 2010-02-11
WOW!  What a difference! THANK YOU for pointing me to Ubuntu Tweak!. Between the additional commands, and UT, I've recovered 700MB of free space on my SSD drive. And my EeePC got a boost in performance, even my wireless internet connects faster. Thank you!


> **kgarbutt said:**
> Hey biomedtech,

I have a 4G 701 eeepc so I know what you mean. There are a few command lines which will help you to reclaim extra space. Type these from your terminal:

sudo apt-get autoclean
sudo apt-get clean
sudo aptitude clean
sudo apt-get autoremove

This will reclaim some of your space from those automatic updates. Finally, download & install the deb file for 'Ubuntu Tweak.' You can get it here: [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/). When it is installed goto: Aplications/Package Cleaner and there are 4 areas which will help you reclaim your remaining space. If you have enough space on your HD then just use Ubuntu Tweak to reclaim your space. This should help because it is how I do it since we both have similar laptops.

---

