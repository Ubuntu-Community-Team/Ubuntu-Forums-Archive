---
title: "vmware, Open Office together = SLOW, SLUGGISH"
date: 2010-07-13
forum: New to Ubuntu
---

### Post by cwmoser on 2010-07-13
I run Windows XP VM using vmware Player on my Ubuntu 10.04.
Running vmware Player and then opening Open Office Writer causes Writer to become sluggish.  The screen turns gray, cannot scroll the Open Office window.  

When I exit vmware Player, Open Office Writer runs just fine.

I am using Compiz and my video adaptor is nVidia.
I have 6GB RAM memory.
My CPU is AMD Athlon X2 6000+
I have the 64-bit version of Ubuntu 10.04.

Any ideas why these products just do not want to work well together?


Carl

---

### Post by cwmoser on 2010-07-14
Here is a screen recording illustrating this problem:

[www.cerant.com/ubuntu/vmware-sluggish.ogv](www.cerant.com/ubuntu/vmware-sluggish.ogv)

I used gtk-record to make the video.
Note that I have VMplayer running a Windows XP VM.
I open Open Office Writer and open a file.
The screen turns gray.
The screen turns gray when I click on the scroll bars too.

Carl

---

### Post by cwmoser on 2010-08-18
Anyone else note that VMware Player and Compiz causes the screen to go gray and sluggish?

Carl

---

### Post by cwmoser on 2010-08-30
Here is a more accessible link to a video showing this problem - on YouTube:
[http://www.youtube.com/watch?v=rPCSWgUCHgk](http://www.youtube.com/watch?v=rPCSWgUCHgk)

Note that the screen turns gray.

Anyone have any ideas on how to keep this from happening?

What I have to do is always exit vmware player.  I would like to leave it minimized and be able to come back to it when I need it.  

Carl

---

### Post by migs73 on 2010-08-30
I don't know how VM player works but with Oracles Virtualbox you can set the amount of memory your VM uses. If possible try knocking this back a bit to see if it makes a difference.
I would have thought with 6GB you should have plenty though. Vbox warns you if you exceed 50% of your total available memory so I would try to stick below this.
Might be worth disabling you desktop effects to see if it is Compiz at fault also.

---

### Post by cwmoser on 2010-08-31
I'm getting frustrated with VMware.  Is there a utility that will take VMware VM's and convert them to VirtualBox format?

Thanks

Carl

---

### Post by CharlesA on 2010-08-31
Check here: [http://www.ubuntugeek.com/howto-convert-vmware-image-to-virtualbox-image.html](http://www.ubuntugeek.com/howto-convert-vmware-image-to-virtualbox-image.html)

---

### Post by cwmoser on 2010-08-31
Was unsuccessful in converting or importing my Windows XP VMware VM into Virtual Box.

I get the startup menu but it hangs immediately after the count down.

---

### Post by CharlesA on 2010-08-31
Probably due to being run on different "hardware."

:(

---

### Post by cwmoser on 2010-08-31
OK, that makes sense running on "different hardware"

Well, I finally got my VM to work using VirtualBox ... but I cannot get the Networking in the WinXP VM to work either with Bridge or NAT.  My host OS is Ubuntu 10.04 and I am using a Static IP (192.168.0.101).

My WinXP VM shows a 169. IP address and its set up for DHCP but fails to contact the DHCP server.  

In essence, I cannot get networking to work with VirtualBox.

Carl

---

### Post by CharlesA on 2010-08-31
Yah, it's probably due to being run on different hardware. You could check device manager to see if it has any "unknown" devices listed.

What network card does it show is being used?

Also, have you tried setting a static IP?

---

