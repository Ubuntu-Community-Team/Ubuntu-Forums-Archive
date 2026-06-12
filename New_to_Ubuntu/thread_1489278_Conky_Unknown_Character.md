---
title: "Conky Unknown Character"
date: 2010-05-20
forum: New to Ubuntu
---

### Post by Ciallmhar on 2010-05-20
Hello all,

I am having a problem with Conky. Well, it's not really a problem, I can live with it, but it bothers me. At the end of my Conky there is a rectangle (the kind that you get from trying to show a character that cannot be shown). I am wondering how I can get rid of this. It is not due to my .conkyrc file, or so it seems, as if I remove the end of the file, the rectangle just bumps up to an earlier spot. Again, this is more of my OCD being annoying than anything else.

Thank you in advance,
Ciallmhar.

---

### Post by bra|10n on 2010-05-20
Not using Sans as a font by any chance? 
Try a different font if you are

---

### Post by Ciallmhar on 2010-05-21
I am using DejaVu Serif currently as my font, and when I try and change it, it does not seem to do anything, including not changing the fonts' appearance, so I am not sure if I am correctly changing my script. I can post what it currently is if that would help.

---

### Post by bra|10n on 2010-05-21
Post your conkyrc for a look-see then

---

### Post by Ciallmhar on 2010-05-21
Here it is: [http://slexy.org/view/s2byoin3zV](http://slexy.org/view/s2byoin3zV)

---

### Post by bra|10n on 2010-05-21
Add these to your conkyrc

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

text_buffer_size 2048

You can't do this...

${voffset -1} Cpu: ${color e0e0e0}[COLOR=Red]${font}[/COLOR]${cpu}% ${color} Mem: ${color  e0e0e0}[COLOR=Red]${font}[/COLOR]${mem} ${color}  |  ${color} Uptime: ${color  e0e0e0}[COLOR=Red]${font}[/COLOR]${uptime_short}${color}  |  ${colo...

Remove the bits in red and all should work with different fonts then

---

### Post by Ciallmhar on 2010-05-21
I added those lines, and removed all of the instances of ${font}, but it still shows up. Also if I take out the XFT font lines by commenting them, it also still shows up, although it is not a rectangle it is a "corner piece", for lack of a better description. Its like a square r.

---

### Post by bra|10n on 2010-05-21
Did you try another font at the same time?
If that doesn't work I'm at a loss. I can only direct you here:
[http://conky.sourceforge.net/config_settings.html](http://conky.sourceforge.net/config_settings.html)

---

### Post by Ciallmhar on 2010-05-21
Fixed it, it turns out it was the newline character showing up because the file was saved in Windows format, so changing it to Unix fixed it.

---

### Post by deityx on 2010-09-28
Thanks for the solution. I had the same problem with line ending format. Worked for me! :)

---

### Post by Nicram on 2010-10-03
> **Ciallmhar said:**
> file was saved in Windows format, so changing it to Unix fixed it.

So simple solution!

Thanks.

---

