---
title: "GTKpod no longer converts FLAC to MP3 for iPod"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by Charlie Chick on 2009-04-26
Hello Everybody,

Before I upgraded to 9.04, I was able to rip CD's into FLAC and then add them to my iPod using GTKpod. GTKpod automatically converted them to MP3 as the iPod doesn't recognise FLAC. 

However, since upgrading to 9.04 it no longer does this, giving the following error message:

"Conversion of ....failed /usr/shared/gtkpod-aac/scripts/convert-2mp3.sh returned exit status 5"

Presumably this means that the conversion script is no longer present. I've looked through Synaptic, but couldn't find anything that looks likely.

Can anybody point me the right direction, please?

Thanks,

Charlie

---

### Post by Charlie Chick on 2009-04-26
Found the solution - I forget to install LAME - the MP3 encoder. Installed it from Synaptic and all is well again. Also, if you want to be able to normalise the volume level of your tracks, install MP3gain from Synaptic.

Charlie

---

