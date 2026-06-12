---
title: "How do I change my login sound on lucid"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by Legendary_Bibo on 2010-05-23
I can't stand that god awful clicking drumming noise and I've been working on a complete Okami theme so I have a sound file I want to use. It's a 9 second mp3 and it's 230 kb, will that work? So how would I go about this?

---

### Post by Copperline on 2010-05-23
Hi - I'm afraid I can't stand the login sound either...I liked it at first but turned it off after a couple of days! I believe there are two places to change the login sound:

one via  administration-->login window-->accessibility

the other is  preferences-->sound-->sounds.

The sound won't work if it is too long and Ubuntu won't recognize it...around 10 seconds should be fine.

Copperline

---

### Post by jerenept on 2010-05-23
Please help us!!!
I want to change the login sound too! 
I wonder if there is a gconf setting... will check it out.

---

### Post by Legendary_Bibo on 2010-05-23
I don't have a login window option, I have a login screen, but that's only to change automatic login, and I can't find it in synaptic or the ubuntu software center. I also don't have that option in sound. I only have sound effects, input, output, and stuff like that.

---

### Post by Silent Warrior on 2010-05-23
It might take a bit of doing, but I think you'll be happiest with setting up your own sound-theme. I think they reside in /usr/share/sounds. Study the available sets to see what filenames are used, fill out your themes accordingly, put them in their own directory, and copy it to where the other soundsets are - you'll need to do this as root, of course. This should also survive an online dist-upgrade.
The easier way is to copy your replacement log-in sound into an existing soundset, but you'll probably have to repeat this with every new Ubuntu-release. I think you'll have to use OGG for this method, though.

Oh, for the first method: Open the Sound settings-thingy and set it to use your fresh soundset. Not necessary for the second method, if you copied your replacement into the set already in use.

---

### Post by Legendary_Bibo on 2010-05-23
Well I know where the login sound is by looking at the startup applications, but it says it's an executable file so I'm confused as to what I should make the sound file.

---

### Post by Legendary_Bibo on 2010-05-23
Oh just follow this guide. It worked like a charm. Remember to convert your sound to .ogg

[http://titotheman.wordpress.com/2009/11/06/changing-startup-sound-in-ubuntu-9-10-karmic/](http://titotheman.wordpress.com/2009/11/06/changing-startup-sound-in-ubuntu-9-10-karmic/)

---

### Post by philinux on 2010-05-23
> **Legendary_Bibo said:**
> Oh just follow this guide. It worked like a charm. Remember to convert your sound to .ogg

[http://titotheman.wordpress.com/2009/11/06/changing-startup-sound-in-ubuntu-9-10-karmic/](http://titotheman.wordpress.com/2009/11/06/changing-startup-sound-in-ubuntu-9-10-karmic/)

Anyone following that remember it's gksudo for graphical apps.

---

### Post by Legendary_Bibo on 2010-05-23
> **philinux said:**
> Anyone following that remember it's gksudo for graphical apps.

I used sudo nautilus and it worked.

---

### Post by CharlesA on 2010-05-23
> **philinux said:**
> Anyone following that remember it's gksudo for graphical apps.

+1

> **Legendary_Bibo said:**
> I used sudo nautilus and it worked.

You can use sudo, but it's generally safer t use gksu when using graphical apps due to permissions and whatnot.

---

### Post by rworloma on 2010-07-05
Read this post at [Liberian Geek]("http://www.liberiangeek.net/2010/07/disableturnoff-startup-booting-sound-ubuntu-10-04-lucid-lynx/")

---

