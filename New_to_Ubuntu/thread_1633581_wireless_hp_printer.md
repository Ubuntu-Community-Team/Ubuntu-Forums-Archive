---
title: "wireless hp printer"
date: 2010-11-29
forum: New to Ubuntu
---

### Post by ornothaloapq on 2010-11-29
has anyone else had trouble connecting to a hp officejet 6500A plus? i am a beginner when it comes to wireless printing, any help is appreciated.

---

### Post by TBABill on 2010-11-29
I go to the printer utility, select add printer, select find network printers, wait, click the printer found, follow the screen prompts.
 
Where is the process failing for you? Or did you take other steps to configure?

---

### Post by ornothaloapq on 2010-11-29
under find network printer, it asks me to type something into the host field. im not sure what i should type here. this is a printer shared between multiple people and i dont know much about it.i could probably look at the manual if you think it will help

---

### Post by TBABill on 2010-11-29
No you don't have to do all that. Just click "find network printer" and just let it sit there. It is scanning the network although it gives no indication it is doing anything at all. Once it finds it the printer model will actually show up right above where you clicked to start looking for printers. Just let the system run and don't click anything else till it comes up with your printer. Make sure the printer is powered on during the process.

---

### Post by ornothaloapq on 2010-11-29
thanks, i dont think i would have found that without your help but it says there is no printer found at that adress. unfortunatly i am back at square one.

---

### Post by TBABill on 2010-11-29
"At that address"?? You should enter nothing into any block, but rather just let the system search. Unless, of course, that is the default response if it does not see a network printer.
 
Could it be that you are using a printer that is hooked to another computer? Does a Windows wireless computer print on the network, or did it work previously? If it is configured on the network correctly it should see it and identify it as an HP, as well as offer to install the driver.

---

### Post by madjr on 2010-11-29
i think this would make a good [papercut]("http://ubuntuforums.org/showpost.php?p=9150240&postcount=12") to report.

---

### Post by ornothaloapq on 2010-11-29
i believe it is connected wirelessly to a windows 7 laptop and i am not sure if it even configured.

---

### Post by pricetech on 2010-11-29
Find out what the IP of the printer is and enter it in the box.

See if that helps.

---

### Post by aeronutt on 2010-11-29
There may be a better way, but here's how I set up my HP 6480 officejet:

- Bring up synaptic package manager, and make sure hplip is loaded, mine has version 3.10.2
- Install hplip-gui (using synaptic package manager)
- open a terminal, and run "hp-setup", a GUI should pop up. 
- When it asks for connection (I/O) type via the graphical radio buttons; pick the "Network/Ethernet/Wireless network" option. Click next, it should find the printer. 
 
I've used this method for the last few versions of Ubuntu, and the printer and scanner on the 6840 work.

---

### Post by bug67 on 2010-11-29
I've noticed with Maverick I *sometimes* have to turn the printer off and then back on before the printer set up utility will "find" the network printer.

---

### Post by Spektakel on 2010-12-17
So, has anyone managed to get the HP OfficeJet 6500A Plus working in Ubuntu? I'd like to buy one, but can't find any confirmation on full linux/ubuntu compatibility.

---

### Post by dreperk on 2011-05-13
> **Spektakel said:**
> So, has anyone managed to get the HP OfficeJet 6500A Plus working in Ubuntu? I'd like to buy one, but can't find any confirmation on full linux/ubuntu compatibility.
Yes!  It definitely works!  It took less than 2 minutes to install once I installed hplip-gui and ran hp-setup (thanks aeronutt).  It discovered the printer right away and I could scan and print perfectly:guitar:!

---

