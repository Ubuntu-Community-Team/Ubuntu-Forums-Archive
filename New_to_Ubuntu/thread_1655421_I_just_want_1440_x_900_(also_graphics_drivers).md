---
title: "I just want 1440 x 900 (also graphics drivers)"
date: 2010-12-29
forum: New to Ubuntu
---

### Post by VimesCarrot on 2010-12-29
(I'm on 10.04)

I'm new to Ubuntu, I wasn't sure if I should post here or in the "multimedia" section, since this is probably a graphics card problem, but since I'm so new I thought here would be best...

Anyway, as in the title, I'm currently displaying 800x600 resolution, and I want 1440x900. To this end, I figured I would probably have to install my graphics card drivers (System > Display > Monitor gives only 800 x 600 or 640 x 480 options currently), but I don't seem to be able to.

One of the stickies at the top of this forum suggested I use 

```
lspci | grep VGA
```

in the terminal in order to get my graphics card details. It told me:

```
01:00.0 VGA compatible controller: nVidia Corporation Device 0de1 (rev a1)
```

Doesn't look right to me, but I don't really know what it was supposed to say. My card is an Nvidia GeForce 430 GT.

When I was on 9.10 a few weeks ago, I tried downloading the drivers directly from the Nvidia website somewhere. But er, I didn't know what to do with them once I had them. I'm not even sure I could find them again.

I've gone to System > Administration > Hardware drivers, which is what everywhere seems to say to do to get proprietary drivers, but it's just blank, there's nothing in it.

Sorry, I seem to have gone on for quite a while. All I want is 1440x900, so anything which will give me that is fine; the graphics drivers I've just assumed are necessary. Can anyone help, please?

---

### Post by cariboo on 2010-12-29
you can install the driver manually using either the Software Center, or Synaptic Package Manager. Search for nvidia-current, then once the driver is installed open a terminal and type:

```
sudo nvidia-xconfig
```

Then reboot. Once back at the desktop go to System->Administration->Nvidia Settings to set your monitor resolution.

---

### Post by VimesCarrot on 2010-12-29
I did that...and now Ubuntu won't load. <.< I'll see the Ubuntu logo and then I get a black screen with a text cursor in the top left.

---

### Post by EifleMan on 2010-12-29
I think you need to edit your xorg.conf file to tell x.org to use your NVIDIA graphics driver.

1. Open a terminal window and navigate to the the directory where your *xorg.conf* file is located, which should be /etc/X11.
2. Make a backup copy of your xorg.conf file by typing the command
```
sudo cp xorg.conf xorg.confBAK
```
3. Open your *xorg.conf* file in gedit using the command
```
sudo gedit xorg.conf
```\
4. Find the section in the file that looks similar to
```

Section "Module"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "type1"
        Load    "vbe"
EndSection

```
and comment out the line reading ```
Load    "dri"
``` using a *#* as shown below.
```
#        Load    "dri"
```
5. Look for another section that looks similar to
```

]Section "Device"
        Identifier      "Card0"
        Driver          "nv"
EndSection

```
and change the line that starts with *Driver* to
```

Driver "nvidia"

```
6. Reboot your computer. GNOME, or your installed desktop manager should load properly again.

I hope that helps.

---

### Post by VimesCarrot on 2010-12-29
Thanks for the help.

Sadly, I don't have a Section "Module", and my Driver is already set to Nvidia, so there's nothing I can change...

---

