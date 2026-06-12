---
title: "Remote Desktop low-res (fuzzy) screen."
date: 2010-02-16
forum: New to Ubuntu
---

### Post by RedOctober on 2010-02-16
The docs at my clinic are warming up to Ubuntu, mainly because since I loaded it onto 50% of our PCs it hasn't crashed once.  (XP crashed about once per day on half the PCs).  Plus, its just soooo dam simple to use.

One of the complaints is that the screen resolution (when .Rdp'd into the server) is low resolution (fuzzy).  I know that in the .Rdp "Command" under Properties, it's possible to dictate the screen size you want... however, all I want is to get the highest resolution possible, regardless of the overall screen size, so the docs can look at detailed X-ray images.

How do I find out the best Width X Height combo?  (Other than tedious trial and error).

Thanks in advance.

---

### Post by mgmiller on 2010-02-16
I have been running my podiatry office this way for close to 2 years.  It is important to note that all of the monitors in my office use 1280 x 1024 as their native resolution.  

1) In the terminal server client, on the General tab,  under protocol, make sure you have selected RDPv5 from the drop down.  

2) In the Display tab, click, "Use specified screen size" and select 1280 x 960 pixels from the drop down.

3) Still in the Display tab, in the Colors area, select True Color (24 bit) or True Color (16 bit).  You can try both to see which works best.  Sometimes the 24 bit gives an error message depending on your video cards.

4) In the Local resources tab, in the keyboard area, select en-us from the drop down.

5) In the performance tab, put a check in the Enable bitmap caching and Hide window manager's decorations boxes.

Click the quick connect and see how it looks.  Ideally, you should get a seamless windows desktop with both your top and bottom Ubuntu panels visible and usable.

If you are happy, then back in the terminal services client, at the bottom of the window, click on "Save As" and give it a name.  I use server.  After that, any time you want to connect with all those setting intact, you just click the drop down where it says "Quick Connect and select the name you saved.

About a year ago, I convinced another podiatrist buddy of mine to do the same thing after one of his staff killed their file server by surfing the internet on one of the Windows work stations.  He had no computers for a week and it cost him $5000 to get it fixed.  Since switching to Ubuntu, everyone is happy.

---

### Post by RedOctober on 2010-02-17
Thanks mgmiller, I'm in the process of trying out your suggestions.  I like the idea of making the server .rdp window fit inside the Ubuntu desktop so that I can see the top menus and bottom task bar.  One thing is still concerning me though... no matter what settings I use, (this sounds weird) but, it seems that the very pixels in the display are "farther apart" in the Ubuntu .rdp server image than in the Xp .rdp server image.  Somehow the XP image is clear, you can't see individual pixels, but in Ubuntu, it's as if only every second or third pixel is "activated" leaving the image very low-resolution.  Is there a way to make the image as clear in Ubuntu as in XP?

---

### Post by superprash2003 on 2010-02-17
a good alternative is running vnc full screen

---

### Post by mgmiller on 2010-02-18
> Somehow the XP image is clear, you can't see individual pixels, but in Ubuntu, it's as if only every second or third pixel is "activated" leaving the image very low-resolution. Is there a way to make the image as clear in Ubuntu as in XP?

I have not noticed this effect in any of the machines I use to RDP into my server.  They all look very clear to me.  Are you sure you are using the correct resolution and video driver on your work stations?  

Also, the video card used may have an effect like this.  I seem to remember not liking the RDP image I got from a netbook I tried once on my network.  IT had Intel integrated graphics and was running Ubuntu 9.04 at the time, which was known to have issues with Intel graphics.  I have not tried RDP with Intel graphics on a machine with Ubuntu 9.10 on it.   I recently got a new notebook with Intel, which is running 9.10 and looks great, but I have not had a chance to try RDP yet.  I will give it a try in the next few days.

---

### Post by jpl888 on 2010-02-18
It sounds like it could be the colour depth. Try changing it to the highest possible (24 bit) in the RDP properties and see what that does.

---

