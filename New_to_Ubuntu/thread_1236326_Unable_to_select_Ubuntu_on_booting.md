---
title: "Unable to select Ubuntu on booting"
date: 2009-08-10
forum: New to Ubuntu
---

### Post by johnexpgn on 2009-08-10
I was inspired by Jason Whittaker's article in PC Advisor on linux/ubuntu to load the system via the DVD.
After installing I rebooted the computer and as stated the choice of ubuntu and windows XP comes up. However when I try to use the up & down keys to select ubuntu they do not work and I get windows XP by default after 5secs.The up and down keys work fine in my windows applications.
How can I get it to work and can I also start the system from the ubuntu folder in the C drive?

---

### Post by drunk-wolf on 2009-08-10
are you using a USB keyboard?, if so try a ps2 one, I had a similar problem, appearently it doesn't enable USB until after a certain point during boot, also try hitting the up arrow to select Ubuntu instead of down.

---

### Post by mapes12 on 2009-08-10
> can I also start the system from the ubuntu folder in the C drive? If you have the option to launch into Ubu and windoze come up at boot time then it sounds to me like you have installed Ubu as a dual boot configuration in which case you shouldn't have a Ubu folder on your windoze C:\ drive?

OR did you set up Ubu via a Wubi installation?

Each works with your system differently. Have a look at this if all this seems gibberish:  [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

---

### Post by johnexpgn on 2009-08-12
Yes I did install via a wubi installation and I do have a usb keyboard.
I am also unable to get into Bios.

---

### Post by anaconda on 2009-08-12
> **drunk-wolf said:**
> are you using a USB keyboard?, if so try a ps2 one, I had a similar problem, appearently it doesn't enable USB until after a certain point during boot, also try hitting the up arrow to select Ubuntu instead of down.

I had the same problem, and I repaired it by changing a setting from BIOS. If I remember correctly it was enabling legacy USB support (or some other USB support)

The thing was that the USB keyboard worked in BIOS, but not in grub, and again worked when the system had started... PS2 keyboard worked also

---

### Post by johnexpgn on 2009-08-12
Thank you for your suggestions!
I will try a ps2 keyboard and see what happens. Are there any particular disadvantages to a ps2 keyboard?

---

### Post by johnexpgn on 2009-08-13
I have tried ps2 keyboard and it now works in bios and ubuntu. Thanks to everyone for your help with that.
However I seem to arrived at another problem.
Having clicked on ubuntu the system installed itself and rebooted and then asked for a user name and password. 
I have not yet registered a user name and password as I recall during the initial downloading process. 
Any ideas how I can set this?

---

### Post by anaconda on 2009-08-13
there are no disadvantages with ps2-keyboards, EXCEPT, new machines dont have an ps2-socket any longer, and most wireless keyboards come with only USB option...

to your another problem, you can boot to recovery mode (you will have admin rights in recovery mode), and then reset your password. If you cant do it from command line, then you can just type: 
startx 
and you will be in graphical environment.

EDIT:
ANd the USB keyboard would work just fine in grub if you enable it from BIOS.

---

### Post by johnexpgn on 2009-08-13
Everything now working ok!!

Many thanks!

---

