---
title: "Media Player That Plays all Media"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by Penguin Guy on 2009-03-26
Q: Is there a media player that has downloadable add-ons - allowing you to play all types of media?
A: Most Linux media players work like this - however there are no extensions for certain types of media such as .swf.

Note: You can play .swf files by opening them in a web browser with the flash player extension.

Thanks to all the people who helped me out!

---

### Post by chazn85 on 2009-03-26
the best player around is vlc player

convertor not to sure

---

### Post by perrti-y02 on 2009-03-26
The media player itself is simply a frontend for an engine (usually). Take, as an example, Amarok which has an option to use either the Xine Engine or Gstreamer engine. For either of these you get codecs that do the work of decoding various formats.

My suggestion is install amarok (it is the best player in my opinion) and then search in Synaptic for anything with the words xine (or amarok) and codec in them.

---

### Post by leonardo_neo on 2009-03-26
It is not the player, but the codec support that makes a player to play everything.

So to have most of the codec supports, you need to install them.

Have you installed 

1. ubunutu-restricted-extras
2. medibuntu repository and codecs?

If not then install them, and you will be good with most of the file formats.

To install restricted extras type the following command in terminal

> sudo apt-get install ubuntu-restricted-extras

To Install medibuntu repository go to the following link.....

> [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

From there, install the 
libdvdcss2
w32codecs

And you are good with most of the file formats.

If you want to have a good media player, then install vlc. It has some cool features, and most of the media support.

:)

---

### Post by Penguin Guy on 2009-03-29
Thanks but that doesn't seem to include a .swf codec. Do you know how I can get one?

---

### Post by Bloch on 2009-03-29
.swf files are flash files - animations and mini-programs. Flash video is .vlc and vlc and Totem will play them.
But .swf will only play with the official flash plug-in, in your browser.

(this is not 100% true, but gnash and other opensource flash players are not yet fully reliable)

---

### Post by Penguin Guy on 2009-03-29
Thanks for the help, I just won't bother trying to play it anymore. :KS

---

### Post by Temposs on 2009-03-29
Just open Firefox and do File->Open, and then open your .swf file. It should play.

---

### Post by Penguin Guy on 2009-03-29
I tried that but it said the file was 0:00 minutes long.

EDIT: It appears it was an error with that particular file - other flash movies work fine.

---

