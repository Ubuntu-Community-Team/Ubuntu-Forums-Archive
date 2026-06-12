---
title: "HELP!  Remote Access Issues &amp; Questions"
date: 2008-06-06
forum: Networking &amp; Wireless
---

### Post by slowtrain on 2008-06-06
Hi folks:  I need to use my desktop remotely while I'm out of town for a month.  Have a number of issues and questions with regard to remote access and conserving energy.  Any thoughts would be helpful!

Remote access:

I've got VNC (remote desktop) set up to work w/ an SSH tunnel.  Was wondering, though, whether there's a more efficient way to access the desktop using the ability of X11 to display windows remotely in another X11-capable system?  Is this any better than VNC?  If so, why does Ubuntu feature remote desktop?

Is it advisable to use VNC to update software with Synaptic on my remote desktop?  I guess I should avoid updating SSH (doing this killed my remote access to the desktop once already), but what about other software?

VNC seems to unlock the screen on the computer itself, which raises security issues.  Is there any way around this?

Energy conservation:

It would be ideal if I could put the machine to sleep or hibernate and wake it as needed (Wake on LAN?), but is there any way to do this?  One alternative might be to instruct the BIOS (Phoenix - AwardBIOS CMOS Setup Utility) to wake up the machine at the same time every day and then turn it off remotely if not needed.  Problem is that I've tried the following settings in the BIOS but the machine does not wake:

Power Management Setup

Resume by Alarm [Enabled]
Date(ofMonth) Alarm [0]
Time(hh:mm:ss) Alarm  9:0:0
  <entered as 09:00:00, but converts to 9:0:0>

Thanks in advance!

---

