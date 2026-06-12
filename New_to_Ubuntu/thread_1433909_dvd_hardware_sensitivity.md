---
title: "dvd hardware sensitivity"
date: 2010-03-19
forum: New to Ubuntu
---

### Post by arisgano on 2010-03-19
I've been using ubuntu for 2 months now. I had a great time using it becuz of aircrack and all the windows decorator it gives. The only PROBLEM I encountered is that most the flash videos i had written to the DVD couldn't read by hardrive. But, when i tried to play it to my friend's WINDOW computers, it works. My laptop is dvd/blu-ray drive. Before, it can play most dvd's but now it become choosy. It's only 3 months old. I tried using dvdisaster from ubuntu. and its say nothing is wrong with the cd's. thank you:)

---

### Post by Ozymandias_117 on 2010-03-19
If you haven't already, install ```
ubuntu-restricted-extras
``` If you have already installed that, and are still having troubles, run ```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
``` to add the Medibuntu repository, then run ```
sudo apt-get install libdvdcss2
``` and that should fix any remaining problems.

edit: Apparently I can't spell :P

---

