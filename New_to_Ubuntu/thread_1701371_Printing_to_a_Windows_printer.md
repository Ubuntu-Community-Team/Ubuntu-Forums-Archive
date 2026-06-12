---
title: "Printing to a Windows printer"
date: 2011-03-06
forum: New to Ubuntu
---

### Post by syntr on 2011-03-06
I've looked up several guides on the internet, but I can't figure out how to do this

When I get to my Printing screen and add "Windows Printer via SAMBA", nothing happens. It freezes for a little bit and then doesn't even show my printer.

[IMG]http://i.imgur.com/qm9gJ.png[/IMG]

My setup is as follows:
Laptop running Ubuntu 10.10 Maverick
Desktop PC running Windows 7 connected to a HP Officejet 6510 All-in-One

Please help :(
I have no clue about SAMBA and the only reason I'm still keeping Windows 7 around is so I can do homrgroup printing...(The other computer isn't mine so I can't put Ubuntu on it lol)

---

### Post by syntr on 2011-03-06
Bump...

---

### Post by Spyderkid on 2011-03-06
all you need to do is this:... (i think)

go to system > administration > printing, then click the big green plus sign. Then wait for the little loading sign in the bottem left of the box to go away and open the network printers tab by clicking the >, then just double click on the printer and folow the instructions (all HP printers are supported i think)

---

### Post by syntr on 2011-03-06
> **Spyderkid said:**
> all you need to do is this:... (i think)

go to system > administration > printing, then click the big green plus sign. Then wait for the little loading sign in the bottem left of the box to go away and open the network printers tab by clicking the >, then just double click on the printer and folow the instructions (all HP printers are supported i think)

My printer doesn't appear :(

---

### Post by syntr on 2011-03-06
Well, whatever xD
Guess I'll just boot into Windows to print every time I have to since Ubuntu provides no good interface to do so

---

### Post by Frogs Hair on 2011-03-06
The Windows live sign in assistant will cause a problem with sharing  if you are using it.

---

### Post by walt.smith1960 on 2011-03-06
This isn't helpful but networked printers sure are handy in mixed windows/*nix environments.  I doubt adding a print server would make sense; a new printer wouldn't cost much more.

---

### Post by syntr on 2011-03-06
> **Frogs Hair said:**
> The Windows live sign in assistant will cause a problem with sharing  if you are using it.

I'm not

---

### Post by syntr on 2011-03-06
> **walt.smith1960 said:**
> This isn't helpful but networked printers sure are handy in mixed windows/*nix environments.  I doubt adding a print server would make sense; a new printer wouldn't cost much more.

Huh? Why would I buy another printer?

---

### Post by papaapa on 2011-03-06
The Windows live sign in assistant will cause a problem with sharing if you are using it.

If i install games for windows is it installed automatically?


It would be helpful if we knew what version of windows was acting as the print server. What problems are you likely to encounter if you enable a version of folder/printer sharing from XP/Me on that machine?

Thank You.

---

### Post by syntr on 2011-03-06
> **papaapa said:**
> The Windows live sign in assistant will cause a problem with sharing if you are using it.

If i install games for windows is it installed automatically?


It would be helpful if we knew what version of windows was acting as the print server. What problems are you likely to encounter if you enable a version of folder/printer sharing from XP/Me on that machine?

Thank You.

Windows 7 is acting as the print server and I followed all of the instructions here: [http://windows.microsoft.com/en-US/windows7/Share-a-printer](http://windows.microsoft.com/en-US/windows7/Share-a-printer)

But I went into System > Administration > Printing > Add > Network Printer > Windows Printer via SAMBA > Browse...

My other computer, "VERA-PC", appears. But nothing else appears under it when I press the triangle and it does not let me hit OK.

---

### Post by syntr on 2011-03-06
bump
no one knows how to make my printer appear on the list?

---

### Post by jimbean on 2011-03-06
i guessing but if you want to share a printer
ive always installed drivers for same printer on both machines {or operating systems}

---

### Post by syntr on 2011-03-06
> **jimbean said:**
> i guessing but if you want to share a printer
ive always installed drivers for same printer on both machines {or operating systems}

ummm....what?

---

### Post by David D. on 2011-03-06
I understand that the printer is attached to a Windows 7 OS computer.  Verify that the printer is set as a shared printer on that Windows computer.  If it not set as shared on the computer the printer is attached to, it will not show up on the list on the Ubuntu machine.  If you do not know how to do this, post back and I will go to my wife's computer and determine the steps (I don't use Windows 7 myself).

---

### Post by Frogs Hair on 2011-03-06
Look this over including the links on the page and the other links as well .[http://www.7tutorials.com/how-access-windows-shared-printer-ubuntu](http://www.7tutorials.com/how-access-windows-shared-printer-ubuntu)

[https://bugs.launchpad.net/ubuntu/lucid/+source/samba/+bug/458637](https://bugs.launchpad.net/ubuntu/lucid/+source/samba/+bug/458637)
[http://us.generation-nt.com/problem-solved-printing-networking-ubuntu-win-7-pc-help-199581601.html](http://us.generation-nt.com/problem-solved-printing-networking-ubuntu-win-7-pc-help-199581601.html)

---

### Post by syntr on 2011-03-06
> **David D. said:**
> I understand that the printer is attached to a Windows 7 OS computer.  Verify that the printer is set as a shared printer on that Windows computer.  If it not set as shared on the computer the printer is attached to, it will not show up on the list on the Ubuntu machine.  If you do not know how to do this, post back and I will go to my wife's computer and determine the steps (I don't use Windows 7 myself).

[IMG]http://i.imgur.com/Umz2A.png[/IMG]
[IMG]http://i.imgur.com/emyoe.png[/IMG]

If there is anything else I need to do, let me know.

---

### Post by syntr on 2011-03-06
> **Frogs Hair said:**
> Look this over including the links on the page.[http://www.7tutorials.com/how-access-windows-shared-printer-ubuntu](http://www.7tutorials.com/how-access-windows-shared-printer-ubuntu)

Like I said, Iv'e done that
I can see my Workgroup (called WORKGROUP), but not my printer :(

---

### Post by Morbius1 on 2011-03-06
Once you do what David D. suggested find out if Win7 is getting in the way of translating it's host name to an ip address by accessing the Windows printer directly by ip address:

System > Administration > Printing > Add > Network Printer > Windows Printer via SAMBA > DO NOT BROWSE

Just fill in the empty box with:
```
 192.168.0.100/printer-mame-on-Win7
```

changing 192.168.0.100 with the ip address of the windows box.

---

### Post by syntr on 2011-03-06
> **Morbius1 said:**
> Once you do what David D. suggested find out if Win7 is getting in the way of translating it's host name to an ip address by accessing the Windows printer directly by ip address:

System > Administration > Printing > Add > Network Printer > Windows Printer via SAMBA > DO NOT BROWSE

Just fill in the empty box with:
```
 192.168.0.100/printer-mame-on-Win7
```

changing 192.168.0.100 with the ip address of the windows box.
well, this got me closer
[IMG]http://i.imgur.com/yaVCh.png[/IMG]
But printing a test page does nothing :(

---

### Post by syntr on 2011-03-06
Whoops, I put down the wrong model
so I deleted it and started over
It still does nothing though, it says it's been printed but the physical printer doesn't even move
[IMG]http://i.imgur.com/Gn6BA.png[/IMG]

---

### Post by syntr on 2011-03-06
Trying hpcups does nothing as well
Never do I have more issues with Linux then when I try to get something to print

---

### Post by syntr on 2011-03-06
Well, after clearing my printer queue on Windows and starting over, now the printer is stuck on "Printing..." but still does nothing. Making progress, I guess

---

### Post by syntr on 2011-03-06
[IMG]http://i.imgur.com/Mgkbn.png[/IMG]
:confused:

---

### Post by syntr on 2011-03-06
Now my printer won't work from either computer. :(
Just gets stuck at that queue...

---

### Post by syntr on 2011-03-06
For anyone in the future that might read this, here's how you fix your printer queue:

Save this as a .bat file and run it as administrator: (from [http://forums.majorgeeks.com/showthread.php?t=156367](http://forums.majorgeeks.com/showthread.php?t=156367))
@echo off
echo.
echo Purging the print queue . . .
net stop Spooler
echo Deleting all print jobs . . .
ping localhost -n 4 > nul
del /q %SystemRoot%\system32\spool\printers\*.*
net start Spooler
echo Done!
ping localhost -n 4 > nul

As for actually getting network printing to work, I wasted a whole afternoon on this nonsense :( Best to print locally or from Windows 7 homegroups

---

### Post by syntr on 2011-03-06
SCRATCH THAT! :D :D :D :D
JUST as I was about to give up, I got it to work by disabling bidirectional support! 

Go to devices & printers, right click your printer. Choose "Printer Properties", Ports tab. Uncheck enable bidirectional support!

lol just when I start to hate Ubuntu it does something to make me love it again :D

[IMG]http://i.imgur.com/oxtjq.jpg[/IMG]

---

