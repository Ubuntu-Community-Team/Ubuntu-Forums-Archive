---
title: "Is there an applet that's just for volume?"
date: 2011-03-01
forum: New to Ubuntu
---

### Post by RichieB07 on 2011-03-01
I don't like the indicator applet because of the Evolution integration and was wondering if there was an applet for just volume.  Or if there's a way to get rid of the Evolution integration since I don't use it (and frankly have it uninstalled on my netbook).

---

### Post by pricetech on 2011-03-01
Right click on the envelope and select "Remove From Panel"

Is that what you want ???

---

### Post by vivek.pandey on 2011-03-01
yes there is an applet just for volume
system->preferences->sound right click attach to panel

---

### Post by Frogs Hair on 2011-03-01
Just tried this and it worked for removing the envelope and leaving the volume.```
sudo apt-get remove indicator-messages
```
```
Killall gnome-panel
```

---

### Post by RichieB07 on 2011-03-01
> **Frogs Hair said:**
> Just tried this and it worked for removing the envelope and leaving the volume.```
sudo apt-get remove indicator-messages
```
```
Killall gnome-panel
```

This worked great, thank you!  I love Ubuntu and it's flexibility, even with applets!

> **neo_aryan said:**
> yes there is an applet just for volume
system->preferences->sound right click attach to panel

This was cool to learn, but I like the functionality of the volume slider, not having to wait for it to load.

> **pricetech said:**
> Right click on the envelope and select "Remove From Panel"

Is that what you want ???

This removes the envelope and the volume icon.

---

### Post by vivek.pandey on 2011-03-01
> **RichieB07 said:**
> 
This was cool to learn, but I like the functionality of the volume slider, not having to wait for it to load.


the best part of that applet is you can increase the volume larger than you can from the sliders.. wat i mean is suppose you maximized the volume using slider you can still increase the volume using sound applet...i like it for watching movies esp when i am not using headphones or external speakers

---

### Post by Frogs Hair on 2011-03-01
> **RichieB07 said:**
> This worked great, thank you!  I love Ubuntu and it's flexibility, even with applets!



This was cool to learn, but I like the functionality of the volume slider, not having to wait for it to load.



This removes the envelope and the volume icon.

Glad it worked , this will not affect notification area messages.

---

### Post by RichieB07 on 2011-03-01
> **neo_aryan said:**
> the best part of that applet is you can increase the volume larger than you can from the sliders.. wat i mean is suppose you maximized the volume using slider you can still increase the volume using sound applet...i like it for watching movies esp when i am not using headphones or external speakers

Makes sense.  I always say do what works for you.  For me I rarely need to do that, as Ubuntu just makes things louder on my laptop than Windows does.

> **Frogs Hair said:**
> Glad it worked , this will not affect notification area messages.

Awesome, good to know!

---

