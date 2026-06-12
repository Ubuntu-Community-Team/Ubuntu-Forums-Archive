---
title: "triple boot?"
date: 2011-02-10
forum: New to Ubuntu
---

### Post by vivek.pandey on 2011-02-10
i have dual boot windows 7 with ubuntu 10.10 though i never use windows...i have to practise hacking so as to get my ceh certificate and for that i have decided to use backtrack.... the problem is should i install as the third os making a triple boot or install inside vm in ubuntu..one prob with vm is internet speed decreases? please help

---

### Post by vivek.pandey on 2011-02-10
anybody plz help

---

### Post by amsterdamharu on 2011-02-10
[http://www.backtrack-linux.org/tutorials/backtrack-hard-drive-install/](http://www.backtrack-linux.org/tutorials/backtrack-hard-drive-install/)
I would definetely use manual partitioning and double check the overview before installing.

You can run it off a live CD or live USB or extract the content of the iso to a partition and add a menu entry in grub.

Add it to the /etc/grub.d/40_custom and run sudo update-grub.

---

### Post by perspectoff on 2011-02-10
The methods I like:

Ubuntuguide:
[http://ubuntuguide.org/wiki/Ubuntu:Maverick#Installing_multiple_OS_on_a_single_computer](http://ubuntuguide.org/wiki/Ubuntu:Maverick#Installing_multiple_OS_on_a_single_computer)

Kubuntuguide:
[http://kubuntuguide.org/Maverick#Installing_multiple_OS_on_a_single_computer](http://kubuntuguide.org/Maverick#Installing_multiple_OS_on_a_single_computer)

It takes a tad more effort at the outset, but is the most robust in the long run. It keeps the operating systems (and their respective bootloaders) completely independent.

---

