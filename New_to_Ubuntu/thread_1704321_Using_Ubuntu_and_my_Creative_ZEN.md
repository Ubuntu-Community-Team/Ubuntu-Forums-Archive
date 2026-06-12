---
title: "Using Ubuntu and my Creative ZEN"
date: 2011-03-10
forum: New to Ubuntu
---

### Post by Themiband on 2011-03-10
Ok so I know that apparently gnomad will solve all my problems here and i&#472;e downloaded gnomad2-2.9-4 and am all ready to give it a try but here it says in the kinda probably helpful to someone with a bit more know how install guide

he simplest way to compile this package is:

  1. `cd' to the directory containing the package's source code and type
     `./configure' to configure the package for your system.  If you're
     using `csh' on an old version of System V, you might need to type
     `sh ./configure' instead to prevent `csh' from trying to execute
     `configure' itself.

     Running `configure' takes awhile.  While running, it prints some
     messages telling which features it is checking for.

I don know how to simply ¨`cd' to the directory containing the package's source code"

any help would be really awesome

---

### Post by Themiband on 2011-03-10
ok so i&#472;e figured out how to CD to stuff (duh!) and now i&#7743; trying to run the whole config thingy and this is my error message

No package 'glib-2.0' found
No package 'gthread-2.0' found
No package 'libnjb' found
No package 'gtk+-2.0' found

so i guess i need to download these thingys well thats what i&#7743; off to do i guess

---

### Post by Themiband on 2011-03-13
alright i have no idea what i need to do here

I've tried installing something called  **libusb** which i think i've done right because the zen is now recognised but whatever files I put onto the player don't show on the zen when i disconnect it and try and play them back

really all i've done is sucessfully wipe all the files i had left on there when i thought i was finally updating the music i had. Any idea on what i could do would be really really appriciated

---

### Post by Themiband on 2011-03-13
ok so i'm still getting the same error message and feel like i've really hit a wall i don't have a clue what do do

I type ./configure and everything looks like its kinda working then it says

"No package 'glib-2.0' found
No package 'gthread-2.0' found
No package 'libnjb' found
No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GN_CFLAGS
and GN_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details."

What on earth am i meant to do with this?

---

### Post by Paqman on 2011-03-13
Gnomad is old and crusty, I don't think it's maintained any more.

You don't need it anyway. Banshee can definitely hook up to your Zen, it handles mine fine. I suspect other players such as Rhythmbox and Amarok will be just the same.

Incidentally, for converting videos for your Zen, check out Arista. You can download a preset for the Zen that will make transcoding videos dead simple.

---

### Post by Themiband on 2011-03-13
None of the programs mentioned in your post recognise my Zen still and this is my new error message

configure: error: *** id3tag.h C header is needed (missing -dev package?) ***\n*** You might have erroneously installed id3lib instead of libid3tag ****\nThis distinction is very delicate, so PLEASE pay attention! ***

any ideas?

---

### Post by lykeion on 2011-03-13
I too have a Creative Zen and used to use Gnomad2 before this project died (haven't been updated since 2009). Nowadays I use Banshee and it works fine with my Zen. You might have to enable MTP Media Player Support in Preferences > Extensions to make it work though.

BTW I think it'll be very problematic to build gnomad2 from source since it relies on old version of libMTP.

---

### Post by Paqman on 2011-03-14
> **Themiband said:**
> 
configure: error: *** id3tag.h C header is needed (missing -dev package?) ***\n*** You might have erroneously installed id3lib instead of libid3tag ****\nThis distinction is very delicate, so PLEASE pay attention! ***


Open up Synaptic and check to see if you have id3lib installed instead of libid3tag. Also, uninstall any extra packages you installed when you were trying to get Gnomad installed, you might have created a conflict.

---

### Post by lykeion on 2011-03-14
It should be said that you shouldn't need to compile gnomad2-2.9.4 because it's in the Ubuntu Lucid repositories. If you're using Maverick you can simply download and install the deb package from [http://packages.ubuntu.com](http://packages.ubuntu.com)

---

### Post by Themiband on 2011-03-14
Oh by god so today i've done nothing different but WHOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOO!!!

i can move files onto my zen again at last

guys this is pretty freakin amazing i've been getting sick of having to listen to the same few songs and not being able to listen to my fav pod casts if any of you are in UK coventry I will buy you all a drink I am so amazingly greatful.

---

### Post by lykeion on 2011-03-15
Did you solve this with Banshee or Gnomad2 - maybe it'll be helpful to others if you shared.

---

### Post by Themiband on 2011-03-15
ah ok

actually its Rythm box thats picking up the Zen, it only worked after I typed 

sudo apt-get install libgtk2.0-dev libnjb-dev

into the console although I have no idea really how or why that made it work

---

### Post by lykeion on 2011-03-15
These dev packages should have no impact on Zen support in Rhythmbox. But anyway glad it worked out for you.

---

