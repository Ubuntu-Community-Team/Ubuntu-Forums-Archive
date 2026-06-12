---
title: "Intrepid choice between On-board HD audio and Hi-Def video?"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by jweaver28 on 2008-12-03
I have an EVGA MOBO with onboard hi-def video (Geforce 7150/Nforce 630i) and audio (Intel/Realtek). When I first installed Intrepid a month ago, I got the audio working, but the video stayed low-res, a problem on a HTPC. Well, installing Intrepid on a different drive and then connecting the pre-existing Vista drive didn't work--Vista kept finding errors on the Intrepid/Linux drive and "correcting" them, degrading the Linux performance. Then I realized that the drive's maker, Seagate, wasn't Linux friendly, and a very large WD drive came on sale for the holidays. So I partitioned it and installed Vista on half and Intrepid on the other.

This time, Intrepid loaded the Nvidia video drivers pretty much off the bat, and even recognized my TV/monitor. Trouble is, I can't get the audio working at all, although it had worked with the other drive four weeks earlier. I've done Ubuntu's sound troubleshooter and installed the HDA Intel sound drivers--first from Alsa, then from Realtek. Not a peep.  

Notice after running  lspci -v at 00:09.0, the sound module shows "access denied". I've also attached results of lsmod and modprobe, which I think strange, but them I'm a noob or newbie! FYI, I am using an HDMI cable, which works for both sound and video under Vista. The prior incarnation of Intrepid taught me that linux required a separate sound jack running to the tv's speakers, but that doesn't work with this clean install. I don't get any sound, even when trying to attach the cable on several different audio connectors. Nothing seems muted. I did try to kill pulse audio per one of the suggestions, but all I managed to do was knock out electricity several miles away (or maybe that wasn't me and my little machine!) I also managed to knock out the sound control once, perhaps when trying to load a song into Amarok, which fyi shows little dancing sound bars but no sound. 

I also don't know whether it matters than this second clean install has another problem: although this is an Intel core processor, I was unable to reload opera and skype, both giving error messages suggesting that I had an AMD64 bit processor. This is an intel system, and googling Realtek suggests that the audio is Intel HDA.

Any suggestions would be appreciated, for I really like Intrepid, but will continue to have to use Vista if I can't get this straightened out.

---

