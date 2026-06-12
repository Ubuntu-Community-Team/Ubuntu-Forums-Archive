---
title: "thin client setup help"
date: 2007-05-10
forum: Networking &amp; Wireless
---

### Post by benner on 2007-05-10
I have been struggling to get a thin client running off of my desktop since dapper and have never been able to sort it out.  i am a teacher with 4 machines running edubuntu in my class and the kids (grade 2) are having a great time with them.  but we have a bunch of old machines that i want to build into a small thin client lab.  i gotta say, without a dedicated forum for edubuntu (our issues and needs can be very different from the rest of the community) and way easier how-to's, i doubt that this project will get very far.  the average teacher is nowhere near able to troubleshoot on a linux box.  anyway, now that i have whined a bit, here is what i have done...

i installed feisty edubuntu desktop edition.  i guess the server edition would have set up everything right out of the box for me but i didn't do it that way.  so i added the package for edubuntu-server from synaptic and for good measure added the lamp server package too.  may come in useful.  i had no idea where to go from there.  read every piece of documentation i could find.  the edubuntu wiki has a how to that was written for 5:10.  i figured it was out of date because every part of the edubuntu server had to be downloaded individually.  i did try the  sudo ltsp-build-client command and as it has every time i have ever tried, ended abnormally after running for a really long time.  i have a second network card.  i have it connected to a hub and i have another machine setup to boot from network that is also connected to the hub.  i assume if i reinstall the server edition it will probably work but if i can't figure it out without reinstalling everything, it still isn't ready for prime time.

can anyone guide me along here?  hopefully this is a no-brainer.  i figure that schools are the place to start in getting more ubuntu users and the edubuntu project could be great but most of the teachers i have worked with absorb computer stuff very slowly.  we need a little hand holding.  can anyone help me out here.  it may take more than a single post for me to get this but i appreciate any help that is offered.  thanks in advance...

---

### Post by chrisblessing on 2007-05-10
Benner,

I just installed my second Edubuntu ltsp lab. My first is running 6.10, while the new one is 7.04. I installed the server edition to a quite powerful pc, and am running 18 thin clients (HP Vectra x310). Because the clients are dual-boot (Windows 98 ), and must remain that way for a while, I had to really fiddle to allow the clients, when booted into Windows 98, to access the LAN/Internet.

I'm pleased with the performance so far, and it truly has breathed new life into our old computers. However, I have a couple of issues I simply have not been able to solve. And, like you, I'm extremely disappointed that there exists no dedicated forum for Edubuntu. In fact, after another fruitless day of trying to get Flash 9 audio work in my new (7.04) lab, I'm about to either downgrade to 6.04 or go back to K12LTSP, a product which I used in the past and which has an exceptionally active support community. You are absolutely correct in pointing out that the LTSP version has unique issues and will require solutions unlike those of the stand-alone.

Ok, I too will stop whining. I will try to help out as much as I can. I am no expert, but I do have two working labs and would be happy to share what I'm able. One thing I do recommend; do a fresh install of only the server edition. If properly installed, the patches should only take you a few minutes, as the current ISO is very up to date. If your clients support LAN booting, set them up to do so, and put them on the same switch as eth1 on your server. Eth0 of the server then goes to your school LAN.

Chris Blessing

---

