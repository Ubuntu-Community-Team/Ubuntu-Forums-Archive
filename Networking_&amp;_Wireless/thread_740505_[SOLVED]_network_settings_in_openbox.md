---
title: "[SOLVED] network settings in openbox"
date: 2008-03-30
forum: Networking &amp; Wireless
---

### Post by HappyFeet on 2008-03-30
i did a minimal install of ubuntu with openbox and need to know what to type in the terminal to launch a gui network configuration dialog box. like the one in ubuntu (system>admin>network) all network tools are installed. also, would it help to download wlassistant?

---

### Post by RadenMu'az on 2008-03-30
how about:
sudo apt-get install gnome-utils
sudo network-admin

---

### Post by HappyFeet on 2008-03-30
it turns out i needed more than just fwcutter. i installed the firmware and wlassistant and all is right in the world. thanks for the reply though. now on to the sound!

---

### Post by urukrama on 2008-03-31
> **RadenMu'az said:**
> how about:
sudo apt-get install gnome-utils

I suppose you mean [gnome-system-tools]("http://packages.ubuntu.com/gutsy/gnome-system-tools")? [Gnome-utils]("http://packages.ubuntu.com/gutsy/gnome-utils") doens't help you with networking.

**HappyFeet**, I'm not sure what you need for sound, but [this page]("http://urukrama.wordpress.com/2007/12/19/managing-sound-volumes-in-openbox/") might help you find something to suit your needs.

---

