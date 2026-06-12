---
title: "myth tv configuration procedure"
date: 2010-01-29
forum: New to Ubuntu
---

### Post by Pikku_pekka on 2010-01-29
Dear All!

I have recently installed Ubuntu linux 9.10 version. I am very satisfied with this operational system.
However, I have problems with the configuration of myth TV backend:
 I have Asus My Cinema P7131 TV tuner card. The configurational program recoginses it. The tuner is connected to cable television. My problem with the configuration lies in the adjustment of the  video source ( I have selected the television setting) . I must have configured something in a wrong way, because I get the following error message when I want to leave the backend configuration: Card 1 (Type Television) is set to Start on Channel Please add, which does not exist. The other difficulty arises when I want to scan for channels that the program refuses to do.

Thank you for the help  in advance!

---

### Post by gslug79 on 2010-01-29
Hello,

You will probably get more responses if you post this question in the mythbuntu forum: [http://ubuntuforums.org/forumdisplay.php?f=301]("http://ubuntuforums.org/forumdisplay.php?f=301")

The error you are getting on exiting mythtv-setup is due to the fact that the tuner must be set to start on a particular channel - and this channel doesn't exist.

I see that your tuner is analogue. I don't have any experience of using these cards, only DVB-T, but I suspect your problem lies in selecting the correct type of card. Options to try could include "Analogue V4L Capture Card" and "MJPEG Capture Card". Try a few and see if any work.

Good luck

---

### Post by Pikku_pekka on 2010-01-30
Thank you for the advice. I will try out the possibilities!

Regards 
Laci

---

