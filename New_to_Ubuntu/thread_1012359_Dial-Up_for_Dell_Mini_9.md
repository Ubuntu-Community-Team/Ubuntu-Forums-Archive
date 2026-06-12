---
title: "Dial-Up for Dell Mini 9"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by drneals on 2008-12-15
Earlier today I posted a question about how to set up a dial-up modem for my new Dell Mini 9.  I followed the directions and tried the DialupModemHowtoSetUpDialer.  It appears that Dell has locked down the System - Administration - Network route so I tried to use the Alternative Way 1 using wvdialconf.  Things looked like they were going well and it found the modem but when I tried the sudo nano /etc/wvdial.conf command it could not find the nano command.  I understand that nano is a text editor but I am new to the Linux world and didn't know how to work around this.  Help!!!

---

### Post by jcsteele on 2008-12-15
replace "nano" with "gedit" - GEdit is a included-by-default text editor that will work on your system. You can also access it from Applications->Accessories->Text Editor

---

### Post by drneals on 2008-12-17
I am still struggling to get my new Dell Mini 9 running Ubuntu 8.04 connected to the internet using a new US Robotics USB Modem USR5637.  The earlier recommendations lead nowhere.  By exploring I found that Network Manager should do the job.  I have been unable to locate any good instructions.  For example: I have the Domain Name Servers but it is not clear to me what format they should be entered into the table. I have a recollection that it should be xxx.xxx.xxx.xxx where the x's stand for a digit.  Is that correct?  Also, there is no provision for a Primary and Secondary DNS address as in Windows. Also there was a 10.0.1.1 in the table. I deleted it.  Why was it there?

Also, in Windows one has to connect to the internet via clicking on buttons.  I have not found such an option in Ubuntu.  Can someone comment on the exact procedure to initiate the dial-up?

---

