---
title: "Atmel 505a + edgy Module Won't build"
date: 2006-12-19
forum: Networking &amp; Wireless
---

### Post by aka47 on 2006-12-19
Can anyone help

My edgy install does'nt want to build/install/work-out-of-box with the my machines atmel 505a usb wifi adapter (Built in), iwconfig on my OQO does'nt show any wireless interfaces (and the 505a is definitely built in)

Module Assistant fails to build the source and install the module.

It actualy fails at the build phase with unable to open debian/changelog.

I checked the /usr/src etc etc and found that the file does'nt exist only a changelog.template

When I cp'd this template file to changelog the m-a build failed claiming that there was a syntax problem at line 1.

Can anyone offer any asistance with this ???](*,) 

Is it a bug or package omision maybe ?? :confused: 

Cheers
aka47

PS I have tried reinstalling headers, module assistant, atmel source and all the usuals. The listed dependancies are all installed

---

