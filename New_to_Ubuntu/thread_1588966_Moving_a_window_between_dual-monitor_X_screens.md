---
title: "Moving a window between dual-monitor X screens"
date: 2010-10-05
forum: New to Ubuntu
---

### Post by Barn on 2010-10-05
Hi,
My setup, two (nVidia) video cards on two monitors, currently works perfectly (including all functions of Compiz) except for this: If I have a window on one monitor/X screen, how can I move/drag it to the other monitor/X screen? I have tried TwinView and neither monitor likes it very much. Thanks.

---

### Post by formaldehyde_spoon on 2010-10-05
Enable Xinerama.

---

### Post by Barn on 2010-10-06
I meant Xinerama, sorry. I've been playing so much with it my mind is going, Dave...
From the little I understand, Xinerama lets me treat 2 screens as one very wide screen and then it won't allow me to use Compiz effects like 'rotate cube'. When I tried that I ended up with one lowres display. Might it be true that I can't have a display spread across 2 screens AND Compiz effects? I realise that, normally, trying to drag a window across to the other display will just trigger Compiz to 'do its thing' and rotate the cube or whatever.
Maybe the answer is a little deeper, being able to tell X that the window wants to move from one Xscreen (Xdisplay?) to another. I guess I'm looking for  way to tell X 'This window wants to move from Xscreen0 to Xscreen1'? Maybe I posted this in the wrong forum?

---

### Post by formaldehyde_spoon on 2010-10-06
1. Without Twinview or Xinerama all monitors are seperate screens and cannot interact with each other, except that the mouse cursor can move between them

2. Twinview spans 1 X screen across 2 monitors (but clicking maximize only maximizes in 1 monitor, from memory).  If you only have 2 monitors  the end result is pretty similar to Xinerama.

3. Then there is Xinerama, which is like option 1, except that only one screen has panels and menus, and windows can be moved between screens.

I don't know about Compiz, sorry.

---

### Post by P4man on 2010-10-07
I could be wrong, but I suspect you have to connect both monitors to the *same* videocard. You make use of the second card by enabling SLI (needs a motherboard that supports it).

---

### Post by formaldehyde_spoon on 2010-10-10
> **P4man said:**
> I could be wrong, but I suspect you have to connect both monitors to the *same* videocard. You make use of the second card by enabling SLI (needs a motherboard that supports it).
No, this is not the case, P4man; Xinerama supports what the OP wants, with multiple cards too (I am using it myself with 2 cards). ;)

---

### Post by P4man on 2010-10-10
But why do you want xinerama when you can have twinview?

---

### Post by formaldehyde_spoon on 2010-10-10
> **P4man said:**
> But why do you want xinerama when you can have twinview?
Me or the OP?  I'm using Xinerama because I have 3 screens.

From memory, what you see, and the behaviour you get, with 2 screens is the same whether you use Xinerama or Twinview (although beneath the surface it's quite different, of course) - when I had 2 screens I used Twinview; can't remember why I didn't use Xinerama.

Twinview won't work on two separate cards.

---

### Post by P4man on 2010-10-10
> **formaldehyde_spoon said:**
> 
Twinview won't work on two separate cards.

Sure it does, if you connect both monitors to the same card, and enable SLI to get a performance boost from the second card. That was my point. OF course that does require SLI support from the motherboard, and it does require two similar cards. Never had issues with twinview and compiz.

---

### Post by formaldehyde_spoon on 2010-10-10
> **P4man said:**
> Sure it does, if you connect both monitors to the same card, and enable SLI to get a performance boost from the second card. That was my point. OF course that does require SLI support from the motherboard, and it does require two similar cards. Never had issues with twinview and compiz.
Not really sure what we're arguing about ;) Anyway, the OP will have to use Xinerama.

---

### Post by P4man on 2010-10-10
> **formaldehyde_spoon said:**
> Not really sure what we're arguing about ;) Anyway, the OP will have to use Xinerama.

Why? If he wants to use two monitors sharing a single X session with compiz enabled, it works fine here using twinview. 3D cube and all, and obviously able to drag apps across screens and maximize to a single screen.

I see no reason it would no longer work if I add a second videocard for SLI?

---

### Post by formaldehyde_spoon on 2010-10-10
> **P4man said:**
> Why? If he wants to use two monitors sharing a single X session with compiz enabled, it works fine here using twinview. 3D cube and all, and obviously able to drag apps across screens and maximize to a single screen.

I see no reason it would no longer work if I add a second videocard for SLI?

He already has a second video card, he's already said it won't play nice with Twinview, and when people talk about running two screens from two cards they are usually *not* talking about actually just using 1 card + an SLIed second.

---

