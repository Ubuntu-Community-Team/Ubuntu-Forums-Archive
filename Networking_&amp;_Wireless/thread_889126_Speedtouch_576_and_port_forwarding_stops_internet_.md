---
title: "Speedtouch 576 and port forwarding stops internet connection working at all"
date: 2008-08-13
forum: Networking &amp; Wireless
---

### Post by TimGS on 2008-08-13
I am trying to figure out how to set up my Mum's internet connection such that I can ssh in from elsewhere (this will hopefully make her IT support service - thats me - have an easier job). I have configured Firestarter to allow SSH from anywhere.

She has a Speedtouch 576. There appears to be an option "assign a public I.P connection to a specific device" which seems to me should do the job of port forwarding. Enabling this however unfortunately results in her connection no longer working. "sudo ifconfig" indicates that it is connected, and that eth0 is successfully bound to a valid IP address from her ADSL provider. However attempting to use a web browser fails, as does a simple ping to elsewhere on the internet.

Plugging my laptop into the Speedtouch instead works fine.

It just seems that this option successfully binds the IP address of the router to her desktop, but renders it blind in the process. Any other machines are unaffected.

There is also a 'Game and Application Sharing' section where you can assign an application i.e. SSH, to a particular machine on the LAN. Doing this has no effect - it neither works nor stops anything else working.

I can SSH to localhost, so the server is functioning.

Suggestions gratefully received, even if they are along the lines of 'throw away the modem and get another'.

-- Tim.

---

### Post by Ryan450 on 2008-08-14
> **TimGS said:**
> I am trying to figure out how to set up my Mum's internet connection such that I can ssh in from elsewhere (this will hopefully make her IT support service - thats me - have an easier job). I have configured Firestarter to allow SSH from anywhere.

She has a Speedtouch 576. There appears to be an option "assign a public I.P connection to a specific device" which seems to me should do the job of port forwarding. Enabling this however unfortunately results in her connection no longer working. "sudo ifconfig" indicates that it is connected, and that eth0 is successfully bound to a valid IP address from her ADSL provider. However attempting to use a web browser fails, as does a simple ping to elsewhere on the internet.

Plugging my laptop into the Speedtouch instead works fine.

It just seems that this option successfully binds the IP address of the router to her desktop, but renders it blind in the process. Any other machines are unaffected.

There is also a 'Game and Application Sharing' section where you can assign an application i.e. SSH, to a particular machine on the LAN. Doing this has no effect - it neither works nor stops anything else working.

I can SSH to localhost, so the server is functioning.

Suggestions gratefully received, even if they are along the lines of 'throw away the modem and get another'.

-- Tim.

Alright if I were you I'd skip the "Assign public IP address to a specific device" bit altogether, and just go with internal addressing for computers behind the router. The biggest reason is that this gives you another layer of firewall for added protection, and it makes port forwarding much easier.

Then assuming you have a usual private address for the internal (192.168.0.100 for example). You'd go to your game application and manually port forward ssh to her internal ip address.

The only other thing is to ensure that fire starter isn't stopping the connection. Should let you ssh into that machine no problem.

---

### Post by TimGS on 2008-08-14
Working now - ta! No idea why this had no effect yesterday...

I have indeed dumped the "Assign public IP address to a specific device" part, and used the Game and App sharing option.

-- Tim.

---

