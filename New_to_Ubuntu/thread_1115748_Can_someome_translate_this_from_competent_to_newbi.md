---
title: "Can someome translate this from competent to newbie language please"
date: 2009-04-04
forum: New to Ubuntu
---

### Post by polkadotteapot on 2009-04-04
I've found a promising site to get the internet working on my Acer Aspire One along with a few other problems here: [http://www.aspireonekernel.com/#Downloads](http://www.aspireonekernel.com/#Downloads)

Downloaded and installed the kernel as stated then I am told to do this:

'After you have installed the kernel, you will need to confugure Ubuntu so that the sound and mic function correctly after suspend/resume. In order to do this open the **file/etc/modprobe.d/options** with your text editor of choice and add the following to the end and then save the file

options snd-hda-intel model=acer-aspire

After rebooting, the new kernel should load. You should notice a reduced boot time and all your hardware functioning as you would expect.'

I don't actually understant what I need to do, is this something you do in the terminal? Can someone explain to me what I need to do?

Thank you.

---

### Post by lavy on 2009-04-04
Hy,

Is simple you need to navigate to that file /etc/modprobe.d/options.  Open the file, go to the end, press enter to be positioned on a new line and copy and paste the text

options snd-hda-intel model=acer-aspire

Save the file and reboot. You don't need the command line to do that.

---

### Post by issih on 2009-04-04
You just need to edit a file and add the line:

```
options snd-hda-intel model=acer-aspire
```

To the end of it.

The file in question is located at:

```
/etc/modprobe.d/options
```

That is it is a file named options in the directory modprobe.d, and modprobe.d is in the directory etc.

Note that this file is almost certainly owned by root, as it is a system file, so you need to use sudo to temporarily gain root powers in order to edit it (this is to stop you messing up your system accidentally)

The easiest way to do this is as follows:

open a terminal window (Applications->Accessories->Terminal)
and enter:

```
sudo gedit /etc/modprobe.d/options
```

enter your login password when prompted and hit enter (it will not echo anything to the screen as you do so)

This command will launch a gui text editor (gedit) opened on the file you need to edit with root permissions (sudo).

Simply add the line "options snd-hda-intel model=acer-aspire" at the end of the file and save it.

Then reboot.

Hope that helps.

---

### Post by VCoolio on 2009-04-04
For gui-applications like gedit you should use gksudo instead of sudo. Read [this]("http://psychocats.net/ubuntu/graphicalsudo") and [this]("http://ubuntuforums.org/showthread.php?t=857244&highlight=gksudo").

---

### Post by polkadotteapot on 2009-04-04
Thank you so much, was being a bit of a moose and not looking properly but I needed the sudo vs. gksudo advice as last time I went into root priveledges I ended up breaking things and had to reinstall.

I'm now writing this in ubuntu - I even get the wireless led on at times too! So than you all for your help. I can now get onto breaking things good and proper so you'll be hearing from me soon!

---

