---
title: "HOWTO Print remotely through ssh access"
date: 2008-04-29
forum: Networking &amp; Wireless
---

### Post by jhetrick62 on 2008-04-29
I needed to access a remote Linux system that was running a CLI driven application and wanted to be able to print to my remote location.  You could use this to print anything that was created with any type of remote access though as long as you can generate a .ps print file or you can get remote X server access to print directly to the printer.

This will explain how to set up your system so that if you need to access it remotely and need to print, you will be able to do so.

**_Scenario #1 - You have a network print server in your remote location._**

1.  Set-up a printer on your Ubuntu system (Performed this on Gutsy) that is a "jet-direct" type printer and define it as 127.0.0.1 and leave the port as 9100.  Pick the proper printer name and model so that the drivers are correct for YOUR REMOTE PRINTER when it's sent over.  Save these settings.

2.  Next set up your ssh access to forward your remote port 9100 to your remote-print-server-address at port 9100 (unless you are using a non-standard port).  This should work for HP and Lexmark print servers.
> 
ssh -R 9100:192.168.0.100:9100 -l your_username

*In the above, 192.168.0.100 would be my print-servers-address on my remote network.*

3.  If you are using a windows machine to remote access, set the same port forwarding in putty under the SSH > Tunnels section.

4.  Now log into your box.  You should now be able to send a print job to this printer and it will automatically forward it through the ssh tunnel to your remote printer.  I used the following command to test this:

> lpr -P print_queue test_doc.ps

If you prefer to print directly from your application, you will need remote access via VNC or FreeNX simultaneously and that will work also.  I did test this both ways.  Otherwise print all application docs directly to file with .ps extensions and then log in via ssh to print them all using lpr command.


**_Scenario #2 - You don't have a network print server in your remote location and want to use a windows printer from your remote windows machine._**

1.  Set-up a printer on your Ubuntu system (Performed this on Gutsy) that is LPD type printer and define it as 127.0.0.1:10515 and set the print queue name to equal your printer's name in the windows machine locate remotely.  Pick the proper printer and model so that the drivers are correct for YOUR REMOTE PRINTER when it's sent over.  Save these settings.  (I used cups via [http://localhost:631](http://localhost:631) to set this one up but it may work in gnome printer setup)  Even though it doesn't have a space for the port designation on LPD, force it by adding it to the address as listed above.

You can't forward the standard LPD port 515, that is why I picked an alternate of 10515 which worked for me.  Any alternate that you choose may work as long as it's above 1024 I believe.

2.  Next install the "Print Services for Unix" under the Add/Remove software > Windows Components > Other Network File and Print Services section in the Control Panel of Windows XP.  Make sure the service is started.  It's listed as TCP/IP Print Server under the Windows Services controls.

3.  Next use Putty to set up your ssh access and again under the SSH > Tunnels tab, set the remote port forward to be 

> 10515:192.168.0.50:515  (192.168.0.50 will be the address of your windows machine)

You must forward directly to the windows machine so you will need it to either be a static address or check it first every time and modify your forwarding settings.  You must forward it to standard LPD port 515 as that is where the windows service will listen.

4.  Now you can print the same way you did above using the LPR command or you can gain remote access via VNC or FreeNX and print a document to the printer that you set-up in step #1.  It should work fine.


I have tested this both ways.  Command line LPR printing and via FreeNX remote access, opening a OpenOffice Calc spreadsheet and printing to my remote printer's name while also having putty open with my ssh tunneling forwarding the ports.  I don't know how to add the port forwarding to FreeNX or you would not need both open if someone knows that answer.

Hopefully this helps those looking for a solution like this.

Jeff

---

### Post by kevdog on 2008-05-06
With the #1 example -- Can you be a little bit more clear what commands are to be run on the client and remote print server?

Something like
**Server:**

**Client:**

---

