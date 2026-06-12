---
title: "How Do I Stop a Computer from Booting"
date: 2010-08-07
forum: New to Ubuntu
---

### Post by EnigmaticCoder on 2010-08-07
How can I cancel startup during the BIOS, grub, or Ubuntu screens? I know that ctrl + delete will reboot, but sometimes I just want to shut it down. I'd rather not have to press the power button.

---

### Post by k3lt01 on 2010-08-07
> **EnigmaticCoder said:**
> I'd rather not have to press the power button.Apart from unplugging it I don't think you have any other option.

---

### Post by presence1960 on 2010-08-07
> **EnigmaticCoder said:**
> How can I cancel startup during the BIOS, grub, or ***_Ubuntu screens_***? I know that ctrl + delete will reboot, but sometimes I just want to shut it down. I'd rather not have to press the power button.

At the Ubuntu log on screen there is an icon which when clicked will give you the options you seek.

---

### Post by EnigmaticCoder on 2010-08-08
> **k3lt01 said:**
> Apart from unplugging it I don't think you have any other option.

Is it okay to press the power button for this purpose without causing harm?

---

### Post by k3lt01 on 2010-08-08
> **EnigmaticCoder said:**
> Is it okay to press the power button for this purpose without causing harm?Yes, the PC will automatically start the shut down process after a short time. Having said that, it isn't a habit I'd get into doing often, you are much better off knowing if you want to start your PC or not before you actually try to start it.

---

### Post by The Cog on 2010-08-08
If you're looking at the BIOS startup screen, there is no harm in just pressing the power button to power off. The problem with using the power button only comes when an operating system has booted enough to start writing to the on-disk filesystems. From then on, just powering off can interrupt in the middle of writing to the disk and leave it in a half-written corrupted state.

---

### Post by oldfred on 2010-08-08
For grub you can add these to 40_custom:

#Blank line for spacer

menuentry " " {
set root= 
}

menuentry "Reboot" {
    reboot
}

menuentry "Halt" {
    halt
}

One user said it did not work for his system but it works for mine. But have not tested with the very newest version.

---

