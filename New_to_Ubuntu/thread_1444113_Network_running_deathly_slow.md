---
title: "Network running deathly slow"
date: 2010-03-31
forum: New to Ubuntu
---

### Post by Saito Chikara on 2010-03-31
Hello everyone!

I recently got my Internet upgraded to MAX12 (~12Mb Down / ~500Kb Up) in February. All of february, i was getting awesome download speeds of 500Kb+ on average from the internet. Youtube vids buffered in mere seconds. I upgraded and Updated Ubuntu to it's highest as of about the 20th of February. I noticed a few days into march, my download speed had dropped to ~10Kb. My landlord supplies the Internet, so accessing the router or main hub is impossible, but i'm assured that we're on the same plan. I've also noticed that when running Flash items (vids or games) they tend to become very laggy, very quick. Is there any way to boost my Internet, and my SWF playback?

Thanks!!

EDIT: I was just using my Xbox360, and I downloaded a 1GB file in less than 30 mins, so I know it's my computer going funky.

---

### Post by 2hot6ft2 on 2010-03-31
> **Saito Chikara said:**
> I upgraded and Updated Ubuntu to it's highest as of about the 20th of February.
Does that mean you're running 9.10 or 10.04?

I take it you're on cable. Do you have wifi?
If you're connected by Ethernet, did you set up wireless?

Open a terminal
Applications > Accessories > Terminal
and run
```
ifconfig
```
Look to see if both eth0 and wlan0 have IP Addresses (something like 192.168.x.xxx).
If they both do and you're using a wired connection run
```
sudo ifconfig wlan0 down
```
Your wlan# may be different adjust the command to match it.

Then right click on network manager in the top panel and select Edit Connections
Click on Wireless then your wireless connection then Edit
Enter your password and hit Enter
Clear the check box that says Connect automatically.
Click Apply then Close

It should be better if it was network manager getting confused by there being two simultaneous connections.

You'll have to connect manually to use wifi or re-enable the Connect automatically option.

---

