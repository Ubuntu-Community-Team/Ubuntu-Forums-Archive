---
title: "Sound not going through speakers (amp)"
date: 2011-08-08
forum: New to Ubuntu
---

### Post by bobman321123 on 2011-08-08
My sound card is not responding for ubuntu, what could be the problem?

---

### Post by ~!geek!~ on 2011-08-08
You should provide the specifics about the machine you are using along with the ubuntu version you are using.
Although, you may check the sound settings. To do this:
Click on the volume button you see on panel -> click sound preferences -> hardware tab-> (Remeber the device set as default there and also profile) Now, While playing some music try to select different device ubuntu can find for your machine. You can try selecting other profiles too if it helps.

---

### Post by FormatSeize on 2011-08-08
Not a very in depth description, but I'll go through some things that I've had to do to get sound working. 
 
One time I installed a distro, and couldn't get the sound to work. I thought that it simply would not work with that particular distro. So I uninstalled it. I ended up using the Live CD as a rescue CD, and it turned out that I didn't have the sound turned up in the music player application.
 
Then there was Kubuntu, which would have been a nightmare if you don't know something about jumping through flaming hoops (which Linux will definitely teach you to do, as it is required). First, I have an nVidia card as my main output for sound and video. By default, some incredibly evil programmer thought that it would be delightful if the HDMI sound. This was silly, so I had to go into systems setting and change the priority to my onboard sound driver. Cool. Still, though, no sound. So what I ended up having to do is then activate the sound driver, as it's off by default. This was all done through menus under "Hardware" in Systems Settings.
 
Also, go to System -> Adminstration -> Proprietary drivers (or something like that, I don't know which version you are using, but you shouldn't have much trouble finding it). There, be sure that your hardware is activated.

---

### Post by whitesferry on 2011-08-08
do you have your sound card going into an amp? if so i have seen it where if the amp is on at the time of boot you will get no sound. (i know it sounds crazy but believe me) try various combination's of booting your computer with the amp on and off.

---

### Post by bobman321123 on 2011-09-16
Thanks guys, I'm not totally sure what happened, but it's working perfectly now. (and yes, it was an amp at one time, I'm not sure if that makes a deference.) 
Thanks so much for the help!

---

