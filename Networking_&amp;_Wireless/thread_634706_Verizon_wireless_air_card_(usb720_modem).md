---
title: "Verizon wireless air card (usb720 modem)"
date: 2007-12-08
forum: Networking &amp; Wireless
---

### Post by rick3878894 on 2007-12-08
Verizon wireless air card (usb720 modem)

[IMG]http://ec1.images-amazon.com/images/I/41FYV4rqoqL._SS350_.jpg[/IMG]

I need some help installing this device. From what I've heard this is suppose to be an easy task. 

The thing is I don't know any thing about Ubuntu and not to much about linux.

What I need to know is if there is any software that I need to get and where to get it. 

How to find the information about the hardware and chip sets that I am running. 

How to install new network connections in the network manager. I am use to the fedora/Red Hat network manager.

And any other information that is present. 

I would appreciate some one knowledgeable in the subject explaining exactly what it is that I will be doing to my system to make it run the air card. 

I intend to make a "how to" on this matter once I get it figured out.

Thank you for reading and/or contributing your help.

[RIGHT]Richard[/RIGHT]

---

### Post by madking on 2007-12-20
ok, follow these steps, and you should be good! :)

Note: you need to boot up with the card pluged in. Also make sure you have KPPP installed.

Before you begin configuring KPPP, you need to find out what the phone number of your card is. You will need all 10 digits of it (Example: 555-555-5555). Now that you have the number, its time to configure KPPP.

First we need to open KPPP. In the "_L_ogin ID:" field, you need to enter in the phone number without dashes. After the numbers add "@vzw3g.com". In the field "_P_assword" type in "vzw".  (5555555555@vzw3g.com is an example for you.)

Next, click on the "Co_n_figure" button. A dialog box will open up, inside of the "_M_odems" tab. Click on the "_N_ew..." button. Give the modem a name. Then set the device to /dev/ttyUSB0

Click on the "_M_odem" tab. In there you should see a "_Q_uery Modem..." button. Click it. A dialog box will appear, looking like the first picture below. When it goes away, a new box will appear. If it tells you that it could not find the card, go back to the modems configuration spot, and change the device to /dev/usb/ttyUSB0. Otherwise you configured it properly.


You may now close the results, and then click "_O_k" button. Now goto the "_A_ccounts" tab and click on the "_N_ew..." button. A window will open up, and you need to choose the "_M_anual Setup" option. A new window will show up, in the first field enter in a name for the connection that is appropriate. After words click the "_A_dd..." button, and type in "#777". Give the account a name, and then click ok.

The last step before you try connecting is go into the "M_i_sc." tab, and check all of the boxes, except for the following ones:
Automatic redial on no carrier
disconnect on X server shutdown

Now you may close the configure window, and click on the "_C_onnect" button.

if all went well...
CONGRATULATIONS!!!

---

### Post by compuniversal on 2007-12-21
Check this post i have the same card USB720 and i followed this tutorial and works for me on my laptop and my desktop
[http://ubuntuforums.org/showthread.php?t=343989&highlight=verizon](http://ubuntuforums.org/showthread.php?t=343989&highlight=verizon)

---

### Post by kaziarl on 2008-01-10
RICHARD!!!!!!!!!!!!!! Whats up!

---

