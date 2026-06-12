---
title: "Unusual SAMBA problem w/ windows printing"
date: 2007-02-15
forum: Networking &amp; Wireless
---

### Post by stiv2k on 2007-02-15
Okay let me describe my setup as follows.  I have a windows XP PC with a printer attached to it.  My ubuntu (edgy) installation is on my laptop, on which I have setup SAMBA using this howto: [http://ubuntuforums.org/showthread.php?t=202605]("http://ubuntuforums.org/showthread.php?t=202605")

Everything appears to work fine, I can easily transfer files between machines.  However, when it comes to printing to the printer from my laptop, problems occur.  Upon clicking the "Print" button on any browser/document/application, the file shows up as "Remote Downlevel Document" on the windows machine in the printer jobs.  So far everything appears to be working fine.  Under the "Size" column, it gives some arbitrary fraction, such as 64.0 KB/ 1.23 MB, indicating that perhaps the entire document has not been spooled to the machine/printer yet.  From this point on, my printer will then proceed to make unusual noises, and hang.  Nothing prints, nothing.

I have searched these forums thoroughly, along with several other SAMBA resources and have yet to come up with a solution.  If anyone here can help, it would be greatly appreciated

The printer is an HP PSC 1315xi using the HPIJS driver attached to the PC via USB cable

---

### Post by Floppyjoe on 2007-02-15
The first thing I would check is if it prints with the windows machine. If not the ink cartridge may be empty. This happened to me not far back but your problem may be different.

---

### Post by stiv2k on 2007-02-15
I haven't tried from this specific laptop, but it will print from other windows laptops on my network if that helps...

---

### Post by stiv2k on 2007-02-16
anyone??

---

### Post by manicmonk on 2007-03-02
I have an exactly similar problem with a HP Deskjet 3847 printer. HPIJS driver.

It is connected to a Win98 machine via USB, shared and prints OK from a WinXP system on the same network (and locally, of course).

The Ubuntu (6.1) machine sees it as a Samba printer and _seems_ to print to it OK. On the Win98 end, the job appears in the spool queue and the printer makes a few noises and then just sits there. Nothing has printed, the queue is now frozen, and nothing (except a reboot) will clear it.

...sounds similar.

I thought it might be printer driver parameters, but nothing I have tried has worked.

Ideas?

---

### Post by JohnPhys on 2007-03-18
Having the same issues here...

---

### Post by dmizer on 2007-03-18
try using cups instead of samba, it's far more reliable.

you'll need to set up your printer in windows as a network printer. select the option labeled as "Connect to a printer on the internet or on your intranet", and enter the url of your printer.  the url will look something like this:

```
http://u.bun.tu.ip[COLOR="Red"]:631/printers[/COLOR]/printername
```
where u.bun.tu.ip is the ip addess of the computer with the attached printer, and "printername" is the name you gave the printer (check this by browsing to [http://localhost:631/printers](http://localhost:631/printers)).  it is necessary to include ":631/printers/" section just as it appears in red, so don't change that part.

---

### Post by drmbogo on 2007-04-04
Ok, I've searched the forums ad nauseum, and was a bit surprised to find that someone else (several someone's in fact :) ) is having the same problem. I am noticing a common thread here: we all have hp printers connected to a windoze box, and are using HPIJS. Could this be an HP issue? I too can see the windoze 'puters from the linux box, and have no problem sharing files, BUT when I attempt to print, it seems that the printer itself locks up, that is: it (the printer) starts making the usual "here comes your paper" sounds, then hangs. The document "Remote Downlevel Document" resists being deleted, requiring a reboot of the server (and, incedentally, of the printer as well).
All this being said, I am thoroughly enjoying goofing around w/ my new linux box, and , dare I say it, LEARNING the command line! Also, the community surrounding linux is a wonderful thing. I've already gleaned an enormous wealth of info, and solved a lot of  issues by reading posts here and on other linux-oriented sites. For that I thank you all!

I noticed there hasn't been any reply to this thread in a few weeks; Anyone have any updates?
Thanks much,
dB

---

### Post by drmbogo on 2007-04-05
I've recently re-tried using CUPS to add the printer, and after I figured out the proper url, I get exactly the same response from the printer: attempts to print then hangs...

Anyone have any ideas?
Thanks
dB

---

### Post by mozzwald on 2007-04-11
I think I've found the answer.  I'm using Kubuntu and have been trying for weeks to get this working at home from my laptop.  My XP machine would show the "Remote Downlevel Document" in the spool and my PSC1400 would try to print, but lock the spooler.  Doing a search for "'remote downlevel document' hp linux" resulted in -->[this]("http://www.linuxquestions.org/linux/answers/Hardware/Troubleshooting_printing_problems_from_SuSE_10_0_to_HP_PSC1350_shared_from_Windows")<-- page at linuxquestions.org. 

It described our symptoms, so I tried it. Now I can print all day long.  Just note that your filenames may be different depending on what version of driver and printer you have.

Happy printing!

---

### Post by Staff Monkey on 2007-04-17
Mozzwald's recommendation worked for me (using an HP 4315v All-in-one connected to a Win XP machine on local intranet), **BUT** I didn't need to delete the registry items listed in Step 3.  I did have to break the association with Shockwave as described in the article.

I believe the primary issue with HP printers that won't print (even tho a "Remote Downlevel Document" appears in the printer queue) is the two files that are written to the Spooler folder on the Windows machine.  

I recommend that this be added as a HOWTO for printing to a Windows machine.

Thanks for the link to those great instructions!

---

