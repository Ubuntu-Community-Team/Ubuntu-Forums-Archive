---
title: "Printer is driving me nuts!"
date: 2011-08-09
forum: New to Ubuntu
---

### Post by weezyrider on 2011-08-09
Ubuntu 10.10
HP1300 laser printer

Is there another printer controller app you can download other than the one that is in the administrator menu? 
I tried to print in landscape yesterday, and could find no settings to do so. I checked the paper sizes, everything else on the menu of the app that controls printers, and there was no way to change from portrait. I assume that this is Ubuntu (10.10) itself, as the Canon inkjet also had no way to change paper orientation. 

The printer in question is a HP1300 laser. 

I needed to print a return shipping label, and it needed to be 2 page landscape. Chrome browser is useless when trying to print, and Opera would show the print preview, but no way to change preferences. The return label was sent via email so it had to print from the browser. I finally had to hook the laptop to the HP printer to get the format I needed.

All the printers work, but not having the settings I do in windows is a PAIN!

---

### Post by ajgreeny on 2011-08-09
Try installing and using **hplip-gui, **if you have not already done so to give you a good toolbox where you can make those changes for most printers.  The HP Laserjet 1300 is supported at least partly by hplip, so the hplip-gui package should help.

---

### Post by Daveth on 2011-08-09
Post #7 here
[HTML]http://ubuntuforums.org/showthread.php?t=1518337[/HTML]

alleges a solution for the hp1300 by switching to cups/gutenprint drivers.The alternative solution in post #8 crashes and burns in the link, so no joy there.

---

### Post by weezyrider on 2011-08-09
Exactly what is Cups? I see a whole list of Cups items, and they make no sense to me. Either the printer used HCL or it didn't. If you wanted to proof for anything on that type of printer it was postscript and you had to use ripware if you used an inkjet.

---

### Post by JKyleOKC on 2011-08-09
CUPS is the Common Unix Printing System, and it's installed by default in every version of Ubuntu that I've ever used. You access it through your browser, with "http://localhost:631" and that gets you its home page with several tabs, one of which is "Printers." From that tab, you can select "Add Printer" to get a wizard that will walk you through the configuration process. It was quite painless for my HP 1320 Series, and offered several drivers for it to choose from. I took the one marked "recommended" and it works much better than the printer did under Windows using the HPLIP package...

---

### Post by dFlyer on 2011-08-09
From a terminal:

sudo apt-get install hplip-gui

---

### Post by weezyrider on 2011-08-10
> **JKyleOKC said:**
> CUPS is the Common Unix Printing System, and it's installed by default in every version of Ubuntu that I've ever used. You access it through your browser, with &quot;[http://localhost:631&quot;](http://localhost:631&quot;) and that gets you its home page with several tabs, one of which is &quot;Printers.&quot; From that tab, you can select &quot;Add Printer&quot; to get a wizard that will walk you through the configuration process. It was quite painless for my HP 1320 Series, and offered several drivers for it to choose from. I took the one marked &quot;recommended&quot; and it works much better than the printer did under Windows using the HPLIP package...

  How do you figure out which one you want? That's what I can't do. I have the HP 1300 laser, and a Canon 6000 Pixma inkjet.  I'm used to the choice of postscript or not.

---

### Post by weezyrider on 2011-08-10
> **dFlyer said:**
> From a terminal:

sudo apt-get install hplip-gui

 I'll try that. Thanks

---

### Post by JKyleOKC on 2011-08-10
> **weezyrider said:**
> How do you figure out which one you want? That's what I can't do. I have the HP 1300 laser, and a Canon 6000 Pixma inkjet.  I'm used to the choice of postscript or not.As the CUPS install wizard goes through its script, you'll reach a page where you first select the manufacturer and then the specific model of your printer. It then offers the driver list, already pointing to those for that printer. As I recall, there are three drivers offered for the HP 1320 Series; I selected the one marked as "recommended" and it's been just fine.

Almost all Linux print drivers handle PostScript as their normal condition, and make it invisible to the user. On occasion, while configuring my virtual Windows systems running as guests under Xubuntu, when the HP 1320 wasn't offered as a choice because of the age of the Windows system (i.e. Windows 2000 Pro), I've selected arbitrary postscript drivers from other manufacturers, and they have worked properly!

With CUPS, you can install both printers, and then have a choice at printing time. I have an Epson all-in-one configured also, for printing in color. Using HPLIP won't support the Canon printer at all.

---

### Post by weezyrider on 2011-08-10
I just found the CUPS printer, but it still doesn't give me a dialog box for setting up a print job! All I get is the default which I don't want at times!
There's times I want to set up 4 up etc, and Windows HP printer dialog box allows me to do that.

---

### Post by JKyleOKC on 2011-08-10
Have you tried [http://localhost:631](http://localhost:631) yet? On its "Printers" tab you can select the printer, and from its opening window you can set up just about anything that the printer can provide.

CUPS is now owned by Apple and as a result much of its interface tries to be Mac-like, but it's well-integrated with Ubuntu (and all other Linux distros) so gives you near total control.

However, if HPLIP works well for you, you don't really have to use CUPS. In fact, I think you can probably have them both installed and use whichever one you want for a given print job! Since I'm networked here and need to use both printers from all the stations on my little LAN, I couldn't make HPLIP work for my needs although I did use it when the printer was physically on a Win98 box and accessed through Samba. When I switched over to Xubuntu four years ago, though, I couldn't get it to work through the LAN so went over to CUPS...

---

### Post by weezyrider on 2011-08-10
This is what I get when I follow your instructions:
All the rest of the instructions are gibberish as far as I'm concerned. It doesn't say outright portrait, landscape, booklet.

I really need a dialog box like Windows print.

---

### Post by dFlyer on 2011-08-10
hplip-gui should provide you with the hp toolbox to setup up your prints.

---

### Post by weezyrider on 2011-08-10
This is what I want. Thunderbird has it, Opera and Chrome don't. I'm not using FF due to a hitch with adobe Flash

Windows print also has something similar

---

### Post by weezyrider on 2011-08-10
I installed that HPLIP, now how do I get it to recognize the printer? The printer is using both USB (I use that for the laptop) and LPT1 which is used on the desktop where Ubuntu is. The printer simply won't find the LPT1 port, but it's printing from that normally.

---

### Post by weezyrider on 2011-08-10
The HPLIP just showed up in the print dialog box. It is working. Thank you.

Now does Canon have one?

---

### Post by weezyrider on 2011-08-10
Something very interesting. HP will not work right with Opera. You can't select Landscape. With Chrome, you can. This all started with a return UPS label. I needed landscape printing. 
Just for a test, the label did print right out of Chrome.

---

