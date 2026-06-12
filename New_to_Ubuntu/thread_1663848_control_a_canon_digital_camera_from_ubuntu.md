---
title: "control a canon digital camera from ubuntu"
date: 2011-01-10
forum: New to Ubuntu
---

### Post by superprash2003 on 2011-01-10
Hi,
   i would like to know if its possible to control a canon digital camera from the ubuntu shell. Basically i need to take a picture from the canon digital camera while its connected to a ubuntu machine via USB. So running a command or an app from the terminal should automatically click a pic on the camera and i should be able to retreive the pic from the canon's SD card on my ubuntu machine..
   Im not sure if its possible..Any help would be appreciated..
Thanks..

---

### Post by Paqman on 2011-01-10
A digital camera could be tricky, but doing it with a webcam shouldn't be too hard. What exactly are you trying to do this for?

---

### Post by expatCM on 2011-01-10
When you connect a Canon camera via USB, Ubuntu will detect and open a window showing all the files on the Canon memory card or at least the directories holding those files.  

Instead of opening the window you can automatically open Shotwell.  I think Shotwell has settings to scan for attached media and to then update by copying images to a directory, Downloads I think is the default location.

With a bit of experimentation I think you can accomplish what you describe but ...  sadly I do not know all the details...

---

### Post by ndefontenay on 2011-01-10
I don't think you can take a shot with the canon digital camera from linux command line.

You can try looking online for a software that manages to let you do that. But it looks like you set yourself a tough challenge.

---

### Post by superprash2003 on 2011-01-10
@paqman
  its a small script that i plan to run once in a few minutes to know whats happening in a room..
@expatCM
   interesting.. i did try to see if canon would be detected as a scanner..but unfortunately no it doesnt..
@ndefontenay
   Yes.. it does look pretty complicated..

I guess a webcam would be easier to work with.. But the crazy thing is i have a spare digital camera ( an old one this is ) but no spare webcam .. SO i thought i'd put this to some use and besides the quality would be better too.
  I know in windows there is this option using zoom browser's camera window to remote control and take a pic from the pc itself. unfortunately i cant find similar software for ubuntu..
 Thanks a lot everybody for your reply. Any more suggestions/solutions are welcome..

---

### Post by superprash2003 on 2011-01-10
deleted..double post by mistake..

---

### Post by migs73 on 2011-01-10
> **superprash2003 said:**
> @paqman
  its a small script that i plan to run once in a few minutes to know whats happening in a room..
@expatCM
   interesting.. i did try to see if canon would be detected as a scanner..but unfortunately no it doesnt..
@ndefontenay
   Yes.. it does look pretty complicated..

I guess a webcam would be easier to work with.. But the crazy thing is i have a spare digital camera ( an old one this is ) but no spare webcam .. SO i thought i'd put this to some use and besides the quality would be better too.
  I know in windows there is this option using zoom browser's camera window to remote control and take a pic from the pc itself. unfortunately i cant find similar software for ubuntu..
 Thanks a lot everybody for your reply. Any more suggestions/solutions are welcome..

I take it you have tried zoombrowser in wine?

---

### Post by superprash2003 on 2011-01-10
i searched regarding this and it looks like WINE does not support zoombrowser , even if it does it wont really be able to detect the camera via USB..

---

### Post by migs73 on 2011-01-10
When the camera is connected in this mode, I would suspect ti would act as a USB serial device. As such if you could sniff the serial comms in windows (when using zoombrowser to initiate the taking of a photo) you could find out what command actually does this.
Then somebody cleverer than me could maybe suggest a way of getting linux to output this command.

---

### Post by superprash2003 on 2011-01-13
well.. that is possible but a bit difficult to figure out.. Anyways thanks a lot everybody for the replies..

---

### Post by jonathanKingston on 2011-06-03
gphoto2 should be all you need for this... I can't get it to work on my camera but should work for an older one.

---

