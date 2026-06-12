---
title: "Silly Question But here goes"
date: 2010-01-01
forum: New to Ubuntu
---

### Post by clay woodruff on 2010-01-01
If i do not want to use my nvidia fx5200 card. and use the ubuntu graphics set up, only i need to tweek it a little where would i find the correct file to make the modification to. (need to add some resolution changes). Heres where i think it's silly. its probably xorg right?

---

### Post by Paqman on 2010-01-01
I'm a little bit confused. Are you saying that you don't want to use the Nvidia drivers, and that you just want to use the default graphics drivers that Ubuntu comes with?

If so, just go to System > Admin > Hardware Drivers and deactivate the Nvidia drivers.

---

### Post by starcraft.man on 2010-01-01
> **clay woodruff said:**
> If i do not want to use my nvidia fx5200 card. and use the ubuntu graphics set up, only i need to tweek it a little where would i find the correct file to make the modification to. (need to add some resolution changes). Heres where i think it's silly. its probably xorg right?

If your not wanting to use the card for graphics output then you'll have to plug into motherboard video. Something has to deliver the graphical output to your monitor, else you'd need to set it up for networking and telnet in.

As to adding the custom resolutions, yes that would require editting the xorg.conf file.

If you just want to disable nvidia drivers, uninstall them by whatever means installed. That will remove 3d ability though.

edit: beaten.

---

### Post by clay woodruff on 2010-01-01
yeah i know it's sort of a doppy idea but i found that there may be a bug in my Xserver. when in firefox viewing a streaming video in full screen. it gets choppy and laggy and my CPU goes through the roof. So i did some research and ran some test and i think it's a infinite loop issue. not sure it's been submited, but when i use the graphics that came with 9.10 i dont have that problem. so............ the only thing its resolution isn't what i like and doesn't give me that option along with proper refresh rate. so hence the need to tweek......no pun intended

---

### Post by Paqman on 2010-01-01
> **clay woodruff said:**
> when in firefox viewing a streaming video in full screen. it gets choppy and laggy and my CPU goes through the roof.

That's probably a Flash problem. Are you using the default Flash plugin, or one of the alternatives (eg: Gnash), and are you on 32-bit or 64-bit?

Also, just out of interest, how fast is your CPU?

---

### Post by clay woodruff on 2010-01-01
I'm gonna have to back to you on that i just got called and have to go to work

---

### Post by clay woodruff on 2010-01-02
I'm using 32 bit and AMD Sempron (tm) processor 3400+ so about 2000 mhz using sfwdec flash player. i thought it was a flash issue at first until i got into the High CPU usage used by Xserver  troubleshooting page from Ubuntu. and after running a few commands the main one being /var/log/gdm/* and thats when i found a ton of repedative error messages there were some 12 tabs attached to the file with similar error messages through out every : 0-greeter.log tab there was

---

### Post by Paqman on 2010-01-02
> **clay woodruff said:**
> using sfwdec flash player.

That could well be your problem. The open source Flash alternatives have always lagged behind proper Adobe Flash in performance.

Try closing your browser, uninstalling swfdec and installing the official Adobe Flash package.

---

### Post by clay woodruff on 2010-01-02
i take it the best place to get that is from the adobe website, not through synaptec

---

### Post by lasleym on 2010-01-02
Should be available.  I've read to use "non-free", which is what I'm using and seems fine.  Although I don't think I use in the same venue you do.
[IMG]http://pix.mickysgreenguide.com/nonfree.png[/IMG]

---

### Post by Paqman on 2010-01-02
> **clay woodruff said:**
> i take it the best place to get that is from the adobe website, not through synaptec

On 32-bit the one you get from Synaptic is fine.

---

### Post by clay woodruff on 2010-01-03
ok thanks i will give that a try................ @ lasleym: by the way, what venue we referring too <grinnin>

---

### Post by lasleym on 2010-01-03
> **clay woodruff said:**
> @ lasleym: by the way, what venue we referring too <grinnin>

Streaming video, full screen.

---

