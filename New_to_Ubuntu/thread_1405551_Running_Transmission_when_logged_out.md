---
title: "Running Transmission when logged out"
date: 2010-02-12
forum: New to Ubuntu
---

### Post by SquALeD on 2010-02-12
Hi people, Linux/Ubuntu newbie here..

Been trying out 904 for a few weeks now and am slowly getting the hang of things - sloowly...

Set up Samba for shares, no probs there. Runs at bootup and when logged out, just what I want

I want Transmision to do the same. Ive got the T Daemon up and running fine but it wont stay active when I log out or run automatically at boot up with no user login.

Whats the best way to achieve this?

TIA

Sq

---

### Post by thatguruguy on 2010-02-12
Go to System --> Preferences --> Startup Applications.  Click "Add". A dialog will pop up; put "Transmission" (without the quotation marks) in the "Name" box and "transmission" (no capitalization, and don't incluce the quotation marks) in the "Command" box. Put whatever you want in the "Comment" section.  When done, hit "OK" and make sure the check box next to Transmission is checked in the startup applications listing.

Transmission will start automatically every time ubuntu starts up, unless you remove the check in the checkbox.

---

### Post by SquALeD on 2010-02-13
Hi mate, thanks loads for the reply.

I think I might have worded my question wrongly. I want Transmission to run unattended when im logged out and of course run at start up which your advice sorted out.

Can I set it up this way? .... Access the GUI to make setting adjustments etc then close the gui leaving Transmission running in the background so to speak? and have it keep running when I log out? I think this would be running it headless yes?

Ive got a feeling im mixing the gui and the cli versions up a bit....could you tell me the best way to set up Transmission.

Another prob is that the webui works fine but doesnt let me load torrents at all lol Any idea about this?

Sorry for the list of Qs but im really a newb when it comes to Ubuntu

TIA again

Sq

---

### Post by SquALeD on 2010-02-14
Hi there, been doing some research and it looks like Ive got the Transmission Daemon running ok. Can edit the settings.json file and the web interface is accessible when Im logged out which is great.

Only prob now is that the web interface wont let me upload any torrents - no errors no nothing it just sits there doing nothing.

Anybody come up against this prob before?

Cheers people 

Sq

---

### Post by SquALeD on 2010-02-15
S ok, all fixed. Transmission is in the bin and has been replaced by deluge - miles better, almost like uTorrent.

Cheers anyway..

---

