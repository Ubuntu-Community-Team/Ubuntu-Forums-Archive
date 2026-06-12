---
title: "Help me save my computer!"
date: 2010-12-26
forum: New to Ubuntu
---

### Post by katiedidit on 2010-12-26
So, I have an Acer Aspire One D250 that has Ubuntu Netbook 10 on it. I was trying to install Sims 3 with Wine and it said that I didn't have a graphic card to run it... and I know that I have one so I was trying to install a driver so it would work and I could play the game.

Long story short, I installed something and now my computer is stuck in terminal?

I tried to just reinstall the whole OS but whenever I put in the USB drive the whole computer just freezes up.

I have no idea what to do from here... someone please help me!

---

### Post by cariboo on 2010-12-26
Check System->Administration->Synaptic Package Manager->File->History to see what you have installed. You can use synaptic to un-install the packages you recently installed.

---

### Post by katiedidit on 2010-12-26
Do you know a code to do that in terminal? It won't let me go to the desktop.

---

### Post by lindel on 2010-12-26
play SIM3 on a netbook ?  i don't think its a good idea. restart your computer and uninstall what you have ever installed.   and you can try enter startx in the termianl.   i hope it can work.

---

### Post by philipballew on 2010-12-26
can you boot into recovery safe graphics mode? press the shift key when your systems loads and grub should come up, perhaps safe graphics mode works and you can check everything that way

---

### Post by katiedidit on 2010-12-26
Startx didn't work and Fail Safe Graphics mode just froze it :(

---

### Post by amjjawad on 2010-12-26
Hello and welcome :)

Don't panic, bad things happened and there's nothing impossible so take a deep breathe and let's start again.

First of all, make sure your machine is set to boot from the LiveUSB.
Your USB must be plugged in before you enter BIOS.
If everything is set, Save, Exit and reboot.

Once your machine will boot from the USB, choose **Test Memory**  (forget the red cursor on this screenshot).

[IMG]http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7132[/IMG]


Let us know what will happen with you.

---

### Post by katiedidit on 2010-12-27
I have it set up to boot from the USB... but when I put it in the BIOS screen freezes up and it won't go to the "Install Ubuntu" thing.

---

### Post by amjjawad on 2010-12-27
> **katiedidit said:**
> I have it set up to boot from the USB... but **when I put it in the BIOS screen freezes up and it won't go to the "Install Ubuntu" thing**.

I'm sorry, I couldn't understand what you mean?!

---

### Post by katiedidit on 2010-12-27
When the USB installer is plugged in the BIOS screen just freezes instead of loading the USB. It just sits there saying "ACER." If the USB is not plugged in it will load to the terminal, but that's about all it does.

---

### Post by amjjawad on 2010-12-27
> **katiedidit said:**
> When the USB installer is plugged in the BIOS screen just freezes instead of loading the USB. It just sits there saying "ACER." If the USB is not plugged in it will load to the terminal, but that's about all it does.

I'm not sure what key you need to press to enter BIOS but in my case, it's F2 on one of my PCs and on the other one it's "Del".

You need to "Enter" BIOS and make sure your machine will boot from USB not just plug the USB and wait :)

I hope I understood your post correctly.

---

### Post by 1v82TIn1 on 2010-12-27
Do you have an external DVD/CD drive?

---

### Post by katiedidit on 2010-12-27
> **amjjawad said:**
> I'm not sure what key you need to press to enter BIOS but in my case, it's F2 on one of my PCs and on the other one it's "Del".

You need to "Enter" BIOS and make sure your machine will boot from USB not just plug the USB and wait :)

I hope I understood your post correctly.


Yeah I did that... I set the computer to boot from the USB. That's what is making it freeze?

---

### Post by katiedidit on 2010-12-27
> **Ryan Brothers said:**
> Do you have an external DVD/CD drive?

No I don't :(

---

### Post by spook1980 on 2010-12-27
how did u install ubuntu on it in the 1st place?

---

### Post by amjjawad on 2010-12-27
> **katiedidit said:**
> Yeah I did that... I set the computer to boot from the USB. That's what is making it freeze?

Try to create the LiveUSB using: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Don't forget to format the USB Drive first.

---

### Post by trinitydan on 2010-12-27
I've had similar issues with my GFs Acer netbook.  It's strange because sometimes if you do what you did it will hang (as you have seen) and you need to select hdd, not USB.  Then other times you can boot with it set to usb.  Try selecting hdd but look for one with a label that sounds like your USB drive, not the actual hdd in the netbook.

---

### Post by 1v82TIn1 on 2010-12-27
Have you tried booting from a different OS?
Something like Windows?

---

