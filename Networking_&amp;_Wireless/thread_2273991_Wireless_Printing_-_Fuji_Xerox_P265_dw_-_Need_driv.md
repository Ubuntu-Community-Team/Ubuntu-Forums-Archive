---
title: "Wireless Printing - Fuji Xerox P265 dw - Need drivers"
date: 2015-04-16
forum: Networking &amp; Wireless
---

### Post by rich1912 on 2015-04-16
Was unsure where to post this thread exactly.

I am trying to connect my PC to my Fuji Xerox P265 wireless printer. Ubuntu is able to locate the printer on the network but is unable to find the correct drivers.

Please help.

Rich

---

### Post by gordintoronto on 2015-04-17
Do you have reason to believe there is a Linux driver for that printer?

---

### Post by pdc on 2015-04-17
Gordon has pinpointed the issue for you: Fuji do not provide linux drivers;

Fuji do say your very excellent printer is google cloud ready; so you might find that the best way to go [http://www.google.com.au/cloudprint/learn/howitworks.html](http://www.google.com.au/cloudprint/learn/howitworks.html)

---

### Post by rich1912 on 2015-04-23
PDC I thank you for your suggestion. It did occur to me to try and take advantage of google cloud printing and found this application [https://www.niftiestsoftware.com/cups-cloud-print/](https://www.niftiestsoftware.com/cups-cloud-print/)
which *"allows any application which prints via CUPS to print to Google Cloud Print directly"* and means I do not need to print from Chrome to print via google cloud

Figured I'd share it here as others in the same position may benefit

---

### Post by ben-winding on 2015-06-16
Hi rich1912,

I recently bought the same computer and am having trouble installing it on my Ubuntu 14.04 machine.

Could you please explain how you got it working?

I hooked it up to wifi, installed the **cups cloud print **and linked it to my account but no success. It freezes whiles installing the **guten-print** drivers, (seems like a common problem), See the attached screen shots from the steps I took.

is that what you did? 

Cheers,
Ben

---

### Post by ben-winding on 2015-06-18
I meant the same *printer* by the way, the [B]Fuji Xerox P265 dw

[/B]It works using the USB cable and installed **gutenprint** drivers, however it cannot be added and accessed over the network using the wifi router.

When I ping the printer's IP address, nothing returns.

How can I see the printer in the *Add printer* dialogue, but not be able to ping the IP?

---

### Post by ben-winding on 2015-06-18
Good News!

I finally got it working over wifi too. My problem was that the printer used a static IP which didn't match the router's gateway mask (I'm new to computing)

To fix I just checked my IP using the wifi router:

My IP = 10.0.0.8

Then using the **Fuji Xerox P265 dw **LCD panel.

Networking > WiFi > IP address

Change (tediuosly) from the default 169.254.12.34 to 10.0.0.anything

Hope this helps someone, as they are a nice quality cheap printer.

Cheers

---

