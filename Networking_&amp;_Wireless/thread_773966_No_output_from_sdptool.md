---
title: "No output from sdptool"
date: 2008-04-29
forum: Networking &amp; Wireless
---

### Post by nlippincott on 2008-04-29
I am trying to enable services on a Samsung cell phone using Bluetooth. I am running Hardy, and can successfully connect to the phone by right-clicking on the Bluetooth icon, selecting "Browse...", and choosing my phone. This opens a file browser, and I can transfer files from my phone to my laptop.

Now, I am trying to set up RFCOMM in order to access other services. I am interested in accessing the phone's address book (if possible with this phone, which I am not sure), and eventually use the phone as a modem.

All tutorials and instructions I have found refer to finding a channel number, which must be used when configuring /etc/bluetooth/rfcomm.conf. I have been using this command:

sdptool browse MAC-ADDRESS

However, when issuing this command, I get:

Browsing MAC-ADDRESS ...

with no further output. I have also tried preceding the command with "sudo", and I get the same (lack of) output.

Is the lack of output telling me something? I would assume that I should get something, being that I can connect to the phone and transfer files.

I have also tried both while connected to the phone (for files transfers), and while not connected.

Can anyone offer an guidance? Thank you.

---

### Post by nlippincott on 2008-04-30
Ok. I think I found the information I need, that being the channel number for Dial-Up Networking. But I could never get sdptool to browse my phone.

Instead, I did this:

sdptool search --bdaddr MAC-ADDRESS DUN

It came back with the information on Dial-Up Networking, which I needed in order to proceed with my project.

I thought perhaps that some setting on the phone caused it to not be browseable. I could not find anything, so I am still puzzled by lack of output I continue to experience with "sdptool browse".

In any case, I thought I would post the command that worked for me, in case anyone else if experiencing the same.

---

