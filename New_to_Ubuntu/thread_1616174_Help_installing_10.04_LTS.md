---
title: "Help installing 10.04 LTS"
date: 2010-11-07
forum: New to Ubuntu
---

### Post by jagb on 2010-11-07
I am new to Ubuntu and looking for help installing it on a laptop

the story so far...

-I have successful setup 10.04LTS on a USB stick 

- I have run Ubuntu from the USB with no issues

- BUT... when I try to install it on to the hard drive if freezes... it gets through all the install options but after I select "Erase and Use entire disk"... and  "Who are you?" account information screen... then at the "Welcome" screen it goes blank (or goes to the purple Ubuntu screen with the white dots) and freezes.


some information 

laptop model: compaq presario V6000, 1800MHz 
Processor: Mobile AMD Sempron Processor 
RAM: 2 GB
Operating System : none (used to be Vista... but been removed)

---

### Post by tkoco on 2010-11-07
> **jagb said:**
> I am new to Ubuntu and looking for help installing it on a laptop

the story so far...

-I have successful setup 10.04LTS on a USB stick 

- I have run Ubuntu from the USB with no issues

- BUT... when I try to install it on to the hard drive if freezes... it gets through all the install options but after I select "Erase and Use entire disk"... and  "Who are you?" account information screen... then at the "Welcome" screen it goes blank (or goes to the purple Ubuntu screen with the white dots) and freezes.


some information 

laptop model: compaq presario V6000, 1800MHz 
Processor: Mobile AMD Sempron Processor 
RAM: 2 GB
Operating System : none (used to be Vista... but been removed)

Sounds like it could be APCI (or is it ACPI?) problems. You may want to try disabling that for your installed Ubuntu.

---

### Post by sandyd on 2010-11-07
> **jagb said:**
> I am new to Ubuntu and looking for help installing it on a laptop

the story so far...

-I have successful setup 10.04LTS on a USB stick 

- I have run Ubuntu from the USB with no issues

- BUT... when I try to install it on to the hard drive if freezes... it gets through all the install options but after I select "Erase and Use entire disk"... and  "Who are you?" account information screen... then at the "Welcome" screen it goes blank (or goes to the purple Ubuntu screen with the white dots) and freezes.


some information 

laptop model: compaq presario V6000, 1800MHz 
Processor: Mobile AMD Sempron Processor 
RAM: 2 GB
Operating System : none (used to be Vista... but been removed)
right after your computer gets through POST, start pressing the ESC key (or shift?).
After the menu displays, press 'e'
at the end of the line (with a space in between) that has "kernel" in it, put in "nomodeset" (without quotes)

---

### Post by jagb on 2010-11-07
Thank you for your reply sandyd

but i need a little clarification

what is do you mean by "get past the POST" ?

---

### Post by jagb on 2010-11-07
thank you tkoco for your reply 

what is APCI/ACPI? and how do i go about disabling it?

---

### Post by sandyd on 2010-11-07
> **jagb said:**
> Thank you for your reply sandyd

but i need a little clarification

what is do you mean by "get past the POST" ?
you know the logo of your computer manufacturer that shows up when you startup your computer?
thats POST

---

### Post by tkoco on 2010-11-07
> **jagb said:**
> thank you tkoco for your reply 

what is APCI/ACPI? and how do i go about disabling it?
 It is another option for GRUB (as pointed out by SandyD). 
POST is the self-test which motherboards do. If all is ok, then the motherboard will typically BEEP once.
GRUB is the Boot Manager used by Ubuntu. It allows the use of over-riding flags to change the behaviour of Ubuntu as it boots up.

So,your procedure would be to listen for the BEEP (or watch the screen), and press the ESC (spacebar?) key as quickly as possible. Then add the flags to the boot up line before pressing ENTER to execute the boot up command. Simple enough, right?

Typically, an option (like ACPI) would be overridden by using NOACPI as a flag.

Hopefully this helps.

---

### Post by jagb on 2010-11-07
Thank you tkoco and sandyd!

success... install completed and my first ubuntu machine is working

---

