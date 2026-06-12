---
title: "Help set up my wireless printer"
date: 2011-01-13
forum: New to Ubuntu
---

### Post by emarkd on 2011-01-13
Hello all,

I've got a Brother MFC-8890DW that I'm trying to print to from my Ubuntu laptop.  It works fine over the network from Windows.  It shows up on my network at 192.168.1.103.

So I click on System > Administration > Printing and select "Add Printer".  The "Select Device" dialog comes up with several general options and within a few seconds, my printer shows up...twice.  I get the following lines:

Brother MFC-8890DW (BRW904CE55FD279)
Brother MFC-8890DW (BRN001BA929796E, 192.168.1.103)

If I select the entry with the IP address, the description comes up as  IPP network printer via DNS-SD with no options.  If I select the other entry, I get a chance to change the host and the queue but they're already filled in.

Selecting either one and clicking forward results in a "Searching for drivers" message, followed by a question on the number of input trays, the chance to rename the printer, and then a prompt to print a test page.

This is where things diverge.  If I select the top entry above, it never prints but I don't get a message.  If I open the print queue, I can see the job with the status:  Processing - Printer warning, but it never completes.

If I select the bottom entry above, I get an immediate error message that says "There was a problem sending document 'Test Page' to the printer" with an option to diagnose, which eventually tells me that the destination printer does not exist.

Help!

--
Mark

---

### Post by Kirboosy on 2011-01-13
Why not click "Find Network Printer" and type the IP in since you know it. It might just work like that. I know I have a Brother 2550DN and if I let Ubuntu auto find it I have the same problem.

(I know I'm being very vague but I'm away from my home network so I can't recreate my steps right now)

---

### Post by emarkd on 2011-01-13
Ok, that works!  Thanks!  I probed that specific IP and it found it as a JetDirect and set it all up correctly, even eventually labeling it as the Brother MFC-8890DW that it is.  I don't really understand what the difference it, but at least it worked.

Now is there any way to get the fax functions to work through Ubuntu?  The windows setup for the printer installs a separate printer called BR-Fax and if I print to that it actually sends it as a fax.

--
Mark

---

### Post by Kirboosy on 2011-01-13
I'm not sure how these work since mine is just a B&W Laser printer and Ubuntu gets the drivers but these should fix your fax

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

Edit: Oh and you can always check the repositories if you don't like building from source! :) (System-->Admin-->Synaptic)

~Drew

---

### Post by Kirboosy on 2011-01-18
Bump? Any progress with the fax end of things?

---

