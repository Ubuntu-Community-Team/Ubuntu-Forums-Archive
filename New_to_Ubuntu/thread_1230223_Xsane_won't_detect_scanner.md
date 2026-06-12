---
title: "Xsane won't detect scanner"
date: 2009-08-03
forum: New to Ubuntu
---

### Post by wardotviking on 2009-08-03
I'm new to Ubuntu.  I'm running 9.04.  I have an Epson TX100 multifunction.  It printed straight out of the box, but xsane says it doesn't detect it. How do I get it to work? I've looked on the forums and the internet and haven't found a solution.  I'm new to this, so please be gentle with me  :neutral:

---

### Post by coldReactive on 2009-08-03
TX100 isn't supported by the proper drivers on Ubuntu 9.04, only 8.04 32-bit and NO 64-bit support.

[Source]("http://avasys.jp/hp/menu000000500/hpg000000442.htm") (Download > All-in-ones > Check OS of Operation > Image Scan! For Linux)

---

### Post by larsman1 on 2009-08-03
**Re: Epson NX300 All-in-One**             
                                                                [SIZE=5][SIZE=3]Thanks for the Avasys link.:smile: The iScan utility for my RX580 "all in one" has more resolution (dpi) options than xsane.
I'm using Jaunty 9.04 AMD64 for my HP Pavilion Slimline.

[http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do)

The above link is an easer scanner interface than xsane.  It shows up as "image scan!" in the pulldown applications/graphics menu.  I right-clicked on the icon to put it in my tool bar.  The tool bar icon has a neater look with a flatbed and spring image.
    If you want to use xSane, then you need to use your "synaptic package manager".  Pulldown - "system/administration/synaptic package manager".    Type epson, and I think the one you need to run Xsane is called "libsane-extras".  If you scroll down in the description when you highlight libsane-extras, you will see it has backends for Epson and other brands that are not included in the official SANE distribution.  Mark it for installation, apply, and it will install it for you.  Your xSane should work.[/SIZE]   
[/SIZE]

---

### Post by wardotviking on 2009-08-04
Thanks for your help.  It will be a few days before I can try your suggestions, but I'll get back to you when I have.

I'm not very experienced at this sort of thing, but we'll see what I can do.  I was amazed how quickly and easily the printer was detected.  All I did was plug it in and switch it on.

---

