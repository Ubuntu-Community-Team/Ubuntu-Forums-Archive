---
title: "Help with Ubuntu LTSP server + clients"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by alejobar on 2009-06-25
Hi there, I'm trying to have a network with one Ubuntu 8.04 LTSP server and 2 thin clients. I already install the LTSP server following this instructions: [https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall]("https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall")

At the end it said that it will be ready to boot the first thin client.... well how???

The computer that I'm testing have 2 network cards, and both where recognize it at the installation, I choose one to be the acces to the internet. After finishing the installation I connecta a second pc to the other ethernet port, boot the second pc and in set up change to the first boot the network card, save and close, reboot and nothing :confused:

Could someone please please please help me to do this setup?

---

### Post by juanoleso on 2009-06-25
If you haven't already, you should take a look at the links at the bottom of the webpage that you posted.  There is a lot of information there, it seems.

---

### Post by Pom2122 on 2009-06-25
How did you connect the host and client? A regular ethernet cable will not work - you will need a crossover cable or else go through a switch.

---

### Post by alejobar on 2009-06-25
thank you guys for your quick answers, Yes I read the links from the page, let me try using a switch. Just a quick question, from what I understood if I connect a pc without HD and just make it boot from the Network Card everything should work? or I need to install or use somtheing to boot the client pc?

---

### Post by smaclean on 2009-06-26
It should work without a hard drive.

---

### Post by alejobar on 2009-06-26
it worked!!!! Pom2122 you were right, I just need to use a  switch, dumb me!. Now my thin client its working ok, I just have a question, how can I change the resolution?. I can only use 640x480, since I using a KVM to share the screen and keyboard do you think that could be the problem?

---

### Post by Pom2122 on 2009-06-26
Find your lts.conf file. It "should" be in /opt/ltsp/{amd64 or i386}/etc. In the [Default] section try adding (if it's not there) a line:

```
 X_MODE_0 = 800x600

```
or whatever resolution you require. The KVM switch shouldn't make a difference.
:)

---

### Post by alejobar on 2009-06-26
Thanks Pom2122, I found 2 lts.conf files, one at opt/ltsp/i386/etc and the second one at opt/ltsp/i386/usr/shared/doc/ltsp-client-core/examples.
The first one said something about not to modify it or I will have to rebuild the client, so it tells me to create a new lts.conf at var/lib/tftpboot/ltsp/i386/lts.conf

So I copy the example to that location, ad the line you told me in Default, and nothign happened :confused: probably I'm doing something wrong

---

### Post by Pom2122 on 2009-06-26
I've never had a lts.conf file under var/lib/tftpboot/ltsp/i386. I've always modified the first one at /opt/ltsp/i386/etc. I would recommend copying your unmodified lts.conf file to something safe like lts.conf.safe and then adding the line to the original. If it gives trouble then just copy your unmodified file back.
I'm sorry I can't be of more help to you, but I run an ltsp server and 4 headless, diskless clients in **console** mode to run BOINC on. :)

---

### Post by alejobar on 2009-07-02
Thanks for all your help Pom2122 and all, I figure it out, it looks like now ubuntu auto-adjust the resolution when it recognize the monitor, because I tried everything in xorg.conf and nothing work, but I just took the computer and connected to the monitor directly without the kvm switch and now everything works.

Thank you all once again

---

