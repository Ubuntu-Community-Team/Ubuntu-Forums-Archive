---
title: "Troubles trying Ubuntu Netbook"
date: 2010-10-08
forum: New to Ubuntu
---

### Post by elemenopy on 2010-10-08
Hey, I'm having some trouble trialling Ubuntu Netbook edition. (I'm new to Ubuntu.)

I've been following the instructions as per: [Ubuntu's page]("http://www.ubuntu.com/netbook/get-ubuntu/download") and everything went well up until step 3. I've got a 4gb usb, but my aging laptop that I want Ubuntu on didn't seem to be able to boot from usbs so I burnt the ISO to a CD instead.

I stick it in, reboot and everything seems OK at first. But then I get to a loading-type screen with Ubuntu and a circles which seems off-colour and pressing ESC gets me this message: ```
(process:240): Glib-WARNING **: getpwuid_r(): failed due to unknown user id (0)
```

Trying again, I reboot but press DEL when I get to the first screen with two little icons at the bottom. This gets me a bit farther and sends me to a language selection page, and I follow the prompts to just try out Ubuntu. Still no luck, and I get the same screen as last time and the same error if I press ESC.

Finally, I try another option available on the CD which is apparently to be used if I'm having trouble booting it up. I reboot and get a OS selection screen. Choosing Ubuntu does pretty much exactly the same as before, except with two more errors: ```
cp: cannot start '/custom-installation/initrd-override/*': No such file or directory
```
And a continuously repeating:
```
/init: line 7: can't open /dev/sr0: No medium found
```

Other info:
[LIST]
[*]I would like to keep my current OS (XP Home SP3)
[*]The laptop I would like to install Ubuntu Netbook on is a Toshiba Satellite 1905-S277 (1.6-GHz Pentium 4, 256 MB RAM, 30 GB hard drive)
[/LIST]

That's basically everything. Please help me, point out something I've done wrong, whatever, I'd love to get Ubuntu netbook running!

---

### Post by snowpine on 2010-10-08
Welcome to the forums!

Ubuntu Netbook Edition is not for "aging laptops" but rather for "netbooks" like the Asus EEE PC with the following minimum specs:

> # Intel Atom processor @ 1.6 GHz
# 512MB of system memory (RAM)
# 4GB of disk space
# Screen of 1024x600 resolution
# Graphics chipset with support for visual effects 

According to the [Ubuntu System Requirements]("https://help.ubuntu.com/community/Installation/SystemRequirements#Ubuntu%20Netbook%20Edition"), you might have better luck with Xubuntu, which is designed specifically for older hardware. I have also had good luck with Puppy Linux on older, low-RAM hardware.  :)

---

### Post by waynefoutz on 2010-10-08
I have to disagree with Snowpine. Xubuntu WAS a good choice for older, slower hardware, but now days that's not so much the case. Xfce and Gnome are pretty much the same as far as system resources go.  

There are much better ones out there.
Lubuntu 
[http://lubuntu.net/]("http://lubuntu.net/")

Peppermint:
[http://peppermintos.com/]("http://peppermintos.com/")


Antix:

[http://antix.mepis.org/index.php?title=Main_Page]("http://antix.mepis.org/index.php?title=Main_Page")


Lucid Puppy:

[http://puppylinux.org/main/index.php?file=Download%20Latest%20Release.htm]("http://puppylinux.org/main/index.php?file=Download%20Latest%20Release.htm")

---

### Post by LinksPatrocinados on 2010-10-08
I recommend these too:

Lubuntu 
[http://lubuntu.net/](http://lubuntu.net/)

Peppermint:
[http://peppermintos.com/](http://peppermintos.com/)

---

### Post by elemenopy on 2010-10-08
Great, thanks for all the suggestions!

I've given Puppy a whirl and it's working perfectly. I'll also try out some of the other suggestions later.

Thanks for the help! :)

---

