---
title: "installing new video card"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by mbehrenbrinker on 2009-02-28
Hi everyone i'm new to this so bear with me. i'm putting together an Ubuntu media server for my living room. i have an older P4 3.0 Ghz 2.5 gig RAM with a 1TB SATA HD. I am running ubuntu 8.1. I am Trying to install an ATI Radeon X800xl AGP video card. There is a Linux x86 driver available off of ATI's website that I downloaded and tried to open / install but it will not let me run the install. it says that it can only be done by the "super user." however, I am the only user set up on the computer and i have a user name and password so i believe i should be the super user. is there something else i need to do or how do i make it recognize me as the super user? thanks

---

### Post by robertyou on 2009-02-28
"super user" means you have to use "sudo" in terminal, providing your password to execute the program..

but anyways, can't you install the driver under System -> Administration -> Hardware Drivers?

---

### Post by mbehrenbrinker on 2009-02-28
ok. im not connected to the internet at the moment because i need to get a longer network cable. so i downloaded the driver on my laptop and put it on a zip drive. ill move it downstairs and connect it and see if i can do it that way. thanks

---

### Post by mbehrenbrinker on 2009-03-03
ok so the problem is this. on my computer, it seems that if i install my video card, the integrated VGA out does not put out a signal. so it seems that i would have to install the drivers before i install the video card. so, when i go to system --> administration--> hardware drivers, it does not detect the video card because it is not plugged in therefore i cannot do it that way because i cant see anything on the screen to do an install when i plug in the video card.  so i believe i have to do it through the terminal. i tried to run it through but it was not working. does anyone have any suggestions or advise for me? thanks.

---

### Post by mbehrenbrinker on 2009-03-04
ok so the problem is this. on my computer, it seems that if i install my video card, the integrated VGA out does not put out a signal. so it seems that i would have to install the drivers before i install the video card. so, when i go to system --> administration--> hardware drivers, it does not detect the video card because it is not plugged in therefore i cannot do it that way because i cant see anything on the screen to do an install when i plug in the video card. so i believe i have to do it through the terminal. i tried to run it through but it was not working. does anyone have any suggestions or advise for me? thanks.

---

### Post by robertyou on 2009-03-05
you can refer to this page for installation instructions:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

There are two ways to install it. I suggest you to try the first method which installs driver from Ubuntu repositories.

just follow the guide for 8.04 hardy (it should have no problem applying on 8.10)

---

### Post by robertyou on 2009-03-06
...and did you mean that you try to install the driver when the video card is un-plugged from motherboard? just make sure you did have the video card plugged in, and reboot computer.

I'm pretty positive that ATI's restricted driver should show up in System -> Administration -> Hardware drivers

One more thing, please make sure that you have enabled the intrepid third party software source. Go to System -> Administration -> Software Source and under "Third party software" tab, check all the boxes


if after all this and you still cannot work it out, this website should help greatly to install ati driver manually:[URL="http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_restricted_drivers_.22the_Ubuntu_way.22"]
http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_restricted_drivers_.22the_Ubuntu_way.22[/URL]

---

