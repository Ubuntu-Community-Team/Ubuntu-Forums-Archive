---
title: "MTS Mbalze installation error on ubuntu 10.10, since its a 64 bit version of ubuntu"
date: 2011-02-22
forum: New to Ubuntu
---

### Post by rpradeep82 on 2011-02-22
Hi Got a MTB Mblaze data card for the internet connection. Mblaze provides a driver/UI for linux and ubuntu platforms. But when i install that, it gives an error. Error could be because my version ubuntu is 64bits. Can i get a MTS driver/UI for 64bits.
Thanks.

---

### Post by rungss on 2011-09-23
Quite Old Thread with no Answer: If you are having the same problem, the following may help.

Try one of these from [http://ubuntuforums.org/showthread.php?t=1447239]("http://ubuntuforums.org/showthread.php?t=1447239")

1) 
Re: MTS MBlaze
hey,
you don't install the mts software, the driver info is already there in ubuntu 11.04. just plugin the usb into ur comp's usb and .. wait for some time then click on the network icon the top right corner, click on new mobile broadband connection then just follow the steps.. its simple
you will also have to edit this connection after the final steps, the username would be: [email]internet@internet.mtsindia.in[/email] and the password: mts

2) Above didn't work for me as it didn't detect automatically.

a) Make sure usb-modeswitch is installed, try installing from synaptic or command line.
b) Edit Network Connection after inserting your MTS Devise in USB.
c) Goto Mobile Broadband Tab, Add a Connection. You should see MBlaze as a device. select that and follow the wizard.
d) Enter one of the following credentials.

Username: [email]internet@internet.mtsindia.in[/email]
phone: #777
password: mts

Or

Username: [email]mts@mtsindia.in[/email]
phone: #777
password: mts

It hasn't worked for me yet but that's perhaps because my connection is not activated yet.

---

