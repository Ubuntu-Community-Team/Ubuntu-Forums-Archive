---
title: "Radeon x1550 pc to tv"
date: 2011-06-27
forum: New to Ubuntu
---

### Post by Org1 on 2011-06-27
I tried using a vga to component {red blue green} cable it didn't work {unusable signal}. 

My cards website just says:
[http://www.visiontek.com/1000-series-cards/radeon-x1550/radeon-x1550-256mb-agp.html](http://www.visiontek.com/1000-series-cards/radeon-x1550/radeon-x1550-256mb-agp.html)
> **Detailed Specifications**                       
[LIST]
[*]VGA, DVI-I, TV-Out, component **HDTV**
[/LIST]
*I think TV-Out is referring to the s-video port

so it might not support component red green blue. My Tv is a 2003 non high def model so it doesn't have any HD ports but it does have a S-Video RGB RWY and a few other.

Does Ubuntu support pc to tv with my card? Do I need to edit something? what cable should I buy?

I think S-video to s-video or S-Video + 3.5mm to Composite AV {RedWhiteYellow} would be my best bet?

---

### Post by crispy_420 on 2011-06-27
Your options expand once you consider there are s-video to composite adapters.

[http://www.bhphotovideo.com/c/product/516322-REG/Hosa_Technology_SVR_487_Model_SVR_487_Male.html](http://www.bhphotovideo.com/c/product/516322-REG/Hosa_Technology_SVR_487_Model_SVR_487_Male.html)

I think once you get the drivers sorted out it should work. It has been a bit since I used linux + ATI but there use to be a gui for configuration I believe to aid it TV out setup.

---

### Post by Org1 on 2011-06-27
This is the only driver I could find:
[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English)

but it says "The Linux ATI Catalyst&#8482; driver will only be supported in Linux distributions prior to February 2009" so it won't work with 11.04? do I have to downgrade? to what version?

---

### Post by Org1 on 2011-06-27
I downloaded the x.org driver it seems to be working {it enabled gnome some desktop enhance thing} haven't tried hooking up the tv yet but I've noticed flash now crashes every time I enter fullscreen.... I did a search and this seems to be common I downloaded flash-aid it still crashes it didn't do this before.

/tv hook up still won't work

---

### Post by crispy_420 on 2011-06-27
Did you ever try the tool under: System -> Administration -> Hardware Drivers ?

Also the version of ATI/AMD Catalyst Control Center is called fglrx-amdcccle, maybe look into that too.

---

### Post by Org1 on 2011-06-28
The whole fglrx-amdcccle is an add-on to the x.org driver.

There's no System -> Administration -> Hardware Drivers but I'm sure I ran prosomehtingoranother driver it had nothing to download its probably what your talking about.

---

### Post by Org1 on 2011-06-28
Once I removed x.org/fglrx-amdcccle and restart the computer flash works {slow but works}. 

Anyone got any suggestions?

---

### Post by crispy_420 on 2011-06-28
Think the proprietary driver installer is called jockey-gtk, is it installed?

---

### Post by Org1 on 2011-06-28
It's installed and when I run it it searches then says there are no drivers in use on this system.

---

### Post by mastablasta on 2011-06-28
you shouldn't be installing proprietary drivers on new Ubuntu if the OS is not supported. by it. if oyu did that then you now need to clean it up/remove it.
 
you can however use the opensource drivers. i am not sure hwo far they are but they should also be able to do dual screens. only maybe an application is needed.

---

### Post by Org1 on 2011-06-28
If I can get flash to stop crashing on fullscreen mode I'd be happy with the x.org/fglrx-amdcccle drivers.

---

### Post by Mark Phelps on 2011-06-28
> **Org1 said:**
> It's installed and when I run it it searches then says there are no drivers in use on this system.

That's because -- there are NO Catalyst drivers that will work with your card and Ubuntu versions newer than 8.10 -- regardless of what other folks are telling you to do.

---

### Post by Org1 on 2011-06-28
Is there a way I can downgrade Ubuntu?

/editI read [https://help.ubuntu.com/community/DowngradeHowto](https://help.ubuntu.com/community/DowngradeHowto) but don't understand it.

Can I just download 8.10 iso USB boot it and install it? being a clean install?

---

### Post by Mark Phelps on 2011-06-29
I believe I read recently that 8.10 has reached end-of-life -- meaning, that it's not going to get anymore upgrades.

So basically, even if you COULD downgrade Ubuntu (which you can't -- you have to reinstall it), you'd end up running a version that is no longer supported.

Sorry ... but the only way you're going to get the display options you want is to upgrade the video card to something newer that is suppored.

---

