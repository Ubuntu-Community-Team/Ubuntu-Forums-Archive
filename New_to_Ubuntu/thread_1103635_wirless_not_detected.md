---
title: "wirless not detected"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by tittiBomber on 2009-03-22
ubuntu is not detecting wireless internet
why is that?

---

### Post by sailthesea on 2009-03-22
What kind of wireless card/USB adaptor are you using?
Oh and which version of Ubuntu?

---

### Post by anewguy on 2009-03-22
Nice to see another new user coming aboard!

First, a very short background:  most manufacturers haven't developed what is called a driver to work in Linux.  A driver is what defines and does the things needed to make a device, such as your wireless work.  But that doesn't mean it won't work - we just need to do a little work first.

We first need more information on your wireless adapter, so we are asking you to do the following:

(1) Open a terminal window.  To do that, look on the top bar of your desktop and you should see "Applications". Click on that, and a drop down menu appears.  On that drop down menu, go to accessories and another menu with pop-up to the side.  On that windows click on "terminal".  This will open a window on your screen with a log in prompt.  Enter your normal userid and press enter, then enter your normal password and press enter.  This will get you to the command line prompt.

(2) Type:

lspci <press enter>

copy and paste that output to a new reply here.

(3) Type:

lsusb <press enter>

copy and paste that output to the same new reply here.

The lscpi [(2)] asks linux to list all the known devices on the hardware PCI buss.  The lsub [(3)] does the same for the USB busses.

This should provide us with the information we need to identify your wireless adapter so we can help you getting a driver installed.

Dave :)

---

### Post by tittiBomber on 2009-08-05
ok sorry haven been on
i believe its a 802.11 wireless LAN card
and the version of ubunto is 8.10 the intrepid ibex

---

### Post by mapes12 on 2009-08-05
> **tittiBomber said:**
> ok sorry haven been on
i believe its a 802.11 wireless LAN card
and the version of ubunto is 8.10 the intrepid ibexOK, but you will need to do what anewguy has suggested for us to help you further please.

---

### Post by tittiBomber on 2009-08-06
thnks for u guyses help but problem seems to have fixed itself

---

