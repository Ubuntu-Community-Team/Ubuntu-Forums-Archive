---
title: "How do I improve the touchpad function?"
date: 2011-03-19
forum: New to Ubuntu
---

### Post by Torp3x on 2011-03-19
I have a touchpad described in Windows only as 'ALPS pointing device'. It has multitouch functionality so it can do some neat stuff in Windows like circular scrolling, pinch zooming etc.

I'd love to get the multitouch working, but can live without it. What I would like though, is the single click sensitivity improved. Now the touchpad is sensitive enough that it will register movement when a finger is as much as 1mm above the pad, not touching it. However, the single click function; tapping the touchpad once to select a link for example- isn't sensitive at all. Usually I find myself having to click something a few times before it's registered.

I have no problems in Windows so presumably it's a driver issue. Can I get some help in fixing this please? 

Many thanks.

---

### Post by Torp3x on 2011-03-21
Ok so from another thread here, I found and entered this command:

```
echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe
```And now my touchpad works perfectly. What does this code do? Where might I find info on how to alter or create conf files to get multitouch working?

Thanks.

---

### Post by Arijit_Kundu on 2011-03-21
One place to look for it is [here]("https://help.ubuntu.com/community/SynapticsTouchpad"), which is ubuntu documentation.

---

### Post by migs73 on 2011-03-21
You don't mention what version of Ubuntu you are using, I believe multitouch is only available in 10.10 onwards.

---

### Post by Torp3x on 2011-03-21
I'm using 10.10.

The Ubuntu documentation linked to above is for a Synaptics device, nothing in there made any difference for me.

xlisting comes up with this:

```

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Generic Wheel Mouse              	id=11	[slave  pointer  (2)]
```

There's no mention of Alps or Synaptics devices. Has my touchpad even been detected properly? 

It does work, but multitouch would be good as I know it's possible in 10.10.

---

### Post by Torp3x on 2011-03-21
Ok, for anyone interested-

After doing some digging, I've discovered that the Alps touchpad on some modern machines (Sony Vaio E series included) is recognised as a ImPS/2 Generic Wheel Mouse in Ubuntu, and not a touchpad, because the correct drivers aren't yet available. This means that while it's usable, many of the functions don't work (3rd button, horizontal scrolling, multitouch) and the use of the touchpad may occasionally be erratic. 

So the bottom line is, it's not supported in Ubuntu, but apparently is being worked on (Bug #565543).

---

