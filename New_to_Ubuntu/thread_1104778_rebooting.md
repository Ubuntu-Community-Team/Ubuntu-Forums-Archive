---
title: "rebooting"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by Stinja on 2009-03-23
hey, I installed ubuntu on my macbook yesterday and have been playing around with it and whatever. I can shutdown the computer fine and then turn it on again using the power button. But what I cant do is restart. I click restart and it shuts itself down and starts to reboot, but when it starts to turn on it stays frozen at a grey/blue screen and it beeps(which is no longer does because I got rid of the drivers or something that has the computer tell the speakers to make noise when certain things happen or w/e. Getting that back on might fix my sound problem(sound doesnt work for anything) but thats another story. any help would be appreciated. ;)

---

### Post by humphreybc on 2009-03-24
Have you tried going into virtual console (ctrl+alt+F2), logging in and then typing sudo reboot to restart from there?

---

### Post by Stinja on 2009-03-24
no difference.

---

### Post by Milky The Brown Cow on 2009-03-24
thats very odd - im not very familiar with macbooks, but i would assume that everything that has to do with booting the computer up to the MBR (post, bios etc) would be firmware built into the computer. Did you try using the live cd before installing ubuntu? and if so did you reboot/have this problem? 

again, i've barely handled mac computers, but i assume there are similarities between them and PCs. How far does your computer get when rebooting? You are going to need to explain the stages, as im unfamiliar, but i would assume there is a screen you get when you first turn on the computer (probably the apple symbol), and if it is anything like a PC an option to hit a key to go into boot options and/or bios options. If it makes it past this initial screen, and then gets hung up on the next step, it is having trouble recognizing something in the master boot record. Try rebooting with all usb/firewire appliances unplugged and see if it gets past it. If not, then i think its a solid bet that your computer is not recognizing something when it gets to the MBR. But you say this only happens when you reboot. I would have to assume then that since the computer (should) go through the same motions whether it is booting from reboot of from powered off, that when the computer reboots it doesnt completely shut off power to the ram, and some module in the ram is causing it to hang. 

If all this is true, the only thing i could recommend would be to try installing again. Hopefully you only installed ubuntu recently, and it wouldnt be a problem to back everything up and reinstall, but i think the simplest answer would be a problem during the installation which is causing this hang-up in your booting cycle. Just for kicks, try putting in a live cd and rebooting (you can take the cd out when it prompts you.) This should indicate if there is some program which installed incorrectly which when you reboot is sticking in your ram. Although if the problem *does[I]* [/I]happen at this point it really wouldnt indicate that the problem *isnt* necessarily that, as the same problem can happen with the program from the boot cd. What im looking for is if the problem *does not* happen, then we have a working theory.

Sorry for the extremely long-winded answer, im really bad when it comes to that.

---

### Post by blazemore on 2009-03-24
There is information on Macbooks in the community Wiki.
Maybe you'll find some answers or tutorials there?
[https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)

---

### Post by Stinja on 2009-03-24
hmm are we talking about the same things here? Im talking about just hitting the restart button in ubuntu and getting the problems as stated above.

---

### Post by Stinja on 2009-03-26
bump?

---

