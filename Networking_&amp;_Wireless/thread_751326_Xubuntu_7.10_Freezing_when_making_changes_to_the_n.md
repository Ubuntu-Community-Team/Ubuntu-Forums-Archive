---
title: "Xubuntu 7.10 Freezing when making changes to the network settings"
date: 2008-04-10
forum: Networking &amp; Wireless
---

### Post by keonne on 2008-04-10
Hi Guys,

 I have Xubuntu 7.10 running at my house no problems

Yesterday i got rid of windows on my dads laptop and replaced it with Xubuntu 7.10. Here is what is going wrong. 

I noticed there is no internet connection. So i go to change the network settings. I turn off 'Roaming Mode' (whatever that is) and put on DHCP. Press Ok. And Freeze.

Proper freeze, not crash. This happens consistently every time.

Any ideas?

Keonne

---

### Post by Eiríkr on 2008-04-10
What do you mean by "proper freeze"?  Is it just the Network Manager app that goes into limbo, or does the whole machine lock up, so that even the Capslock light on the keyboard won't toggle?

Cheers,

Eiríkr

---

### Post by keonne on 2008-04-10
I'm sorry I wasnt specific enough.

The whole machine locks up. The mouse obviously doesn't work and pressing the caps lock key does not cause the light to go on.

---

### Post by Eiríkr on 2008-04-10
Hard lock-ups usually indicate a problem at the hardware or driver level.  Wireless on laptops is a notoriously difficult area for Linux and drivers.  However, I'm afraid I'm no help once things get to that point, so we'll have to ask for someone else to chime in.

Any ideas, anyone?

Cheers,

Eiríkr

---

### Post by keonne on 2008-04-10
Thanks,

 I know wireless and linux can be a pain in the ***. Which is why I am connecting through ethernet.

---

### Post by keonne on 2008-04-11
bump

any ideas anyone?

---

### Post by Iowan on 2008-04-11
If it's freezing up that hard, then checking an error log (or even using CTRL-ALT-F1 to get a terminal) is out of the question.  What kind of card? (**lspci** or **dmesg |grep eth**) - does it work before you change network settings (or is it now locked up tight)?

---

### Post by keonne on 2008-04-11
@ Iowan

Thanks for response. I will have to check what kind of card it is when I get to my dads house.

Basically everything runs fine until I save the changes I made to the network settings. Once I save the changes within 3 seconds the computer locks up. and I need to do a hard restart

---

### Post by Iowan on 2008-04-11
Not making any accusations ;)
what changes did you make???

---

### Post by keonne on 2008-04-11
lol.

It was a fresh install!

I literallt finished installing it. Told my dad how fantastic linux was. Opened FireFox. Noticed the internet wasnt working. Opened network settings turned off Roaming Mode and turned on DHCP. Saved. Froze.

Repeat x 5

For real!

---

### Post by keonne on 2008-04-11
VIA Technologies Inc. VT6102 [Rhine-II]  (rev 74) is the network card

---

