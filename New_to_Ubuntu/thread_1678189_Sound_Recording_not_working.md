---
title: "Sound Recording not working?"
date: 2011-01-29
forum: New to Ubuntu
---

### Post by rom3lol on 2011-01-29
I just recently tried to use skype and the other person couldn't hear a word I was saying.
I went into Sound Recording and nothing gets recorded, I think my built it Mic is not working ? How can I get around this?

---

### Post by Nytram on 2011-01-29
It might just be that the mic volume levels are set too low, that was the case on my setup. Try raising the levels in System->Preferences->Volume Control and/or typing **alsamixer** into a terminal.

---

### Post by rom3lol on 2011-01-30
> **Nytram said:**
> It might just be that the mic volume levels are set too low, that was the case on my setup. Try raising the levels in System->Preferences->Volume Control and/or typing **alsamixer** into a terminal.

Wow thanks alot. ```
alsamixer
``` did the job! ):P
Volume Control is not In Preferences ? Thanks alot

---

### Post by Nytram on 2011-01-31
You're welcome. I was using another distro so I got the location of the volume control wrong.. you can get the same effect by clicking on the speaker icon, but you've probably already tried that :)

---

