---
title: "Wireless problems with Edgy!"
date: 2006-10-26
forum: Networking &amp; Wireless
---

### Post by newlinuxuser on 2006-10-26
My card worked fine in Dapper, tried to install in Edgy and boom... are the steps I took before the error message.

1. downloaded ndiswrapper 1.8 in XP and usb sticked it over to ubuntu.

2. sudo ndiswrapper -i (My driver)

3. sudo modprobe ndiswrapper   

at the third step I was stopped in my tracks by the message below. I "sudo ndiswrapper -l" i think thats the one and it said both hardware and driver are installed.](*,) 

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

I hear alot of people are having similar problems, its just a shame i had to install windows to get on the net lol after a fresh install of ubuntu. well any help would be great, and im sure many other users are awaiting a resolution as alot of people seem to be getting nowhere, me being one of em.:p 

Mike

---

### Post by cvmostert on 2006-10-26
> **newlinuxuser said:**
> My card worked fine in Dapper, tried to install in Edgy and boom... are the steps I took before the error message.

1. downloaded ndiswrapper 1.8 in XP and usb sticked it over to ubuntu.

2. sudo ndiswrapper -i (My driver)

3. sudo modprobe ndiswrapper   

at the third step I was stopped in my tracks by the message below. I "sudo ndiswrapper -l" i think thats the one and it said both hardware and driver are installed.](*,) 

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

I hear alot of people are having similar problems, its just a shame i had to install windows to get on the net lol after a fresh install of ubuntu. well any help would be great, and im sure many other users are awaiting a resolution as alot of people seem to be getting nowhere, me being one of em.:p 

Mike

Hi there Mike, I have the same problem... I think it might be ndiswrapper that is not installed properly... but looking into it. And you did not have to install win to get the ndiswrapper installs... it is on the desktop cd... just put in the cd and open synaptic and install ndiswrapper... but the problem persists... so something else is wrong.. maby the wrong versions or sth.

---

### Post by squibT on 2006-10-27
:evil: ](*,) 
I installed NDISWrapper using the Edgy instructions and got the same error...WTF <sigh>

---

