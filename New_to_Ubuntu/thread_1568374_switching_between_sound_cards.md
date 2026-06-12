---
title: "switching between sound cards"
date: 2010-09-05
forum: New to Ubuntu
---

### Post by DavidVader on 2010-09-05
Hey! Please help me with this issue. I have two sound cards on my desktop. The first one is set by default cause it's integrated. But I've got another one connected to one of my PCI slots. So how can I turn off the integrated one and switch to the one on my PCI slot?
I don't know the name of the integrated sound card but the one I want to switch to is Creative Sound Blaster 5.1.

Ubuntu Linux 10.04(lucid) x86_64

Thanks.

---

### Post by 101011010010 on 2010-09-05
Hello.
I had a similar problem myself. There are 2 ways that I have found to fix this.
1. Click on the sound icon, select Sound Preferences. Open the Hardware tab, highlight the device that you want to turn off. Click on Settings for selected device and select "off".
2. Open a terminal, Applications/Accessories/Terminal. Type in,> alsamixer Select F6, choose the device that you want (using the arrow keys), press Enter. To finish just push the Escape key and your done. I hope this helps.

---

### Post by candtalan on 2010-09-05
Click on to the sound icon (small loudspeaker shape) and just below the volume adjust you will see 
sound preferences
click on these words and then examine the tabs you see in the window.

 One tab will allow you to chose the non integrated card. It might be the devices or it might be the input, I am not sure, maybe both. anyway this is where it should happen for you.

hth

---

### Post by DavidVader on 2010-09-05
Thank you very much, guys. Although the quality of the sound is quite rubbish. How can I make it 5.1 surround, with a fine quality?

---

