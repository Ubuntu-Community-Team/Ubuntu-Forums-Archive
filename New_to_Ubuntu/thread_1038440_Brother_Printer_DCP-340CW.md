---
title: "Brother Printer DCP-340CW"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by Bruv on 2009-01-12
Could someone give me a walk through how I get a printer up and running on Kubuntu.
I have gone so far then have lost the plot somewhere, I don't seem to be able to find any specific information concerning installing printers and the drivers.I did find myself in a wizard when trying to sort it out, but my printer, a Brother DCP-340CW, wasn't listed and then it got confusing.
Thanks for any helping hands out there.
Bruv

---

### Post by HotShotDJ on 2009-01-12
Open System --> Administration --> Synaptic Package Manager
Search for and install brother-lpr-drivers-extra.  After it has been installed (along with dependencies), close the package manager and then REBOOT.

You should now be able to find your printer in the printer setup wizard.

---

### Post by Bruv on 2009-01-12
> **HotShotDJ said:**
> Open System --> Administration --> Synaptic Package Manager
Search for and install brother-lpr-drivers-extra.  After it has been installed (along with dependencies), close the package manager and then REBOOT.

You should now be able to find your printer in the printer setup wizard.

I have Adept installed, using that I installed Synaptic, I did a search but cannot figure out what I am doing wrong.

---

### Post by HotShotDJ on 2009-01-12
> **Bruv said:**
> I have Adept installed, using that I installed Synaptic, I did a search but cannot figure out what I am doing wrong.ARGH!!  That is SO my fault... I gave you Ubuntu instructions even though you have quite clearly indicated that you are running Kubuntu.

You can remove Synaptic... you don't need it. (I'm so embarrassed!)

Use Adept to install brother-lpr-drivers-extra.  The rest of what I said is correct for you.

---

### Post by Bruv on 2009-01-14
No problem....I hope.

---

### Post by Bruv on 2009-01-14
I had downloaded and installed the drivers from Synaptic, but it did not work.
I have since removed Synaptic and purged the files it downloaded.
I now cannot find the Brother drivers with Adept, should I install Hardware Drivers,the program, from the selection on Adept ?

---

### Post by Bruv on 2009-01-14
I don't know how, but I have managed to install my printer.
The 'How to' that talked me through step by step is found[ here]("http://ubuntuforums.org/showthread.php?t=590793&highlight=Brother+printers")
How do get the printer to print emails directly from Thunderbird ?
And finaly what do I do with the LPR and CUPS wrapper files left on my desktop ?

---

