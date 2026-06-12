---
title: "lap top not booting up"
date: 2011-02-20
forum: New to Ubuntu
---

### Post by stick747 on 2011-02-20
Hi I have installed 10.10 on laptop but wont boot up, have also burned a cd and still wont boot. Cd works fine on my desk top. Any ideas?

---

### Post by Hedgehog1 on 2011-02-20
Would you provide more information on both the laptop (manufacturer, model number and such).

Exactly how far you get when running the LiveCD on the laptop?

What are the things you saw on the screen?

Are you stopping at flashing cursor, or something else?

---

### Post by stick747 on 2011-02-20
Toshiba L650
Model # PSK1JA-078017

yes its stopping at the flashing cursor

---

### Post by Hedgehog1 on 2011-02-20
OK - I think I am following now.

Your installed OK, but get that flashing cursor after the install.

Please do this:

Press <shift> during a reboot (without the CD installed) to see the GRUB menu.

Arrow down and select Ubuntu with (recovery mode), and press enter/return.

Once the menu comes up (after lots of text scrolls by) arrow down to the 'failsafeX' (Run in failsafe/graphic mode) and hit enter/return.

You will then get options to run in low graphics mode for one session, or to reconfigure graphics.

Select Reconfigure your graphics, click [OK].

Select the default (Generic) configuration, click [OK].

If your see the GUI - think means that the drivers the update loaded for your laptop are not compatible with the video 'card' in the laptop.

Please let us know if you are able to see the screen following the above steps.

:KS

---

### Post by Bucky Ball on 2011-02-20
Press shift to get to grub menu then follow stage 2 here and see if it works:

[http://ubuntuforums.org/showthread.php?t=1612648](http://ubuntuforums.org/showthread.php?t=1612648)

You need 'acpi=copy_dsdt' at the end of your kernel line. 10.10 has the Toshiba patch compiled with it. This previously needed to be done manually by OP. ;)

---

### Post by Hedgehog1 on 2011-02-20
And I keep learning, too!

Thanks Bucky Ball!

:popcorn:

---

### Post by stick747 on 2011-02-21
No joy,
Message is : GNU GRUB version 1.98+20100804-5ubuntu2
miinimal bash-like line editing is supported. for first word, tab lists possible command completions. Anywhere else tab lists possible device or file completions
grub>

This is the only screen I can get now and I have to power down to get out of this.

---

### Post by Hedgehog1 on 2011-02-21
> **stick747 said:**
> No joy,
Message is : GNU GRUB version 1.98+20100804-5ubuntu2
miinimal bash-like line editing is supported. for first word, tab lists possible command completions. Anywhere else tab lists possible device or file completions
grub>

This is the only screen I can get now and I have to power down to get out of this.

A little more info here - was this from the:

  'acpi=copy_dsdt' 

or from the 'Select the default (Generic) configuration' suggestion?


You gotta help us help you...

---

### Post by stick747 on 2011-02-21
Ok 
Power up computer, comes to windows boot manager, select ubuntu netbook and comes up with message on previous post with cursor flashing. Pressing the shift key dosn't change any function.

---

### Post by Hedgehog1 on 2011-02-21
Perhaps another forum member will have better luck helping you.

---

### Post by Bucky Ball on 2011-02-21
Windows boot manager? It should be coming up with grub (which should be written to MBR) which is where you would perform Stage 2 of the link I gave you earlier ...

Scroll to the Ubuntu entry and hit 'e' to edit it ...

---

### Post by stick747 on 2011-02-21
Thanks for trying, maybe Ill try and remove it and start again.

---

