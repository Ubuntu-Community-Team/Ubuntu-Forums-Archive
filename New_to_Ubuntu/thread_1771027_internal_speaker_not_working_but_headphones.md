---
title: "internal speaker not working but headphones"
date: 2011-05-29
forum: New to Ubuntu
---

### Post by nicolai_hel on 2011-05-29
Hi All,

I just registered to the forum. I apologize if I missed a similar thread. I am using ubuntu 10.04 lucid on my vaio laptop. I have been using only this O.S. for a quite while without any problem. However, today I was watching a web-based video, then speaker sound got lost. When I tried my headphones, I was able to listen again. 

Now, after trying many other solutions like editing the following path and cheking that nothing is muted in alsamixer, I gave up and decided to post something here.

sudo gedit /etc/modprobe.d/alsa-base.conf 


Hope someone can help me fix this.

Thanks in advance, 
Nick

---

### Post by Allavona on 2011-05-30
I have an Acer Aspire and my sound card took a dump a year or so ago. The first thing to go was the internal speakers, followed two weeks later by the jacks - input and headphone. 

But no trouble at all, thanks to USB sound devices.

On another note: Is there a 'POP' from the speakers when you first turn on the computer followed by a whine type noise that fades once the OS starts to load?

---

### Post by nicolai_hel on 2011-05-30
Well, hope my sound card is OK. Normally, while restarting brand logo appears on the screen with sound, it is not popping up any sound either.

Any other solutions?

---

### Post by Allavona on 2011-05-30
You could right click the speaker and choose sound settings. Once this is up see if you have the correct hardware selected and on the output tab make sure you have the same type selected. Go back to hardware tab and choose test speakers.

If your getting sound through your headphones though your card may be fine. Your internal speakers just may simply be blown.

---

### Post by nicolai_hel on 2011-05-30
In hardware tab, it says 
"internal Audio"
1 output/ 1 input
Analog stereo duplex

and in output tab;

internal audio analog stereo is chosen.

There is no test my speaker button in "hardware".

I am not sure if the speakers are blown or not! When I was trying to remove and re install alsamixer, I faced with the following error;

Errors were encountered while processing:  alsa-driver-linuxant

Thank you very much anyway for the effort to help me on this

Nick

[IMG]file:///tmp/moz-screenshot-2.png[/IMG][IMG]file:///tmp/moz-screenshot-3.png[/IMG]

---

