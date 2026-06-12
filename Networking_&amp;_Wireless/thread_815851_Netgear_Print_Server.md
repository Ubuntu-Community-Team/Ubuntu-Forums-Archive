---
title: "Netgear Print Server"
date: 2008-06-02
forum: Networking &amp; Wireless
---

### Post by Euphorion on 2008-06-02
In our house we have 3 PCs with windows and Ubuntu. In windows I print using a Netgear WGPS606 Wireless Print Server. The Print Server is linked (has to be) to DSL-Router (location Germany). 2 PCs are connected by wireless with the router and one via cable. In windows, I use the netgear utility to attach a Printer to the Print Server. The Utility modifies the Port to which the printer was originally assigned (in all cases USB). In windows all works well and all PCs can print to a selection of 2 printers using the Server. Does anyone know how I can user the Print Server with Ubuntu Hardy 8.04. Netgear do not provide Linux support.

From what I can deduct in Windows is that the Utility redirects (sets up) a TCP/IP Printer connection to the Print Server.

**** Edit Solved ****

In the mean while 08.07.2009 I have solved the problem and have the Print Server up and running with Jaunty. This is how I did it.

1. Gain access to the print server via cable as described in the manual supplied.
2 Log on as administrator
3. Set up a fixed ip address on Server and/or Router e.g. 192.168.1.206. This is to prevent the Print Server from getting different IP address from your DHCP Router which would inhibit the working for we are going to hard code the ip address below.
4. Check in Status the firmware version, if less than V1.0_020 then update the firmware. Firmware can be obtained from the Netgear site, at best the US site.
5. After having setup and or updated then switch off the print server. This is to ensure that the server boots with the new Firmware.
6. Connect Printers to Server and switch on the Printers.
7. Switch on the Print Server. Server is now correctly initialized and we have no spurious data on the interfaces which may inhibit printing. Ensure that the Print Server has a wireless contact to your Router.
8. Logon to Print Server and in Status note which printers are connected to which queue L1 and L2. (LPT1 and LPT2)
9. In Ubuntu go to System->Administration->Printing
10. Select New->Printer
11. Select Network Printer->LPD/LPR Host Printer
12. In Host type in the IP address of the print server e.g. 192.168.1.206
13. In Queue type in L1 (or L2 as required)
14. Confirm Forward
15. Select Printer from List.
16. Select Manufacturer. Confirm Forward
17. Select Driver/Model. Confirm Forward
18. Enter the description for the printer (to your liking) Confirm Apply
19. Confirm Print Test Page.

Ubuntu should now confirm Job Queued and Printing, Print Server LEDs should flashing and printer should start working. I have found that after Ubuntu confirms accepting the print job, it takes several seconds until the LEDs on the Print Server start to flash, but be patient it all works.

Depending upon US or ECE set up the printer properties especially paper size and decide upon which printer should be default.

That's it.

---

### Post by ewan86 on 2010-06-24
> **Euphorion said:**
> In our house we have 3 PCs with windows and Ubuntu. In windows I print using a Netgear WGPS606 Wireless Print Server. The Print Server is linked (has to be) to DSL-Router (location Germany). 2 PCs are connected by wireless with the router and one via cable. In windows, I use the netgear utility to attach a Printer to the Print Server. The Utility modifies the Port to which the printer was originally assigned (in all cases USB). In windows all works well and all PCs can print to a selection of 2 printers using the Server. Does anyone know how I can user the Print Server with Ubuntu Hardy 8.04. Netgear do not provide Linux support.

From what I can deduct in Windows is that the Utility redirects (sets up) a TCP/IP Printer connection to the Print Server.

**** Edit Solved ****

In the mean while 08.07.2009 I have solved the problem and have the Print Server up and running with Jaunty. This is how I did it.

1. Gain access to the print server via cable as described in the manual supplied.
2 Log on as administrator
3. Set up a fixed ip address on Server and/or Router e.g. 192.168.1.206. This is to prevent the Print Server from getting different IP address from your DHCP Router which would inhibit the working for we are going to hard code the ip address below.
4. Check in Status the firmware version, if less than V1.0_020 then update the firmware. Firmware can be obtained from the Netgear site, at best the US site.
5. After having setup and or updated then switch off the print server. This is to ensure that the server boots with the new Firmware.
6. Connect Printers to Server and switch on the Printers.
7. Switch on the Print Server. Server is now correctly initialized and we have no spurious data on the interfaces which may inhibit printing. Ensure that the Print Server has a wireless contact to your Router.
8. Logon to Print Server and in Status note which printers are connected to which queue L1 and L2. (LPT1 and LPT2)
9. In Ubuntu go to System->Administration->Printing
10. Select New->Printer
11. Select Network Printer->LPD/LPR Host Printer
12. In Host type in the IP address of the print server e.g. 192.168.1.206
13. In Queue type in L1 (or L2 as required)
14. Confirm Forward
15. Select Printer from List.
16. Select Manufacturer. Confirm Forward
17. Select Driver/Model. Confirm Forward
18. Enter the description for the printer (to your liking) Confirm Apply
19. Confirm Print Test Page.

Ubuntu should now confirm Job Queued and Printing, Print Server LEDs should flashing and printer should start working. I have found that after Ubuntu confirms accepting the print job, it takes several seconds until the LEDs on the Print Server start to flash, but be patient it all works.

Depending upon US or ECE set up the printer properties especially paper size and decide upon which printer should be default.

That's it.

Thank you worked perfectly for me with my canon mp180 and ubuntu 10.04 installed. I had to follow these instructions [http://ubuntuforums.org/showthread.php?p=9505197#post9505197](http://ubuntuforums.org/showthread.php?p=9505197#post9505197)

to connect to my print server with an ethernet cable and my computer, then followed your instructions and worked perfectly.

Thanks:guitar:

---

### Post by NuahHuan on 2010-09-24
Absolutely Spot on - worked for 2 Windows XP PC's and Ubuntu Netbook Remix with HP980CXi and Brother HL-2030 thank you for taking the time to post this helpful item

---

