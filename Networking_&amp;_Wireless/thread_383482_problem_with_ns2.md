---
title: "problem with ns2"
date: 2007-03-13
forum: Networking &amp; Wireless
---

### Post by dungnt025 on 2007-03-13
I am trying to install ns2 to study 802.11e. But, when I typed ./configure, the error occured:
```
checking for X11 header files
can't find X includes
```
How should I resolve?

---

### Post by lloyd_b on 2007-03-13
Try installing the package "xorg-dev".  Hopefully this will install the necessary header files.

Lloyd B.

---

### Post by dungnt025 on 2007-03-15
I don't kown how to the install package "xorg-dev". Can you help me? Thanks.

---

### Post by lloyd_b on 2007-03-15
> I don't kown how to the install package "xorg-dev". Can you help me? Thanks.
Open a terminal window, and enter the following command:
```
sudo apt-get install xorg-dev
```

Lloyd B.

---

### Post by dungnt025 on 2007-03-17
thanks. I have tried. But error has occured. oh, my god. Will I install all package????????

```
The following packages have unmet dependencies:
  xorg-dev: Depends: libdmx-dev but it is not going to be installed
            Depends: libfontenc-dev but it is not going to be installed
            Depends: libfs-dev but it is not going to be installed
            Depends: libice-dev but it is not going to be installed
            Depends: libsm-dev but it is not going to be installed
            Depends: libx11-dev but it is not going to be installed
            Depends: libx11-dev but it is not going to be installed
            Depends: libxau-dev but it is not going to be installed
            Depends: libxaw7-dev but it is not going to be installed
            Depends: libxcomposite-dev but it is not going to be installed
            Depends: libxcursor-dev but it is not going to be installed
            Depends: libxdamage-dev but it is not going to be installed
            Depends: libxdmcp-dev but it is not going to be installed
            Depends: libxevie-dev but it is not going to be installed
            Depends: libxext-dev but it is not going to be installed
            Depends: libxfixes-dev but it is not going to be installed
            Depends: libxfont-dev but it is not going to be installed
            Depends: libxft-dev but it is not going to be installed
            Depends: libxi-dev but it is not going to be installed
            Depends: libxinerama-dev but it is not going to be installed
            Depends: libxkbfile-dev but it is not going to be installed
            Depends: libxkbui-dev but it is not going to be installed
            Depends: libxmu-dev but it is not going to be installed
            Depends: libxmuu-dev but it is not going to be installed
            Depends: libxpm-dev but it is not going to be installed
            Depends: libxrandr-dev but it is not going to be installed
            Depends: libxrender-dev but it is not going to be installed
            Depends: libxres-dev but it is not going to be installed
            Depends: libxss-dev but it is not going to be installed
            Depends: libxt-dev but it is not going to be installed
            Depends: libxtrap-dev but it is not going to be installed
            Depends: libxtst-dev but it is not going to be installed
            Depends: libxv-dev but it is not going to be installed
            Depends: libxvmc-dev but it is not going to be installed
            Depends: libxxf86dga-dev but it is not going to be installed
            Depends: libxxf86misc-dev but it is not going to be installed
            Depends: libxxf86vm-dev but it is not going to be installed
            Depends: x11proto-composite-dev but it is not going to be installed
            Depends: x11proto-damage-dev but it is not going to be installed
            Depends: x11proto-fixes-dev but it is not going to be installed
            Depends: x11proto-xext-dev but it is not going to be installed
            Depends: xserver-xorg-dev but it is not going to be installed

```

---

### Post by lloyd_b on 2007-03-17
I don't entirely understand why you're getting those errors.  "apt-get" should automatically download all dependencies for "xorg-dev".  So it should have automatically selected all those to download (and yes, you do need to install all of them to be sure you have the header files you need), and the only thing you should have seen is a report on how much would be downloaded, how much disk space would be used, and a prompt as to whether or not you wanted to continue.

Note: the entire set of headers only occupies about 10Mb of disk space.  It's a long list of packages, but they're fairly small.

May I suggest trying to retrieve that package via "synaptic".  In a terminal window, just type "sudo synaptic" - this will bring up a GUI based package manager (it's also in the menu, under "system" or "administration" - I run Xubuntu rather than Ubuntu, so my menus are different).

Once you've got synaptic running, find the "xorg-dev" package, right click on it, and select "mark for installation".  Then click the "apply" button toward the top of the screen.

I don't entirely understand why your apt-get doesn't work exactly like mine, but hopefully using synaptic will bypass the issue.

Lloyd B.

---

