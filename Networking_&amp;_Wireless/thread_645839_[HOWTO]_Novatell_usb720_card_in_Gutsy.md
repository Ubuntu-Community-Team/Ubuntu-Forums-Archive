---
title: "[HOWTO] Novatell usb720 card in Gutsy"
date: 2007-12-20
forum: Networking &amp; Wireless
---

### Post by madking on 2007-12-20
So that you do not take months trying to figure it out, and then hit your forehead like i did, i am telling you how to setup your Verizon Novatell usb720.

Start a package manager (synaptic, aptitude, etc.) (note: this guide will give examples using synaptic). Once inside of your manager mark the KPPP package for install. In synaptic you can do this by right clicking the check box next to the package name, and selecting "Mark for Instilation". Then apply the changes. Once they have been applied, you may exit your manager.

Before you begin configuring KPPP, you need to find out what the phone number of your card is. You will need all 10 digits of it (Example: 555-555-5555). Now that you have the number, its time to configure KPPP.

First we need to open KPPP. In the "_L_ogin ID:" field, you need to enter in the phone number without dashes. After the numbers add "@vzw3g.com". In the field "_P_assword" type in "vzw".

Next, click on the "Co_n_figure" button. A dialog box will open up, inside of the "_M_odems" tab. Click on the "_N_ew..." button. Give the card a name, and set the device to /dev/ttyUSB0

Click on the "_M_odem" tab. In there you should see a "_Q_uery Modem..." button. Click it. A dialog box will appear. When it goes away, a new box will appear. If it says that it could not find the card, make sure you booted up with it plugged in. If you did and it gave you the message, then you need to redo the configuration steps, and switch the device to /dev/usb/ttyUSB0. Otherwise you configured it properly.

You may now close the results, and then click "_O_k" button. Now goto the "_A_ccounts" tab and click on the "_N_ew..." button. A window will open up, and you need to choose the "_M_anual Setup" option. A new window will show up, in the first field enter in a name for the connection that is appropriate. After words click the "_A_dd..." button, and type in "#777".

Now you may close the configure window, and click on the "_C_onnect" button.

If all went well..
CONGRATULATIONS!

---

### Post by K.Mandla on 2007-12-21
Moved to Networking and Wireless.

---

