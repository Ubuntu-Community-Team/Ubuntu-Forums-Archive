---
title: "Notification tab"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by jermza on 2010-01-11
I don't know how to ask this, so work with me here.

When a new IM message or email arrives, a little black notification tab appears towards the top right of the screen.  When I mouse over it, thinking that I can click on it (to open the corresponding IM or email), it alphas / becomes transparent.  (Which is odd because you'd think the logical way would be for it to allow me to click on it.)

I then have to click on the mail icon to see where the notification stems from.

This all seems a little tedious. 

Is it supposed to alpha when I mouse over it?  Is there a way to change that so that it can open what its notifying me of?

---

### Post by Temposs on 2010-01-11
The notifications are purposefully designed to not be clicked on. They're supposed to be unintrusive notifications that you can ignore easily if you're working on something. That's why if you mouse over them, they become semi-transparent and you can actually still click on whatever is below them.

The idea is that if you're doing a task, you don't want to be always checking every single message that comes through, disrupting your workflow. Instead, you get to a stopping point in your work, click the notification icon(the envelope), and see what messages you have.

There is not a way to change this behaviour unless you want to do some programming in libnotify.

---

### Post by Paqman on 2010-01-11
> **jermza said:**
> 
Is it supposed to alpha when I mouse over it?  


Yep. That way it doesn't stop you from clicking things under it.

> 
Is there a way to change that so that it can open what its notifying me of?

Nope.

One of the big design choices the devs faced when designing that system (notify-osd) was how to keep people plugged into the stream of information coming to them without letting it disrupt their workflow.

The idea is that notifications are ephemeral. They don't require you to respond if you don't want to, so that you can concentrate on whatever it was before you were doing when it popped up.

---

### Post by jermza on 2010-01-11
That is a very smart concept.  I didn't think of it that way.  I quite like it, now that you've explained it.  Thank you for your prompt answers. :D

This might be off topic...

That little envelope next to the date changes colour when there are messages.  Is there a setting / plugin that adds a little number to it, telling you how many messages you have?  (Like the mail dock icon in Snow Leopard.)

---

