---
title: "How to show desktop on TV-screen?"
date: 2009-07-18
forum: New to Ubuntu
---

### Post by 2blue on 2009-07-18
My TV has only HDMI connections. I am have trouble connecting my old laptop to the TV-screen, and the laptop has only VGA connections. I have just bought a VGA to HDMI cable and nothing is detected either in the laptop or the TV screen. What could be the problem? In Vista this works automatically, but that is a different laptop.

---

### Post by 2blue on 2009-07-18
Is this usually a bit tricky? I wonder if I might have the wrong cable? I couldn't find VGA to HMDI in any of the stores. I ordered one from Ebay not asking what it usually is used for. In the VGA input on the laptop there is a tiny screen-icon, so I figured this was the right connection? 

I also wonder if I should have a split cable at the VGA-end, but I couldn't find any with only the VGA and one audio plug. The only alternative seems to be a video cable, split four ways; VGA, and three round video plugs. I assumed this wasn't the correct ones. 

Am I making and sense here?

---

### Post by jeppewinther on 2009-07-18
You might have slight difficulties making that connection work, since your VGA port sends out an Analog signal, and HDMI only works with Digital signals.

You say it used to work with a different Laptop? I am assuming you weren't using the VGA output on that one, since that would involve magic or a separate Analog -> Digital converter.
Solutions exist, but they will run you a fair amount of cash.

---

### Post by cariboo on 2009-07-18
Try this command:

```
 xrandr --output LVDS --auto --output VGA --auto --same-as LVDS

```

This command will clone your laptop screen.

For more info on xrandr on a terminal and type:

```
man xrandr
```

---

### Post by 2blue on 2009-07-19
Thank you for the reply both of you. I have not had the chance to try anything further, not until tonight. The new laptop has HDMI to HDMI connection, and that works automatically. There is a VGA in-put too, but I never thought of that until now.

---

