---
title: "Video Card install HELP!"
date: 2011-08-24
forum: New to Ubuntu
---

### Post by Greg Mueller on 2011-08-24
I have an Intel D945GCNL motherboard and I am trying to install an Asus EN8600GT card.

I put the Asus card in and I get a black screen.

Take the card out and everything works.

The Mbrd has a built in video display. Do I need to disable that first or somehow tell it to disconnect? How? (It makes trouble shooting tough when you can't see anything)

Is there something in the Bios I need to set?

The monitor is a 19" Samsung 193P.

I have tried hooking it to the new card with a digital cable and also using the analog cable with a digital adapter. Either way it does not work.

If I leave the card in and connect to the onboard video plugin using an analog cable it does not show anything and the monitor "goes to sleep".

Just a single monitor nothing tricky.

Can someone help?

---

### Post by I8NY on 2011-08-24
well you tried hooking the monitor to the 8600GT with different ports / adapters.  the next thing to try is uninstall all video drivers before inserting the card then see if it works.  current intel drivers may blocking the new card from working.  if that still doesn't work try the card in another pc and maybe try a different monitor.  if all that fails you may need a RMA.

---

### Post by GWBouge on 2011-08-24
> **I8NY said:**
> uninstall all video drivers before inserting the card

This is always a good step (assuming you have any video drivers installed), but from what you've said, I'm guessing the black screen occurs long before any drivers are loaded.  First I would check your BIOS ... there may be a settings to enable accelerated graphics (can't think of exactly what it's called, but mine has that option, even though there's no on-board graphics ...)

---

### Post by Greg Mueller on 2011-08-24
I have looked under "Additional Drivers" under Administration and it shows "No proprietary drivers are used in use in this system"

Is there another way to tell?

---

### Post by dozycat on 2011-08-24
The computer is passing post? did you heard anything?

---

### Post by gandaran on 2011-08-24
check the BIOS if is it has an option to disable the onboard video card, the new one should just about work with the default open source driver but you will have to install the nvidea drivers from additional drivers.

---

### Post by Greg Mueller on 2011-08-24
I just looked at the Bios and here is what I have

Video Configuration

DVNT MODE             <**DVMT**>

                       DVMT
                       Fixed
                       Both

IGD DVMT MEMORY        <**128MB**>

                         32MB
                         64MB
                        128MB
                        Maximum

PRIMARY VIDEO ADAPTER         <**AUTO**>

                               AUTO
                               Int Graphics (IGD)
                               Ext PCIE Graphics (PEG)
                               Ext PCI Graphics 

Pretty sure I should have it set at **Ext PCIE Graphics (PEG)** but I'm a bit paranoid about setting it to something which might not give me any graphics at all and I will not be able to see the BIOs to put it back.

It is a PCIE card with 256MB on board.

I can't tell if it's getting past the POST as there is no video output at all. It does not beep or make any other noise

---

### Post by GWBouge on 2011-08-24
> **Greg Mueller said:**
> Pretty sure I should have it set at **Ext PCIE Graphics (PEG)**

PEG, that's it.  I'm surprised Auto doesn't pick it up, but yes, PEG should make it look at the PCIe graphics slot.

---

### Post by Greg Mueller on 2011-08-24
Ok I changed the BIOS settings and I am getting video, **BUT NOW IT WANTS A PASSWORD**

It has been so long since I have had to do this that I can't remember a user name. I do remember the password that I use to do administrative things, but not a use name.

White letters on a black screen


HELP!

---

### Post by dozycat on 2011-08-24
It is the same password, you must had login without password.
All you need to remember is the user login.

---

### Post by Greg Mueller on 2011-08-24
Can't remember the user name. I've been trying everything I can think of.

Is there a way to reset both?

---

### Post by Greg Mueller on 2011-08-24
What a mess

I guessed my user name and password and am now at a command prompt

How to get Ubuntu going?

---

### Post by Greg Mueller on 2011-08-24
Pulled the card out and turned it back on and now I am back to where I was. Everything works and no passwords or all the rest of the BS.

I'll never do that again

---

### Post by dozycat on 2011-08-25
I know it's late but did you tried the computer with graphic card and live cd?
Did you checked the logs, they are located in /var/log check Xorg.
But sometimes when you get new hardware is easier to install from zero, that's why I ask about the live cd, usually you can check how will the system will work from a fresh installation.

---

