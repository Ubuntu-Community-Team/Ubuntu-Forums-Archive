---
title: "Windows and menus upside down"
date: 2011-01-10
forum: New to Ubuntu
---

### Post by mp87 on 2011-01-10
Hi everybody,

this is the second critical problem I'm experiencing in these days, I hope it's correct to post it on a separate thread.
When I login to Ubuntu 10.10, all the windows and menus are upside down. The problem originated quite unexpectedly, since I didn't modify any graphics card driver.
Sorry if I'm not giving enough informations, please ask me anything.

Thanks,

Mattia

---

### Post by corncob on 2011-01-10
> **mp87 said:**
> Hi everybody,

this is the second critical problem I'm experiencing in these days, I hope it's correct to post it on a separate thread.
When I login to Ubuntu 10.10, all the windows and menus are upside down. The problem originated quite unexpectedly, since I didn't modify any graphics card driver.
Sorry if I'm not giving enough informations, please ask me anything.

Thanks,

Mattia

Sounds like the monitor rotation has gotten changed to "upside down".  Go to System > Preferences > Monitor and change rotation back to "Normal".

---

### Post by gmargo on 2011-01-11
> **mp87 said:**
> please ask me anything.

Please post a picture!

Sorry, just thinking about it has made me LOL.

---

### Post by mp87 on 2011-01-11
> **corncob said:**
> Sounds like the monitor rotation has gotten changed to "upside down".  Go to System > Preferences > Monitor and change rotation back to "Normal".

Hi corncob,

Thanks for the reply.

Sorry, I didn't explain my problem correctly. Actually, it's not the whole screen to be upside down, but just the writings.
I managed to do a print screen (to gmargo's joy ;)), which probably will be more meaningful. Although in the picture only the menus seem to have this problem, also the windows were upside down when I printed it.

Anyway, I tried to follow your hint, but I was unable to find this option under the Monitor window. It could be useful to highlight that when I opened it, it came out this advice:
> It seems that the graphics card driver doesn't support the extensions necessary to use this instrument. Do you want to use the instrument of the driver producer?
I hope it makes sense to you (I translated it from Italian).

-------
Sorry, forgot to mention a part of the reply: if I answer yes to the previous question, it comes out another advice (this time in English):
> You do not appear to be using the NVIDIA x driver. Please edit your X configuration file (just run 'nvidia-xconfig' as root), and restart the X server.

---

### Post by corncob on 2011-01-11
> **corncob said:**
> Sounds like the monitor rotation has gotten changed to "upside down".  Go to System > Preferences > Monitor and change rotation back to "Normal".

Did you get to try this, Mattia?  If it didn't work I was going to say, if somehow the rotation says "Normal" and the screen is still upside down, change the rotation to "Upside Down".  It would be like putting a bandaid over the problem but it beats turning the monitor upside down lol.

---

### Post by corncob on 2011-01-11
Mattia, you were writing at the same time I was.  Did you say "yes" to that advice?  You could look in System > Administration > Additional Drivers and see if there is anything there..

---

### Post by gmargo on 2011-01-11
Wow, thank you.  It's even better now.

It looks like the text is upside down AND reversed.  Is someone playing a prank on you?

---

### Post by mp87 on 2011-01-11
> **corncob said:**
> Mattia, you were writing at the same time I was.  Did you say "yes" to that advice?  You could look in System > Administration > Additional Drivers and see if there is anything there..

If I answer "no" it appears the window you probably referred to, but at the moment (I'm working in recovery mode conditions) there are no options under Rotation except the Normal one.
If I answer "yes" I get the previously mentioned advice. If I enter the "sudo nvidia-xconfig" command into the terminal, it prints:
> Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'
I attached the xorg.conf file to this post.

Anyway, things are getting even more complicated now... It seems that I can no longer access to the "upside down" ubuntu, just the recovery mode still works.

> **gmargo said:**
> Wow, thank you.  It's even better now.

It looks like the text is upside down AND reversed.  Is someone playing a prank on you?

It should be a very expert user, since I work with my notebook only at home. :)

---

### Post by corncob on 2011-01-12
I'm not good at xorg.conf and don't have Nvidia to compare it to.  Maybe someone else could jump in here.
 The next thing I'd try is System > Preferences > Appearance >  Fonts -- and change the Application Font.

---

