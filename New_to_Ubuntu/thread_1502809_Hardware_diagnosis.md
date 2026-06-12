---
title: "Hardware diagnosis"
date: 2010-06-06
forum: New to Ubuntu
---

### Post by mattsweegold on 2010-06-06
Hey everybody, recently I have been trying to upgrade from a Compaq SR1750NX to a Dell rig, [http://h20000.www2.hp.com/bizsupport...ctID=c00572530](http://h20000.www2.hp.com/bizsupport...ctID=c00572530), the only problem, however is that there is something wrong with the Dell computer, as it does not allow me to even access the bios. I was wondering if anyone can make any sense out of this occurrence. 
[LIST]
*The hard drive of the Dell was confirmed to be corrupted but  when placed in the Compaq, the bios can still be accessed.
*The Dell used to beep twice at startup but after substituting the Compaq's hard drive instead, the Dell only beeps once. 
*The Dell is able to power on seemingly without problems. 
Also,
*I do not know much about the "insides" of a computer and it is possible for me to have switched plugs of close proximity.
*The Dell hard drive is Sata II where as the Compaq's hard drive is Sata I.
*The power cable that connects the computer to the power surge is not stock but instead belongs to another computer although there doesn't seem to be any problems in compatibility.
[/LIST]
Thanks in advance and I can post pictures if helpful.

---

### Post by an0dos on 2010-06-06
Dell has some fairly good information on their support site that will help troubleshoot problems with their computers. 

Let me get this straight. When you turn on the dell computer with a monitor connected, you get a black screen (no text or pictures), the computer beeps, and nothing happens?

If this is the case, then there is probably a hardware problem unrelated to the hard drive. The BIOS of the dell computer should be accessible even if there is no hard drive installed.

It can take time to figure out hardware problems and fix them.

What model is your dell computer? How did you confirm that the hard drive is corrupted? Have you done anything inside the Dell other than take out the hard drive? Did you buy the Dell used, if so has it ever worked while you have owned it?

Once you figure out the Dell's model number, you should find the user's manual and troubleshooting guide on Dell's support page and familiarize yourself with the names of the different components so that we can communicate clearly.

I won't make any promises that you'll be able to get it working easily. It sounds like you may have a dead graphics card or motherboard.

---

### Post by diablo75 on 2010-06-06
A lot of Dell computers happen to have error code lights on the back, usually four of them side by side.  So it might look like this:

[IMG]http://support.dell.com/support/edocs/systems/op745/en/ug_en/troubl21.jpg[/IMG]

You can read more about them here:

[http://support.dell.com/support/edocs/systems/op745/en/ug_en/trouble.htm](http://support.dell.com/support/edocs/systems/op745/en/ug_en/trouble.htm)

---

### Post by mattsweegold on 2010-06-06
I appreciate the quick replies, and yes the Dell Studio 540 Q9550  displays no image only a black screen. The reason I know the hard drive is corrupted is because when I used the drive on the Compaq, bios reported it as failing. I have not done anything inside the dell, aside from possibly switching some of the clamps that are part of the same cable. (Like switching the black clamp 3 with the black clamp 4 even though the clamps are connected to the same series of wires which then connects to a spot on the hard drive.) The computer itself though was actually my parents. They also did in fact take it to Geek Squad and after which no image has been able to be displayed. Before Geek Squad, the bios was able to accessed about one out of every two startups. As for the lights only have one on the front, and it is a white/blue, and I wasn't able to find the system information on beeps.

---

### Post by an0dos on 2010-06-06
> **mattsweegold said:**
> I appreciate the quick replies, and yes the Dell Studio 540 Q9550  displays no image only a black screen. The reason I know the hard drive is corrupted is because when I used the drive on the Compaq, bios reported it as failing. I have not done anything inside the dell, aside from possibly switching some of the clamps that are part of the same cable. (Like switching the black clamp 3 with the black clamp 4 even though the clamps are connected to the same series of wires which then connects to a spot on the hard drive.) The computer itself though was actually my parents. They also did in fact take it to Geek Squad and after which no image has been able to be displayed. Before Geek Squad, the bios was able to accessed about one out of every two startups. As for the lights only have one on the front, and it is a solid green, and I wasn't able to find the system information on beeps.

The service manual for your computer is located here: [http://support.dell.com/support/edocs/systems/STD540/en/SM/sm_en.zip](http://support.dell.com/support/edocs/systems/STD540/en/SM/sm_en.zip)

You will also want to look at the Dell Technology Guide here: [http://support.dell.com/support/edocs/systems/xlob/dtg/en/en_dtg.zip](http://support.dell.com/support/edocs/systems/xlob/dtg/en/en_dtg.zip) The part that deals with troubleshooting begins at page 273.

Once you download the service manual, you need to unzip it and double-click on "index.htm"

Before you begin doing anything inside the computer, read the "Before you Begin" section of the Dell service manual.

Try re-seating your RAM (taking it out and putting it back in) following the procedure in your dell service manual under the topic of "Replacing Memory Modules".

If that doesn't work (if you don't get any text on your monitor when you turn your computer on), then I think your motherboard is probably toast. In which case, it may be easier for you to just look into getting a new computer than trying to fix the old one. I wouldn't want you to spend lots of money on parts that may or may not fix your problem.

BTW when you are testing the computer, make sure your monitor is turned on and that the cables are connected snugly.

---

### Post by mattsweegold on 2010-06-07
I have recently fixed the problem. As it turns out, aside from the defective hard drive, the main problem was the pci express graphics card (good call An0dos). The computer works now, thanks to everyone for contributing

---

