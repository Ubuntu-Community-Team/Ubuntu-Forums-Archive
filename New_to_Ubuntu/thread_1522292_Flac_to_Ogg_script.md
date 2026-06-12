---
title: "Flac to Ogg script"
date: 2010-07-02
forum: New to Ubuntu
---

### Post by h8uthemost on 2010-07-02
Anyone know of a good Flac to Ogg script that will let me pick what bitrate I want the Ogg files to be before I convert? I already have a pretty good script for this, but for some reason the script will spit out some albums with garbled tags or folder names. So I'm looking to try out a different one.

Thanks for any help.

---

### Post by inameiname on 2010-07-05
This one might be able to do that. I've only used it a few times as SoundConverter app does my bidding just fine for most:

---

### Post by size_XXM on 2010-10-14
You might want to check out [dir2ogg](http://packages.ubuntu.com/search?keywords=dir2ogg&searchon=names&suite=all&section=all). It supports setting the quality (the relation between quality and bitrate is somewhat complicated depending on the source material) which IME works better than setting bitrate.

---

### Post by cascade9 on 2010-10-14
> **size_XXM said:**
> You might want to check out [dir2ogg]("http://packages.ubuntu.com/search?keywords=dir2ogg&searchon=names&suite=all&section=all"). It supports setting the quality (the relation between quality and bitrate is somewhat complicated depending on the source material) which IME works better than setting bitrate.

With .ogg vorbis, setting quality is the same as setting bitrate. They are VBR files- well, unless you use a switch to make them CBR, but dont do that.

---

### Post by size_XXM on 2010-10-14
> **cascade9 said:**
> With .ogg vorbis, setting quality is the same as setting bitrate. They are VBR files- well, unless you use a switch to make them CBR, but dont do that.

Not quite, the resulting bitrate will be affected by acoustic complexity of the recording, frequencies contained, etc so there's no clear quality-to-bitrate mapping. For an extreme example, encoding CD audio with quality=4 will result in a vorbis file at 128-160 kbps, as opposed to an 128kbps mp3 or FM radio source, which would hardly be over 100kbps. oggenc allows for bitrate-targeted encoding (see the -b option), but this is not what dir2ogg does.

---

### Post by cascade9 on 2010-10-14
True enough, there is no exact quality-to-bitrate. As far as I know, setting quality works the same as setting bitrate, but I've been out of vorbis for a long time (sorry, I moved to flac), things may have changed. 

BTW, that sort of thing isnt just from the quality of the source. I've used the same quality setting (or was it bitrate? I forget) and got very different bitrates from different CDs, depending on the style of music, etc. Quieter, or 'cleaner' tracks compress more, noisy or 'dirty' tracks dont compress so well.

---

