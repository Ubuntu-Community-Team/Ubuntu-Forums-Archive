---
title: "printer driver installs"
date: 2011-01-22
forum: New to Ubuntu
---

### Post by Robing Goodfellow on 2011-01-22
Running 10.10 on an HP G62, have nearly made a complete switch to Ubuntu from Windoze.  Really, the only thing I still keep windoze on the machine for is printing.  I have a Lexmark Pro205 wireless at home and an HP Deskjet 1000 (J100 iirc) at work.

I have gone into System/Administration/Printing and added them both, using the recommended packages (neither of which are for the specific printers).  When I go to print the test page, nothing happens.  Okay, kind of expected.  

I did some web searching, including in the forums, primarily for the Lexmark, and it would seem that there just is / was no support or way to make it work with the 64 bit OS, or at least not a few months ago.

I have found, through a Lexmark page, a recommended Debian tar.gz for the printer, which I downloaded and extracted.  It is sitting in the /Download file as we speak.

1.  How do I go about installing it? Or is it still the case that its just not going to work?

2.  Any recommendations on the HP?

3.  If neither of these are an option, what printers ARE compatible with Ubuntu?  I'm perfectly willing to buy another printer if I have to, though I would rather not.

regards, Robin

---

### Post by Daveth on 2011-01-22
worth checking this site out

[HTML]http://www.openprinting.org/printers/[/HTML]

---

### Post by walt.smith1960 on 2011-01-22
> **Robing Goodfellow said:**
> Running 10.10 on an HP G62, have nearly made a complete switch to Ubuntu from Windoze.  Really, the only thing I still keep windoze on the machine for is printing.  I have a Lexmark Pro205 wireless at home and an HP Deskjet 1000 (J100 iirc) at work.

I have gone into System/Administration/Printing and added them both, using the recommended packages (neither of which are for the specific printers).  When I go to print the test page, nothing happens.  Okay, kind of expected.  

I did some web searching, including in the forums, primarily for the Lexmark, and it would seem that there just is / was no support or way to make it work with the 64 bit OS, or at least not a few months ago.

I have found, through a Lexmark page, a recommended Debian tar.gz for the printer, which I downloaded and extracted.  It is sitting in the /Download file as we speak.

1.  How do I go about installing it? Or is it still the case that its just not going to work?

2.  Any recommendations on the HP?

3.  If neither of these are an option, what printers ARE compatible with Ubuntu?  I'm perfectly willing to buy another printer if I have to, though I would rather not.

regards, Robin

Once you've extracted the .deb file, what happens if you navigate to it in Nautilus then right click on it? Does it ask if you want to open with Ubuntu Software Center or Gdebi? You'll need to do this from an account with administrative privileges.  You're fortunate to have a Lexmark machine that has Linux support, many Lexmark machines are categorized as "paperweights".  I'm surprised the HP didn't "just work".  I assume you've done the system -> administration ->printing -> add printer routine?

You may have an issue with 64 bit.  I have a Brother printer where I can use the GUI install with 32 bit OSs.  The GUI doesn't work with 64 bit, I get a "this software is not the right version for this machine" type message.  I have to do a command line install with the --force switch as instructed by Brother.

---

### Post by lifeboy on 2011-06-07
Have you managed to solve this?  I had a similar problem and found that Lexmark don't take the presence of apparmour into account during installation.  You have to manually tell apparmour that it must allow the lexmark drivers to run.

The thread describing the fix is over here: 
[http://lifeboysays.giesler.za.net/2011/06/07/ubuntu-lexmark-pro-200-series-printing/](http://lifeboysays.giesler.za.net/2011/06/07/ubuntu-lexmark-pro-200-series-printing/)

Hope that helps

---

### Post by electronforce on 2011-06-07
[http://localhost:631](http://localhost:631) to go to Cups server - Try this to see if you can make headway. From your browser on the Ubuntu machine.

---

### Post by collisionystm on 2011-06-07
> **Robing Goodfellow said:**
> Running 10.10 on an HP G62, have nearly made a complete switch to Ubuntu from Windoze.  Really, the only thing I still keep windoze on the machine for is printing.  I have a Lexmark Pro205 wireless at home and an HP Deskjet 1000 (J100 iirc) at work.

I have gone into System/Administration/Printing and added them both, using the recommended packages (neither of which are for the specific printers).  When I go to print the test page, nothing happens.  Okay, kind of expected.  

I did some web searching, including in the forums, primarily for the Lexmark, and it would seem that there just is / was no support or way to make it work with the 64 bit OS, or at least not a few months ago.

I have found, through a Lexmark page, a recommended Debian tar.gz for the printer, which I downloaded and extracted.  It is sitting in the /Download file as we speak.

1.  How do I go about installing it? Or is it still the case that its just not going to work?

2.  Any recommendations on the HP?

3.  If neither of these are an option, what printers ARE compatible with Ubuntu?  I'm perfectly willing to buy another printer if I have to, though I would rather not.

regards, Robin

For the HP install HPLIP from the software center.

For your Lexmark, use a generic PCL5 driver. I have a lexmark x463de and It just uses generic PCL just fine.

---

### Post by Dondermans on 2011-06-07
HP does quite a good job on Linux support in my opinion. Check out their site for detailed instructions on using HP printers in Linux:

[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

---

