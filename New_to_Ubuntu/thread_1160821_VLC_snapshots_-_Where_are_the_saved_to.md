---
title: "VLC snapshots - Where are the saved to???"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by RandomP on 2009-05-16
So I decided to take a snapshot while watching a video. The thing is, it did not save to my pictures file or the documents menu as far as I could tell. It saved apparently to here: (My Username here)/.local/share/vlc-vlcsnap-74646.png.

Can anyone tell me where I can find these snapshots?

---

### Post by cosine352 on 2009-05-16
> mv (My Username here)/.local/share/vlc-vlcsnap-74646.png ~/Desktop
you can find it in you desktop then.


or you can use the 'print screen" to get the snapshot and save it where ever you want.

---

### Post by RandomP on 2009-05-16
Yes, but I do not see it on the desktop.

I know how print screen works, but I cannot find the ones I took using the snapshot option...

---

### Post by cosine352 on 2009-05-16
I found them at ".local/share/vlc" folder.

---

### Post by andrew.46 on 2009-05-17
Hi RandomP,

> **RandomP said:**
> So I decided to take a snapshot while watching a video. The thing is, it did not save to my pictures file or the documents menu as far as I could tell. It saved apparently to here: (My Username here)/.local/share/vlc-vlcsnap-74646.png.

Can anyone tell me where I can find these snapshots?

The file will be in $HOME/.local/share/ according to your information here, although I suspect a typo and perhaps $HOME/.local/share/vlc/ might be the correct location. This is a 'hidden' directory courtesy of the '.', have you enabled 'show hidden files'? Control + h will usually do this.

Mind you there will be a setting in vlc that allows you to place these snapshots *wherever* you want. I attach a screenshot to illustrate this. My version  vlc is 1.0.0 rc1 so perhaps you version will look a little different but the option *will* be there.

All the best,

Andrew

---

### Post by RandomP on 2009-05-21
Thanks, that helped me out.

---

