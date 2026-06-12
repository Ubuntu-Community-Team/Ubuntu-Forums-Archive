---
title: "Will this drawing tablet work with GIMP?"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by Legendary_Bibo on 2010-06-01
I've been bored and need a hobby so I took up drawing web comics and I need something to make drawing easier and I've read that Wacom tablets work out of the box for linux, but then I see websites talking about some sort of process to get them to work. So does anyone know if this one will work out of the box, or if it just takes a download of a few lib files?

[http://www.amazon.com/gp/product/B002OOWC3I/ref=s9_simh_gw_p23_csp?pf_rd_m=ATVPDKIKX0DER&pf_rd_s=center-2&pf_rd_r=13K9N2KS10B6C77EWWPF&pf_rd_t=101&pf_rd_p=470938631&pf_rd_i=507846](http://www.amazon.com/gp/product/B002OOWC3I/ref=s9_simh_gw_p23_csp?pf_rd_m=ATVPDKIKX0DER&pf_rd_s=center-2&pf_rd_r=13K9N2KS10B6C77EWWPF&pf_rd_t=101&pf_rd_p=470938631&pf_rd_i=507846)

I'm on lucid by the way.

---

### Post by Phrea on 2010-06-01
I found this: [http://ubuntuforums.org/showthread.php?t=1469731&highlight=Wacom+Bamboo+Pen+Tablet](http://ubuntuforums.org/showthread.php?t=1469731&highlight=Wacom+Bamboo+Pen+Tablet)

---

### Post by Legendary_Bibo on 2010-06-01
> **Phrea said:**
> I found this: [http://ubuntuforums.org/showthread.php?t=1469731&highlight=Wacom+Bamboo+Pen+Tablet](http://ubuntuforums.org/showthread.php?t=1469731&highlight=Wacom+Bamboo+Pen+Tablet)

Ah great reference once I get it. Thanks :)

---

### Post by Favux on 2010-06-01
Hi Legendary_Bibo,

Right, for Lucid you'll need to compile a newer wacom.ko than the default one.  Your Bamboo Pen tablet is too new for the default one.  You'll want to use linuxwacom 0.8.6-2.  The wacom.ko is the usb kernel driver.  See the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

---

