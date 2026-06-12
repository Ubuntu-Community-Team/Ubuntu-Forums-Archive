---
title: "Question about my microphone"
date: 2011-03-09
forum: New to Ubuntu
---

### Post by rradbel on 2011-03-09
I am trying to use a xbox 360 headset on my ubuntu 10.10 laptop. I have a small adapter that lets the headset fit into a standard headphone/microphone jack, but unlike the other computers that i have tried this on, ubuntu does not seem to pick up the headset at all. any ideas would be greatly appreciated. Thanks a bunches.

---

### Post by gekken on 2011-03-09
> **rradbel said:**
> I am trying to use a xbox 360 headset on my ubuntu 10.10 laptop. I have a small adapter that lets the headset fit into a standard headphone/microphone jack, but unlike the other computers that i have tried this on, ubuntu does not seem to pick up the headset at all. any ideas would be greatly appreciated. Thanks a bunches.
  

Click System > Preferences > Sound

 Click Input

????

Profit.

If you've already done this

open a terminal (Applications, Accessories, Terminal)
type in "alsamixer" (no quotes)

depending on your soundcard, you should see something that says "Mic" or "Line-In" or both

in a little box under the bars is there a "MM" ?

if so,

click the arrow buttons to get to that bar, and type the letter "M" it should now show a number representing the volume
hit "Esc"

go back to the sound window, make sure your headphone is properly plugged in and test again.

let us know how that works out!

---

### Post by rradbel on 2011-03-09
> **gekken said:**
> Click System > Preferences > Sound

 Click Input

????

Profit.
Alas, the microphone does not show up in this list, only the built-in speakers.

---

### Post by gekken on 2011-03-09
> **rradbel said:**
> Alas, the microphone does not show up in this list, only the built-in speakers.


OK, follow the alsamixer info I added above.

If that does not work; YOU my friend, have just encountered your first Linux fun-time hardware issue!

[http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)

That is the Alsa Project. (really nice guys, sound nerds....)

There are literally GBs of documentation waiting for you.

Before you lose all hope, what -exact- make/model "adapter" do you have?

---

### Post by rradbel on 2011-03-09
> **gekken said:**
> OK, follow the alsamixer info I added above.

If that does not work; YOU my friend, have just encountered your first Linux fun-time hardware issue!

[http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)

That is the Alsa Project. (really nice guys, sound nerds....)

There are literally GBs of documentation waiting for you.

Before you lose all hope, what -exact- make/model "adapter" do you have?
I went through the alsamixer, the number came up as 00 (I am guessing that is bad). As far as the adapter goes it is just a simple audio jack adapter that adapts a 2.5mm jack to a standard jack. thanks for your help though, I'll be sure to check check out your link.

---

### Post by gekken on 2011-03-09
> **rradbel said:**
> I went through the alsamixer, the number came up as 00 (I am guessing that is bad). As far as the adapter goes it is just a simple audio jack adapter that adapts a 2.5mm jack to a standard jack. thanks for your help though, I'll be sure to check check out your link.

"00" bad? no. that means no volume, turn the volume up.

---

### Post by rradbel on 2011-03-09
> **gekken said:**
> "00" bad? no. that means no volume, turn the volume up.
The volume is up, but I still get no input or output from the headset or any recognition of the headsets existence from my computer.

---

### Post by rradbel on 2011-03-09
I actually think I have made a mistake, the field i was looking at where i found the 00 was not actually for my microphone. the microphone field gives me no such options.

---

### Post by mastablasta on 2011-03-09
Only the headset doens't work or any kind of microphone? if any kind of microphone then your soudn card is likely not propperly recognised by drivers. in that case you will need to add one of the alsa packages so you can configure the card by using the ocmmand
 
sudo alsaconf
 
in the terminal. I don't think this command works by default in 10.10. Perhaps adding the ALSA PPA to your repositories would help.

---

### Post by rradbel on 2011-03-10
That seems to be the problem. I only have one other microphone to test it with though, and that one is a usb as opposed to the audio jack mic. I'll give this a try too, thank you.

edit: I added the ALSA PPA to my repositories, but the alsaconf command still does not work. any ideas?

2nd edit: after updating the alsa packages the mic does actually record sound, but it still does not show up as anything when i got to preferences > sound, but this may very well be good enough for me.

---

