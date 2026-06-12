---
title: "Totem preferences"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by rmc36 on 2009-03-31
Hi,

(Sorry to repeat this posting. I first posted on the multimedia & video forum)

I have no sound and am using Totem Movie Player Ubuntu 8.04 + Gnome.. 

And when i go to click on Totem's Edit Preferences button it does nothing - and its got an icon on it like a spanner. 

Does that mean its locked and how do i get around this.

Thanks,

Robt.

---

### Post by Sam Lars on 2009-03-31
I'm not sure what icon spanner you're referring to...
Do you get sound from anything else?

---

### Post by rmc36 on 2009-03-31
Yes. I have full system sounds and full you tube video and sounds.

Its like a tiny red thing symbol thingy on it - over the preferences button.

I switched from Kubuntu 8.10 to Ubuntu 8.04 to try and solve the sound and I'm almost there if i can get to the equaliser in Totem.

---

### Post by rmc36 on 2009-04-01
ump..

---

### Post by Sam Lars on 2009-04-01
Could you post a screenshot of what you're seeing?

---

### Post by rmc36 on 2009-04-10
heres the screenshot

---

### Post by irrdev on 2009-04-10
From the screenshot, it appears that you are clicking on the Properties menu. Clicking this displays the current movie's properties, as you can see to the right. Try clicking Edit->Preferences instead of Movie->Properties. Additionally, your Master Sound Icon in the upper-right corner of the screen next to the current time appears to be turned on low; maybe this needs to be turned up a bit.;)

---

### Post by glotz on 2009-04-10
I see you're trying to play a MIDI file. Do other audio file types work?

Do you have **gstreamer0.10-plugins-bad** package installed?

Or you could install the **timidity** package to play MIDI files.

---

### Post by rmc36 on 2009-04-11
> **irrdev said:**
>  > Try clicking Edit->Preferences instead of Movie->Properties.
Thanks. I have tried that. Nothing helpful on the audio tab.


 [QUOTE]your Master Sound Icon in the upper-right corner of the screen next needs to be turned up a bit.;
No - tried that thanks.. didnt do it..

---

### Post by rmc36 on 2009-04-11
> **glotz said:**
> > I see you're trying to play a MIDI file. Do other audio file types work?
Yep. They do work.

[QUOTE]Do you have **gstreamer0.10-plugins-bad** package installed?

Yep. I have got that. 


> Or you could install the **timidity** package to play MIDI files.
Yep. Okay i could try that. Thanks.

---

### Post by taavikko on 2009-04-12
```
gstreamer-properties
```
Let's you fiddle with it's settings (audio/video-output modules)

---

