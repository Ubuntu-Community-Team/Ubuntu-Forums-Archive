---
title: "Ubuntu-restricted-extras not working"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by Andy06 on 2009-05-10
So I installed the package ubuntu-restricted-extras in 9.04 but it did not load the microsoft fonts or Java. It seems to have loads the codecs for .mpeg,.avi,.mp3 and flash plug in though.

So what gives? Why hasn't it loaded java and the fonts? I restarted multiple times.

---

### Post by Didius Falco on 2009-05-10
> **Andy06 said:**
> So I installed the package ubuntu-restricted-extras in 9.04 but it did not load the microsoft fonts or Java. It seems to have loads the codecs for .mpeg,.avi,.mp3 and flash plug in though.

So what gives? Why hasn't it loaded java and the fonts? I restarted multiple times.

Hi,

Go into the **Synaptic Package Manager** and search for **ttf-mscorefonts-installer** and **sun-java6-bin**. If they are marked in green, they are installed, if not, install them.

Regards,

Didius

---

### Post by gandaran on 2009-05-10
> **Andy06 said:**
> So I installed the package ubuntu-restricted-extras in 9.04 but it did not load the microsoft fonts or Java. It seems to have loads the codecs for .mpeg,.avi,.mp3 and flash plug in though.

So what gives? Why hasn't it loaded java and the fonts? I restarted multiple times.
java is no longer included in ubuntu-restricted-extras package but the microsoft fonts are, if the ubuntu package is installed then the fonts must also be.
to install java just go to synaptic and mark sun-java6-plugin for install and click apply, all other java packages will be pulled along and installed with the plugin.

---

### Post by Didius Falco on 2009-05-10
+1 gandaran - I forgot about the plugin.

Regards,

Didius

---

### Post by Andy06 on 2009-05-11
Neither Java nor the fonts were installed. 
I checked synaptic already, they aren't marked in green. They are also not marked in the simpler add/remove app.

How did you find out that Java is removed? Blog and news? Or is says so somewhere? Coz the ubuntu -restricted-extras package still mentions java as a part of it so is there any way to push forward a recommendation to update it? I went mad installing and reinstalling on a dozen comps just because it would not show.

Also Microsoft fonts (ttf-mscorefonts-installer) did not install either.

I know how to do them separately, but the point is why did it not do it automatically? I sat and watched the details pane of the installation whilst installing restricted extras and it made no mention of the things it did not install. So it's definitely not just a bug where it installs them but fails to mark them as installed.

Thank you very much

---

### Post by gandaran on 2009-05-11
> **Andy06 said:**
> Neither Java nor the fonts were installed. 
I checked synaptic already, they aren't marked in green. They are also not marked in the simpler add/remove app.

How did you find out that Java is removed? Blog and news? Or is says so somewhere? Coz the ubuntu -restricted-extras package still mentions java as a part of it so is there any way to push forward a recommendation to update it? I went mad installing and reinstalling on a dozen comps just because it would not show.

Also Microsoft fonts (ttf-mscorefonts-installer) did not install either.

I know how to do them separately, but the point is why did it not do it automatically? I sat and watched the details pane of the installation whilst installing restricted extras and it made no mention of the things it did not install. So it's definitely not just a bug where it installs them but fails to mark them as installed.

Thank you very much
to find out which packages are part of the ubuntu-restricted-extras meta package check ubuntu-restricted-extras properties in synaptic, you will notice that sun-java is not listed anymore.

---

### Post by durand on 2009-05-11
Java isn't a restricted package anymore because it's open source now. Not sure about mscorefonts.

---

### Post by Andy06 on 2009-05-14
Problem is that Java runtime environment is still listed under the description in both Synaptic and Add/remove. They should probably update that. Is there any way to remind them?

It's not really a bug so no go at launchpad

---

