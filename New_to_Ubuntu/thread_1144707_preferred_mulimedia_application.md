---
title: "preferred mulimedia application"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by Messyhair42 on 2009-05-01
under system>preferences>preferred applications>multimedia there's a custom option. i would like files such as .avi and .mkv to open in VLC by default b/c currently when i click it defaults to totem which never has the right codecs and i always have to force quit the app.

---

### Post by Bucky Ball on 2009-05-01
Click custom and in the command line type:

vlc

Not sure if that is the correct command to run it, but you need to enter the command that will get it to run from a terminal.

* Update: After a quick check, that looks like the command. Type vlc, try to open something that normally opens in Totem (know what you mean, never use it) and let us know. :)

---

### Post by Messyhair42 on 2009-05-01
i made the command change and i just tried to normally open an .avi file, opens movie player, and it tells me "error occured...following decoders...MP3...XVID MPEG layer 4"

---

### Post by Bucky Ball on 2009-05-01
Ah ha. Have you added Medibuntu repository to your sources? This contains many third-party codecs and applications, which is why you need to add it manually (will also add skype to Synaptics along with a bunch of other things). If your okay with that:

[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories]("https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories")

Add the version for 9.04 and the keyring and you should be good to go after updates.

Regards Bucky (alias Messyhair48!)

---

### Post by Messyhair42 on 2009-05-01
i've got medibuntu enabled. but some things still aren't opening in vlc, i've got run in terminal checked and the custom option under multimedia.

---

### Post by Bucky Ball on 2009-05-01
Uncheck run in terminal. Not right.

---

### Post by Messyhair42 on 2009-05-01
still no change

---

