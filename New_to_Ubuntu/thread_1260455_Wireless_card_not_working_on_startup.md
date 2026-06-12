---
title: "Wireless card not working on startup"
date: 2009-09-07
forum: New to Ubuntu
---

### Post by scorpianato on 2009-09-07
I am not good with titles so I should explain everything if you've expected something else.

Using the internet away from the router and without an ethernet cable isn't an easy thing to do, the laptop's wireless card doesn't work and when I get it to work it may stop working at a sudden moment.

I've found these workarounds but now they don't even work:

1. Plugging in the cable and starting the laptop.

2. Staying by the router and waiting until it is connected before moving away.

3. Doing (1) but then unplugging the cable and hoping it has connected itself.
---

Isn't there a way to get the laptop to connect automatically to the router on EACH startup?
------
I'm not sure what is going on(or if this is relevant) but when the dialogue box to type the password pops on the password typed becomes a long string of random numbers instead.
========================

Information which might help:

The laptop is a 2006 Sony-Vaio model Fz, the exact serial/type is: VGN-FZ106E
2.00 GB ram and processor.

Former OS: Windows Vista...

Current OS: Ubuntu Jaunty Jackalope.

Do I know what am I talking about/Do I have technical skills? No

I've posted it here instead of support because this maybe a simple problem that doesn't need the support forum(And because this post feels like it is not detailed enough)

---

### Post by keplerspeed on 2009-09-07
Is the network SSID hidden? This will be the cause of the issues, hidden wpa2 networks have been trouble on lots of hardware for quite a while.

For example, my workaround is to wait until the network doesnt connect and the box pops up asking for the password again. Press cancel, then right click on network icon and select the network. This connects to hidden ssid wpa2 on my eeepc.

Try to get the SSID to be broadcast (ie non hidden network).

What wireless card do you have, btw? Enter this to terminal to see:
```

sudo lshw -C network 

```

---

