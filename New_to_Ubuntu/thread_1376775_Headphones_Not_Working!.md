---
title: "Headphones Not Working!"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by gregdwulet on 2010-01-09
Hey everyone,
I have recently installed 9.10 and have run into a very annoying problem.
I plug in my headphones to the computer tower, but sounds play both from the computer's speakers (in the moniter) AND in the headphones. This kind of defeats the purpose of headphones anyway... Apparently, it is because both the moniter and tower have sound cards, and Ubuntu is using both of them to play my music. Is there some way to only use one of the cards to play music only in the headphones?
Thanks,
Greg

---

### Post by Temposs on 2010-01-09
I don't personally know how to fix that problem(but I know some people have had this problem before). A temporary workaround would be to plug in the headphones into the headphone jack in the speakers, if your speakers have one.

---

### Post by daimaru on 2010-01-09
not sure if this will work for you but i am using it with my usb headphones and onboard sound chip. Give it a try if it does not work ... well one can alway try :)
install PulseAudio Device Chooser
```
sudo apt-get install padevchooser
```
open it from apps>sound&video>PulseAudio Device Chooser.  An icon should pop up in your notification are (top right next to date and time in gnome) "left" click it and choose "Volume control" go to the Configuration tab and under Profile choose "off" for  the card that should be disabled. Of couse there has to be 2 cards listed there for this to work. With my computer I have my usb headphones and my internal audio listed there so i can choose one and set it to off.

hope this works but i have the bad feeling that it probably won't since i cant imagine there being a soundcard inside your monitor..

---

### Post by nexes128 on 2010-01-09
Ubuntu sometimes controls the volume of line-out and headphone jack separately if u click on the volume icon and slide it down u should notice the speaker volume go down but not the headphones, if that doesn't work click on volume control and start turning everything down until u get the desired result

---

