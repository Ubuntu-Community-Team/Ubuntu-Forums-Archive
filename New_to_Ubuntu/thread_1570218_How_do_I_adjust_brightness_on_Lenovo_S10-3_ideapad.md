---
title: "How do I adjust brightness on Lenovo S10-3 ideapad?"
date: 2010-09-07
forum: New to Ubuntu
---

### Post by mr.xulu on 2010-09-07
Hi! I'm very new to ubuntu (installed it last week) and have a dual boot of lucid alongside windows 7 starer on my lenovo S10-3 netbook.

I'm trying to look for a way to adjust brightness but I can't. I've tried the following:

1. pressing function key arrow up or down. in windows 7 I have a scroll bar that appears on the bottom of the screen similar to like when you adjust brigthness or volume on a tv set. but it doesn't appear when I'm booted to lucid.

2. using the brightness adjustment bar in 'preferences' when i click on the battery icon. this bar appears on my neo laptop (also on lucid, can't remember the exact model) but this bar doesn't appear on my lenovo netbook.

3. gconf-editor/apps/gnome power manager/backlight - I've tried adjusting thru gconf-editor as well but it doesn't seem to work.

4. I've also tried adding the brightness applet on the panel but it's not working either.

Please help. My panel's too bright #-o

Thanks :D

---

### Post by mr.xulu on 2010-09-07
I forgot to mention that I also installed the lubuntu desktop environment on my lucid. But the brightness problem already existed before I installed lubuntu package.

Thanks :)

---

### Post by mr.xulu on 2010-09-08
By they way, this is my video card: Intel Corporation N10 Family Integrated Graphics Controller

---

### Post by Arla on 2010-09-08
Are you comfortable editing the grub command line? If so, when grub menu comes up, try pressing e against the linux kernel and adding the following to the end of it
```

acpi_backlight=vendor

```

That MAY work, [alternatively]("http://lgallardo.com/en/2010/08/31/control-del-brillo-de-lenovo-s10-3-video-gma-3150-on-linux/") this link shows some ways to do it (but it's not desparately pretty)

---

### Post by mr.xulu on 2010-09-08
[QUOTE=Arla;9821494]Are you comfortable editing the grub command line? If so, when grub menu comes up, try pressing e against the linux kernel and adding the following to the end of it
```

acpi_backlight=vendor

```


Hi Arla!

I am afraid. But I'm willing to try. I'd like to try the first option as the second one really doesn't seem pretty.

But before I do i'd like to ask for more details how to do the first option. I hope you understand. It's only in the past week that I ever entered commands in terminal in my seventeen years of using computers. I've never gone this far inside my computer before.

1. I checked out grub by pressing 'e' and it gave me several options but I didn't select any yet. One of them was to select for a command line. is that where i go?

2. If so, what's the environment like? is it like terminal inside desktop where i just type "acpi_backlight=vendor" and press enter? Or is there some other action?

3. If I make a mistake in entering the command (misspell, or wrong spacing) do I risk disrupting my grub hence not be able to boot into my OS or some other disruption in the system?

Thank you for understanding and thank you for your help :)

---

### Post by soulston on 2010-09-11
Hi

If you look at this link this has been an ongoing issue although the last post in the thread seems to suggest it has been fixed in a new kernal.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/538256](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/538256)

I am currently using:

sudo setpci -s 00:02.0 F4.B=29

Where "29" can be B=00 to B=FF, respectively black to full, although it's annoying and the netbook always starts very bright.

---

### Post by mr.xulu on 2010-09-11
> **soulston said:**
> Hi

If you look at this link this has been an ongoing issue although the last post in the thread seems to suggest it has been fixed in a new kernal.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/538256](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/538256)

I am currently using:

sudo setpci -s 00:02.0 F4.B=29

Where "29" can be B=00 to B=FF, respectively black to full, although it's annoying and the netbook always starts very bright.


Hi soulston! Thanks for the link and thank you so much for that command line! It worked! :)

---

