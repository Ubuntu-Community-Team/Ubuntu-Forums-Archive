---
title: "Wireless Printing Help HP Photosmart"
date: 2010-08-22
forum: New to Ubuntu
---

### Post by djk21108 on 2010-08-22
Hello all. I just purchased a wireless printer from HP.

I am having a bit of an issue making it work with ubuntu. I have the IP address of the wireless printer and it is on my network.

I have installed the hplip application and am able to print with wires.

How do I configure a wireless hp printer?

---

### Post by jonnywombat on 2010-08-22
Going from memory you need to have the printer connected via usb to a windows computer to input the wireless configuration, but it was a while ago when I did mine.

Once you have set up your wireless info then you can do everything via HPLIP toolbox.

---

### Post by jonnywombat on 2010-08-22
There is more info [here]("https://help.ubuntu.com/community/HpAllInOne")... looks like you can configure newer printers directly.

---

### Post by djk21108 on 2010-08-22
> **jonnywombat said:**
> There is more info [here]("https://help.ubuntu.com/community/HpAllInOne")... looks like you can configure newer printers directly.

Thanks for your interest.

I have set it up with the USB cable and have put the printer on my school's network. I'm not sure where to go from there though. Once I unplug the printer I don't know how to start using it wirelessly.

---

### Post by Morbius1 on 2010-08-22
What's the model number of the printer?

---

### Post by djk21108 on 2010-08-22
> **Morbius1 said:**
> What's the model number of the printer?

This is the HP Photosmart Plus. No numbers.

---

### Post by hotrodder on 2010-08-22
Installing HPLIP from HP and not the repos is the better software choice.

You should just have to tell HPLIP that the printer is wireless and everything should work fine.

Print out a set up sheet from the printer to make sure you have the IP address correct.

Make sure that wireless is turned on in the printer set up screen.

Last but not least, make sure the printer has power.

---

### Post by djk21108 on 2010-08-22
> **hotrodder said:**
> Installing HPLIP from HP and not the repos is the better software choice.

You should just have to tell HPLIP that the printer is wireless and everything should work fine.

Print out a set up sheet from the printer to make sure you have the IP address correct.

Make sure that wireless is turned on in the printer set up screen.

Last but not least, make sure the printer has power.

Quick question:

Do I have to be on the same network as my printer? My school has a wireless B and G network and the printer I believe is B only.

Anywho, I know the printer is connected to the network I'm on. I enter the ip address into the add printer utility on Ubuntu. 

When I try to print on it, nothing comes out.

---

### Post by mapes12 on 2010-08-23
Left click your Network Manager icon and enable the printer. Any luck?

---

### Post by mhawkins2 on 2010-08-25
This may or may not be helpful in your specific case it does address HPLIP device setup problems and I just spent 2 days trying to fix it.  I hope I can save others the frustration.

My HP Photosmart C309g-m was working perfectly until it didn't.  The HPLIP device manager could no longer find it.  I removed and reinstalled the software several times from both the HP site and the Ubuntu repositories trying different options.

Finally it was the simple option that fixed it.  If your wireless printer is not found by the device discover in HPLIP, 
1) Open the Device Discovery Dialogue, 
2) Show the Advanced Options, 
3) Select Manual Discovery
4) Enter the IP address of the wireless printer

Note you can get the IP address by using the printer's own control panel to print a status report.

Now my printer and scanner are working again.

I hope this helps others.

---

