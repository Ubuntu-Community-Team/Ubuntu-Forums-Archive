---
title: "Can't select correct resolution for second screen"
date: 2009-06-03
forum: New to Ubuntu
---

### Post by tampablendie on 2009-06-03
I just installed 9.04 on my work comp and can't select the correct resolution for my second screen.  I am running an Nvidia card with one monitor hooked up to the VGA port( is working correctly), and one on the DVI port.  They are the same screen.  They are setup with twin view.  I have saved the xConfig file and restarted.  Still no correct option.

---

### Post by doas777 on 2009-06-03
> **tampablendie said:**
> I just installed 9.04 on my work comp and can't select the correct resolution for my second screen.  I am running an Nvidia card with one monitor hooked up to the VGA port( is working correctly), and one on the DVI port.  They are the same screen.  They are setup with twin view.  I have saved the xConfig file and restarted.  Still no correct option.


you said you're using Twinview, right? and they are both set to the same resolution in nvidia-settings, right?

also remember, you need to reboot before twinview works correctly (would be nice if they told us that...).

---

### Post by tampablendie on 2009-06-03
No they aren't set to the same resolution in Nvidia-Settings.  That's the problem Nvidia settings does not give me the option to do that.  The native resolution for both screens is 1680x1050, and nvidia settings only lets me select that option for the first screen.  1280x1024 is the largest resolution available for the second screen in the dropdown.

Thanks for the help.

---

### Post by tampablendie on 2009-06-03
So I've been doing some more digging around in the Nvidia settings, and it's reading the frontend input from the screen as 1280x1024.  Even though the screen has a resolution warning that's flashing "Resolution should be set at 1680x1050."  Must be something with the driver.

The driver version that is being used is 93.  I know the latest version is 180, but in restricted drivers there is no option to install any other version other than 93.  Is this because of the age of the video card?  Or should I be able to use one of the newer drivers?


Thanks

---

### Post by tampablendie on 2009-06-03
The card is a winfast a180 ddr, which uses the geforce 4mx gpu chipset.

---

### Post by richtl on 2009-06-16
> **tampablendie said:**
> 
The driver version that is being used is 93.  I know the latest version is 180...

I'm having exactly the same problem with 180. I upgraded to Jaunty last week and the second of my two identical screens won't give me better than 1360x768. (The resolution for the first screen is 1440x900).

Twinview worked properly in Intrepid on 173.

RichTL

---

