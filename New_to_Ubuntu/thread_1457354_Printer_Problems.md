---
title: "Printer Problems"
date: 2010-04-18
forum: New to Ubuntu
---

### Post by doninsa on 2010-04-18
Very new to Ubuntu.  Managed to connect to a shared printer on my Windows XP machine, but every time I try to print from Ubuntu I get a request to Authenticate.  Tried entering my Ubuntu password, but no help.  The Windows machine is not password protected.  Here's the error message I'm getting from Ubuntu
Printer State: Idle - ERRDOS - ERRbadaccess (Invalid open mode.) opening remote spool Test Page.
Other specifics on the Settings are:
Description: HP Deskjet 820C
Location: Den Computer
Device URL: smb://192.168.1.2/Printer3
Make and Model: HP Deskjet 820C Foomatic/pnm2ppa (recommended)

I feel like I'm almost there, but the printer is still not moving.  Any help would be appreciated.

I'm using Ubuntu 10.04 LTS beta, just couldn't wait.

Don

---

### Post by cogier on 2010-04-18
Why not run the printer from your Ubuntu computer.

Go to the Software Centre and load up HPLIP and follow the instructions.

I am not sure but you may need to add a password to Windows so that you can access the printer from Ubuntu if you still want to do the printing that way.

---

### Post by doninsa on 2010-04-18
> **cogier said:**
> Why not run the printer from your Ubuntu computer.

Go to the Software Centre and load up HPLIP and follow the instructions.

I am not sure but you may need to add a password to Windows so that you can access the printer from Ubuntu if you still want to do the printing that way.


Hello and thanks for the reply.

  Windows XP in the den is still my primary computer so moving the printer to the Ubuntu computer wasn't an option.  Good news, however, I fixed the problem by correcting the printer setup to point to the correct printer.  Not sure why Ubuntu found Printer3 and none of the others when several others existed, but Printer3 was a Quicken PDF printer.  And why this resulted in a request for a password is still a puzzle.  But when I checked my work and found that the printer I wanted had another name, I corrected the name in Ubuntu Printer setup and it worked without asking for a password.

---

### Post by lwvmobile on 2010-04-18
I'm wondering if Ubuntu is asking for the authentication for connecting to the XP machine, all though it is not password protected locally, I have encountered where when you do file sharing and shared printers from XP to Linux, it will still want you to authenticate.

Is it asking for a username and password, or just a password.

If its asking for both, try your XP's username and a blank password.

Otherwise, you may need to tweak the settings for printer sharing in XP to allow Everyone to connect, or maybe try adding a new user to your XP machine that matches the username and password on your linux machine and make sure the new user has permissions to connect to your shared printer.

Good Luck.

---

### Post by doninsa on 2010-04-19
> **lwvmobile said:**
> I'm wondering if Ubuntu is asking for the authentication for connecting to the XP machine, all though it is not password protected locally, I have encountered where when you do file sharing and shared printers from XP to Linux, it will still want you to authenticate.

Is it asking for a username and password, or just a password.

If its asking for both, try your XP's username and a blank password.

Otherwise, you may need to tweak the settings for printer sharing in XP to allow Everyone to connect, or maybe try adding a new user to your XP machine that matches the username and password on your linux machine and make sure the new user has permissions to connect to your shared printer.

Good Luck.

It was asking for my name and password and the name was already filled in with my Ubuntu login name.  But I'm pretty sure this wasn't really a password problem to begin with.

The problem was that I was trying to access a pdf file printer created by another program.  When doing initial setup, Ubuntu found this pdf printer and not the HP printer that I intended to use.  After I modified Ubuntu printer setup to point to the correct printer it worked without requesting a password.

---

