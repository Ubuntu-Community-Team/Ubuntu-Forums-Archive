---
title: "Windows printer share to Ubuntu via Samba"
date: 2007-01-03
forum: Networking &amp; Wireless
---

### Post by anthropop on 2007-01-03
I have an existing Windows network that I am converting over to Linux in stages.  Right now I have two windows PCs and a Ubuntu Dapper Drake 6.06 linux laptop.  I need to get the laptop to be able to print to a Windows network shared printer that is directly attached to a Windows PC (XP).  I have setup samba on the linux box and can browse files on the Windows machines and see the network shared printer.  I can even attempt to install a network driver for the printer and send a test page to the printer, but that is as good as it gets!  

The problem is that my exact printer (Brother MFC 7420, USB connection - printer has parallel option as well) does not showup as a supported printer in the list of printers (I assume this is via a CUPS driver in linux, but I'm using the Ubuntu printer GUI).  So I tried some of the other drivers in the same range but they all fail (they connect to the printer but junk comes out or blank pages).  I also searched for "PPD" files on my windows box that has the Brother drivers and found one that was for WinXP 7420.  I brought it over to the linux box, tried to load it, but there was an error message about "PPD Adobe header file not found."  Other PPD files were accepted but that doesn't help me too much.

Talking to people at work there are several ideas, but no clear solution:
1) Load Ghostscript on the Windows box to act as a postscript print server and use a generic postscript driver on Linux.
2) Go to Linux on the Windows box, but I can't make that leap yet - it is a longer path. I have considered dual booting Linux to start the process, but that is a big change with all the Windows software currently running.
3) Connect the printer to the Linux box.  The problem with this option is that the laptop is not always on or around!
4) Add an external ethernet print server (ie Brother NC2100P 10/100 BaseT Ethernet External Print Server).  Not sure if this would solve it.

I have not seen anything related to this in the forums.  Most people are going to a Linux print server.  

If I go with the external print server, what is the setup under Ubutu?  Do I have the same problem with the PPD files for this printer or is there a generic postscript driver that I can use?

Thanks for any feedback and ideas.

- Daniel

---

### Post by dannyboy79 on 2007-01-03
you need to use the cups printer setup, not the gnome printer gui. using the cups printer setup will allow you to utilize the drivers available here; [http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html)
you need to enable admin rights to the cups web browser setup location, I forget how to do this but i know it's in gogle somewhere since I did it. i wish I could be more specific in helping you but I know it can be. good luck.

i even did a little gogle search for ya:
To "solve" the root/password access on localhost:631
Edit the /etc/group file.
Add cupsys to the shadow line.

Restart cups /etc/init.d/cupsys restart

so first do the above, then to access the cups web interface, type in gksudo firefox in a terminal and type in
localhost:631
and you should be on your way to adding your printer to cups which will allow you to print to it.

---

### Post by anthropop on 2007-01-03
I will give that a try this evening!  I guess I assumed that the Gnome print GUI would have CUPS underneath it as that appears to be the preferred standard for printer support, but you never know.

Thanks for the tip.

- Daniel

---

### Post by dannyboy79 on 2007-01-03
well you could always try to use the drivers at the website I pointed out with the normal gnome-cups-manger, it's worth a try.

---

### Post by anthropop on 2007-01-03
Well it works...kind of.  I did the install according to the Brother web site and that was smooth.  Also the configuration screen through the browser was easy, I didn't run into any problems or need a workaround for permissions.  I can now print, but only if the app doesn't crash and only some of the pages graphics shows up!  It printed a test page perfectly with grey-scale transitions, however.  It also prints text just fine.  On some web pages it prints some graphics (greyscale) and then not other graphics on the same page.  Also, it crashed Mozilla Firefox on the page this thread is on.  I went to my windows computer and printed to the same printer without a problem, also from Mozilla Firefox for windows.

I noted that print preview shows just what it will print, so I checked my settings and clicked on "print background" and that did nothing at all.  Any ideas?

- Daniel

---

### Post by anthropop on 2007-01-03
Ok. now it started playing with my head and now works for all graphics and for all posts.  I'll see if it continues to work and hope it was a startup glitch.  I was starting to wonder if it was a recursive artificial intelligence problem where it was recursing over the installation instructions of the post that got it working! :p  I thought it might start saying, "I'm sorry Dave, now I can't do that Dave."  (I hope I'm not dating myself with that reference).

---

### Post by dannyboy79 on 2007-01-03
glad you got it working! yeah, you only need to do that permissions thing with the cups web interface otherwise if you use gnome-cups manager you should be ok. glad you got it working! just as an fyi, all I did was gogle your printer model and stated cups and I found the answer that quickly! you can always count on gogle!

---

### Post by anthropop on 2007-01-04
There is one other issue.  My internet browsing is much slower on the laptop than on my windows desktop.  Now granted my laptop is 8 years old vs. my desktop a couple of years, so CPU wise there is no comparison.  Still, what bothers me is that the measured download speed at PCPitstop is the same on both machines, yet opening a page takes over twice as long.  Both machines are recorded at 1400 kb/s.  

One thing I noticed was that name resolution appears to take forever on the laptop.  Is there a way to measure the name resolution time?  I don't really know if this is just a symptom of something else.  I did try another network card but it get the same 1400 kb/s and takes just as long to download a page.

Is it possible that the download test at PCPitstop works as fast on the two machines only because it is not going to disk, but only to the screen?  Maybe it is just the sluggishness of the laptop?

I am pretty sure I have a valid name server address that goes to my ISP.  If not I would expect name resolution to fail entirely.

---

### Post by anthropop on 2007-01-04
From talking to other people this may in fact be due to the graphics rendering speed of the laptop.  It is an old machine after all.

---

### Post by nevernamed on 2007-01-16
I am having the exact same problem. As the fellow above. Will somebody please help?
Thanks.

---

