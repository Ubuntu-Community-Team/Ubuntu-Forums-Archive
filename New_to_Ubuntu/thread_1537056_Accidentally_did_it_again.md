---
title: "Accidentally did it again"
date: 2010-07-23
forum: New to Ubuntu
---

### Post by JaxM on 2010-07-23
I think I have an idea of how I got to this issue i'm having yet again with the sound being lower than what the volume says. I was trying to fix sound for a new game I got on my computer so I went into Sound Preferences to see what I could do. I went to the Output tab and found that my headset was already selected for the default output. It didn't seem to do anything with the game so I decided to take another look at the Output tab. This time I tried changing connectors (Analog Speakers, Analog Output) I think I had it set to Analog Speakers then changed it to Analog Output which made it sound like someone turning the volume way down suddenly on you. what can I do to pull myself out of this? Do I keep switching connectors or should I pick the Connector I've been using and then restart? All help is greatly appreciated.

---

### Post by cariboo on 2010-07-25
I would suggest you check the volume settings in alsamixer. Just open an Applications->Accessories->Termianl and type:

```
alsamixer
```

Use the tab and arrow keys to make changes, when you are done, press esc to exit, then to save the changes you made type:

```
sudo alsactl store
```

---

