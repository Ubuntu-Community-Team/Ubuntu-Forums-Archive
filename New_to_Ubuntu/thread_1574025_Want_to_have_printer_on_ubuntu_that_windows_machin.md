---
title: "Want to have printer on ubuntu that windows machines can print to"
date: 2010-09-13
forum: New to Ubuntu
---

### Post by watson524 on 2010-09-13
Hi all,

I'm a newbie to all of this. I am trying to set up a printer on ubuntu that my other windows machines in the network can print to. I have the printer set up locally and can print from the ubuntu machine (it's 8.04.4 with an HP serial deskjet k80 printer) but I can't seem to print to it from my laptop running Windows. I can map network drives on my linux machine and see and access them from my windows machines so I know that there's some talking between the two.

In windows when I type in the \\ path to the printer on the linux box, it says the server for the printer doesn't have the correct printer driver installed and if you want to search for a proper drive, click ok get the driver and it shows up in the printer list but it says access denied, unable to connect.

And that's where I'm stuck.

Thanks in advance!

---

### Post by avb123 on 2010-09-13
Is it a wireless printer?

---

### Post by watson524 on 2010-09-13
Nope, serial (i.e. about 6 years old). All in one scan/copy/print/fax.

---

### Post by amjjawad on 2010-09-13
> **watson524 said:**
> Hi all,

I'm a newbie to all of this. I am trying to set up a printer on ubuntu that my other windows machines in the network can print to. I have the printer set up locally and can print from the ubuntu machine (it's 8.04.4 with an HP serial deskjet k80 printer) but I can't seem to print to it from my laptop running Windows. I can map network drives on my linux machine and see and access them from my windows machines so I know that there's some talking between the two.

In windows when I type in the \\ path to the printer on the linux box, it says the server for the printer doesn't have the correct printer driver installed and if you want to search for a proper drive, click ok get the driver and it shows up in the printer list but it says access denied, unable to connect.

And that's where I'm stuck.

Thanks in advance!

Would you please simplify it more? I don't really understand from which machine you want to print and which machine can NOT print?

Thank you!

---

### Post by mick222 on 2010-09-13
have you shared your printer go to admin-> printing right click on printer and make sure polices are set to share and access control is set to everyone.

---

### Post by watson524 on 2010-09-13
I can print from the ubuntu machine the printer is psychically hooked up to but can't print from any other machine in the network (all happen to be windows) to that printer.

mick222 - I can't right click on the printer but when I go into printers, it's listed under local. Then on the policies tab I have state = shared checked. On access control I checked "everyone except these users" (and didn't list anyone). And on server settings in printer I have everything checked, share published printers, etc).

thanks!

---

### Post by mick222 on 2010-09-13
have you installed the printer drivers on the windows machine.

---

### Post by watson524 on 2010-09-13
and I need to correct myself, it's parallel, not serial.

---

### Post by uRock on 2010-09-13
Here is a link that explains setting up a network printer, which is what I think you are looking for. [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu) This is what I use on my network.

---

### Post by amjjawad on 2010-09-13
> **watson524 said:**
> I can print from the ubuntu machine the printer is psychically hooked up to but can't print from any other machine in the network (all happen to be windows) to that printer.

thanks!

Fair enough.
If the printer's drivers installed in your other Windows-Machine(s) AND is listed under Printer Folder, then:

Go to Printers (Windows)
Remove the printers
Restart
Go to Printers (Windows) again
and try to add them again

Let's see what could happen!

---

### Post by watson524 on 2010-09-13
I've gotten a bit further, I think:

Here: [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
I followed this:
Ubuntu Client

   1.

      Again go to System -> Administration -> Printing
   2. Click "New Printer" in the upper right. In the next menu select "Windows Printer via SAMBA". Now enter your Ubuntu Samba Print Server (set up as above) IP address in the box on the left titled "smb://". Click the "Browse" button.
   3. Select the printer in the "SMB Browser" window (Click on the little arrows). Once you have selected your printer, check the "Authentication required" and enter your samba user name and password. Then click the "Verify" button. You should see confirmation that the share is available.
   4. Click the "Forward" button and install the drivers for your printer as you would for any other printer. 

Then from here [https://help.ubuntu.com/community/NetworkPrintingFromWinXP](https://help.ubuntu.com/community/NetworkPrintingFromWinXP) I followed the on the windows machine instructions and it seemed to like it better. It let me set it up, said it was connected but when I print a test job from windows, it just says processing and nothing comes out. On the linux box, I look at the status of that printer, and it says processing too. In windows, I bring up printer queue and it says paused but then in the lower right it says error processing command. Doesn't seem to want to print a test page either on the linux box. I picked CUPS+Gutenprint v 5.0.2...

---

### Post by cakie on 2010-10-15
I've got the same problem. My hp deskjet 5550 is connected physically (serial port) to my computer running ubuntu. It prints fine from this computer, but my laptop running windows 7 can't find the printer when I search for it on the network.

All the shared printer settings are selected, but it's still not coming up. I also noticed that the windows computer doesn't recognise that the ubuntu computer is on the network at all. If I go to network and internet -> view network computers and devices in the Window's control panel, the ubuntu computer isn't there.

I'm thinking that if I can get the windows computer to recognise the ubuntu computer, the printer should also work.

(Just so you know, i've only been using ubuntu for about a week, but i do have a little bit of experience with unix, so command lines don't really scare me! ;))

---

### Post by jtarin on 2010-10-15
> **cakie said:**
> I've got the same problem. My hp deskjet 5550 is connected physically (serial port) to my computer running ubuntu. It prints fine from this computer, but my laptop running windows 7 can't find the printer when I search for it on the network.

All the shared printer settings are selected, but it's still not coming up. I also noticed that the windows computer doesn't recognise that the ubuntu computer is on the network at all. If I go to network and internet -> view network computers and devices in the Window's control panel, the ubuntu computer isn't there.

I'm thinking that if I can get the windows computer to recognise the ubuntu computer, the printer should also work.

(**_Just so you know_**, i've only been using ubuntu for about a week, but i do have a little bit of experience with unix, so command lines don't really scare me! ;))And just so you know....entering threads with your own problem and no solution is called hijacking in forum parlance. Please post your specific topic in its own thread about specific hardware so your thread can reach a wider range of forum participants.

---

